---
title: "Wubi Install/Uninstall Fails"
date: 2008-11-23
forum: General Help
---

### Post by imp0steur on 2008-11-23
I currently have Vista Ultimate 64-Bit installed.

I inserted Ubuntu 8.10 disk and then clicked **Install within windoze**.

I choose D drive for installation.

After I reboot I don't see Ubuntu boot entries. (have the wubildr and wubildr.mbr on both C and D drives .. but no boot entries)

Tried uninstalling .. the uninstaller simply quits ..

Did a manual uninstall. Again installed using Wubi from CD.

This time also I did not get the boot entries. So used EasyBCD to create a Wubi entry. This time when I choose Ubuntu (EasyBCD Entry) .. it simply lands onto grub (grub>) ..

any pointers?

**Wubi Logs**
```

============ Installer ============
PLUGINSDIR=C:\Users\<username>\AppData\Local\Temp\nsx8019.tmp
detect_all
Parsing cmdline "C:\Users\<username>\AppData\Local\Temp\7zS7D88.tmp\wubi.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=-2 MB
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD E:
      IsValid Ubuntu 8.10 "Intrepid Ibex" - Release amd64 (20081029.2)
      cdversion=8.10 cddistro=Ubuntu cdarch=amd64 cdcodename=Intrepid Ibex cdsubversion=Release cdbuild=20081029.2 
      GetDistroInfo distrofullname=Ubuntu-amd64 distro= cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
Found a good ISO: Ubuntu 8.10 "Intrepid Ibex" - Release amd64 (20081029.2)
Found CD E:
Found CD cddrive=E:
Changing icon to Ubuntu.ico
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive D:\ubuntu
AlreadyInstalled=false OldInstallationDrive= InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1720; Volume name Vista; Max #/chars in vol name 6256304; Volume Serial # 1014404599; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem D:
Drive & Path name 1720; Volume name Data; Max #/chars in vol name 6256308; Volume Serial # -1972347580; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 6166488; Volume name Vista; Max #/chars in vol name 30; Volume Serial # 1014404599; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = c:
FreeSpace in c: is 53958
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
GMT=5
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=<username>-PC
ComputerName=<username>-PC
EnvUsername=<username>
UserDomain=<username>-PC
UserInfoName=<username>
UserProfileFolder=C:\Users\<username>
UserProfileName=<username> 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1786; Volume name Vista; Max #/chars in vol name 6408888; Volume Serial # 1014404599; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
IsValidFileSystem D:
Drive & Path name 1786; Volume name Data; Max #/chars in vol name 6408892; Volume Serial # -1972347580; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
Adding drive D:
Drive list = C:|D:
ChangeInstallationDrive to c:
ChangeInstallationSize to 15
PopulateDistroList
DistroList = Ubuntu
PopulateLanguageListBox
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
ChangeInstallationDrive to D:
ChangeInstallationSize to 15
LeaveMainPage
Locale=en_US.UTF-8
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.metalink
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
      IsValid Ubuntu 8.10 "Intrepid Ibex" - Release amd64 (20081029.2)
      cdversion=8.10 cddistro=Ubuntu cdarch=amd64 cdcodename=Intrepid Ibex cdsubversion=Release cdbuild=20081029.2 
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
Found a good ISO: Ubuntu 8.10 "Intrepid Ibex" - Release amd64 (20081029.2)
Found CD E:
Found CD cddrive=E:
Installing in automatic mode from CD
CheckCD
check_internet_connection
Dialer online
connected
md5=3b9575338d15124f6d6346f1631af332
Checking md5 of E:\casper\filesystem.squashfs
CheckCD raw status = success:E:\casper\filesystem.squashfs
CheckCD status = success
CD2ISO D:\ubuntu\install\installation.iso
CD2ISO finished successfully
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
Checking/Downloading Ubuntu-8.10
Skipmd5 is true, using D:\ubuntu\install\installation.iso
CopyKernel isokernel=casper\vmlinuz, iso=D:\ubuntu\install\installation.iso, cddrive=E:
Extracting with 7z kernel/initrd from D:\ubuntu\install\installation.iso
UncompressFilesPriorInstall
Drive & Path name success; Volume name Data; Max #/chars in vol name <username>; Volume Serial # -1972347580; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive D: has filesystem NTFS
rootSize=14000 homesize=0, swapsize=1000, usrsize=0
DoMenuLst D:\ubuntu\install\boot\grub\menu.lst
editBootDrive
editBootDrive NT
CopyWubildr
CopyWubildrMbr
EditBootIni
editBootDrive
editBootDrive NT
CopyWubildr
CopyWubildrMbr
EditBootIni
Drive & Path name success; Volume name Data; Max #/chars in vol name <username>; Volume Serial # -1972347580; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive D: has filesystem NTFS
rootSize=14000 homesize=0, swapsize=1000, usrsize=0
AllocFile filename=D:\ubuntu\disks\root.disk size=14000
AllocFile status=success
AllocFile filename=D:\ubuntu\disks\home.disk size=0
AllocFile filename=D:\ubuntu\disks\swap.disk size=1000
AllocFile status=success
UncompressFilesAfterInstall
EjectCD
Ejecting CDHandle=520 for drive=E:
EjectCD DeviceIoControl exited with code 1 (1==success)
Installation completed successfully!
============ Uninstaller ============
PLUGINSDIR=C:\Users\<username>\AppData\Local\Temp\nsmABCA.tmp
Could not find \ubuntu, quitting...

```

---

### Post by imp0steur on 2008-11-24
Bump .. anybody plz?

---

### Post by ago on 2008-11-25
Uninstall, remove any wubildr.mbr
Use EasyBCD to point to wubildr.mbr manually

---

### Post by imp0steur on 2008-11-26
I did that .. but When choosing Ubuntu in boot menu .. it simply landed on Grub .. i mean with a prompt **grub>** ..

Will try again tonight ..

---

### Post by imp0steur on 2008-11-29
Ok .. first Wubi fails to create boot entiries ..

I manually created neosmart (easybcd) wubi entries .. that simply landed on the grub prompt 

Replaced the NST\menu.lst file with the \ubuntu\winboot\menu.lst .. now ubuntu boots fine ..

does some installations .. reboots and now it says its invalid boot partition ..

Does wubi 8.10 works for anybody here?

---

### Post by imp0steur on 2008-11-29
I really love Ubuntu .. I am sad to say untill this is fixed I have to stay with Vista .. atleast it doesn't have booting issues

---

### Post by ago on 2008-12-01
Please post the full error message and the menu.lst used. Note that the \ubuntu\winboot\menu.lst will normally load a second menu.lst in \ubuntu\disks\boot\grub\menu.lst

---

### Post by Jammanuser on 2008-12-03
> **imp0steur said:**
> 
I choose D drive for installation.


uhh...maybe that's the problem! it could be that Windows is not installed on the D drive...normally it would be on the C drive! so ur probably trying to install wubi on the recovery partition...and i'm not sure if that works or not! wubi's designed to be installed on TOP of ur Windows OS, like a regular Windows app, and not on a separate partition!

Hope my 2 cents helps!;)

Cheers!

-jammanuser

:D

---

### Post by imp0steur on 2008-12-18
My windows is on C drive .. when I install wubi on C it works but not on D .. 

Is not possible to install wubi in a different partition other than system partition?

---

### Post by ago on 2008-12-19
> **imp0steur said:**
> My windows is on C drive .. when I install wubi on C it works but not on D .. 

Is not possible to install wubi in a different partition other than system partition?

Normally yes. It might be that your D drive is not accessible at boot

---

