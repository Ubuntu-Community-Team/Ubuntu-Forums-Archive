---
title: "Wubi wont find ISO or download one"
date: 2008-11-17
forum: General Help
---

### Post by th3 pla6u3 on 2008-11-17
Well, I am trying to install Ubuntu with Wubi and no luck...
I have the iso in the same folder as seen in attached screen shot, and I have also coded the log... someone help? lol


```
============ Installer ============
PLUGINSDIR=C:\Users\Patty\AppData\Local\Temp\nso5964.tmp
detect_all
Parsing cmdline "C:\Users\Patty\Desktop\wubi.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=1014 MB
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD E:
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
No CD found
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive D:\ubuntu
AlreadyInstalled=false OldInstallationDrive= InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1720; Volume name ; Max #/chars in vol name 3529992; Volume Serial # -1262275503; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem D:
Drive & Path name 1720; Volume name RECOVERY; Max #/chars in vol name 3529996; Volume Serial # 1215914170; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 3000304; Volume name ; Max #/chars in vol name 69; Volume Serial # -1262275503; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = c:
FreeSpace in c: is 162335
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
GMT=-6
Country=US
Locale=en_US.UTF-8
TimeZone=America/Chicago
Domain=localdomain
HostName=Patty-PC
ComputerName=PATTY-PC
EnvUsername=Patty
UserDomain=Patty-PC
UserInfoName=Patty
UserProfileFolder=C:\Users\Patty
UserProfileName=Patty 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1786; Volume name ; Max #/chars in vol name 3606328; Volume Serial # -1262275503; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
IsValidFileSystem D:
Drive & Path name 1786; Volume name RECOVERY; Max #/chars in vol name 3606332; Volume Serial # 1215914170; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
Skipping drive D:, not enough free space 4538 <= 5000
Drive list = C:
ChangeInstallationDrive to c:
ChangeInstallationSize to 15
PopulateDistroList
DetectIso
      IsValidIso ispoath=C:\Users\Patty\Desktop\ubuntu-8.10-desktop-i386.iso
      ExtractIsoInfo
      C:\Users\Patty\AppData\Local\Temp\nso5964.tmp\7z.exe e -y -i!.disk\info -oC:\Users\Patty\AppData\Local\Temp C:\Users\Patty\Desktop\ubuntu-8.10-desktop-i386.iso
C:\Users\Patty\AppData\Local\Temp\nso5964.tmp\7z error: error
      IsValid 
no cdinfo
CDInfo cleared
      IsValidIso ispoath=C:\Users\Patty\Desktop\ubuntu-8.10-desktop-i386.iso
      ExtractIsoInfo
      C:\Users\Patty\AppData\Local\Temp\nso5964.tmp\7z.exe e -y -i!.disk\info -oC:\Users\Patty\AppData\Local\Temp C:\Users\Patty\Desktop\ubuntu-8.10-desktop-i386.iso
C:\Users\Patty\AppData\Local\Temp\nso5964.tmp\7z error: error
      IsValid 
no cdinfo
CDInfo cleared
AddDistroToList Ubuntu-i386
AddDistroToList Ubuntu-amd64
AddDistroToList Kubuntu-i386
AddDistroToList Kubuntu-amd64
AddDistroToList Xubuntu-i386
AddDistroToList Xubuntu-amd64
AddDistroToList Mythbuntu-i386
AddDistroToList Mythbuntu-amd64
DistroList = Ubuntu|Kubuntu|Xubuntu|Mythbuntu
PopulateLanguageListBox
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro= cdarch= arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
ChangeInstallationSize to 30
LeaveMainPage
Locale=en_US.UTF-8
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro= cdarch= arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
CreateInstallationFolders
MakeUninstall
Created C:\ubuntu\Uninstall-Ubuntu.exe
Created reg key HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
CopyDistFolders
GetIso
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD E:
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
No CD found
DetectIso
      IsValidIso ispoath=C:\Users\Patty\Desktop\ubuntu-8.10-desktop-i386.iso
      ExtractIsoInfo
      C:\Users\Patty\AppData\Local\Temp\nso5964.tmp\7z.exe e -y -i!.disk\info -oC:\Users\Patty\AppData\Local\Temp C:\Users\Patty\Desktop\ubuntu-8.10-desktop-i386.iso
C:\Users\Patty\AppData\Local\Temp\nso5964.tmp\7z error: error
      IsValid 
no cdinfo
CDInfo cleared
      IsValidIso ispoath=C:\Users\Patty\Desktop\ubuntu-8.10-desktop-i386.iso
      ExtractIsoInfo
      C:\Users\Patty\AppData\Local\Temp\nso5964.tmp\7z.exe e -y -i!.disk\info -oC:\Users\Patty\AppData\Local\Temp C:\Users\Patty\Desktop\ubuntu-8.10-desktop-i386.iso
C:\Users\Patty\AppData\Local\Temp\nso5964.tmp\7z error: error
      IsValid 
no cdinfo
CDInfo cleared
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro= cdarch= arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
Checking/Downloading Ubuntu-8.10
retrieve_partial_files
check_internet_connection
Dialer online
connected
Trying remote metalink: http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.metalink
get_md5 http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.metalink
Downloading: trymefirst= url=http://releases.ubuntu.com/8.10/MD5SUMS-metalink.gpg md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink.gpg
Downloading: trymefirst= url=http://releases.ubuntu.com/8.10/MD5SUMS-metalink md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink
      Verifying signature C:\ubuntu\install\MD5SUMS-metalink.asc
error; ; ; ; 
Error verifying signature: error
Trying remote metalink2: http://cdimage.ubuntu.com/daily-live/current/intrepid-desktop-amd64.metalink
get_md5 http://cdimage.ubuntu.com/daily-live/current/intrepid-desktop-amd64.metalink
Downloading: trymefirst= url=http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink.gpg md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink.gpg
Downloading: trymefirst= url=http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink
      Verifying signature C:\ubuntu\install\MD5SUMS-metalink.asc
error; ; ; ; 
Error verifying signature: error

```

