---
title: "Wubi won't install 8.10 but installs 8.04"
date: 2008-11-19
forum: General Help
---

### Post by Sijomo on 2008-11-19
Hi,

I downloaded the 8.10 ISO and then discovered Wubi, so downloaded that to do the install. Wubi didn't detect the ISO (which was in the same folder) and then tried downloading it; I let it do that, but it turns out it had downloaded & installed 8.04.

I downloaded Wubi from link on the bottom-right of the 8.10 download page: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

(I'm using a Thinkpad R52 and in the UK if this is in any way relevant.)

Any suggestions? All help appreciated.

S.

---

### Post by ago on 2008-11-19
There is a log in your temp folder (type %temp% in windows explorer), please post it here.

---

### Post by Sijomo on 2008-11-19
Wubi-8.04.1-rev505.log

The log had two prior ==installer== sections which I've not included, as I cancelled the install initially; if you want these please say.

I guess it looks like I've got the wrong Wubi, as it saw the 8.10 but wanted 8.04.1

Am I missing the obvious on where to download the correct Wubi?

[http://www.ubuntu.com/getubuntu/downloadmirrors#wubi](http://www.ubuntu.com/getubuntu/downloadmirrors#wubi)

Cheers

Simon

============ Installer ============
PLUGINSDIR=C:\DOCUME~1\SIMONM~1\LOCALS~1\Temp\nsw1D0.tmp
detect_all
Parsing cmdline "C:\simon\downloads\ubuntu 8.10\wubi.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=1534 MB
arch=i386
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
Found InstallationDrive C:\ubuntu
AlreadyInstalled=true OldInstallationDrive=C: InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1712; Volume name IBM_PRELOAD; Max #/chars in vol name 1867864; Volume Serial # 1211746531; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1419880; Volume name IBM_PRELOAD; Max #/chars in vol name 47; Volume Serial # 1211746531; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = C:
FreeSpace in C: is 21690
DetectBackupFolder
IsBackupFolder C:\
GMT=0
Country=GB
Locale=en_GB.UTF-8
TimeZone=Europe/London
Domain=localdomain
HostName=SIMON
ComputerName=SIMON
EnvUsername=SimonMorgan
UserDomain=SIMON
UserInfoName=SimonMorgan
UserProfileFolder=C:\Documents and Settings\SimonMorgan
UserProfileName=SimonMorgan 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name IBM_PRELOAD; Max #/chars in vol name 1871536; Volume Serial # 1211746531; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to C:
ChangeInstallationSize to 10
PopulateDistroList
DetectIso
      IsValidIso ispoath=C:\simon\downloads\ubuntu 8.10\ubuntu-8.10-desktop-i386.iso
      ExtractIsoInfo
      C:\DOCUME~1\SIMONM~1\LOCALS~1\Temp\nsw1D0.tmp\7z.exe e -y -i!.disk\info -oC:\DOCUME~1\SIMONM~1\LOCALS~1\Temp C:\simon\downloads\ubuntu 8.10\ubuntu-8.10-desktop-i386.iso
      IsValid Ubuntu 8.10 "Intrepid Ibex" - Release i386 (20081029.5)
      cdversion=8.10 cddistro=Ubuntu cdarch=i386 cdcodename=Intrepid Ibex cdsubversion=Release cdbuild=20081029.5 
      GetDistroInfo distrofullname=Ubuntu-i386 distro= cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
different version 8.04.1 != 8.10
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
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
Locale=en_GB.UTF-8
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink
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
      Is Valid CD D:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
No CD found
DetectIso
      IsValidIso ispoath=C:\simon\downloads\ubuntu 8.10\ubuntu-8.10-desktop-i386.iso
      ExtractIsoInfo
      C:\DOCUME~1\SIMONM~1\LOCALS~1\Temp\nsw1D0.tmp\7z.exe e -y -i!.disk\info -oC:\DOCUME~1\SIMONM~1\LOCALS~1\Temp C:\simon\downloads\ubuntu 8.10\ubuntu-8.10-desktop-i386.iso
      IsValid Ubuntu 8.10 "Intrepid Ibex" - Release i386 (20081029.5)
      cdversion=8.10 cddistro=Ubuntu cdarch=i386 cdcodename=Intrepid Ibex cdsubversion=Release cdbuild=20081029.5 
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
different version 8.04.1 != 8.10
CDInfo cleared
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Checking/Downloading Ubuntu-8.04.1
retrieve_partial_files
check_internet_connection
Dialer online
connected
Trying remote metalink: [http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink](http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink)
get_md5 [http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink](http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink)
Downloading: trymefirst= url=http://releases.ubuntu.com/8.04.1/MD5SUMS-metalink.gpg md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink.gpg
Downloading: trymefirst= url=http://releases.ubuntu.com/8.04.1/MD5SUMS-metalink md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink
      Verifying signature C:\ubuntu\install\MD5SUMS-metalink.asc
0; gpgv: error loading `iconv.dll': The specified module could not be found.


gpgv: Signature made 07/03/08 22:36:17 GMT Daylight Time using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
; ; ; 
      Parsing C:\ubuntu\install\MD5SUMS-metalink
Found md5 cde82e1566ad8a88e36138853c195b5f
Downloading: trymefirst= url=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink md5=cde82e1566ad8a88e36138853c195b5f
Download status=success:C:\ubuntu\install\ubuntu-8.04.1-desktop-i386.iso
ISO file ubuntu-8.04.1-desktop-i386.iso retrieved!!!
CopyKernel isokernel=casper\vmlinuz, iso=C:\ubuntu\install\ubuntu-8.04.1-desktop-i386.iso, cddrive=
Extracting with 7z kernel/initrd from C:\ubuntu\install\ubuntu-8.04.1-desktop-i386.iso
UncompressFilesPriorInstall
Drive & Path name C:\ubuntu\install\ubuntu-8.04.1-desktop-i386.iso; Volume name IBM_PRELOAD; Max #/chars in vol name ; Volume Serial # 1211746531; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 2147352576
Drive C: has filesystem NTFS
rootSize=9000 homesize=0, swapsize=1000, usrsize=0
DoMenuLst C:\ubuntu\install\boot\grub\menu.lst
editBootDrive
editBootDrive NT
CopyWubildr
CopyWubildrMbr
EditBootIni
EditBootIni C:\boot.ini
Drive & Path name C:\ubuntu\install\ubuntu-8.04.1-desktop-i386.iso; Volume name IBM_PRELOAD; Max #/chars in vol name ; Volume Serial # 1211746531; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 2147352576
Drive C: has filesystem NTFS
rootSize=9000 homesize=0, swapsize=1000, usrsize=0
AllocFile filename=C:\ubuntu\disks\root.disk size=9000
AllocFile status=success
AllocFile filename=C:\ubuntu\disks\home.disk size=0
AllocFile filename=C:\ubuntu\disks\swap.disk size=1000
AllocFile status=success
UncompressFilesAfterInstall
Installation completed successfully!

---

### Post by Sijomo on 2008-11-19
Hi,

I've just tried that link again(?), and Wubi 8.10 has now been downloaded, so I'll try that.

I'll let you know how it goes, but didn't want you to put any further effort in for now.

I don't know what I clicked incorrectly last time, ho-hum.

S.

---

### Post by ago on 2008-11-19
Yes, you used wubi 8.04. Not sure how or why you got that though. The version on ubuntu.com should be correct.

---

### Post by Sijomo on 2008-11-19
Thanks.

I'm replying from Linux now, so that's it. Dunno what I clicked previously.

Cheers

Simon

---

### Post by JuL.LeVi on 2008-11-19
[B]hi sijomo ,

ubuntu 8.10 contains wubi installer itself. why don't you just mount ubuntu ISO image , then click the virtual disk and install inside windows :)

[COLOR="Red"]JuL[/COLOR][/B]

---

