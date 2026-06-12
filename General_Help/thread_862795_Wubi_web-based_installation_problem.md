---
title: "Wubi web-based installation problem"
date: 2008-07-17
forum: General Help
---

### Post by ebolaRETURNS on 2008-07-17
Hello all.
I am trying to install Ubuntu using the Wubi web-based installer ver. 8.04.1, rev. 506 on my laptop.  Said laptop is AMD64, and I am trying to install on a partition other than windows' root dir.  What happens is that the installer will download numerous iterations of ~500-600 megs of files.  Between each iteration, the top progress bar, "checking installation files", will advance just a little bit.  Is this supposed to be happening?  I've been running the installer for a few days.

Thanks in advanced,
ebola hemorrhagic fever

---

### Post by ebolaRETURNS on 2008-07-17
Per my own impatience, I'm just downloading the appropriate .iso file now, which I'll burn to a cd to install.

---

### Post by ago on 2008-07-18
Would you mind to post the wubi log so that I can check whether there is an issue to be fixed? It is in your user temp folder (type %temp% in windows explorer)

---

### Post by ebolaRETURNS on 2008-07-18
The log is pretty long, so I've attached it as a .txt file.  So I tried to install via CD last night, but it didn't work.  The damn computer stubbornly continued to boot to windows, even with CDROM first on boot order and the hard drive last.  I checked, and the iso file was indeed burned on there properly.

Thanks again for your help.

edit: in fact, the log is long enough that it exceeds the forum's limits for attachments, so I'll just post what I can directly.

============ Installer ============
PLUGINSDIR=C:\DOCUME~1\Ebola\LOCALS~1\Temp\nsl65.tmp
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
Drive & Path name 1712; Volume name ACER; Max #/chars in vol name 1868168; Volume Serial # 1490867238; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive C: has valid filesystem FAT32
IsValidFileSystem D:
Drive & Path name 1712; Volume name ACERDATA; Max #/chars in vol name 1868172; Volume Serial # 813147998; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive D: has valid filesystem FAT32
IsValidFileSystem c:
Drive & Path name 1427224; Volume name ACER; Max #/chars in vol name 38; Volume Serial # 1490867238; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size 2147352576
Drive c: has valid filesystem FAT32
Installation drive chosen = D:
FreeSpace in D: is 12127
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
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
Drive & Path name 1778; Volume name ACER; Max #/chars in vol name 1871680; Volume Serial # 1490867238; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive C: has valid filesystem FAT32
Skipping drive C:, not enough free space 3200 <= 5000
IsValidFileSystem D:
Drive & Path name 1778; Volume name ACERDATA; Max #/chars in vol name 1871684; Volume Serial # 813147998; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive D: has valid filesystem FAT32
Adding drive D:
Drive list = D:
ChangeInstallationDrive to D:
ChangeInstallationSize to 8
PopulateDistroList
DetectIso
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
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\Ebola\LOCALS~1\Temp\nsd68.tmp
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
Drive & Path name 1712; Volume name ACER; Max #/chars in vol name 1862656; Volume Serial # 1490867238; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive C: has valid filesystem FAT32
IsValidFileSystem D:
Drive & Path name 1712; Volume name ACERDATA; Max #/chars in vol name 1862660; Volume Serial # 813147998; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive D: has valid filesystem FAT32
IsValidFileSystem c:
Drive & Path name 1426808; Volume name ACER; Max #/chars in vol name 38; Volume Serial # 1490867238; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size 2147352576
Drive c: has valid filesystem FAT32
Installation drive chosen = D:
FreeSpace in D: is 12127
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
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
Drive & Path name 1778; Volume name ACER; Max #/chars in vol name 1866832; Volume Serial # 1490867238; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive C: has valid filesystem FAT32
Skipping drive C:, not enough free space 3198 <= 5000
IsValidFileSystem D:
Drive & Path name 1778; Volume name ACERDATA; Max #/chars in vol name 1866836; Volume Serial # 813147998; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive D: has valid filesystem FAT32
Adding drive D:
Drive list = D:
ChangeInstallationDrive to D:
ChangeInstallationSize to 8
PopulateDistroList
DetectIso
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
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro= cdarch= arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Checking/Downloading Ubuntu-8.04.1
retrieve_partial_files
check_internet_connection
Dialer online
connected
Trying remote metalink: [http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink](http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink)
get_md5 [http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink](http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink)
Downloading: trymefirst= url=http://releases.ubuntu.com/8.04.1/MD5SUMS-metalink.gpg md5=
Download status=success:D:\ubuntu\install\MD5SUMS-metalink.gpg
Downloading: trymefirst= url=http://releases.ubuntu.com/8.04.1/MD5SUMS-metalink md5=
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\Ebola\LOCALS~1\Temp\nsr6C.tmp
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
Found InstallationDrive D:\ubuntu
AlreadyInstalled=true OldInstallationDrive=D: InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1712; Volume name ACER; Max #/chars in vol name 1862656; Volume Serial # 1490867238; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive C: has valid filesystem FAT32
IsValidFileSystem D:
Drive & Path name 1712; Volume name ACERDATA; Max #/chars in vol name 1862660; Volume Serial # 813147998; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive D: has valid filesystem FAT32
IsValidFileSystem c:
Drive & Path name 1426808; Volume name ACER; Max #/chars in vol name 37; Volume Serial # 1490867238; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size 2147352576
Drive c: has valid filesystem FAT32
Installation drive chosen = D:
FreeSpace in D: is 12125
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
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
Drive & Path name 1778; Volume name ACER; Max #/chars in vol name 1867384; Volume Serial # 1490867238; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive C: has valid filesystem FAT32
Skipping drive C:, not enough free space 3193 <= 5000
IsValidFileSystem D:
Drive & Path name 1778; Volume name ACERDATA; Max #/chars in vol name 1867388; Volume Serial # 813147998; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive D: has valid filesystem FAT32
Adding drive D:
Drive list = D:
ChangeInstallationDrive to D:
ChangeInstallationSize to 8
PopulateDistroList
DetectIso
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
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro= cdarch= arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Checking/Downloading Ubuntu-8.04.1
retrieve_partial_files
check_internet_connection
Dialer online
connected
Trying remote metalink: [http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink](http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink)
get_md5 [http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink](http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink)
Downloading: trymefirst= url=http://releases.ubuntu.com/8.04.1/MD5SUMS-metalink.gpg md5=
Download status=success:D:\ubuntu\install\MD5SUMS-metalink.gpg
Downloading: trymefirst= url=http://releases.ubuntu.com/8.04.1/MD5SUMS-metalink md5=
Download status=success:D:\ubuntu\install\MD5SUMS-metalink
      Verifying signature D:\ubuntu\install\MD5SUMS-metalink.asc
