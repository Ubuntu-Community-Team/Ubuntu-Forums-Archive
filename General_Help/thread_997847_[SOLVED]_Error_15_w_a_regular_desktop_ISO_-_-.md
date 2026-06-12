---
title: "[SOLVED] Error 15 w/ a regular desktop ISO -_-"
date: 2008-11-30
forum: General Help
---

### Post by xander111 on 2008-11-30
Hi all,

I know there are a million of posts like these, and I have read a lot of them, but I haven't found one yet that matches my scenario.

Got Wubi 8.10.0.515, chose Ubuntu 8.10 Desktop, downloaded, rebooted. Chose Ubuntu at the bootloader, but running any of the options presents the text:

```

find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz

Error 15: File not found

Press any key to continue...
```

And no I can't see this folder in Windows in the stated directory. As far as I could tell the ISO downloaded without a problem, but I have included my installation log as well.

```

============ Installer ============
PLUGINSDIR=C:\DOCUME~1\Alex\LOCALS~1\Temp\nst3.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\Alex\My Documents\wubi.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=1015 MB
arch=i386
DetectCD
      Is Valid CD C:
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
Drive & Path name 1720; Volume name ; Max #/chars in vol name 1968496; Volume Serial # 1830808; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem D:
Drive & Path name 1720; Volume name ; Max #/chars in vol name 1968500; Volume Serial # 411539248; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1495272; Volume name ; Max #/chars in vol name 43; Volume Serial # 1830808; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = D:
FreeSpace in D: is 35236
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
GMT=10
Country=AU
Locale=en_AU.UTF-8
TimeZone=Australia/Sydney
Domain=localdomain
HostName=ALEXEEE
ComputerName=ALEXEEE
EnvUsername=Alex
UserDomain=ALEXEEE
UserInfoName=Alex
UserProfileFolder=C:\Documents and Settings\Alex
UserProfileName=Alex 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1786; Volume name ; Max #/chars in vol name 1973816; Volume Serial # 1830808; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
IsValidFileSystem D:
Drive & Path name 1786; Volume name ; Max #/chars in vol name 1973820; Volume Serial # 411539248; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
Adding drive D:
Drive list = C:|D:
ChangeInstallationDrive to D:
ChangeInstallationSize to 15
PopulateDistroList
DetectIso
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
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
ChangeInstallationDrive to D:
ChangeInstallationSize to 15
LeaveMainPage
ChangeInstallationSize to 30
LeaveMainPage
ChangeInstallationSize to 15
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1786; Volume name ; Max #/chars in vol name 2061776; Volume Serial # 1830808; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
IsValidFileSystem D:
Drive & Path name 1786; Volume name ; Max #/chars in vol name 2061780; Volume Serial # 411539248; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
Adding drive D:
Drive list = C:|D:
ChangeInstallationDrive to D:
ChangeInstallationSize to 15
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
Locale=en_AU.UTF-8
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
CreateInstallationFolders
MakeUninstall
Created D:\ubuntu\Uninstall-Ubuntu.exe
Created reg key HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
CopyDistFolders
GetIso
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD E:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
No CD found
DetectIso
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
Checking/Downloading Ubuntu-8.10
retrieve_partial_files
check_internet_connection
Dialer online
connected
Trying remote metalink: http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-i386.metalink
get_md5 http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-i386.metalink
Downloading: trymefirst= url=http://releases.ubuntu.com/8.10/MD5SUMS-metalink.gpg md5=
Download status=success:D:\ubuntu\install\MD5SUMS-metalink.gpg
Downloading: trymefirst= url=http://releases.ubuntu.com/8.10/MD5SUMS-metalink md5=
Download status=success:D:\ubuntu\install\MD5SUMS-metalink
      Verifying signature D:\ubuntu\install\MD5SUMS-metalink.asc
0; gpgv: error loading `iconv.dll': The specified module could not be found.


gpgv: Signature made 10/30/08 22:47:06 E. Australia Standard Time using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
; ; ; 
      Parsing D:\ubuntu\install\MD5SUMS-metalink
Found md5 c05fb1364236bfd66290ab4eaeaf5396
Downloading: trymefirst= url=http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-i386.metalink md5=c05fb1364236bfd66290ab4eaeaf5396
Download status=success:D:\ubuntu\install\ubuntu-8.10-desktop-i386.iso
ISO file ubuntu-8.10-desktop-i386.iso retrieved!!!
CopyKernel isokernel=casper\vmlinuz, iso=D:\ubuntu\install\ubuntu-8.10-desktop-i386.iso, cddrive=
Extracting with 7z kernel/initrd from D:\ubuntu\install\ubuntu-8.10-desktop-i386.iso
UncompressFilesPriorInstall
Drive & Path name D:\ubuntu\install\ubuntu-8.10-desktop-i386.iso; Volume name ; Max #/chars in vol name ; Volume Serial # 411539248; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size 2147352576
Drive D: has filesystem NTFS
rootSize=14000 homesize=0, swapsize=1000, usrsize=0
DoMenuLst D:\ubuntu\install\boot\grub\menu.lst
editBootDrive
editBootDrive NT
CopyWubildr
CopyWubildrMbr
EditBootIni
EditBootIni C:\boot.ini
editBootDrive
editBootDrive NT
CopyWubildr
CopyWubildrMbr
EditBootIni
Drive & Path name D:\ubuntu\install\ubuntu-8.10-desktop-i386.iso; Volume name ; Max #/chars in vol name ; Volume Serial # 411539248; Max #/chars in dir/file names 255; File System Flags 327935; File System Type NTFS; File System Name Size 2147352576
Drive D: has filesystem NTFS
rootSize=14000 homesize=0, swapsize=1000, usrsize=0
AllocFile filename=D:\ubuntu\disks\root.disk size=14000
AllocFile status=success
AllocFile filename=D:\ubuntu\disks\home.disk size=0
AllocFile filename=D:\ubuntu\disks\swap.disk size=1000
AllocFile status=success
UncompressFilesAfterInstall
Installation completed successfully!
```

All help is much appreciated.

Thanks in advance,
Al

---

### Post by xander111 on 2008-12-01
Problem solved. Turns out my paranoid firewall was prompting for permission to allow 7zip to unzip some files during setup, however I had left the computer while it was downloading the image and the prompts timed out and denied the operation.

Uninstalled, then re-installed using the backup and made sure to allow 7zip to do its thing. Booted and installing ubuntu as I type :)

---

