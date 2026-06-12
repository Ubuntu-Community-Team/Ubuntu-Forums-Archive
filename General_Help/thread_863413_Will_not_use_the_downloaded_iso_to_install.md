---
title: "Will not use the downloaded iso to install"
date: 2008-07-18
forum: General Help
---

### Post by xxchixorxx on 2008-07-18
I followed the directions to install Ubu to windows through Wubi via the downloaded iso file, but it still tells me to connect to the internet.  The reason I wanted to use the downloaded iso is that the download is extremely slow (around 3kbs).  

I put wubi and the correct iso in a folder, ran wubi, and after it checked the checksums, it told me to connect to the internet even though the iso is inside the same folder.  Why won't it pick up the iso file?

I'm running Vista on the machine that will have it installed.

---

### Post by damis648 on 2008-07-18
If you are sure you are going to use wubi, just burn the ISO to a CD. Then pop it back in and a menu will pop up and you can easily install it from there.

---

### Post by xxchixorxx on 2008-07-18
I tried that first but it still wanted to download from the internet, which is why I tried the offline method of installation.

---

### Post by neoncore on 2008-07-18
disconnect from internet while trying to run wubi might work

---

### Post by ago on 2008-07-21
There is a wubi log in your user temp directory, in there it will mention why it did not like the ISO.

---

### Post by ebolaRETURNS on 2008-07-22
I am having a similar issue.

The key error message appears to be this:

Could not find C:\DOCUME~1\Ebola\LOCALS~1\Temp\info
      IsValid

---

### Post by ago on 2008-07-22
could you please post the full log? Ideally delete it first and do a clean run, so I do not get mixed with the logs of 10 different attempts.

---

### Post by ebolaRETURNS on 2008-07-22
No problem.
Sorry about that.

============ Installer ============
PLUGINSDIR=C:\DOCUME~1\Ebola\LOCALS~1\Temp\nsx16.tmp
detect_all
Parsing cmdline "D:\Wubi-8.04.1-rev506.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=1470 MB
arch=amd64
DetectCD
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
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
Drive & Path name 1712; Volume name ACER; Max #/chars in vol name 1862152; Volume Serial # 1490867238; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive C: has valid filesystem FAT32
IsValidFileSystem D:
Drive & Path name 1712; Volume name ACERDATA; Max #/chars in vol name 1862156; Volume Serial # 813147998; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive D: has valid filesystem FAT32
IsValidFileSystem c:
Drive & Path name 1426808; Volume name ACER; Max #/chars in vol name 36; Volume Serial # 1490867238; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size 2147352576
Drive c: has valid filesystem FAT32
Installation drive chosen = D:
FreeSpace in D: is 10475
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
Found BackupFolder D:\ubuntu-backup
GMT=-8
Country=US
Locale=en_US.UTF-8
TimeZone=America/Los_Angeles
Domain=localdomain
HostName=EBOLALAND
ComputerName=EBOLALAND
EnvUsername=Ebola
UserDomain=EBOLALAND
UserInfoName=Ebola
UserProfileFolder=C:\Documents and Settings\Ebola
UserProfileName=Ebola 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name ACER; Max #/chars in vol name 1866328; Volume Serial # 1490867238; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive C: has valid filesystem FAT32
Skipping drive C:, not enough free space 2753 <= 5000
IsValidFileSystem D:
Drive & Path name 1778; Volume name ACERDATA; Max #/chars in vol name 1866332; Volume Serial # 813147998; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive D: has valid filesystem FAT32
Adding drive D:
Drive list = D:
ChangeInstallationDrive to D:
ChangeInstallationSize to 7
PopulateDistroList
DetectIso
      IsValidIso ispoath=D:\ubuntu-8.04.1-desktop-amd64.iso
      ExtractIsoInfo
      C:\DOCUME~1\Ebola\LOCALS~1\Temp\nsx16.tmp\7z.exe e -y -i!.disk\info -oC:\DOCUME~1\Ebola\LOCALS~1\Temp D:\ubuntu-8.04.1-desktop-amd64.iso
Could not find C:\DOCUME~1\Ebola\LOCALS~1\Temp\info
      IsValid 
no cdinfo
CDInfo cleared
AddDistroToList Ubuntu-i386
AddDistroToList Ubuntu-amd64
AddDistroToList Kubuntu-i386
AddDistroToList Kubuntu-amd64
AddDistroToList Kubuntu-KDE4-i386
AddDistroToList Kubuntu-KDE4-amd64
AddDistroToList Xubuntu-i386
AddDistroToList Xubuntu-amd64
DistroList = Ubuntu|Kubuntu|Kubuntu-KDE4|Xubuntu
PopulateLanguageListBox
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro= cdarch= arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
ChangeInstallationSize to 8
LeaveMainPage
Locale=en_US.UTF-8
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro= cdarch= arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
CreateInstallationFolders
MakeUninstall
Created D:\ubuntu\Uninstall-Ubuntu.exe
Created reg key HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
CopyDistFolders
GetIso
DetectCD
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
No CD found
DetectIso
      IsValidIso ispoath=D:\ubuntu-8.04.1-desktop-amd64.iso
      ExtractIsoInfo
      C:\DOCUME~1\Ebola\LOCALS~1\Temp\nsx16.tmp\7z.exe e -y -i!.disk\info -oC:\DOCUME~1\Ebola\LOCALS~1\Temp D:\ubuntu-8.04.1-desktop-amd64.iso
Could not find C:\DOCUME~1\Ebola\LOCALS~1\Temp\info
      IsValid 
no cdinfo
CDInfo cleared
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro= cdarch= arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Checking/Downloading Ubuntu-8.04.1
retrieve_partial_files
check_internet_connection
Dialer offline
not connected
User cancelled Internet Connection Retry, quitting

I didn't go on to let it fetch **** from the internet because that is having problems too.

Thanks again! :)

---

### Post by ago on 2008-07-22
It is not possible to extract files from your ISO please make sure that the ISO is not corrupt by checking the md5 against the one on ubuntu.com

---

### Post by ebolaRETURNS on 2008-07-22
many thanks.
i could also just re-download the iso.

---

### Post by dorkdork777 on 2008-07-22
If you're still having problems, you could try mounting the ISO with a tool like DAEMON Tools or Alcohol 120% (both are for Windows). This way, you don't have to worry about whether it's the CD or the ISO that's the problem... plus it will install faster. :)

---

