---
title: "No kubuntu option on vista boot menu after Wubi install"
date: 2008-10-23
forum: General Help
---

### Post by kamitsukai on 2008-10-23
I installed wubi on my vista pc (yesterdays daily build of 8.10) but there's no option for it on my boot menu and it just boots vista...

thanks in advance!

---

### Post by kamitsukai on 2008-10-24
Just uninstalled and tried with todays kubuntu RC1 release and still there is no option after reboot, isnt this a pretty large bug for a release candidate??? how can I fix this?

---

### Post by kamitsukai on 2008-10-24
Just added it using easybcd but on restart I selected it yet I only got as far as a grub screen and then some type of command prompt?

---

### Post by kamitsukai on 2008-10-24
Nobody??? ...oh :(

---

### Post by ago on 2008-10-24
What does wubibcd shows exactly after Wubi installation? No entry at all?
What are your privileges on that machine are you and administrator?
There should be a log in your temp folder (type %temp% in windows explorer), post it here

You need a boot menu entry pointing to c:\wubildr.mbr

---

### Post by kamitsukai on 2008-10-24
Hi thanks for the help,

1)after reeboot there wasnt an option so i dl easy bcd and then added the wubi option thats available and then i managed to get to some type of grub error?

2)yep im admin

```
============ Installer ============
PLUGINSDIR=C:\Users\Carl\AppData\Local\Temp\nsi5784.tmp
detect_all
Parsing cmdline "C:\Users\Carl\AppData\Local\Temp\7zS27EB.tmp\wubi.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=1789 MB
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
No CD found
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
AlreadyInstalled=false OldInstallationDrive= InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1713; Volume name ; Max #/chars in vol name 3076984; Volume Serial # 1515417713; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 2303136; Volume name ; Max #/chars in vol name 45; Volume Serial # 1515417713; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = c:
FreeSpace in c: is 76855
DetectBackupFolder
IsBackupFolder C:\
GMT=0
Country=GB
Locale=en_GB.UTF-8
TimeZone=Europe/London
Domain=localdomain
HostName=Carl-PC
ComputerName=CARL-PC
EnvUsername=Carl
UserDomain=Carl-PC
UserInfoName=Carl
UserProfileFolder=C:\Users\Carl
UserProfileName=Carl 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1779; Volume name ; Max #/chars in vol name 2559856; Volume Serial # 1515417713; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to c:
ChangeInstallationSize to 15
PopulateDistroList
DetectIso
      IsValidIso ispoath=C:\Users\Carl\Desktop\intrepid-desktop-i386.iso
      ExtractIsoInfo
      C:\Users\Carl\AppData\Local\Temp\nsi5784.tmp\7z.exe e -y -i!.disk\info -oC:\Users\Carl\AppData\Local\Temp C:\Users\Carl\Desktop\intrepid-desktop-i386.iso
      IsValid Kubuntu 8.10 "Intrepid Ibex" - Release Candidate i386 (20081022)
      cdversion=8.10 cddistro=Kubuntu cdarch=i386 cdcodename=Intrepid Ibex cdsubversion=Release Candidate cdbuild=20081022 
      GetDistroInfo distrofullname=Kubuntu-i386 distro= cddistro=Kubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/kubuntu/8.10/kubuntu-8.10-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
Found a good ISO: Kubuntu 8.10 "Intrepid Ibex" - Release Candidate i386 (20081022)
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
      GetDistroInfo distrofullname=Kubuntu-i386 distro=Kubuntu cddistro=Kubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/kubuntu/8.10/kubuntu-8.10-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
Changing artwork to distro=Kubuntu
Changing icon to Kubuntu.ico
InitMainPageToolTips
LeaveMainPage
LeaveMainPage
LeaveMainPage
      GetDistroInfo distrofullname=Kubuntu-i386 distro=Kubuntu cddistro=Kubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/kubuntu/8.10/kubuntu-8.10-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
Changing artwork to distro=Kubuntu
Changing icon to Kubuntu.ico
LeaveMainPage
Locale=en_GB.UTF-8
      GetDistroInfo distrofullname=Kubuntu-i386 distro=Kubuntu cddistro=Kubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/kubuntu/8.10/kubuntu-8.10-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
CreateInstallationFolders
MakeUninstall
Created C:\ubuntu\Uninstall-Kubuntu.exe
Created reg key HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
CopyDistFolders
GetIso
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
No CD found
DetectIso
      IsValidIso ispoath=C:\Users\Carl\Desktop\intrepid-desktop-i386.iso
      ExtractIsoInfo
      C:\Users\Carl\AppData\Local\Temp\nsi5784.tmp\7z.exe e -y -i!.disk\info -oC:\Users\Carl\AppData\Local\Temp C:\Users\Carl\Desktop\intrepid-desktop-i386.iso
      IsValid Kubuntu 8.10 "Intrepid Ibex" - Release Candidate i386 (20081022)
      cdversion=8.10 cddistro=Kubuntu cdarch=i386 cdcodename=Intrepid Ibex cdsubversion=Release Candidate cdbuild=20081022 
      GetDistroInfo distrofullname=Kubuntu-i386 distro=Kubuntu cddistro=Kubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/kubuntu/8.10/kubuntu-8.10-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
Found a good ISO: Kubuntu 8.10 "Intrepid Ibex" - Release Candidate i386 (20081022)
Copying C:\Users\Carl\Desktop\intrepid-desktop-i386.iso -> C:\ubuntu\install\intrepid-desktop-i386.iso
Copying done
      GetDistroInfo distrofullname=Kubuntu-i386 distro=Kubuntu cddistro=Kubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/kubuntu/8.10/kubuntu-8.10-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
Checking/Downloading Kubuntu-8.10
retrieve_partial_files
check_internet_connection
Dialer online
connected
Trying remote metalink: http://releases.ubuntu.com/kubuntu/8.10/kubuntu-8.10-desktop-i386.metalink
get_md5 http://releases.ubuntu.com/kubuntu/8.10/kubuntu-8.10-desktop-i386.metalink
Downloading: trymefirst= url=http://releases.ubuntu.com/kubuntu/8.10/MD5SUMS-metalink.gpg md5=
Download status=cancel
User cancelled download, quitting.
============ Installer ============
PLUGINSDIR=C:\Users\Carl\AppData\Local\Temp\nsf647F.tmp
detect_all
Parsing cmdline "C:\Users\Carl\AppData\Local\Temp\7zS4894.tmp\wubi.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=1789 MB
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
      IsValid Kubuntu 8.10 "Intrepid Ibex" - Release Candidate i386 (20081022)
      cdversion=8.10 cddistro=Kubuntu cdarch=i386 cdcodename=Intrepid Ibex cdsubversion=Release Candidate cdbuild=20081022 
      GetDistroInfo distrofullname=Kubuntu-i386 distro= cddistro=Kubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/kubuntu/8.10/kubuntu-8.10-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
Found a good ISO: Kubuntu 8.10 "Intrepid Ibex" - Release Candidate i386 (20081022)
Found CD E:
Found CD cddrive=E:
Changing icon to Kubuntu.ico
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
Found InstallationDrive C:\ubuntu
AlreadyInstalled=true OldInstallationDrive=C: InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1713; Volume name ; Max #/chars in vol name 1965072; Volume Serial # 1515417713; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1778848; Volume name ; Max #/chars in vol name 45; Volume Serial # 1515417713; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = c:
FreeSpace in c: is 83486
DetectBackupFolder
IsBackupFolder C:\
GMT=0
Country=GB
Locale=en_GB.UTF-8
TimeZone=Europe/London
Domain=localdomain
HostName=Carl-PC
ComputerName=CARL-PC
EnvUsername=Carl
UserDomain=Carl-PC
UserInfoName=Carl
UserProfileFolder=C:\Users\Carl
UserProfileName=Carl 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1779; Volume name ; Max #/chars in vol name 1958728; Volume Serial # 1515417713; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to C:
ChangeInstallationSize to 15
PopulateDistroList
DistroList = Kubuntu
PopulateLanguageListBox
      GetDistroInfo distrofullname=Kubuntu-i386 distro=Kubuntu cddistro=Kubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/kubuntu/8.10/kubuntu-8.10-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
Changing artwork to distro=Kubuntu
Changing icon to Kubuntu.ico
InitMainPageToolTips
LeaveMainPage
Locale=en_GB.UTF-8
      GetDistroInfo distrofullname=Kubuntu-i386 distro=Kubuntu cddistro=Kubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/kubuntu/8.10/kubuntu-8.10-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
CreateInstallationFolders
MakeUninstall
Created C:\ubuntu\Uninstall-Kubuntu.exe
Created reg key HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
CopyDistFolders
GetIso
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
      IsValid Kubuntu 8.10 "Intrepid Ibex" - Release Candidate i386 (20081022)
      cdversion=8.10 cddistro=Kubuntu cdarch=i386 cdcodename=Intrepid Ibex cdsubversion=Release Candidate cdbuild=20081022 
      GetDistroInfo distrofullname=Kubuntu-i386 distro=Kubuntu cddistro=Kubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/kubuntu/8.10/kubuntu-8.10-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
Found a good ISO: Kubuntu 8.10 "Intrepid Ibex" - Release Candidate i386 (20081022)
Found CD E:
Found CD cddrive=E:
Installing in automatic mode from CD
CheckCD
check_internet_connection
Dialer online
connected
md5=b9c8c58b9319d9b51bc38cfcb6c28fec
Checking md5 of E:\casper\filesystem.squashfs
CheckCD raw status = success:E:\casper\filesystem.squashfs
CheckCD status = success
CD2ISO C:\ubuntu\install\installation.iso
CD2ISO finished successfully
      GetDistroInfo distrofullname=Kubuntu-i386 distro=Kubuntu cddistro=Kubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/kubuntu/8.10/kubuntu-8.10-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
Checking/Downloading Kubuntu-8.10
Skipmd5 is true, using C:\ubuntu\install\installation.iso
CopyKernel isokernel=casper\vmlinuz, iso=C:\ubuntu\install\installation.iso, cddrive=E:
Extracting with 7z kernel/initrd from C:\ubuntu\install\installation.iso
UncompressFilesPriorInstall
Drive & Path name success; Volume name ; Max #/chars in vol name carl; Volume Serial # 1515417713; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive C: has filesystem NTFS
rootSize=14000 homesize=0, swapsize=1000, usrsize=0
DoMenuLst C:\ubuntu\install\boot\grub\menu.lst
editBootDrive
editBootDrive Vista
CopyWubildr
CopyWubildrMbr
editBCD
C:\Users\Carl\AppData\Local\Temp\nsf647F.tmp\wubibcd.exe 
 1:-532459699 
 2:
Unhandled Exception: System.ComponentModel.Win32Exception: Access is denied
   at System.Diagnostics.Process.StartWithCreateProcess(ProcessStartInfo startInfo)
   at System.Diagnostics.Process.Start()
   at WubiBCD.WubiBCD.Install(String drive, String path, String title)
   at WubiBCD.WubiBCD.Main(String[] args)
 
 3:HDD 
 4:3
Error while trying to execute wubibcd:: 
Unhandled Exception: System.ComponentModel.Win32Exception: Access is denied
   at System.Diagnostics.Process.StartWithCreateProcess(ProcessStartInfo startInfo)
   at System.Diagnostics.Process.Start()
   at WubiBCD.WubiBCD.Install(String drive, String path, String title)
   at WubiBCD.WubiBCD.Main(String[] args)

vistaBootDriveCode = {} <=> Win32Exception: Access is denied
   a
vistaBootDriveCode {}
Drive & Path name /Users/Carl; Volume name ; Max #/chars in vol name success; Volume Serial # 1515417713; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 255
Drive C: has filesystem NTFS
rootSize=14000 homesize=0, swapsize=1000, usrsize=0
AllocFile filename=C:\ubuntu\disks\root.disk size=14000
AllocFile status=success
AllocFile filename=C:\ubuntu\disks\home.disk size=0
AllocFile filename=C:\ubuntu\disks\swap.disk size=1000
AllocFile status=success
UncompressFilesAfterInstall
EjectCD
Ejecting CDHandle=756 for drive=E:
EjectCD DeviceIoControl exited with code 1 (1==success)
Installation completed successfully!
============ Installer ============
PLUGINSDIR=C:\Users\Carl\AppData\Local\Temp\nsn9C81.tmp
detect_all
Parsing cmdline "C:\Users\Carl\AppData\Local\Temp\7zS8029.tmp\wubi.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=1789 MB
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
      IsValid Kubuntu 8.10 "Intrepid Ibex" - Release Candidate i386 (20081022)
      cdversion=8.10 cddistro=Kubuntu cdarch=i386 cdcodename=Intrepid Ibex cdsubversion=Release Candidate cdbuild=20081022 
      GetDistroInfo distrofullname=Kubuntu-i386 distro= cddistro=Kubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/kubuntu/8.10/kubuntu-8.10-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
Found a good ISO: Kubuntu 8.10 "Intrepid Ibex" - Release Candidate i386 (20081022)
Found CD E:
Found CD cddrive=E:
Changing icon to Kubuntu.ico
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
Found InstallationDrive C:\ubuntu
AlreadyInstalled=true OldInstallationDrive=C: InstallCompleted=true
IsValidFileSystem C:
Drive & Path name 1713; Volume name ; Max #/chars in vol name 2448736; Volume Serial # 1515417713; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 2369808; Volume name ; Max #/chars in vol name 46; Volume Serial # 1515417713; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = c:
FreeSpace in c: is 62190
DetectBackupFolder
IsBackupFolder C:\
GMT=0
Country=GB
Locale=en_GB.UTF-8
TimeZone=Europe/London
Domain=localdomain
HostName=Carl-PC
ComputerName=CARL-PC
EnvUsername=Carl
UserDomain=Carl-PC
UserInfoName=Carl
UserProfileFolder=C:\Users\Carl
UserProfileName=Carl 
detect_all finished
ShowMainPage
Existing installation detected, calling old uninstaller and quitting.
============ Uninstaller ============
PLUGINSDIR=C:\Users\Carl\AppData\Local\Temp\nsiBDE6.tmp
un.install
un.BackupIso
Backup C:\ubuntu\install\installation.iso
Backup C:\ubuntu\install\intrepid-desktop-i386.iso
un.CleanBcd
Error while trying to execute bcdedit:: 1 
un.RemoveInstallationFolder C:\ubuntu
un.CleanThisDrive C:\
un.CleanConfig.sys C:\
un.CleanRegistry Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
Uninstallation completed successfully!
============ Installer ============
PLUGINSDIR=C:\Users\Carl\AppData\Local\Temp\nsn4C4F.tmp
detect_all
Parsing cmdline "C:\Users\Carl\AppData\Local\Temp\7zS2ECE.tmp\wubi.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=1789 MB
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
      IsValid Kubuntu 8.10 "Intrepid Ibex" - Release Candidate i386 (20081022)
      cdversion=8.10 cddistro=Kubuntu cdarch=i386 cdcodename=Intrepid Ibex cdsubversion=Release Candidate cdbuild=20081022 
      GetDistroInfo distrofullname=Kubuntu-i386 distro= cddistro=Kubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/kubuntu/8.10/kubuntu-8.10-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
Found a good ISO: Kubuntu 8.10 "Intrepid Ibex" - Release Candidate i386 (20081022)
Found CD E:
Found CD cddrive=E:
Changing icon to Kubuntu.ico
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
AlreadyInstalled=false OldInstallationDrive= InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1713; Volume name ; Max #/chars in vol name 3629776; Volume Serial # 1515417713; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 3024952; Volume name ; Max #/chars in vol name 49; Volume Serial # 1515417713; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = c:
FreeSpace in c: is 76506
DetectBackupFolder
IsBackupFolder C:\
Found BackupFolder C:\ubuntu-backup
GMT=0
Country=GB
Locale=en_GB.UTF-8
TimeZone=Europe/London
Domain=localdomain
HostName=Carl-PC
ComputerName=CARL-PC
EnvUsername=Carl
UserDomain=Carl-PC
UserInfoName=Carl
UserProfileFolder=C:\Users\Carl
UserProfileName=Carl 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1779; Volume name ; Max #/chars in vol name 3585000; Volume Serial # 1515417713; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to c:
ChangeInstallationSize to 15
PopulateDistroList
DistroList = Kubuntu
PopulateLanguageListBox
      GetDistroInfo distrofullname=Kubuntu-i386 distro=Kubuntu cddistro=Kubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/kubuntu/8.10/kubuntu-8.10-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
Changing artwork to distro=Kubuntu
Changing icon to Kubuntu.ico
InitMainPageToolTips
LeaveMainPage
Locale=en_GB.UTF-8
      GetDistroInfo distrofullname=Kubuntu-i386 distro=Kubuntu cddistro=Kubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/kubuntu/8.10/kubuntu-8.10-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
CreateInstallationFolders
MakeUninstall
Created C:\ubuntu\Uninstall-Kubuntu.exe
Created reg key HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
CopyDistFolders
GetIso
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
      IsValid Kubuntu 8.10 "Intrepid Ibex" - Release Candidate i386 (20081022)
      cdversion=8.10 cddistro=Kubuntu cdarch=i386 cdcodename=Intrepid Ibex cdsubversion=Release Candidate cdbuild=20081022 
      GetDistroInfo distrofullname=Kubuntu-i386 distro=Kubuntu cddistro=Kubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/kubuntu/8.10/kubuntu-8.10-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
Found a good ISO: Kubuntu 8.10 "Intrepid Ibex" - Release Candidate i386 (20081022)
Found CD E:
Found CD cddrive=E:
Installing in automatic mode from CD
CheckCD
check_internet_connection
Dialer online
connected
md5=b9c8c58b9319d9b51bc38cfcb6c28fec
Checking md5 of E:\casper\filesystem.squashfs
CheckCD raw status = success:E:\casper\filesystem.squashfs
CheckCD status = success
CD2ISO C:\ubuntu\install\installation.iso
CD2ISO finished successfully
      GetDistroInfo distrofullname=Kubuntu-i386 distro=Kubuntu cddistro=Kubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/kubuntu/8.10/kubuntu-8.10-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
Checking/Downloading Kubuntu-8.10
Skipmd5 is true, using C:\ubuntu\install\installation.iso
CopyKernel isokernel=casper\vmlinuz, iso=C:\ubuntu\install\installation.iso, cddrive=E:
Extracting with 7z kernel/initrd from C:\ubuntu\install\installation.iso
UncompressFilesPriorInstall
Drive & Path name success; Volume name ; Max #/chars in vol name carl; Volume Serial # 1515417713; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive C: has filesystem NTFS
rootSize=14000 homesize=0, swapsize=1000, usrsize=0
DoMenuLst C:\ubuntu\install\boot\grub\menu.lst
editBootDrive
editBootDrive NT
CopyWubildr
CopyWubildrMbr
EditBootIni
Drive & Path name success; Volume name ; Max #/chars in vol name carl; Volume Serial # 1515417713; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive C: has filesystem NTFS
rootSize=14000 homesize=0, swapsize=1000, usrsize=0
AllocFile filename=C:\ubuntu\disks\root.disk size=14000
AllocFile status=success
AllocFile filename=C:\ubuntu\disks\home.disk size=0
AllocFile filename=C:\ubuntu\disks\swap.disk size=1000
AllocFile status=success
UncompressFilesAfterInstall
EjectCD
Ejecting CDHandle=676 for drive=E:
EjectCD DeviceIoControl exited with code 1 (1==success)
Installation completed successfully!
============ Installer ============
PLUGINSDIR=C:\Users\Carl\AppData\Local\Temp\nskA992.tmp
detect_all
Parsing cmdline "C:\Users\Carl\AppData\Local\Temp\7zS73E0.tmp\wubi.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=1789 MB
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
      IsValid Kubuntu 8.10 "Intrepid Ibex" - Release Candidate i386 (20081022)
      cdversion=8.10 cddistro=Kubuntu cdarch=i386 cdcodename=Intrepid Ibex cdsubversion=Release Candidate cdbuild=20081022 
      GetDistroInfo distrofullname=Kubuntu-i386 distro= cddistro=Kubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/kubuntu/8.10/kubuntu-8.10-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
Found a good ISO: Kubuntu 8.10 "Intrepid Ibex" - Release Candidate i386 (20081022)
Found CD E:
Found CD cddrive=E:
Changing icon to Kubuntu.ico
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
Found InstallationDrive C:\ubuntu
AlreadyInstalled=true OldInstallationDrive=C: InstallCompleted=true
IsValidFileSystem C:
Drive & Path name 1713; Volume name ; Max #/chars in vol name 7332368; Volume Serial # 1515417713; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 6564112; Volume name ; Max #/chars in vol name 35; Volume Serial # 1515417713; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = c:
FreeSpace in c: is 63861
DetectBackupFolder
Found BackupFolder C:\ubuntu-backup
GMT=0
Country=GB
Locale=en_GB.UTF-8
TimeZone=Europe/London
Domain=localdomain
HostName=Carl-PC
ComputerName=CARL-PC
EnvUsername=Carl
UserDomain=Carl-PC
UserInfoName=Carl
UserProfileFolder=C:\Users\Carl
UserProfileName=Carl 
detect_all finished
ShowMainPage
Existing installation detected, calling old uninstaller and quitting.
============ Uninstaller ============
PLUGINSDIR=C:\Users\Carl\AppData\Local\Temp\nsuCAB8.tmp
un.install
un.BackupIso
Backup C:\ubuntu\install\installation.iso
un.CleanBcd
un.RemoveInstallationFolder C:\ubuntu
un.CleanThisDrive C:\
un.CleanConfig.sys C:\
un.CleanRegistry Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
Uninstallation completed successfully!
============ Installer ============
PLUGINSDIR=C:\Users\Carl\AppData\Local\Temp\nsq410.tmp
detect_all
Parsing cmdline "C:\Users\Carl\AppData\Local\Temp\7zSE825.tmp\wubi.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=1789 MB
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
      IsValid Kubuntu 8.10 "Intrepid Ibex" - Release Candidate i386 (20081022)
      cdversion=8.10 cddistro=Kubuntu cdarch=i386 cdcodename=Intrepid Ibex cdsubversion=Release Candidate cdbuild=20081022 
      GetDistroInfo distrofullname=Kubuntu-i386 distro= cddistro=Kubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/kubuntu/8.10/kubuntu-8.10-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
Found a good ISO: Kubuntu 8.10 "Intrepid Ibex" - Release Candidate i386 (20081022)
Found CD E:
Found CD cddrive=E:
Changing icon to Kubuntu.ico
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
AlreadyInstalled=false OldInstallationDrive= InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1713; Volume name ; Max #/chars in vol name 1856360; Volume Serial # 1515417713; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1583376; Volume name ; Max #/chars in vol name 36; Volume Serial # 1515417713; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = c:
FreeSpace in c: is 79556
DetectBackupFolder
IsBackupFolder C:\
GMT=0
Country=GB
Locale=en_GB.UTF-8
TimeZone=Europe/London
Domain=localdomain
HostName=Carl-PC
ComputerName=CARL-PC
EnvUsername=Carl
UserDomain=Carl-PC
UserInfoName=Carl
UserProfileFolder=C:\Users\Carl
UserProfileName=Carl 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1779; Volume name ; Max #/chars in vol name 1904528; Volume Serial # 1515417713; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to c:
ChangeInstallationSize to 15
PopulateDistroList
DistroList = Kubuntu
PopulateLanguageListBox
      GetDistroInfo distrofullname=Kubuntu-i386 distro=Kubuntu cddistro=Kubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/kubuntu/8.10/kubuntu-8.10-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
Changing artwork to distro=Kubuntu
Changing icon to Kubuntu.ico
InitMainPageToolTips
LeaveMainPage
LeaveMainPage
Locale=en_GB.UTF-8
      GetDistroInfo distrofullname=Kubuntu-i386 distro=Kubuntu cddistro=Kubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/kubuntu/8.10/kubuntu-8.10-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
CreateInstallationFolders
MakeUninstall
Created C:\ubuntu\Uninstall-Kubuntu.exe
Created reg key HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
CopyDistFolders
GetIso
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
      IsValid Kubuntu 8.10 "Intrepid Ibex" - Release Candidate i386 (20081022)
      cdversion=8.10 cddistro=Kubuntu cdarch=i386 cdcodename=Intrepid Ibex cdsubversion=Release Candidate cdbuild=20081022 
      GetDistroInfo distrofullname=Kubuntu-i386 distro=Kubuntu cddistro=Kubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/kubuntu/8.10/kubuntu-8.10-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
Found a good ISO: Kubuntu 8.10 "Intrepid Ibex" - Release Candidate i386 (20081022)
Found CD E:
Found CD cddrive=E:
Installing in automatic mode from CD
CheckCD
check_internet_connection
Dialer online
connected
md5=b9c8c58b9319d9b51bc38cfcb6c28fec
Checking md5 of E:\casper\filesystem.squashfs
CheckCD raw status = success:E:\casper\filesystem.squashfs
CheckCD status = success
CD2ISO C:\ubuntu\install\installation.iso
CD2ISO finished successfully
      GetDistroInfo distrofullname=Kubuntu-i386 distro=Kubuntu cddistro=Kubuntu cdarch=i386 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/kubuntu/8.10/kubuntu-8.10-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
Checking/Downloading Kubuntu-8.10
Skipmd5 is true, using C:\ubuntu\install\installation.iso
CopyKernel isokernel=casper\vmlinuz, iso=C:\ubuntu\install\installation.iso, cddrive=E:
Extracting with 7z kernel/initrd from C:\ubuntu\install\installation.iso
UncompressFilesPriorInstall
Drive & Path name success; Volume name ; Max #/chars in vol name carl; Volume Serial # 1515417713; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive C: has filesystem NTFS
rootSize=14000 homesize=0, swapsize=1000, usrsize=0
DoMenuLst C:\ubuntu\install\boot\grub\menu.lst
editBootDrive
editBootDrive NT
CopyWubildr
CopyWubildrMbr
EditBootIni
Drive & Path name success; Volume name ; Max #/chars in vol name carl; Volume Serial # 1515417713; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive C: has filesystem NTFS
rootSize=14000 homesize=0, swapsize=1000, usrsize=0
AllocFile filename=C:\ubuntu\disks\root.disk size=14000
AllocFile status=success
AllocFile filename=C:\ubuntu\disks\home.disk size=0
AllocFile filename=C:\ubuntu\disks\swap.disk size=1000
AllocFile status=success
UncompressFilesAfterInstall
EjectCD
Ejecting CDHandle=740 for drive=E:
EjectCD DeviceIoControl exited with code 1 (1==success)
Installation completed successfully!

```