0; gpgv: Signature made 07/03/08 14:36:17 Pacific Daylight Time using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
; ; ; 
      Parsing D:\ubuntu\install\MD5SUMS-metalink
Found md5 1f8a4eb23752b8782651c67bdf48f66b
Downloading: trymefirst= url=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink md5=1f8a4eb23752b8782651c67bdf48f66b
Download status=Could not resolve host: es.releases.ubuntu.com; No data record of requested type
Trying remote metalink2: [http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-amd64.metalink](http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-amd64.metalink)
get_md5 [http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-amd64.metalink](http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-amd64.metalink)
Downloading: trymefirst= url=http://cdimage.ubuntu.com/hardy/daily-live/current/MD5SUMS-metalink.gpg md5=
Download status=success:D:\ubuntu\install\MD5SUMS-metalink.gpg
Downloading: trymefirst= url=http://cdimage.ubuntu.com/hardy/daily-live/current/MD5SUMS-metalink md5=
Download status=success:D:\ubuntu\install\MD5SUMS-metalink
      Verifying signature D:\ubuntu\install\MD5SUMS-metalink.asc
0; gpgv: Signature made 07/12/08 01:19:43 Pacific Daylight Time using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
; ; ; 
      Parsing D:\ubuntu\install\MD5SUMS-metalink