[[IMG]http://img261.imageshack.us/img261/4010/ssma6.th.jpg[/IMG]](http://img261.imageshack.us/my.php?image=ssma6.jpg)[[IMG]http://img261.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

---

### Post by Yownanymous on 2008-11-17
Because I don't understand a word of code, what distro were you trying to get?

---

### Post by th3 pla6u3 on 2008-11-17
Ubuntu

---

### Post by th3 pla6u3 on 2008-11-17
anyone?

---

### Post by abn91c on 2008-11-17
that error is usually your firewall blocking the install. Also it is best to do a wired connection,not a wireless to download the file.

---

### Post by th3 pla6u3 on 2008-11-17
> **abn91c said:**
> that error is usually your firewall blocking the install. Also it is best to do a wired connection,not a wireless to download the file.

I am not running a firewall, unless the built in Vista POS is blocking it... o.O 
*just added an exception to the Vista Firewall, and it still did not work.

And I am on a wired connection.

---

### Post by abn91c on 2008-11-17
from what i see in that log ubuntu needs to be in c:\ubuntu
the folder for the iso will be in c:\ubuntu\install

---

### Post by th3 pla6u3 on 2008-11-17
Na, just tried both with the 32 bit, and thet 64 bit versions. Same error.

---

### Post by abn91c on 2008-11-17
just make sure the firewall is disabled and double check in windows explorer that you have a c:\ubuntu\install folder put the iso file there.

---

### Post by th3 pla6u3 on 2008-11-17
Just did, with both versions, did not work on either version

---

### Post by th3 pla6u3 on 2008-11-18
Well I just decided to try and mount the ISO, and this is the error I got (attached picture). The setup finishes and prompts me to reboot but then there is no option to boot Ubuntu or Vista.

[[IMG]http://img248.imageshack.us/img248/7921/picim4.th.jpg[/IMG]](http://img248.imageshack.us/my.php?image=picim4.jpg)[[IMG]http://img248.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

---

### Post by th3 pla6u3 on 2008-11-18
I just followed the guide here.
```
http://ubuntuforums.org/showthread.php?t=983302
```

It worked the first time, but after that, when I boot into Ubuntu, it gives me some kind of NTFS error.

---

### Post by ago on 2008-11-18
The ISO C:\Users\Patty\Desktop\ubuntu-8.10-desktop-i386.iso seems corrupt (7zip cannot browse it), you can run an md5 checksum to verify it. Strangely enough your download of the metalink file (the file containing the actual download url) fails verification too as if it was compromised.

---

### Post by th3 pla6u3 on 2008-11-18
Compromised as in how? I am running AVG8 and do a daily scan, as well as Spybot S&D daily. I am pretty sure that I do not have any vriuses or spyware. BUT I will uninstall AVG and go with something a little bit better, as well as a better Anti-Spyware and do a scan and then see how things go. 

Something else that is confusing me is I have downloaded the ISO more then once, about 3 or 4 times, thinking I got a crupted one, and it has given me the same error. When I get home, I will check the MD5 and see how it looks.

*Edit 
Screw it, I just installed Ubuntu on a separate partition the hard way, just was looking for an easy way to install it. BUT I am still interested into why this was happening with Wubi, so I will continue to try and figure it out.

---

### Post by markg48 on 2008-11-19
just burn the iso to cd like its sippose to be and you wont have any proublems hopefully

---

### Post by ago on 2008-11-19
> **th3 pla6u3 said:**
> Compromised as in how?

Wubi runs 7zip to extract the content from the ISO and 7zip cannot access the ISO you have. There are md5sum programs that can check that the ISO file is indeed correct, such programs basically calculate a unique number for your file and you can then check that with the one published on ubuntu.com. If they do not match your ISO is corrupted.

---

### Post by th3 pla6u3 on 2008-11-19
> **ago said:**
> Wubi runs 7zip to extract the content from the ISO and 7zip cannot access the ISO you have. There are md5sum programs that can check that the ISO file is indeed correct, such programs basically calculate a unique number for your file and you can then check that with the one published on ubuntu.com. If they do not match your ISO is corrupted.

ISO is NOT corrupted.
Jeez everything that seems wrong is not wrong.  

[[IMG]http://img167.imageshack.us/img167/4296/md5tw4.th.jpg[/IMG]](http://img167.imageshack.us/my.php?image=md5tw4.jpg)[[IMG]http://img167.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

> **markg48 said:**
> just burn the iso to cd like its sippose to be and you wont have any proublems hopefully

I would but it gives me an error saying that the CD drive is busy or something like that. I will take a screen shot and post it up in a few.

---

