---
title: "New to linux Need Help with WUBI installation."
date: 2009-06-24
forum: Installation &amp; Upgrades
---

### Post by wickedwit on 2009-06-24
I have downloaded 'ubuntu-8.04.2-desktop-i386' from a listed server. I would like to install it via wubi. Initially i was getting a download error, it was fixed. But now the wubi, that came with the package is downloding the whole iso again, i have the same files i think. Please tell me how to skip this step and continue with the installation? My iso is saved @ C:\Downloads I opened the file run the 'wubi' it created a folder C:\ubuntu again i saved the iso and wubi here.:confused: 



Wubi-8.04.2-rev507
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\nso19.tmp
detect_all
Parsing cmdline "C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\7zS16.tmp\wubi.exe " 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=246 MB
Not enough memory: 246 < 256
arch=i386
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD G:
CDInfo cleared
      Is Valid CD H:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
No CD found
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
Found InstallationDrive C:\ubuntu
AlreadyInstalled=true OldInstallationDrive=C: InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1712; Volume name ; Max #/chars in vol name 1869844; Volume Serial # -458752432; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem D:
Drive & Path name 1712; Volume name D; Max #/chars in vol name 1869848; Volume Serial # 819204289; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive D: has valid filesystem FAT32
IsValidFileSystem E:
Drive & Path name 1712; Volume name ; Max #/chars in vol name 1869852; Volume Serial # -657524706; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive E: has valid filesystem FAT32
IsValidFileSystem F:
Drive & Path name 1712; Volume name ; Max #/chars in vol name 1869856; Volume Serial # -1201629022; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive F: has valid filesystem FAT32
IsValidFileSystem c:
Drive & Path name 1433072; Volume name ; Max #/chars in vol name 85; Volume Serial # -458752432; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = C:
FreeSpace in C: is 5831
DetectBackupFolder
Found BackupFolder C:\ubuntu-backup
GMT=-8
Country=US
Locale=en_US.UTF-8
TimeZone=America/Los_Angeles
Domain=localdomain
HostName=stlr
ComputerName=STLR
EnvUsername=Administrator
UserDomain=STLR
UserInfoName=Administrator
UserProfileFolder=C:\Documents and Settings\Administrator
UserProfileName=Administrator 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name ; Max #/chars in vol name 1887556; Volume Serial # -458752432; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
IsValidFileSystem D:
Drive & Path name 1778; Volume name D; Max #/chars in vol name 1887560; Volume Serial # 819204289; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive D: has valid filesystem FAT32
Skipping drive D:, not enough free space 1578 <= 5000
IsValidFileSystem E:
Drive & Path name 1778; Volume name ; Max #/chars in vol name 1887564; Volume Serial # -657524706; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive E: has valid filesystem FAT32
Skipping drive E:, not enough free space 4726 <= 5000
IsValidFileSystem F:
Drive & Path name 1778; Volume name ; Max #/chars in vol name 1887568; Volume Serial # -1201629022; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive F: has valid filesystem FAT32
Skipping drive F:, not enough free space 1260 <= 5000
Drive list = C:
ChangeInstallationDrive to C:
ChangeInstallationSize to 4
PopulateDistroList
DetectIso
      IsValidIso ispoath=C:\ubuntu\ubuntu-8.04.2-desktop-i386.iso
      ExtractIsoInfo
      C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\nso19.tmp\7z.exe e -y -i!.disk\info -oC:\DOCUME~1\ADMINI~1\LOCALS~1\Temp C:\ubuntu\ubuntu-8.04.2-desktop-i386.iso
C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\nso19.tmp\7z error: 2
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
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04.2/ubuntu-8.04.2-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.2
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
Locale=en_US.UTF-8
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04.2/ubuntu-8.04.2-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.2
CreateInstallationFolders
MakeUninstall
Created C:\ubuntu\Uninstall-Ubuntu.exe
Created reg key HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
CopyDistFolders
GetIso
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD G:
CDInfo cleared
      Is Valid CD H:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
No CD found
DetectIso
      IsValidIso ispoath=C:\ubuntu\ubuntu-8.04.2-desktop-i386.iso
      ExtractIsoInfo
      C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\nso19.tmp\7z.exe e -y -i!.disk\info -oC:\DOCUME~1\ADMINI~1\LOCALS~1\Temp C:\ubuntu\ubuntu-8.04.2-desktop-i386.iso
C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\nso19.tmp\7z error: 2
      IsValid 
no cdinfo
CDInfo cleared
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04.2/ubuntu-8.04.2-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.2
Checking/Downloading Ubuntu-8.04.2
retrieve_partial_files
check_internet_connection
Dialer online
connected
Trying remote metalink: [http://releases.ubuntu.com/8.04.2/ubuntu-8.04.2-desktop-i386.metalink](http://releases.ubuntu.com/8.04.2/ubuntu-8.04.2-desktop-i386.metalink)
get_md5 [http://releases.ubuntu.com/8.04.2/ubuntu-8.04.2-desktop-i386.metalink](http://releases.ubuntu.com/8.04.2/ubuntu-8.04.2-desktop-i386.metalink)
Downloading: trymefirst= url=http://releases.ubuntu.com/8.04.2/MD5SUMS-metalink.gpg md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink.gpg
Downloading: trymefirst= url=http://releases.ubuntu.com/8.04.2/MD5SUMS-metalink md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink
      Verifying signature C:\ubuntu\install\MD5SUMS-metalink.asc
0; gpgv: error loading `iconv.dll': The specified module could not be found.


gpgv: Signature made 01/22/09 12:29:01 Pacific Standard Time using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
; ; ; 
      Parsing C:\ubuntu\install\MD5SUMS-metalink
Found md5 50fb370ad83dd012a2e933813582bd08
Downloading: trymefirst= url=http://releases.ubuntu.com/8.04.2/ubuntu-8.04.2-desktop-i386.metalink md5=50fb370ad83dd012a2e933813582bd08
Download status=cancel
User cancelled download, quitting.

---

### Post by philcamlin on 2009-06-24
try torrenting the ubuntu wubi from the site its much faster :)

just click it choose the hard drive space 

make a username and your done!

have fun with your ubuntu installation

and if you ever want it off wich i doubt you will you can uninstall it through there too! :p

---