---

### Post by ago on 2008-10-24
yes please post the log

---

### Post by kamitsukai on 2008-10-24
> **ago said:**
> yes please post the log

Sorry log posted! I thought it was attached but it appears I exceeded the file size limit...:mad:

---

### Post by ago on 2008-10-24
Hmm your OS is detected as NT/XP not as Vista

---

### Post by kamitsukai on 2008-10-24
> **ago said:**
> Hmm your OS is detected as NT/XP not as Vista

oh..whys that?:lolflag:

---

### Post by ago on 2008-10-24
No idea, I didn't write that part of code (is part of nsis) but worked well so far. Do you happen to dual boot xp/vista and having installed in xp?

---

### Post by kamitsukai on 2008-10-24
Nope I'm using vista ultimate on it's own...

---

### Post by ago on 2008-10-24
I need the output of [http://msdn.microsoft.com/en-us/library/ms724439(VS.85).aspx](http://msdn.microsoft.com/en-us/library/ms724439(VS.85).aspx)

if you have python, you can get the output with

import ctypes
ctypes.windll.kernel32.GetVersion

---

### Post by kamitsukai on 2008-10-25
> **ago said:**
> I need the output of [http://msdn.microsoft.com/en-us/library/ms724439(VS.85).aspx](http://msdn.microsoft.com/en-us/library/ms724439(VS.85).aspx)

if you have python, you can get the output with

import ctypes
ctypes.windll.kernel32.GetVersion

How would I do this without python? :confused::lolflag:

---

### Post by garferi on 2008-10-26
Did you try to run Wubi installer as administrator (right click on file, run as administrator)?

---

### Post by kamitsukai on 2008-10-26
> **garferi said:**
> Did you try to run Wubi installer as administrator (right click on file, run as administrator)?

erm no why are you meant too? i just used the option from the ubuntu install disc...

---

### Post by garferi on 2008-10-27
Place the latest Kubuntu [intrepid-desktop-i386.iso]("http://cdimage.ubuntu.com/kubuntu/daily-live/current/intrepid-desktop-i386.iso") and [Wubi-8.10-rev514.exe]("http://wubi-installer.org/devel/minefield/Wubi-8.10-rev514.exe") in the same folder and right click on Wubi-8.10-rev514.exe, run as administrator.
Good luck!

**Edit: New Ubuntu is out!**

Download the final release of Kubuntu 8.10 instead of what I linked above.
[Kubuntu 8.10]("http://ie.releases.ubuntu.com/kubuntu/intrepid/kubuntu-8.10-desktop-i386.iso")
[Wubi.exe]("http://releases.ubuntu.com/8.10/wubi.exe")

---