Found md5 ad70ba4937f878e0d14bfb62515b44bb
Downloading: trymefirst= url=http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-amd64.metalink md5=ad70ba4937f878e0d14bfb62515b44bb
Download status=cancel
User cancelled download, quitting.
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\Ebola\LOCALS~1\Temp\nsi4.tmp
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
Found InstallationDrive D:\ubuntu
AlreadyInstalled=true OldInstallationDrive=D: InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1712; Volume name ACER; Max #/chars in vol name 1862248; Volume Serial # 1490867238; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive C: has valid filesystem FAT32
IsValidFileSystem D:
Drive & Path name 1712; Volume name ACERDATA; Max #/chars in vol name 1862252; Volume Serial # 813147998; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive D: has valid filesystem FAT32
IsValidFileSystem c:
Drive & Path name 1426808; Volume name ACER; Max #/chars in vol name 30; Volume Serial # 1490867238; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size 2147352576
Drive c: has valid filesystem FAT32
Installation drive chosen = D:
FreeSpace in D: is 11650
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
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
Drive & Path name 1778; Volume name ACER; Max #/chars in vol name 1865448; Volume Serial # 1490867238; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive C: has valid filesystem FAT32
Skipping drive C:, not enough free space 3199 <= 5000
IsValidFileSystem D:
Drive & Path name 1778; Volume name ACERDATA; Max #/chars in vol name 1865452; Volume Serial # 813147998; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive D: has valid filesystem FAT32
Adding drive D:
Drive list = D:
ChangeInstallationDrive to D:
ChangeInstallationSize to 8
PopulateDistroList
DetectIso
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
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro= cdarch= arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Checking/Downloading Ubuntu-8.04.1
retrieve_partial_files
check_internet_connection
Dialer online
connected
Trying remote metalink: [http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink](http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink)
get_md5 [http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink](http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink)
Downloading: trymefirst= url=http://releases.ubuntu.com/8.04.1/MD5SUMS-metalink.gpg md5=
Download status=success:D:\ubuntu\install\MD5SUMS-metalink.gpg
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\Ebola\LOCALS~1\Temp\nsj8.tmp
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
Found InstallationDrive D:\ubuntu
AlreadyInstalled=true OldInstallationDrive=D: InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1712; Volume name ACER; Max #/chars in vol name 1862248; Volume Serial # 1490867238; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive C: has valid filesystem FAT32
IsValidFileSystem D:
Drive & Path name 1712; Volume name ACERDATA; Max #/chars in vol name 1862252; Volume Serial # 813147998; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive D: has valid filesystem FAT32
IsValidFileSystem c:
Drive & Path name 1426808; Volume name ACER; Max #/chars in vol name 30; Volume Serial # 1490867238; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size 2147352576
Drive c: has valid filesystem FAT32
Installation drive chosen = D:
FreeSpace in D: is 11650
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\

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
Drive & Path name 1778; Volume name ACER; Max #/chars in vol name 1865448; Volume Serial # 1490867238; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive C: has valid filesystem FAT32
Skipping drive C:, not enough free space 3194 <= 5000
IsValidFileSystem D:
Drive & Path name 1778; Volume name ACERDATA; Max #/chars in vol name 1865452; Volume Serial # 813147998; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Drive D: has valid filesystem FAT32
Adding drive D:
Drive list = D:
ChangeInstallationDrive to D:
ChangeInstallationSize to 8
PopulateDistroList
DetectIso
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
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro= cdarch= arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Checking/Downloading Ubuntu-8.04.1
retrieve_partial_files
check_internet_connection
Dialer online
connected
Trying remote metalink: [http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink](http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink)
get_md5 [http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink](http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink)
Downloading: trymefirst= url=http://releases.ubuntu.com/8.04.1/MD5SUMS-metalink.gpg md5=
Download status=success:D:\ubuntu\install\MD5SUMS-metalink.gpg
Downloading: trymefirst= url=http://releases.ubuntu.com/8.04.1/MD5SUMS-metalink md5=
Download status=success:D:\ubuntu\install\MD5SUMS-metalink
      Verifying signature D:\ubuntu\install\MD5SUMS-metalink.asc
0; gpgv: Signature made 07/03/08 14:36:17 Pacific Daylight Time using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
; ; ; 
      Parsing D:\ubuntu\install\MD5SUMS-metalink
Found md5 1f8a4eb23752b8782651c67bdf48f66b
Downloading: trymefirst= url=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink md5=1f8a4eb23752b8782651c67bdf48f66b
Download status=Hash check failed!
Trying remote metalink2: [http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-amd64.metalink](http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-amd64.metalink)
get_md5 [http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-amd64.metalink](http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-amd64.metalink)
Downloading: trymefirst= url=http://cdimage.ubuntu.com/hardy/daily-live/current/MD5SUMS-metalink.gpg md5=
Download status=success:D:\ubuntu\install\MD5SUMS-metalink.gpg
Downloading: trymefirst= url=http://cdimage.ubuntu.com/hardy/daily-live/current/MD5SUMS-metalink md5=
Download status=success:D:\ubuntu\install\MD5SUMS-metalink
      Verifying signature D:\ubuntu\install\MD5SUMS-metalink.asc
0; gpgv: Signature made 07/12/08 01:19:43 Pacific Daylight Time using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
; ; ; 
      Parsing D:\ubuntu\install\MD5SUMS-metalink
Found md5 ad70ba4937f878e0d14bfb62515b44bb
Downloading: trymefirst= url=http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-amd64.metalink md5=ad70ba4937f878e0d14bfb62515b44bb
Download status=cancel
User cancelled download, quitting.
============ Uninstaller ============
PLUGINSDIR=C:\DOCUME~1\Ebola\LOCALS~1\Temp\nsiB8.tmp
un.install
un.BackupIso
un.CleanBcd
un.RemoveInstallationFolder D:\ubuntu
un.CleanThisDrive C:\
un.CleanThisDrive D:\
un.CleanRegistry Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi

---

### Post by ebolaRETURNS on 2008-07-18
*shameless bump to reflect changes in edit* :)

---

### Post by ebolaRETURNS on 2008-07-20
Okay.  So reading the Wubi guide, it seems that if you run the Wubi-installer with the appropriate iso in the same directory, it will make use of the iso rather than downloading from the web.  I did this once, and it crashed.  I did this again, and the top progress bar got about where it did with my attempts at web-based installation, and then the installer began downloading files from the web again.  I can post the log too if need be.

ebola

---

### Post by ago on 2008-07-21
It isn't always the same error: e.g.

Download status=Could not resolve host: es.releases.ubuntu.com
Download status=Hash check failed!

Not sure about the reason

Download [http://releases.ubuntu.com/hardy/ubuntu-8.04.1-desktop-amd64.iso](http://releases.ubuntu.com/hardy/ubuntu-8.04.1-desktop-amd64.iso)
Check that the MD5 is b78ef719e3361e726b89bab78c526ad0

remove old ISOs

---

