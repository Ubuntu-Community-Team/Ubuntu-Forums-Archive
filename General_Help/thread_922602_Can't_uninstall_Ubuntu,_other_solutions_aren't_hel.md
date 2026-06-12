---
title: "Can't uninstall Ubuntu, other solutions aren't helping"
date: 2008-09-17
forum: General Help
---

### Post by BobbySoSlo on 2008-09-17
I've tried uninstalling via the Wubi-uninstaller, the "Add or Remove Programs", and the downloaded uninstaller.

All result in a Admin permission request (UAC) and then nothing happens.

I'm using 64 bit Vista and I installed onto a non C: drive.

I started to do the manual uninstall found here:
[https://wiki.ubuntu.com/WubiGuide#Ho...nstall%20Wubi?](https://wiki.ubuntu.com/WubiGuide#Ho...nstall%20Wubi?)

But I don't understand bcdedit.exe and without understanding it I don't want to mess anything up.

I'd like to fresh install (this time onto my C: Drive) but my urge to deal with Linux outside of work is falling rapidly.

Any solutions out there on what to try next?

---

### Post by ago on 2008-09-17
[https://wiki.ubuntu.com/WubiGuide#Cannot%20uninstall%20Ubuntu](https://wiki.ubuntu.com/WubiGuide#Cannot%20uninstall%20Ubuntu)

---

### Post by BobbySoSlo on 2008-09-17
I appreciate the response and all but this is the downloaded uninstaller I mentioned, I should have been a little more descriptive but I already had found it from your other responses.

Anyone else have any solutions?

---

### Post by BobbySoSlo on 2008-09-18
I promise I have spent much time looking for already discovered answered.

I already installed Ubuntu. I did the 64 bit version through windows (Wubi) onto a non-C: drive. It had a little bit of trouble and then I was unable to properly uninstall it so I could start fresh. 

I then followed the manual uninstall instructions and now Ubuntu and Wubi are cleared from my computer, not in the boot, not in the registry, nothing.  However I have reinstalled it without an error in the process, but it didn't get added to the boot (it was in registry and program list).

It uninstalls fine now and I've tried multiple times for a fresh install but to no avail.  Please help, I am pretty computer savvy being a nearly graduated programmer but find myself frustratingly helpless at the moment.

---

### Post by BobbySoSlo on 2008-09-18
Bump. Please help

Best I can tell it's not being added to the bootloader during installation... I don't know why though

---

### Post by Sef on 2008-09-18
First, please wait 24 hours before bumping your thread.  We are all volunteers here, so sometimes your question can be answered fast, and sometimes slow.

Second, you reinstalled Ubuntu via wubi, but only XP boots up, correct?  If that is the case, I would download [SuperGRUBDisk]("http://supergrubdisk.org"), and reinstall GRUB.

---

### Post by BobbySoSlo on 2008-09-18
My apologies, my goal is to eventually become a contributor to Linux as well. 

I'm using Wubi w/ Vista actually, but I will see what I can do with Supergrub. Thank you for the response despite my ignorance of the rules, and I'll report the amount of success I acheive.

---

### Post by BobbySoSlo on 2008-09-18
Well I used SuperGrub and the automatic SuperGrub, nothing changed (Except I managed to get a giant command line ascii character crying).

Is there any other way to make it work? I'll try and put it back on a seperate drive again I guess...

---

### Post by ago on 2008-09-18
BobbySoSlo if you use wubi rev 505 you need the special uninstaller provided in the WubiGuide ([https://wiki.ubuntu.com/WubiGuide#Cannot%20uninstall%20Ubuntu](https://wiki.ubuntu.com/WubiGuide#Cannot%20uninstall%20Ubuntu))

If an Ubuntu opetion is not added to your bootloader, if you have vista check with easybcd, if you have XP look into boot.ini. 

If you have UAC issues try to login as administrator.

Wubi errors are normally reported in the log file which sits in the user temp folder. Post it here.

---

### Post by BobbySoSlo on 2008-09-18
EasyBCD doesn't show anything but my Vista boot. 

I used it to remove ubuntu from the boot when uninstalling Wubi didn't work appropriately the first time.

I've been trying that uninstaller and have yet to see any change in effect compared to the regular uninstaller.

```
============ Uninstaller ============
PLUGINSDIR=C:\Users\Bobby\AppData\Local\Temp\nsgE88C.tmp
Could not find \ubuntu, quitting...
============ Uninstaller ============
PLUGINSDIR=C:\Users\Bobby\AppData\Local\Temp\nsd6ECB.tmp
Could not find \ubuntu, quitting...
============ Uninstaller ============
PLUGINSDIR=C:\Users\Bobby\AppData\Local\Temp\nsh263D.tmp
Could not find \ubuntu, quitting...
============ Uninstaller ============
PLUGINSDIR=C:\Users\Bobby\AppData\Local\Temp\nsh2DCB.tmp
Could not find \ubuntu, quitting...
============ Uninstaller ============
PLUGINSDIR=C:\Users\Bobby\AppData\Local\Temp\nsm9DD6.tmp
Could not find \ubuntu, quitting...
============ Uninstaller ============
PLUGINSDIR=C:\Users\Bobby\AppData\Local\Temp\nsaB31A.tmp
un.install
un.BackupIso
un.CleanBcd
un.RemoveInstallationFolder \ubuntu
un.CleanThisDrive C:\
un.CleanThisDrive D:\
un.CleanRegistry Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
============ Uninstaller ============
PLUGINSDIR=C:\Users\Bobby\AppData\Local\Temp\nsb87C7.tmp
un.install
un.BackupIso
un.CleanBcd
un.RemoveInstallationFolder \ubuntu
un.CleanThisDrive C:\
un.CleanThisDrive D:\
un.CleanRegistry Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
============ Uninstaller ============
PLUGINSDIR=C:\Users\Bobby\AppData\Local\Temp\nshE457.tmp
un.install
un.BackupIso
un.CleanBcd
un.RemoveInstallationFolder \ubuntu
un.CleanThisDrive C:\
un.CleanThisDrive D:\
un.CleanRegistry Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
============ Uninstaller ============
PLUGINSDIR=C:\Users\Bobby\AppData\Local\Temp\nsx68A3.tmp
un.install
un.BackupIso
un.CleanBcd
un.RemoveInstallationFolder \ubuntu
un.CleanThisDrive C:\
un.CleanThisDrive D:\
un.CleanRegistry Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
============ Uninstaller ============
PLUGINSDIR=C:\Users\Bobby\AppData\Local\Temp\nsbE105.tmp
un.install
un.BackupIso
un.CleanBcd
un.RemoveInstallationFolder \ubuntu
un.CleanThisDrive C:\
un.CleanThisDrive D:\
un.CleanRegistry Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi

```

```
============ Installer ============
PLUGINSDIR=C:\Users\Bobby\AppData\Local\Temp\nsdBC0D.tmp
detect_all
Parsing cmdline "C:\Users\Bobby\AppData\Local\Temp\7zSB612.tmp\wubi.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=-1 MB
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD E:
      IsValid Ubuntu 8.04.1 "Hardy Heron" - Release amd64 (20080702.1)
      cdversion=8.04.1 cddistro=Ubuntu cdarch=amd64 cdcodename=Hardy Heron cdsubversion=Release cdbuild=20080702.1 
      GetDistroInfo distrofullname=Ubuntu-amd64 distro= cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Found a good ISO: Ubuntu 8.04.1 "Hardy Heron" - Release amd64 (20080702.1)
Found CD E:
Found CD cddrive=E:
Changing icon to Ubuntu.ico
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive D:\ubuntu
AlreadyInstalled=false OldInstallationDrive= InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1712; Volume name Vista64; Max #/chars in vol name 3243392; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem D:
Drive & Path name 1712; Volume name DATA; Max #/chars in vol name 3243396; Volume Serial # 2021506582; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 2953016; Volume name Vista64; Max #/chars in vol name 46; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = D:
FreeSpace in D: is 66711
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
GMT=-8
Country=US
Locale=en_US.UTF-8
TimeZone=America/Los_Angeles
Domain=localdomain
HostName=Bobby-PC
ComputerName=BOBBY-PC
EnvUsername=Bobby
UserDomain=Bobby-PC
UserInfoName=Bobby
UserProfileFolder=C:\Users\Bobby
UserProfileName=Bobby 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name Vista64; Max #/chars in vol name 3098376; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
IsValidFileSystem D:
Drive & Path name 1778; Volume name DATA; Max #/chars in vol name 3098380; Volume Serial # 2021506582; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
Adding drive D:
Drive list = C:|D:
ChangeInstallationDrive to D:
ChangeInstallationSize to 15
PopulateDistroList
DistroList = Ubuntu
PopulateLanguageListBox
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
LeaveMainPage
Locale=en_US.UTF-8
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
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
      Is Valid CD C:
CDInfo cleared
      Is Valid CD E:
      IsValid Ubuntu 8.04.1 "Hardy Heron" - Release amd64 (20080702.1)
      cdversion=8.04.1 cddistro=Ubuntu cdarch=amd64 cdcodename=Hardy Heron cdsubversion=Release cdbuild=20080702.1 
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Found a good ISO: Ubuntu 8.04.1 "Hardy Heron" - Release amd64 (20080702.1)
Found CD E:
Found CD cddrive=E:
Installing in automatic mode from CD
CheckCD
check_internet_connection
Dialer online
connected
md5=fcdd21bfd391a3618ee13159d7030ab9
Checking md5 of E:\casper\filesystem.squashfs
CheckCD raw status = success:E:\casper\filesystem.squashfs
CheckCD status = success
CD2ISO D:\ubuntu\install\installation.iso
CD2ISO finished successfully
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Checking/Downloading Ubuntu-8.04.1
Skipmd5 is true, using D:\ubuntu\install\installation.iso
CopyKernel isokernel=casper\vmlinuz, iso=D:\ubuntu\install\installation.iso, cddrive=E:
Extracting with 7z kernel/initrd from D:\ubuntu\install\installation.iso
UncompressFilesPriorInstall
Drive & Path name success; Volume name DATA; Max #/chars in vol name bobby; Volume Serial # 2021506582; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive D: has filesystem NTFS
rootSize=14000 homesize=0, swapsize=1000, usrsize=0
DoMenuLst D:\ubuntu\install\boot\grub\menu.lst
editBootDrive
editBootDrive Vista
CopyWubildr
CopyWubildrMbr
editBCD
C:\Users\Bobby\AppData\Local\Temp\nsdBC0D.tmp\wubibcd.exe 
 1:0 
 2:Employing Vista x64 sysnative workaround.
Operation completed successfully. New ID is {9cbc34b0-847c-11dd-abaa-0022150389be}
 
 3:HDD 
 4:3
vistaBootDriveCode = {9cbc34b0-847c-11dd-abaa-0022150389be} <=> peration completed successfully. New I
vistaBootDriveCode {9cbc34b0-847c-11dd-abaa-0022150389be}
Drive & Path name /Users/Bobby; Volume name DATA; Max #/chars in vol name success; Volume Serial # 2021506582; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 255
Drive D: has filesystem NTFS
rootSize=14000 homesize=0, swapsize=1000, usrsize=0
AllocFile filename=D:\ubuntu\disks\root.disk size=14000
AllocFile status=success
AllocFile filename=D:\ubuntu\disks\home.disk size=0
AllocFile filename=D:\ubuntu\disks\swap.disk size=1000
AllocFile status=success
UncompressFilesAfterInstall
EjectCD
Ejecting CDHandle=292 for drive=E:
EjectCD DeviceIoControl exited with code 1 (1==success)
Installation completed successfully!
============ Installer ============
PLUGINSDIR=C:\Users\Bobby\AppData\Local\Temp\nssE002.tmp
detect_all
Parsing cmdline "C:\Users\Bobby\AppData\Local\Temp\7zSDBDB.tmp\wubi.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=-1 MB
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD E:
      IsValid Ubuntu 8.04.1 "Hardy Heron" - Release amd64 (20080702.1)
      cdversion=8.04.1 cddistro=Ubuntu cdarch=amd64 cdcodename=Hardy Heron cdsubversion=Release cdbuild=20080702.1 
      GetDistroInfo distrofullname=Ubuntu-amd64 distro= cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Found a good ISO: Ubuntu 8.04.1 "Hardy Heron" - Release amd64 (20080702.1)
Found CD E:
Found CD cddrive=E:
Changing icon to Ubuntu.ico
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive D:\ubuntu
Found InstallationDrive D:\ubuntu
AlreadyInstalled=true OldInstallationDrive=D: InstallCompleted=true
IsValidFileSystem C:
Drive & Path name 1712; Volume name Vista64; Max #/chars in vol name 6731312; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem D:
Drive & Path name 1712; Volume name DATA; Max #/chars in vol name 6731316; Volume Serial # 2021506582; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 6426424; Volume name Vista64; Max #/chars in vol name 44; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = D:
FreeSpace in D: is 51703
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
GMT=-8
Country=US
Locale=en_US.UTF-8
TimeZone=America/Los_Angeles
Domain=localdomain
HostName=Bobby-PC
ComputerName=BOBBY-PC
EnvUsername=Bobby
UserDomain=Bobby-PC
UserInfoName=Bobby
UserProfileFolder=C:\Users\Bobby
UserProfileName=Bobby 
detect_all finished
ShowMainPage
Existing installation detected, calling old uninstaller and quitting.
============ Uninstaller ============
PLUGINSDIR=C:\Users\Bobby\AppData\Local\Temp\nscE436.tmp
Could not find \ubuntu, quitting...
============ Installer ============
PLUGINSDIR=C:\Users\Bobby\AppData\Local\Temp\nseA4C.tmp
detect_all
Parsing cmdline "C:\Users\Bobby\AppData\Local\Temp\7zS606.tmp\wubi.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=-1 MB
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD E:
      IsValid Ubuntu 8.04.1 "Hardy Heron" - Release amd64 (20080702.1)
      cdversion=8.04.1 cddistro=Ubuntu cdarch=amd64 cdcodename=Hardy Heron cdsubversion=Release cdbuild=20080702.1 
      GetDistroInfo distrofullname=Ubuntu-amd64 distro= cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Found a good ISO: Ubuntu 8.04.1 "Hardy Heron" - Release amd64 (20080702.1)
Found CD E:
Found CD cddrive=E:
Changing icon to Ubuntu.ico
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive D:\ubuntu
Found InstallationDrive D:\ubuntu
AlreadyInstalled=true OldInstallationDrive=D: InstallCompleted=true
IsValidFileSystem C:
Drive & Path name 1712; Volume name Vista64; Max #/chars in vol name 5536520; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem D:
Drive & Path name 1712; Volume name DATA; Max #/chars in vol name 5536524; Volume Serial # 2021506582; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 5316816; Volume name Vista64; Max #/chars in vol name 44; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = D:
FreeSpace in D: is 51703
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
GMT=-8
Country=US
Locale=en_US.UTF-8
TimeZone=America/Los_Angeles
Domain=localdomain
HostName=Bobby-PC
ComputerName=BOBBY-PC
EnvUsername=Bobby
UserDomain=Bobby-PC
UserInfoName=Bobby
UserProfileFolder=C:\Users\Bobby
UserProfileName=Bobby 
detect_all finished
ShowMainPage
Existing installation detected, calling old uninstaller and quitting.
============ Uninstaller ============
PLUGINSDIR=C:\Users\Bobby\AppData\Local\Temp\nseE90.tmp
Could not find \ubuntu, quitting...
============ Installer ============
PLUGINSDIR=C:\Users\Bobby\AppData\Local\Temp\nsw5236.tmp
detect_all
Parsing cmdline "C:\Users\Bobby\AppData\Local\Temp\7zS4BED.tmp\wubi.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=-1 MB
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD E:
      IsValid Ubuntu 8.04.1 "Hardy Heron" - Release amd64 (20080702.1)
      cdversion=8.04.1 cddistro=Ubuntu cdarch=amd64 cdcodename=Hardy Heron cdsubversion=Release cdbuild=20080702.1 
      GetDistroInfo distrofullname=Ubuntu-amd64 distro= cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Found a good ISO: Ubuntu 8.04.1 "Hardy Heron" - Release amd64 (20080702.1)
Found CD E:
Found CD cddrive=E:
Changing icon to Ubuntu.ico
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive D:\ubuntu
Found InstallationDrive D:\ubuntu
AlreadyInstalled=true OldInstallationDrive=D: InstallCompleted=true
IsValidFileSystem C:
Drive & Path name 1712; Volume name Vista64; Max #/chars in vol name 7094784; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem D:
Drive & Path name 1712; Volume name DATA; Max #/chars in vol name 7094788; Volume Serial # 2021506582; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 6429000; Volume name Vista64; Max #/chars in vol name 29; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = D:
FreeSpace in D: is 51693
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
GMT=-8
Country=US
Locale=en_US.UTF-8
TimeZone=America/Los_Angeles
Domain=localdomain
HostName=Bobby-PC
ComputerName=BOBBY-PC
EnvUsername=Bobby
UserDomain=Bobby-PC
UserInfoName=Bobby
UserProfileFolder=C:\Users\Bobby
UserProfileName=Bobby 
detect_all finished
ShowMainPage
Existing installation detected, calling old uninstaller and quitting.
============ Uninstaller ============
PLUGINSDIR=C:\Users\Bobby\AppData\Local\Temp\nsw56C8.tmp
Could not find \ubuntu, quitting...
============ Uninstaller ============
PLUGINSDIR=C:\Users\Bobby\AppData\Local\Temp\nsx8019.tmp
Could not find \ubuntu, quitting...
============ Uninstaller ============
PLUGINSDIR=C:\Users\Bobby\AppData\Local\Temp\nss4B82.tmp
Could not find \ubuntu, quitting...
============ Uninstaller ============
PLUGINSDIR=C:\Users\Bobby\AppData\Local\Temp\nsi60A.tmp
Could not find \ubuntu, quitting...
============ Uninstaller ============
PLUGINSDIR=C:\Users\Bobby\AppData\Local\Temp\nsd4BFF.tmp
Could not find \ubuntu, quitting...
============ Uninstaller ============
PLUGINSDIR=C:\Users\Bobby\AppData\Local\Temp\nsj450D.tmp
Could not find \ubuntu, quitting...
============ Uninstaller ============
PLUGINSDIR=C:\Users\Bobby\AppData\Local\Temp\nsk8C8.tmp
Could not find \ubuntu, quitting...
============ Uninstaller ============
PLUGINSDIR=C:\Users\Bobby\AppData\Local\Temp\nsa27EC.tmp
Could not find \ubuntu, quitting...
============ Uninstaller ============
PLUGINSDIR=C:\Users\Bobby\AppData\Local\Temp\nsqAC38.tmp
Could not find \ubuntu, quitting...
============ Uninstaller ============
PLUGINSDIR=C:\Users\Bobby\AppData\Local\Temp\nsfC4A7.tmp
Could not find \ubuntu, quitting...
============ Uninstaller ============
PLUGINSDIR=C:\Users\Bobby\AppData\Local\Temp\nsa28C6.tmp
Could not find \ubuntu, quitting...
============ Uninstaller ============
PLUGINSDIR=C:\Users\Bobby\AppData\Local\Temp\nsxB26F.tmp
Could not find \ubuntu, quitting...
============ Uninstaller ============
PLUGINSDIR=C:\Users\Bobby\AppData\Local\Temp\nscC4D6.tmp
Could not find \ubuntu, quitting...
============ Uninstaller ============
PLUGINSDIR=C:\Users\Bobby\AppData\Local\Temp\nsoA91C.tmp
Could not find \ubuntu, quitting...
============ Installer ============
PLUGINSDIR=C:\Users\Bobby\AppData\Local\Temp\nsi64A.tmp
detect_all
Parsing cmdline "C:\Users\Bobby\AppData\Local\Temp\7zSFFF2.tmp\wubi.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=-1 MB
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD E:
      IsValid Ubuntu 8.04.1 "Hardy Heron" - Release amd64 (20080702.1)
      cdversion=8.04.1 cddistro=Ubuntu cdarch=amd64 cdcodename=Hardy Heron cdsubversion=Release cdbuild=20080702.1 
      GetDistroInfo distrofullname=Ubuntu-amd64 distro= cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Found a good ISO: Ubuntu 8.04.1 "Hardy Heron" - Release amd64 (20080702.1)
Found CD E:
Found CD cddrive=E:
Changing icon to Ubuntu.ico
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive D:\ubuntu
AlreadyInstalled=false OldInstallationDrive= InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1712; Volume name Vista64; Max #/chars in vol name 2623408; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem D:
Drive & Path name 1712; Volume name DATA; Max #/chars in vol name 2623412; Volume Serial # 2021506582; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 2562376; Volume name Vista64; Max #/chars in vol name 38; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = D:
FreeSpace in D: is 40951
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
GMT=-8
Country=US
Locale=en_US.UTF-8
TimeZone=America/Los_Angeles
Domain=localdomain
HostName=Bobby-PC
ComputerName=BOBBY-PC
EnvUsername=Bobby
UserDomain=Bobby-PC
UserInfoName=Bobby
UserProfileFolder=C:\Users\Bobby
UserProfileName=Bobby 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name Vista64; Max #/chars in vol name 2895632; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
IsValidFileSystem D:
Drive & Path name 1778; Volume name DATA; Max #/chars in vol name 2895636; Volume Serial # 2021506582; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
Adding drive D:
Drive list = C:|D:
ChangeInstallationDrive to D:
ChangeInstallationSize to 15
PopulateDistroList
DistroList = Ubuntu
PopulateLanguageListBox
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
LeaveMainPage
Locale=en_US.UTF-8
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
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
      Is Valid CD C:
CDInfo cleared
      Is Valid CD E:
      IsValid Ubuntu 8.04.1 "Hardy Heron" - Release amd64 (20080702.1)
      cdversion=8.04.1 cddistro=Ubuntu cdarch=amd64 cdcodename=Hardy Heron cdsubversion=Release cdbuild=20080702.1 
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Found a good ISO: Ubuntu 8.04.1 "Hardy Heron" - Release amd64 (20080702.1)
Found CD E:
Found CD cddrive=E:
Installing in automatic mode from CD
CheckCD
check_internet_connection
Dialer online
connected
md5=fcdd21bfd391a3618ee13159d7030ab9
Checking md5 of E:\casper\filesystem.squashfs
CheckCD raw status = success:E:\casper\filesystem.squashfs
CheckCD status = success
CD2ISO D:\ubuntu\install\installation.iso
CD2ISO finished successfully
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Checking/Downloading Ubuntu-8.04.1
Skipmd5 is true, using D:\ubuntu\install\installation.iso
CopyKernel isokernel=casper\vmlinuz, iso=D:\ubuntu\install\installation.iso, cddrive=E:
Extracting with 7z kernel/initrd from D:\ubuntu\install\installation.iso
UncompressFilesPriorInstall
Drive & Path name success; Volume name DATA; Max #/chars in vol name rcook; Volume Serial # 2021506582; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
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
Drive & Path name success; Volume name DATA; Max #/chars in vol name rcook; Volume Serial # 2021506582; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive D: has filesystem NTFS
rootSize=14000 homesize=0, swapsize=1000, usrsize=0
AllocFile filename=D:\ubuntu\disks\root.disk size=14000
AllocFile status=success
AllocFile filename=D:\ubuntu\disks\home.disk size=0
AllocFile filename=D:\ubuntu\disks\swap.disk size=1000
AllocFile status=success
UncompressFilesAfterInstall
EjectCD
Ejecting CDHandle=288 for drive=E:
EjectCD DeviceIoControl exited with code 1 (1==success)
Installation completed successfully!
============ Uninstaller ============
PLUGINSDIR=C:\Users\Bobby\AppData\Local\Temp\nsv13DF.tmp
Could not find \ubuntu, quitting...
============ Installer ============
PLUGINSDIR=C:\Users\Bobby\AppData\Local\Temp\nsc140E.tmp
detect_all
Parsing cmdline "C:\Users\Bobby\AppData\Local\Temp\7zSDA6.tmp\wubi.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=-1 MB
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD E:
      IsValid Ubuntu 8.04.1 "Hardy Heron" - Release amd64 (20080702.1)
      cdversion=8.04.1 cddistro=Ubuntu cdarch=amd64 cdcodename=Hardy Heron cdsubversion=Release cdbuild=20080702.1 
      GetDistroInfo distrofullname=Ubuntu-amd64 distro= cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Found a good ISO: Ubuntu 8.04.1 "Hardy Heron" - Release amd64 (20080702.1)
Found CD E:
Found CD cddrive=E:
Changing icon to Ubuntu.ico
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive D:\ubuntu
AlreadyInstalled=false OldInstallationDrive= InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1712; Volume name Vista64; Max #/chars in vol name 5929104; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem D:
Drive & Path name 1712; Volume name DATA; Max #/chars in vol name 5929108; Volume Serial # 2021506582; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 5644472; Volume name Vista64; Max #/chars in vol name 35; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = D:
FreeSpace in D: is 40352
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
GMT=-8
Country=US
Locale=en_US.UTF-8
TimeZone=America/Los_Angeles
Domain=localdomain
HostName=Bobby-PC
ComputerName=BOBBY-PC
EnvUsername=Bobby
UserDomain=Bobby-PC
UserInfoName=Bobby
UserProfileFolder=C:\Users\Bobby
UserProfileName=Bobby 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name Vista64; Max #/chars in vol name 5916976; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
IsValidFileSystem D:
Drive & Path name 1778; Volume name DATA; Max #/chars in vol name 5916980; Volume Serial # 2021506582; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
Adding drive D:
Drive list = C:|D:
ChangeInstallationDrive to D:
ChangeInstallationSize to 15
PopulateDistroList
DistroList = Ubuntu
PopulateLanguageListBox
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
ChangeInstallationDrive to C:
ChangeInstallationSize to 15
LeaveMainPage
ChangeInstallationSize to 10
LeaveMainPage
Locale=en_US.UTF-8
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
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
      IsValid Ubuntu 8.04.1 "Hardy Heron" - Release amd64 (20080702.1)
      cdversion=8.04.1 cddistro=Ubuntu cdarch=amd64 cdcodename=Hardy Heron cdsubversion=Release cdbuild=20080702.1 
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Found a good ISO: Ubuntu 8.04.1 "Hardy Heron" - Release amd64 (20080702.1)
Found CD E:
Found CD cddrive=E:
Installing in automatic mode from CD
CheckCD
check_internet_connection
Dialer online
connected
md5=fcdd21bfd391a3618ee13159d7030ab9
Checking md5 of E:\casper\filesystem.squashfs
CheckCD raw status = success:E:\casper\filesystem.squashfs
CheckCD status = success
CD2ISO C:\ubuntu\install\installation.iso
CD2ISO finished successfully
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Checking/Downloading Ubuntu-8.04.1
Skipmd5 is true, using C:\ubuntu\install\installation.iso
CopyKernel isokernel=casper\vmlinuz, iso=C:\ubuntu\install\installation.iso, cddrive=E:
Extracting with 7z kernel/initrd from C:\ubuntu\install\installation.iso
UncompressFilesPriorInstall
Drive & Path name success; Volume name Vista64; Max #/chars in vol name rcook; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive C: has filesystem NTFS
rootSize=9000 homesize=0, swapsize=1000, usrsize=0
DoMenuLst C:\ubuntu\install\boot\grub\menu.lst
editBootDrive
editBootDrive NT
CopyWubildr
CopyWubildrMbr
EditBootIni
Drive & Path name success; Volume name Vista64; Max #/chars in vol name rcook; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive C: has filesystem NTFS
rootSize=9000 homesize=0, swapsize=1000, usrsize=0
AllocFile filename=C:\ubuntu\disks\root.disk size=9000
AllocFile status=success
AllocFile filename=C:\ubuntu\disks\home.disk size=0
AllocFile filename=C:\ubuntu\disks\swap.disk size=1000
AllocFile status=success
UncompressFilesAfterInstall
EjectCD
Ejecting CDHandle=492 for drive=E:
EjectCD DeviceIoControl exited with code 1 (1==success)
Installation completed successfully!
============ Uninstaller ============
PLUGINSDIR=C:\Users\Bobby\AppData\Local\Temp\nsl9213.tmp
un.install
un.BackupIso
un.CleanBcd
un.RemoveInstallationFolder C:\ubuntu
un.CleanThisDrive C:\
un.CleanThisDrive D:\
un.CleanRegistry Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
============ Installer ============
PLUGINSDIR=C:\Users\Bobby\AppData\Local\Temp\nsw1D70.tmp
detect_all
Parsing cmdline "C:\Users\Bobby\AppData\Local\Temp\7zS1718.tmp\wubi.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=-1 MB
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD E:
      IsValid Ubuntu 8.04.1 "Hardy Heron" - Release amd64 (20080702.1)
      cdversion=8.04.1 cddistro=Ubuntu cdarch=amd64 cdcodename=Hardy Heron cdsubversion=Release cdbuild=20080702.1 
      GetDistroInfo distrofullname=Ubuntu-amd64 distro= cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Found a good ISO: Ubuntu 8.04.1 "Hardy Heron" - Release amd64 (20080702.1)
Found CD E:
Found CD cddrive=E:
Changing icon to Ubuntu.ico
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive D:\ubuntu
AlreadyInstalled=false OldInstallationDrive= InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1712; Volume name Vista64; Max #/chars in vol name 3026552; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem D:
Drive & Path name 1712; Volume name DATA; Max #/chars in vol name 3026556; Volume Serial # 2021506582; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 2955592; Volume name Vista64; Max #/chars in vol name 31; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = D:
FreeSpace in D: is 40352
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
GMT=-8
Country=US
Locale=en_US.UTF-8
TimeZone=America/Los_Angeles
Domain=localdomain
HostName=Bobby-PC
ComputerName=BOBBY-PC
EnvUsername=Bobby
UserDomain=Bobby-PC
UserInfoName=Bobby
UserProfileFolder=C:\Users\Bobby
UserProfileName=Bobby 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name Vista64; Max #/chars in vol name 3865496; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
IsValidFileSystem D:
Drive & Path name 1778; Volume name DATA; Max #/chars in vol name 3865500; Volume Serial # 2021506582; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
Adding drive D:
Drive list = C:|D:
ChangeInstallationDrive to D:
ChangeInstallationSize to 15
PopulateDistroList
DistroList = Ubuntu
PopulateLanguageListBox
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
ChangeInstallationDrive to C:
ChangeInstallationSize to 15
LeaveMainPage
ChangeInstallationSize to 10
LeaveMainPage
Locale=en_US.UTF-8
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
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
      IsValid Ubuntu 8.04.1 "Hardy Heron" - Release amd64 (20080702.1)
      cdversion=8.04.1 cddistro=Ubuntu cdarch=amd64 cdcodename=Hardy Heron cdsubversion=Release cdbuild=20080702.1 
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Found a good ISO: Ubuntu 8.04.1 "Hardy Heron" - Release amd64 (20080702.1)
Found CD E:
Found CD cddrive=E:
Installing in automatic mode from CD
CheckCD
check_internet_connection
Dialer online
connected
md5=fcdd21bfd391a3618ee13159d7030ab9
Checking md5 of E:\casper\filesystem.squashfs
CheckCD raw status = File check failed
CheckCD status = failure
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Checking/Downloading Ubuntu-8.04.1
retrieve_partial_files
check_internet_connection
Dialer online
connected
Trying remote metalink: http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
get_md5 http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
Downloading: trymefirst= url=http://releases.ubuntu.com/8.04.1/MD5SUMS-metalink.gpg md5=
Download status=connect() timed out!
Error downloading http://releases.ubuntu.com/8.04.1/MD5SUMS-metalink.gpg, connect
Trying remote metalink2: http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-amd64.metalink
get_md5 http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-amd64.metalink
Downloading: trymefirst= url=http://cdimage.ubuntu.com/hardy/daily-live/current/MD5SUMS-metalink.gpg md5=
Download status=connect() timed out!
Error downloading http://cdimage.ubuntu.com/hardy/daily-live/current/MD5SUMS-metalink.gpg, connect
The download was interrupted with the error: 
============ Installer ============
PLUGINSDIR=C:\Users\Bobby\AppData\Local\Temp\nszE5DD.tmp
detect_all
Parsing cmdline "C:\Users\Bobby\AppData\Local\Temp\7zSDFB4.tmp\wubi.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=-1 MB
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD E:
      IsValid Ubuntu 8.04.1 "Hardy Heron" - Release amd64 (20080702.1)
      cdversion=8.04.1 cddistro=Ubuntu cdarch=amd64 cdcodename=Hardy Heron cdsubversion=Release cdbuild=20080702.1 
      GetDistroInfo distrofullname=Ubuntu-amd64 distro= cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Found a good ISO: Ubuntu 8.04.1 "Hardy Heron" - Release amd64 (20080702.1)
Found CD E:
Found CD cddrive=E:
Changing icon to Ubuntu.ico
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
Found InstallationDrive C:\ubuntu
AlreadyInstalled=true OldInstallationDrive=C: InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1712; Volume name Vista64; Max #/chars in vol name 6399168; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem D:
Drive & Path name 1712; Volume name DATA; Max #/chars in vol name 6399172; Volume Serial # 2021506582; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 6035784; Volume name Vista64; Max #/chars in vol name 30; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = D:
FreeSpace in D: is 40352
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
GMT=-8
Country=US
Locale=en_US.UTF-8
TimeZone=America/Los_Angeles
Domain=localdomain
HostName=Bobby-PC
ComputerName=BOBBY-PC
EnvUsername=Bobby
UserDomain=Bobby-PC
UserInfoName=Bobby
UserProfileFolder=C:\Users\Bobby
UserProfileName=Bobby 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name Vista64; Max #/chars in vol name 6415432; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
IsValidFileSystem D:
Drive & Path name 1778; Volume name DATA; Max #/chars in vol name 6415436; Volume Serial # 2021506582; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
Adding drive D:
Drive list = C:|D:
ChangeInstallationDrive to C:
ChangeInstallationSize to 10
PopulateDistroList
DistroList = Ubuntu
PopulateLanguageListBox
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
Locale=en_US.UTF-8
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
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
      IsValid Ubuntu 8.04.1 "Hardy Heron" - Release amd64 (20080702.1)
      cdversion=8.04.1 cddistro=Ubuntu cdarch=amd64 cdcodename=Hardy Heron cdsubversion=Release cdbuild=20080702.1 
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Found a good ISO: Ubuntu 8.04.1 "Hardy Heron" - Release amd64 (20080702.1)
Found CD E:
Found CD cddrive=E:
Installing in automatic mode from CD
CheckCD
check_internet_connection
Dialer online
connected
md5=fcdd21bfd391a3618ee13159d7030ab9
Checking md5 of E:\casper\filesystem.squashfs
CheckCD raw status = success:E:\casper\filesystem.squashfs
CheckCD status = success
CD2ISO C:\ubuntu\install\installation.iso
CD2ISO finished successfully
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Checking/Downloading Ubuntu-8.04.1
Skipmd5 is true, using C:\ubuntu\install\installation.iso
CopyKernel isokernel=casper\vmlinuz, iso=C:\ubuntu\install\installation.iso, cddrive=E:
Extracting with 7z kernel/initrd from C:\ubuntu\install\installation.iso
UncompressFilesPriorInstall
Drive & Path name success; Volume name Vista64; Max #/chars in vol name rcook; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive C: has filesystem NTFS
rootSize=9000 homesize=0, swapsize=1000, usrsize=0
DoMenuLst C:\ubuntu\install\boot\grub\menu.lst
editBootDrive
editBootDrive NT
CopyWubildr
CopyWubildrMbr
EditBootIni
Drive & Path name success; Volume name Vista64; Max #/chars in vol name rcook; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive C: has filesystem NTFS
rootSize=9000 homesize=0, swapsize=1000, usrsize=0
AllocFile filename=C:\ubuntu\disks\root.disk size=9000
AllocFile status=success
AllocFile filename=C:\ubuntu\disks\home.disk size=0
AllocFile filename=C:\ubuntu\disks\swap.disk size=1000
AllocFile status=success
UncompressFilesAfterInstall
EjectCD
Ejecting CDHandle=288 for drive=E:
EjectCD DeviceIoControl exited with code 1 (1==success)
Installation completed successfully!
============ Installer ============
PLUGINSDIR=C:\Users\Bobby\AppData\Local\Temp\nsv24A1.tmp
detect_all
Parsing cmdline "C:\Users\Bobby\AppData\Local\Temp\7zS1F81.tmp\wubi.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=-1 MB
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD E:
      IsValid Ubuntu 8.04.1 "Hardy Heron" - Release amd64 (20080702.1)
      cdversion=8.04.1 cddistro=Ubuntu cdarch=amd64 cdcodename=Hardy Heron cdsubversion=Release cdbuild=20080702.1 
      GetDistroInfo distrofullname=Ubuntu-amd64 distro= cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Found a good ISO: Ubuntu 8.04.1 "Hardy Heron" - Release amd64 (20080702.1)
Found CD E:
Found CD cddrive=E:
Changing icon to Ubuntu.ico
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive D:\ubuntu
AlreadyInstalled=false OldInstallationDrive= InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1712; Volume name Vista64; Max #/chars in vol name 6519440; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem D:
Drive & Path name 1712; Volume name DATA; Max #/chars in vol name 6519444; Volume Serial # 2021506582; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 6232392; Volume name Vista64; Max #/chars in vol name 28; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = D:
FreeSpace in D: is 40352
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
GMT=-8
Country=US
Locale=en_US.UTF-8
TimeZone=America/Los_Angeles
Domain=localdomain
HostName=Bobby-PC
ComputerName=BOBBY-PC
EnvUsername=Bobby
UserDomain=Bobby-PC
UserInfoName=Bobby
UserProfileFolder=C:\Users\Bobby
UserProfileName=Bobby 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name Vista64; Max #/chars in vol name 6512552; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
IsValidFileSystem D:
Drive & Path name 1778; Volume name DATA; Max #/chars in vol name 6512556; Volume Serial # 2021506582; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
Adding drive D:
Drive list = C:|D:
ChangeInstallationDrive to D:
ChangeInstallationSize to 15
PopulateDistroList
DistroList = Ubuntu
PopulateLanguageListBox
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
ChangeInstallationDrive to C:
ChangeInstallationSize to 15
LeaveMainPage
Locale=en_US.UTF-8
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
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
      IsValid Ubuntu 8.04.1 "Hardy Heron" - Release amd64 (20080702.1)
      cdversion=8.04.1 cddistro=Ubuntu cdarch=amd64 cdcodename=Hardy Heron cdsubversion=Release cdbuild=20080702.1 
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Found a good ISO: Ubuntu 8.04.1 "Hardy Heron" - Release amd64 (20080702.1)
Found CD E:
Found CD cddrive=E:
Installing in automatic mode from CD
CheckCD
check_internet_connection
Dialer online
connected
md5=fcdd21bfd391a3618ee13159d7030ab9
Checking md5 of E:\casper\filesystem.squashfs
CheckCD raw status = success:E:\casper\filesystem.squashfs
CheckCD status = success
CD2ISO C:\ubuntu\install\installation.iso
CD2ISO finished successfully
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Checking/Downloading Ubuntu-8.04.1
Skipmd5 is true, using C:\ubuntu\install\installation.iso
CopyKernel isokernel=casper\vmlinuz, iso=C:\ubuntu\install\installation.iso, cddrive=E:
Extracting with 7z kernel/initrd from C:\ubuntu\install\installation.iso
UncompressFilesPriorInstall
Drive & Path name success; Volume name Vista64; Max #/chars in vol name rcook; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive C: has filesystem NTFS
rootSize=14000 homesize=0, swapsize=1000, usrsize=0
DoMenuLst C:\ubuntu\install\boot\grub\menu.lst
editBootDrive
editBootDrive NT
CopyWubildr
CopyWubildrMbr
EditBootIni
Drive & Path name success; Volume name Vista64; Max #/chars in vol name rcook; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive C: has filesystem NTFS
rootSize=14000 homesize=0, swapsize=1000, usrsize=0
AllocFile filename=C:\ubuntu\disks\root.disk size=14000
AllocFile status=success
AllocFile filename=C:\ubuntu\disks\home.disk size=0
AllocFile filename=C:\ubuntu\disks\swap.disk size=1000
AllocFile status=success
UncompressFilesAfterInstall
EjectCD
Ejecting CDHandle=520 for drive=E:
EjectCD DeviceIoControl exited with code 1 (1==success)
Installation completed successfully!
============ Installer ============
PLUGINSDIR=C:\Users\Bobby\AppData\Local\Temp\nss208C.tmp
detect_all
Parsing cmdline "C:\Users\Bobby\AppData\Local\Temp\7zS1BD9.tmp\wubi.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=-1 MB
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD E:
      IsValid Ubuntu 8.04.1 "Hardy Heron" - Release amd64 (20080702.1)
      cdversion=8.04.1 cddistro=Ubuntu cdarch=amd64 cdcodename=Hardy Heron cdsubversion=Release cdbuild=20080702.1 
      GetDistroInfo distrofullname=Ubuntu-amd64 distro= cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Found a good ISO: Ubuntu 8.04.1 "Hardy Heron" - Release amd64 (20080702.1)
Found CD E:
Found CD cddrive=E:
Changing icon to Ubuntu.ico
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
Found InstallationDrive C:\ubuntu
AlreadyInstalled=true OldInstallationDrive=C: InstallCompleted=true
IsValidFileSystem C:
Drive & Path name 1712; Volume name Vista64; Max #/chars in vol name 9370848; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem D:
Drive & Path name 1712; Volume name DATA; Max #/chars in vol name 9370852; Volume Serial # 2021506582; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 9310008; Volume name Vista64; Max #/chars in vol name 32; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = D:
FreeSpace in D: is 39195
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
GMT=-8
Country=US
Locale=en_US.UTF-8
TimeZone=America/Los_Angeles
Domain=localdomain
HostName=Bobby-PC
ComputerName=BOBBY-PC
EnvUsername=Bobby
UserDomain=Bobby-PC
UserInfoName=Bobby
UserProfileFolder=C:\Users\Bobby
UserProfileName=Bobby 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name Vista64; Max #/chars in vol name 9611776; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
IsValidFileSystem D:
Drive & Path name 1778; Volume name DATA; Max #/chars in vol name 9611780; Volume Serial # 2021506582; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
Adding drive D:
Drive list = C:|D:
ChangeInstallationDrive to C:
ChangeInstallationSize to 5
PopulateDistroList
DistroList = Ubuntu
PopulateLanguageListBox
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
============ Installer ============
PLUGINSDIR=C:\Users\Bobby\AppData\Local\Temp\nsy48D4.tmp
detect_all
Parsing cmdline "C:\Users\Bobby\AppData\Local\Temp\7zS4691.tmp\wubi.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=-1 MB
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD E:
      IsValid Ubuntu 8.04.1 "Hardy Heron" - Release amd64 (20080702.1)
      cdversion=8.04.1 cddistro=Ubuntu cdarch=amd64 cdcodename=Hardy Heron cdsubversion=Release cdbuild=20080702.1 
      GetDistroInfo distrofullname=Ubuntu-amd64 distro= cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Found a good ISO: Ubuntu 8.04.1 "Hardy Heron" - Release amd64 (20080702.1)
Found CD E:
Found CD cddrive=E:
Changing icon to Ubuntu.ico
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive D:\ubuntu
AlreadyInstalled=false OldInstallationDrive= InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1712; Volume name Vista64; Max #/chars in vol name 6542384; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem D:
Drive & Path name 1712; Volume name DATA; Max #/chars in vol name 6542388; Volume Serial # 2021506582; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 5902136; Volume name Vista64; Max #/chars in vol name 34; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = D:
FreeSpace in D: is 40254
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
GMT=-8
Country=US
Locale=en_US.UTF-8
TimeZone=America/Los_Angeles
Domain=localdomain
HostName=Bobby-PC
ComputerName=BOBBY-PC
EnvUsername=Bobby
UserDomain=Bobby-PC
UserInfoName=Bobby
UserProfileFolder=C:\Users\Bobby
UserProfileName=Bobby 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name Vista64; Max #/chars in vol name 6424312; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
IsValidFileSystem D:
Drive & Path name 1778; Volume name DATA; Max #/chars in vol name 6424316; Volume Serial # 2021506582; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
Adding drive D:
Drive list = C:|D:
ChangeInstallationDrive to D:
ChangeInstallationSize to 15
PopulateDistroList
DistroList = Ubuntu
PopulateLanguageListBox
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
ChangeInstallationDrive to C:
ChangeInstallationSize to 15
LeaveMainPage
ChangeInstallationSize to 10
LeaveMainPage
ChangeInstallationSize to 15
LeaveMainPage
Locale=en_US.UTF-8
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
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
      IsValid Ubuntu 8.04.1 "Hardy Heron" - Release amd64 (20080702.1)
      cdversion=8.04.1 cddistro=Ubuntu cdarch=amd64 cdcodename=Hardy Heron cdsubversion=Release cdbuild=20080702.1 
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Found a good ISO: Ubuntu 8.04.1 "Hardy Heron" - Release amd64 (20080702.1)
Found CD E:
Found CD cddrive=E:
Installing in automatic mode from CD
CheckCD
check_internet_connection
Dialer offline
not connected
md5=fcdd21bfd391a3618ee13159d7030ab9
Checking md5 of E:\casper\filesystem.squashfs
CheckCD raw status = File check failed
CheckCD status = failure
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Checking/Downloading Ubuntu-8.04.1
retrieve_partial_files
check_internet_connection
Dialer offline
not connected
User cancelled Internet Connection Retry, quitting
============ Installer ============
PLUGINSDIR=C:\Users\Bobby\AppData\Local\Temp\nspD99.tmp
detect_all
Parsing cmdline "C:\Users\Bobby\AppData\Local\Temp\7zSA1D.tmp\wubi.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=-1 MB
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD E:
      IsValid Ubuntu 8.04.1 "Hardy Heron" - Release amd64 (20080702.1)
      cdversion=8.04.1 cddistro=Ubuntu cdarch=amd64 cdcodename=Hardy Heron cdsubversion=Release cdbuild=20080702.1 
      GetDistroInfo distrofullname=Ubuntu-amd64 distro= cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Found a good ISO: Ubuntu 8.04.1 "Hardy Heron" - Release amd64 (20080702.1)
Found CD E:
Found CD cddrive=E:
Changing icon to Ubuntu.ico
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
Found InstallationDrive C:\ubuntu
AlreadyInstalled=true OldInstallationDrive=C: InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1712; Volume name Vista64; Max #/chars in vol name 3406776; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem D:
Drive & Path name 1712; Volume name DATA; Max #/chars in vol name 3406780; Volume Serial # 2021506582; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 2564304; Volume name Vista64; Max #/chars in vol name 31; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = D:
FreeSpace in D: is 40254
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
GMT=-8
Country=US
Locale=en_US.UTF-8
TimeZone=America/Los_Angeles
Domain=localdomain
HostName=Bobby-PC
ComputerName=BOBBY-PC
EnvUsername=Bobby
UserDomain=Bobby-PC
UserInfoName=Bobby
UserProfileFolder=C:\Users\Bobby
UserProfileName=Bobby 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name Vista64; Max #/chars in vol name 2945128; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
IsValidFileSystem D:
Drive & Path name 1778; Volume name DATA; Max #/chars in vol name 2945132; Volume Serial # 2021506582; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
Adding drive D:
Drive list = C:|D:
ChangeInstallationDrive to C:
ChangeInstallationSize to 10
PopulateDistroList
DistroList = Ubuntu
PopulateLanguageListBox
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
Locale=en_US.UTF-8
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
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
      IsValid Ubuntu 8.04.1 "Hardy Heron" - Release amd64 (20080702.1)
      cdversion=8.04.1 cddistro=Ubuntu cdarch=amd64 cdcodename=Hardy Heron cdsubversion=Release cdbuild=20080702.1 
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Found a good ISO: Ubuntu 8.04.1 "Hardy Heron" - Release amd64 (20080702.1)
Found CD E:
Found CD cddrive=E:
Installing in automatic mode from CD
CheckCD
check_internet_connection
Dialer offline
not connected
md5=fcdd21bfd391a3618ee13159d7030ab9
Checking md5 of E:\casper\filesystem.squashfs
CheckCD raw status = success:E:\casper\filesystem.squashfs
CheckCD status = success
CD2ISO C:\ubuntu\install\installation.iso
CD2ISO finished successfully
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Checking/Downloading Ubuntu-8.04.1
Skipmd5 is true, using C:\ubuntu\install\installation.iso
CopyKernel isokernel=casper\vmlinuz, iso=C:\ubuntu\install\installation.iso, cddrive=E:
Extracting with 7z kernel/initrd from C:\ubuntu\install\installation.iso
UncompressFilesPriorInstall
Drive & Path name success; Volume name Vista64; Max #/chars in vol name bobby; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive C: has filesystem NTFS
rootSize=9000 homesize=0, swapsize=1000, usrsize=0
DoMenuLst C:\ubuntu\install\boot\grub\menu.lst
editBootDrive
editBootDrive NT
CopyWubildr
CopyWubildrMbr
EditBootIni
Drive & Path name success; Volume name Vista64; Max #/chars in vol name bobby; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive C: has filesystem NTFS
rootSize=9000 homesize=0, swapsize=1000, usrsize=0
AllocFile filename=C:\ubuntu\disks\root.disk size=9000
AllocFile status=success
AllocFile filename=C:\ubuntu\disks\home.disk size=0
AllocFile filename=C:\ubuntu\disks\swap.disk size=1000
AllocFile status=success
UncompressFilesAfterInstall
EjectCD
Ejecting CDHandle=288 for drive=E:
EjectCD DeviceIoControl exited with code 1 (1==success)
Installation completed successfully!
============ Installer ============
PLUGINSDIR=C:\Users\Bobby\AppData\Local\Temp\nsq7938.tmp
detect_all
Parsing cmdline "C:\Users\Bobby\AppData\Local\Temp\7zS72A1.tmp\wubi.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=-1 MB
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD E:
      IsValid Ubuntu 8.04.1 "Hardy Heron" - Release amd64 (20080702.1)
      cdversion=8.04.1 cddistro=Ubuntu cdarch=amd64 cdcodename=Hardy Heron cdsubversion=Release cdbuild=20080702.1 
      GetDistroInfo distrofullname=Ubuntu-amd64 distro= cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Found a good ISO: Ubuntu 8.04.1 "Hardy Heron" - Release amd64 (20080702.1)
Found CD E:
Found CD cddrive=E:
Changing icon to Ubuntu.ico
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive D:\ubuntu
AlreadyInstalled=false OldInstallationDrive= InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1712; Volume name Vista64; Max #/chars in vol name 3063544; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem D:
Drive & Path name 1712; Volume name DATA; Max #/chars in vol name 3063548; Volume Serial # 2021506582; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 2824448; Volume name Vista64; Max #/chars in vol name 31; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = D:
FreeSpace in D: is 40254
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
GMT=-8
Country=US
Locale=en_US.UTF-8
TimeZone=America/Los_Angeles
Domain=localdomain
HostName=Bobby-PC
ComputerName=BOBBY-PC
EnvUsername=Bobby
UserDomain=Bobby-PC
UserInfoName=Bobby
UserProfileFolder=C:\Users\Bobby
UserProfileName=Bobby 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name Vista64; Max #/chars in vol name 2978968; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
IsValidFileSystem D:
Drive & Path name 1778; Volume name DATA; Max #/chars in vol name 2978972; Volume Serial # 2021506582; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
Adding drive D:
Drive list = C:|D:
ChangeInstallationDrive to D:
ChangeInstallationSize to 15
PopulateDistroList
DistroList = Ubuntu
PopulateLanguageListBox
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
ChangeInstallationDrive to C:
ChangeInstallationSize to 15
LeaveMainPage
ChangeInstallationSize to 10
LeaveMainPage
Locale=en_US.UTF-8
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
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
      IsValid Ubuntu 8.04.1 "Hardy Heron" - Release amd64 (20080702.1)
      cdversion=8.04.1 cddistro=Ubuntu cdarch=amd64 cdcodename=Hardy Heron cdsubversion=Release cdbuild=20080702.1 
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Found a good ISO: Ubuntu 8.04.1 "Hardy Heron" - Release amd64 (20080702.1)
Found CD E:
Found CD cddrive=E:
Installing in automatic mode from CD
CheckCD
check_internet_connection
Dialer online
connected
md5=fcdd21bfd391a3618ee13159d7030ab9
Checking md5 of E:\casper\filesystem.squashfs
CheckCD raw status = success:E:\casper\filesystem.squashfs
CheckCD status = success
CD2ISO C:\ubuntu\install\installation.iso
CD2ISO finished successfully
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Checking/Downloading Ubuntu-8.04.1
Skipmd5 is true, using C:\ubuntu\install\installation.iso
CopyKernel isokernel=casper\vmlinuz, iso=C:\ubuntu\install\installation.iso, cddrive=E:
Extracting with 7z kernel/initrd from C:\ubuntu\install\installation.iso
UncompressFilesPriorInstall
Drive & Path name success; Volume name Vista64; Max #/chars in vol name rcook; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive C: has filesystem NTFS
rootSize=9000 homesize=0, swapsize=1000, usrsize=0
DoMenuLst C:\ubuntu\install\boot\grub\menu.lst
editBootDrive
editBootDrive NT
CopyWubildr
CopyWubildrMbr
EditBootIni
Drive & Path name success; Volume name Vista64; Max #/chars in vol name rcook; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive C: has filesystem NTFS
rootSize=9000 homesize=0, swapsize=1000, usrsize=0
AllocFile filename=C:\ubuntu\disks\root.disk size=9000
AllocFile status=success
AllocFile filename=C:\ubuntu\disks\home.disk size=0
AllocFile filename=C:\ubuntu\disks\swap.disk size=1000
AllocFile status=success
UncompressFilesAfterInstall
EjectCD
Ejecting CDHandle=596 for drive=E:
EjectCD DeviceIoControl exited with code 1 (1==success)
Installation completed successfully!
============ Uninstaller ============
PLUGINSDIR=C:\Users\Bobby\AppData\Local\Temp\nsq1288.tmp
un.install
un.BackupIso
un.CleanBcd
un.RemoveInstallationFolder C:\ubuntu
un.CleanThisDrive C:\
un.CleanThisDrive D:\
un.CleanRegistry Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
============ Installer ============
PLUGINSDIR=C:\Users\Bobby\AppData\Local\Temp\nsw3C56.tmp
detect_all
Parsing cmdline "C:\Users\Bobby\AppData\Local\Temp\7zS3810.tmp\wubi.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=-1 MB
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD E:
      IsValid Ubuntu 8.04.1 "Hardy Heron" - Release amd64 (20080702.1)
      cdversion=8.04.1 cddistro=Ubuntu cdarch=amd64 cdcodename=Hardy Heron cdsubversion=Release cdbuild=20080702.1 
      GetDistroInfo distrofullname=Ubuntu-amd64 distro= cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Found a good ISO: Ubuntu 8.04.1 "Hardy Heron" - Release amd64 (20080702.1)
Found CD E:
Found CD cddrive=E:
Changing icon to Ubuntu.ico
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive D:\ubuntu
AlreadyInstalled=false OldInstallationDrive= InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1712; Volume name Vista64; Max #/chars in vol name 3085784; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem D:
Drive & Path name 1712; Volume name DATA; Max #/chars in vol name 3085788; Volume Serial # 2021506582; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 2824520; Volume name Vista64; Max #/chars in vol name 29; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = D:
FreeSpace in D: is 40254
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
GMT=-8
Country=US
Locale=en_US.UTF-8
TimeZone=America/Los_Angeles
Domain=localdomain
HostName=Bobby-PC
ComputerName=BOBBY-PC
EnvUsername=Bobby
UserDomain=Bobby-PC
UserInfoName=Bobby
UserProfileFolder=C:\Users\Bobby
UserProfileName=Bobby 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name Vista64; Max #/chars in vol name 3130704; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
IsValidFileSystem D:
Drive & Path name 1778; Volume name DATA; Max #/chars in vol name 3130708; Volume Serial # 2021506582; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
Adding drive D:
Drive list = C:|D:
ChangeInstallationDrive to D:
ChangeInstallationSize to 15
PopulateDistroList
DistroList = Ubuntu
PopulateLanguageListBox
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
ChangeInstallationDrive to C:
ChangeInstallationSize to 15
LeaveMainPage
ChangeInstallationSize to 15
LeaveMainPage
ChangeInstallationSize to 10
LeaveMainPage
Locale=en_US.UTF-8
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
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
      IsValid Ubuntu 8.04.1 "Hardy Heron" - Release amd64 (20080702.1)
      cdversion=8.04.1 cddistro=Ubuntu cdarch=amd64 cdcodename=Hardy Heron cdsubversion=Release cdbuild=20080702.1 
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Found a good ISO: Ubuntu 8.04.1 "Hardy Heron" - Release amd64 (20080702.1)
Found CD E:
Found CD cddrive=E:
Installing in automatic mode from CD
CheckCD
check_internet_connection
Dialer online
connected
md5=fcdd21bfd391a3618ee13159d7030ab9
Checking md5 of E:\casper\filesystem.squashfs
CheckCD raw status = success:E:\casper\filesystem.squashfs
CheckCD status = success
CD2ISO C:\ubuntu\install\installation.iso
CD2ISO finished successfully
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Checking/Downloading Ubuntu-8.04.1
Skipmd5 is true, using C:\ubuntu\install\installation.iso
CopyKernel isokernel=casper\vmlinuz, iso=C:\ubuntu\install\installation.iso, cddrive=E:
Extracting with 7z kernel/initrd from C:\ubuntu\install\installation.iso
UncompressFilesPriorInstall
Drive & Path name success; Volume name Vista64; Max #/chars in vol name rcook; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive C: has filesystem NTFS
rootSize=9000 homesize=0, swapsize=1000, usrsize=0
DoMenuLst C:\ubuntu\install\boot\grub\menu.lst
editBootDrive
editBootDrive NT
CopyWubildr
CopyWubildrMbr
EditBootIni
Drive & Path name success; Volume name Vista64; Max #/chars in vol name rcook; Volume Serial # 410644787; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive C: has filesystem NTFS
rootSize=9000 homesize=0, swapsize=1000, usrsize=0
AllocFile filename=C:\ubuntu\disks\root.disk size=9000
AllocFile status=success
AllocFile filename=C:\ubuntu\disks\home.disk size=0
AllocFile filename=C:\ubuntu\disks\swap.disk size=1000
AllocFile status=success
UncompressFilesAfterInstall
EjectCD
Ejecting CDHandle=512 for drive=E:
EjectCD DeviceIoControl exited with code 1 (1==success)
Installation completed successfully!

```

I'm trying to go through them now for clues on what to do next.

---

### Post by ago on 2008-09-18
The logs are fine. EasyBcd can also install the wubi boot option in Vista, try that.

---

### Post by BobbySoSlo on 2008-09-18
Ok, I was hoping eBCD would help me out but I've been playing with it and couldn't figure out how to use it to add the Wubi Boot. I've been playing with that for a while but I never could figure out what to do in BCD to activate it.

I also tried the superGrub and AutoSuperGrub with no results but a sad ascii face.

If you could toss me a little direction on what I'm doing in easyBCD I'd appreciate it.

---

### Post by ago on 2008-09-18
[http://ubuntuforums.org/showthread.php?t=463849](http://ubuntuforums.org/showthread.php?t=463849)

---

### Post by BobbySoSlo on 2008-09-18
Ok followed the procedure and just got a corrupted boot file (or something similar) error message (will return and put a little more detail). But don't I have to point the new boot entry at my installed wubi or something, just hitting add entry can't be all..?

(It's not a problem I'm doing this on my C: drive is it?)

Edit: This time I put it on D and reinstalled but I got a grub> command line..? Don't know if that was intentional or not.

---

### Post by BobbySoSlo on 2008-09-18
I hit the wrong button on EasyBCD and now my entire system will not boot.

Currently posting from Desktop because system repairs as such are no longer on the manufacturer cds (only destructive and I have very important projects that are not fully backed up due to my work server being down).

I'm currently booting from the Ubuntu CD on my laptop to try and see if I can fix the boot, wish me luck (and luck to any telemarketers that call me because I will kill any annoyances atm). *Frustrated at my own boneheaded move

---

### Post by BobbySoSlo on 2008-09-20
Finally recovered back to working. Still can't get ubuntu working though..I think I'm just going to go ahead and partition the sucker and stop trying to take the weasly way out.

Any advice before I do that?

---

