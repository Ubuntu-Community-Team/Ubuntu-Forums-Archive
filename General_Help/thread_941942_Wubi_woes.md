---
title: "Wubi woes"
date: 2008-10-08
forum: General Help
---

### Post by Gregor Lumpkus on 2008-10-08
Ok, so I got wubi, i got the iso file, I out them on a flash drive and transferred them to another computer. For some reason it won't install through the iso file, even though they are in the same folder. And when it tries to install the normal way it just says the installation was stopped because of error: and then it's blank past the colon. I need help! 
Thanks,
-Gregor

---

### Post by Gregor Lumpkus on 2008-10-08
Ok, so I skipped the memory check, and it started to install the normal way! But, it's downloading at a rousing 4 to 6 kb a second.... zzzzzz... Wait what? Oh, sorry. Just an update.

---

### Post by crazypenguin2008 on 2008-10-09
seems wubi is a slow download. mines been going for about 6hrs not and its still got 72hrs to go lol

---

### Post by ago on 2008-10-09
You can download the iso manually and place it in the same folder of wubi.exe. If wubi refuses to use it, it is because the ISO is incorrect (wrong version or distro) or it is corrupted. There is a log in you user temp folder.

---

### Post by crazypenguin2008 on 2008-10-09
how does one go about doing that? do you download the .iso for standard ubuntu hardy?

---

### Post by ago on 2008-10-09
> **crazypenguin2008 said:**
> how does one go about doing that? do you download the .iso for standard ubuntu hardy?

Yes you need the Live Desktop CD ISO of the matching version.

---

### Post by crazypenguin2008 on 2008-10-09
then wich folder do i move it to? im using my windows notebook. when i go into my computer>drive c> there is 2 folders,ubuntu and i386,,,wich folder to i move the .iso image to?

---

### Post by ago on 2008-10-09
> **crazypenguin2008 said:**
> then wich folder do i move it to? im using my windows notebook. when i go into my computer>drive c> there is 2 folders,ubuntu and i386,,,wich folder to i move the .iso image to?

Uninstall Wubi first, then put the ISO and Wubi.exe in the same folder, any folder will do. Wubi looks into the containing folder for an ISO before attempting a download.

---

### Post by crazypenguin2008 on 2008-10-09
not to sound like a tit but where is the wubi.ext file at? ive got the .iso downloading now. this is my first attempt at wubi. used ubuntu plenty but id like to run wubi on my work pc thats gotta have windows

---

### Post by ago on 2008-10-09
[http://wubi-installer.org/latest.php](http://wubi-installer.org/latest.php)

---

### Post by crazypenguin2008 on 2008-10-09
thanks its doing its thing and going much much faster. 30% in under 20mins

---

### Post by crazypenguin2008 on 2008-10-09
ok i got the .iso downloaded what now> do i have ot do the installation process?

---

### Post by crazypenguin2008 on 2008-10-09
did the .iso thing and tried to install and its still going slow and taking forever.....is it normal for a wubi install to take 20+ hrs?

---

### Post by crazypenguin2008 on 2008-10-09
is wubi allways slow to install?

---

### Post by ago on 2008-10-09
No it's not normal, it should not download a new ISO if you have one already, unless you got the wrong ISO or it is corrupted. See the wubi log in your user temp folder.

---

### Post by crazypenguin2008 on 2008-10-09
what am i looking for in the wubi user log? i see 2 of them

---

### Post by crazypenguin2008 on 2008-10-09
heres a copy paste from the logs 

* About to connect() to releases.ubuntu.com port 80 (#0)
*   Trying 91.189.88.33... * connected
* Connected to releases.ubuntu.com (91.189.88.33) port 80 (#0)
> GET /8.04.1/MD5SUMS-metalink.gpg HTTP/1.1
User-Agent: Metadl/1.0 (NSIS plugin)
Host: releases.ubuntu.com
Accept: */*

< HTTP/1.1 200 OK
< Date: Thu, 09 Oct 2008 11:47:07 GMT
< Server: Apache/2.2.8 (Ubuntu)
< Last-Modified: Thu, 03 Jul 2008 21:36:17 GMT
< ETag: "d82268-bd-4512566317640"
< Accept-Ranges: bytes
< Content-Length: 189
< Content-Type: text/plain
< 
* Connection #0 to host releases.ubuntu.com left intact
* About to connect() to releases.ubuntu.com port 80 (#0)
*   Trying 91.189.88.33... * connected
* Connected to releases.ubuntu.com (91.189.88.33) port 80 (#0)
> GET /8.04.1/MD5SUMS-metalink HTTP/1.1
User-Agent: Metadl/1.0 (NSIS plugin)
Host: releases.ubuntu.com
Accept: */*

< HTTP/1.1 200 OK
< Date: Thu, 09 Oct 2008 11:47:13 GMT
< Server: Apache/2.2.8 (Ubuntu)
< Last-Modified: Thu, 03 Jul 2008 21:36:17 GMT
< ETag: "d82267-11e-4512566317640"
< Accept-Ranges: bytes
< Content-Length: 286
< Content-Type: text/plain
< 
* Connection #0 to host releases.ubuntu.com left intact
* About to connect() to releases.ubuntu.com port 80 (#0)
*   Trying 91.189.88.33... * Timeout
* couldn't connect to host
* Closing connection #0
* About to connect() to releases.ubuntu.com port 80 (#0)
*   Trying 91.189.88.33... * Timeout
* couldn't connect to host
* Closing connection #0
* About to connect() to releases.ubuntu.com port 80 (#0)
*   Trying 91.189.88.33... * Timeout
* connect() timed out!
* Closing connection #0
* About to connect() to releases.ubuntu.com port 80 (#0)
*   Trying 91.189.88.33... * connected
* Connected to releases.ubuntu.com (91.189.88.33) port 80 (#0)
> GET /8.04.1/ubuntu-8.04.1-desktop-amd64.metalink HTTP/1.1
User-Agent: Metadl/1.0 (NSIS plugin)
Host: releases.ubuntu.com
Accept: */*

< HTTP/1.1 200 OK
< Date: Thu, 09 Oct 2008 11:47:40 GMT
< Server: Apache/2.2.8 (Ubuntu)
< Last-Modified: Thu, 03 Jul 2008 21:36:17 GMT
< ETag: "d82342-190b-4512566317640"
< Accept-Ranges: bytes
< Content-Length: 6411
< Content-Type: text/plain
< 
* Connection #0 to host releases.ubuntu.com left intact
* About to connect() to mirror.anl.gov port 80 (#1)
*   Trying 146.137.96.7... * connected
* Connected to mirror.anl.gov (146.137.96.7) port 80 (#1)
> GET /pub/ubuntu-iso/CDs/8.04.1/ubuntu-8.04.1-desktop-amd64.iso HTTP/1.1
User-Agent: Metadl/1.0 (NSIS plugin)
Host: mirror.anl.gov
Accept: */*

< HTTP/1.1 200 OK
< Date: Thu, 09 Oct 2008 11:47:41 GMT
< Server: Apache
< Last-Modified: Wed, 02 Jul 2008 10:47:19 GMT
< ETag: "1d4f92-2b4c0800-4510837775bc0"
< Accept-Ranges: bytes
< Content-Length: 726403072
< Content-Type: application/x-iso9660-image
< 
* Callback aborted
* Callback aborted
* Closing connection #1


* About to connect() to releases.ubuntu.com port 80 (#0)
*   Trying 91.189.88.33... * connected
* Connected to releases.ubuntu.com (91.189.88.33) port 80 (#0)
> GET /8.04.1/MD5SUMS-metalink.gpg HTTP/1.1
User-Agent: Metadl/1.0 (NSIS plugin)
Host: releases.ubuntu.com
Accept: */*

< HTTP/1.1 200 OK
< Date: Thu, 09 Oct 2008 11:36:07 GMT
< Server: Apache/2.2.8 (Ubuntu)
< Last-Modified: Thu, 03 Jul 2008 21:36:17 GMT
< ETag: "d82268-bd-4512566317640"
< Accept-Ranges: bytes
< Content-Length: 189
< Content-Type: text/plain
< 
* Connection #0 to host releases.ubuntu.com left intact
* About to connect() to releases.ubuntu.com port 80 (#0)
*   Trying 91.189.88.33... * Timeout
* couldn't connect to host
* Closing connection #0
* About to connect() to releases.ubuntu.com port 80 (#0)
*   Trying 91.189.88.33... * connected
* Connected to releases.ubuntu.com (91.189.88.33) port 80 (#0)
> GET /8.04.1/MD5SUMS-metalink HTTP/1.1
User-Agent: Metadl/1.0 (NSIS plugin)
Host: releases.ubuntu.com
Accept: */*

< HTTP/1.1 200 OK
< Date: Thu, 09 Oct 2008 11:36:23 GMT
< Server: Apache/2.2.8 (Ubuntu)
< Last-Modified: Thu, 03 Jul 2008 21:36:17 GMT
< ETag: "d82267-11e-4512566317640"
< Accept-Ranges: bytes
< Content-Length: 286
< Content-Type: text/plain
< 
* Connection #0 to host releases.ubuntu.com left intact
* About to connect() to releases.ubuntu.com port 80 (#0)
*   Trying 91.189.88.33... * connected
* Connected to releases.ubuntu.com (91.189.88.33) port 80 (#0)
> GET /8.04.1/ubuntu-8.04.1-desktop-amd64.metalink HTTP/1.1
User-Agent: Metadl/1.0 (NSIS plugin)
Host: releases.ubuntu.com
Accept: */*

< HTTP/1.1 200 OK
< Date: Thu, 09 Oct 2008 11:36:27 GMT
< Server: Apache/2.2.8 (Ubuntu)
< Last-Modified: Thu, 03 Jul 2008 21:36:17 GMT
< ETag: "d82342-190b-4512566317640"
< Accept-Ranges: bytes
< Content-Length: 6411
< Content-Type: text/plain
< 
* Connection #0 to host releases.ubuntu.com left intact
* About to connect() to mirror.anl.gov port 80 (#1)
*   Trying 146.137.96.7... * connected
* Connected to mirror.anl.gov (146.137.96.7) port 80 (#1)
> GET /pub/ubuntu-iso/CDs/8.04.1/ubuntu-8.04.1-desktop-amd64.iso HTTP/1.1
Range: bytes=70052065-
User-Agent: Metadl/1.0 (NSIS plugin)
Host: mirror.anl.gov
Accept: */*

< HTTP/1.1 206 Partial Content
< Date: Thu, 09 Oct 2008 11:36:29 GMT
< Server: Apache
< Last-Modified: Wed, 02 Jul 2008 10:47:19 GMT
< ETag: "1d4f92-2b4c0800-4510837775bc0"
< Accept-Ranges: bytes
< Content-Length: 656351007
< Content-Range: bytes 70052065-726403071/726403072
< Content-Type: application/x-iso9660-image
< 
* Failed writing body
* Callback aborted
* Closing connection #1
* About to connect() to releases.ubuntu.com port 80 (#0)
*   Trying 91.189.88.33... * connected
* Connected to releases.ubuntu.com (91.189.88.33) port 80 (#0)
> GET /8.04.1/MD5SUMS-metalink.gpg HTTP/1.1
User-Agent: Metadl/1.0 (NSIS plugin)
Host: releases.ubuntu.com
Accept: */*

< HTTP/1.1 200 OK
< Date: Thu, 09 Oct 2008 11:39:20 GMT
< Server: Apache/2.2.8 (Ubuntu)
< Last-Modified: Thu, 03 Jul 2008 21:36:17 GMT
< ETag: "d82268-bd-4512566317640"
< Accept-Ranges: bytes
< Content-Length: 189
< Content-Type: text/plain
< 
* Connection #0 to host releases.ubuntu.com left intact
* About to connect() to releases.ubuntu.com port 80 (#0)
*   Trying 91.189.88.33... * connected
* Connected to releases.ubuntu.com (91.189.88.33) port 80 (#0)
> GET /8.04.1/MD5SUMS-metalink HTTP/1.1
User-Agent: Metadl/1.0 (NSIS plugin)
Host: releases.ubuntu.com
Accept: */*

< HTTP/1.1 200 OK
< Date: Thu, 09 Oct 2008 11:39:29 GMT
< Server: Apache/2.2.8 (Ubuntu)
< Last-Modified: Thu, 03 Jul 2008 21:36:17 GMT
< ETag: "d82267-11e-4512566317640"
< Accept-Ranges: bytes
< Content-Length: 286
< Content-Type: text/plain
< 
* Connection #0 to host releases.ubuntu.com left intact
* About to connect() to mirror.anl.gov port 80 (#0)
*   Trying 146.137.96.7... * connected
* Connected to mirror.anl.gov (146.137.96.7) port 80 (#0)
> GET /pub/ubuntu-iso/CDs/8.04.1/ubuntu-8.04.1-desktop-amd64.iso HTTP/1.1
Range: bytes=71096412-
User-Agent: Metadl/1.0 (NSIS plugin)
Host: mirror.anl.gov
Accept: */*

< HTTP/1.1 206 Partial Content
< Date: Thu, 09 Oct 2008 11:39:30 GMT
< Server: Apache
< Last-Modified: Wed, 02 Jul 2008 10:47:19 GMT
< ETag: "1d4f92-2b4c0800-4510837775bc0"
< Accept-Ranges: bytes
< Content-Length: 655306660
< Content-Range: bytes 71096412-726403071/726403072
< Content-Type: application/x-iso9660-image
< 
* Failed writing body
* Callback aborted
* Closing connection #0

parsing arguments:
     COUNTRY
     TRYMEFIRST
     RETRYTIME
     HASHTRIES
     MAXTRIES
     TRANSLATE:
Source
Source is a url: adding url to mirrors
Downloading File=C:\ubuntu\install\MD5SUMS-metalink.gpg
    no tryme file
Check if the file already exists
Check for a partial download
Create or append to partial download file
Mirror: [http://releases.ubuntu.com/8.04.1/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/8.04.1/MD5SUMS-metalink.gpg) score:75
Init download: url='http://releases.ubuntu.com/8.04.1/MD5SUMS-metalink.gpg', g_startsize=0, proxy=''
Display connect message.
Perform the download.
Starting download: [http://releases.ubuntu.com/8.04.1/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/8.04.1/MD5SUMS-metalink.gpg)

Download returned: 0 

info_code == CURLE_OK
Checking file C:\ubuntu\install\MD5SUMS-metalink.gpg.partial
File check successful!

parsing arguments:
     COUNTRY
     TRYMEFIRST
     RETRYTIME
     HASHTRIES
     MAXTRIES
     TRANSLATE:
Source
Source is a url: adding url to mirrors
Downloading File=C:\ubuntu\install\MD5SUMS-metalink
    no tryme file
Check if the file already exists
Check for a partial download
Create or append to partial download file
Mirror: [http://releases.ubuntu.com/8.04.1/MD5SUMS-metalink](http://releases.ubuntu.com/8.04.1/MD5SUMS-metalink) score:75
Init download: url='http://releases.ubuntu.com/8.04.1/MD5SUMS-metalink', g_startsize=0, proxy=''
Display connect message.
Perform the download.
Starting download: [http://releases.ubuntu.com/8.04.1/MD5SUMS-metalink](http://releases.ubuntu.com/8.04.1/MD5SUMS-metalink)

Download returned: 0 

info_code == CURLE_OK
Checking file C:\ubuntu\install\MD5SUMS-metalink.partial
File check successful!

parsing arguments:
     MD5
     COUNTRY
     TRYMEFIRST
     RETRYTIME
     HASHTRIES
     MAXTRIES
     TRANSLATE:
Source
Source is a url: adding url to mirrors
Downloading File=C:\ubuntu\install\ubuntu-8.04.1-desktop-amd64.metalink
    no tryme file
Check if the file already exists
Check for a partial download
Create or append to partial download file
Mirror: [http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink](http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink) score:75
Init download: url='http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink', g_startsize=0, proxy=''
Display connect message.
Perform the download.
Starting download: [http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink](http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink)

Download returned: 7 couldn't connect to host

info_code == CURLE_OK
Mirror: [http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink](http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink) score:15
Init download: url='http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink', g_startsize=0, proxy=''
Display connect message.
Perform the download.
Starting download: [http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink](http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink)

Download returned: 7 couldn't connect to host

info_code == CURLE_OK
Mirror: [http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink](http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink) score:-45
Init download: url='http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink', g_startsize=0, proxy=''
Display connect message.
Perform the download.
Starting download: [http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink](http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink)

Download returned: 28 connect() timed out!

info_code == CURLE_OK
Mirror: [http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink](http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink) score:-105
Init download: url='http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink', g_startsize=0, proxy=''
Display connect message.
Perform the download.
Starting download: [http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink](http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink)

Download returned: 0 connect() timed out!

info_code == CURLE_OK
Checking file C:\ubuntu\install\ubuntu-8.04.1-desktop-amd64.metalink.partial
MD5: 1f8a4eb23752b8782651c67bdf48f66b 1f8a4eb23752b8782651c67bdf48f66b
File check successful!

Downloading File=C:\ubuntu\install\ubuntu-8.04.1-desktop-amd64.iso
    no tryme file
Check if the file already exists
Check for a partial download
Create or append to partial download file
Mirror: [http://mirror.anl.gov/pub/ubuntu-iso/CDs/8.04.1/ubuntu-8.04.1-desktop-amd64.iso](http://mirror.anl.gov/pub/ubuntu-iso/CDs/8.04.1/ubuntu-8.04.1-desktop-amd64.iso) score:160
Init download: url='http://mirror.anl.gov/pub/ubuntu-iso/CDs/8.04.1/ubuntu-8.04.1-desktop-amd64.iso', g_startsize=0, proxy=''
Display connect message.
Perform the download.
Starting download: [http://mirror.anl.gov/](http://mirror.anl.gov/)

---

### Post by ago on 2008-10-09
There should be another log in the same folder. And a log in your user temp folder (type %temp% in windows explorer). Please attach them here.

---

### Post by Gregor Lumpkus on 2008-10-09
Here are mine...

============ Installer ============
PLUGINSDIR=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\nsh38.tmp
detect_all
Parsing cmdline "C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\7zS35.tmp\wubi.exe " 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=382 MB
arch=i386
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
No CD found
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
AlreadyInstalled=false OldInstallationDrive= InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1712; Volume name ; Max #/chars in vol name 1755044; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1288672; Volume name ; Max #/chars in vol name 58; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = C:
FreeSpace in C: is 15841
DetectBackupFolder
IsBackupFolder C:\
GMT=-5
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=DPOPE2
ComputerName=DPOPE2
EnvUsername=Administrator
UserDomain=DPOPE2
UserInfoName=Administrator
UserProfileFolder=C:\Documents and Settings\Administrator
UserProfileName=Administrator 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name ; Max #/chars in vol name 1761620; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to C:
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
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
LeaveMainPage
Locale=en_US.UTF-8
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
      Is Valid CD C:
CDInfo cleared
No CD found
DetectIso
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Checking/Downloading Ubuntu-8.04.1
retrieve_partial_files
check_internet_connection
Dialer offline
not connected
check_internet_connection
Dialer offline
not connected
User cancelled Internet Connection Retry, quitting
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\nsr3E.tmp
detect_all
Parsing cmdline "C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\7zS3B.tmp\wubi.exe " 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=382 MB
arch=i386
DetectCD
      Is Valid CD C:
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
Drive & Path name 1712; Volume name ; Max #/chars in vol name 1750884; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1288672; Volume name ; Max #/chars in vol name 58; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = C:
FreeSpace in C: is 15841
DetectBackupFolder
IsBackupFolder C:\
GMT=-5
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=DPOPE2
ComputerName=DPOPE2
EnvUsername=Administrator
UserDomain=DPOPE2
UserInfoName=Administrator
UserProfileFolder=C:\Documents and Settings\Administrator
UserProfileName=Administrator 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name ; Max #/chars in vol name 1752964; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to C:
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
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
Locale=en_US.UTF-8
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
      Is Valid CD C:
CDInfo cleared
No CD found
DetectIso
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Checking/Downloading Ubuntu-8.04.1
retrieve_partial_files
check_internet_connection
Dialer offline
not connected
User cancelled Internet Connection Retry, quitting
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\nsj4D.tmp
detect_all
Parsing cmdline "C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\7zS4A.tmp\wubi.exe " 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=382 MB
arch=i386
DetectCD
      Is Valid CD C:
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
Drive & Path name 1712; Volume name ; Max #/chars in vol name 1750820; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1288672; Volume name ; Max #/chars in vol name 61; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = C:
FreeSpace in C: is 15840
DetectBackupFolder
IsBackupFolder C:\
GMT=-5
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=DPOPE2
ComputerName=DPOPE2
EnvUsername=Administrator
UserDomain=DPOPE2
UserInfoName=Administrator
UserProfileFolder=C:\Documents and Settings\Administrator
UserProfileName=Administrator 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name ; Max #/chars in vol name 1752900; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to C:
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
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
      GetDistroInfo distrofullname=Xubuntu-i386 distro=Xubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/xubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Xubuntu
Changing icon to Xubuntu.ico
LeaveMainPage
Locale=en_US.UTF-8
      GetDistroInfo distrofullname=Xubuntu-i386 distro=Xubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/xubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
CreateInstallationFolders
MakeUninstall
Created C:\ubuntu\Uninstall-Xubuntu.exe
Created reg key HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
CopyDistFolders
GetIso
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
No CD found
DetectIso
      GetDistroInfo distrofullname=Xubuntu-i386 distro=Xubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/xubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Checking/Downloading Xubuntu-8.04.1
retrieve_partial_files
check_internet_connection
Dialer online
connected
Trying remote metalink: [http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/xubuntu-8.04.1-desktop-i386.metalink](http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/xubuntu-8.04.1-desktop-i386.metalink)
get_md5 [http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/xubuntu-8.04.1-desktop-i386.metalink](http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/xubuntu-8.04.1-desktop-i386.metalink)
Downloading: trymefirst= url=http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/MD5SUMS-metalink.gpg md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink.gpg
Downloading: trymefirst= url=http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/MD5SUMS-metalink md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink
      Verifying signature C:\ubuntu\install\MD5SUMS-metalink.asc
2; gpgv: error loading `iconv.dll': The specified module could not be found.


gpgv: Signature made 07/17/08 09:02:08 Eastern Daylight Time using DSA key ID FBB75451
gpgv: key FBB75451 was created 157366305 seconds in the future (time warp or clock problem)
gpgv: key FBB75451 was created 157366305 seconds in the future (time warp or clock problem)
gpgv: Can't check signature: timestamp conflict
; ; ; 
Error verifying signature: 2
Trying remote metalink2: [http://cdimage.ubuntu.com/xubuntu/hardy/daily-live/current/hardy-desktop-i386.metalink](http://cdimage.ubuntu.com/xubuntu/hardy/daily-live/current/hardy-desktop-i386.metalink)
get_md5 [http://cdimage.ubuntu.com/xubuntu/hardy/daily-live/current/hardy-desktop-i386.metalink](http://cdimage.ubuntu.com/xubuntu/hardy/daily-live/current/hardy-desktop-i386.metalink)
Downloading: trymefirst= url=http://cdimage.ubuntu.com/xubuntu/hardy/daily-live/current/MD5SUMS-metalink.gpg md5=
Download status=The requested URL returned error: 404
Error downloading [http://cdimage.ubuntu.com/xubuntu/hardy/daily-live/current/MD5SUMS-metalink.gpg](http://cdimage.ubuntu.com/xubuntu/hardy/daily-live/current/MD5SUMS-metalink.gpg), The req
The download was interrupted with the error: 
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\nsu54.tmp
detect_all
Parsing cmdline "C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\7zS51.tmp\wubi.exe " 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=382 MB
arch=i386
DetectCD
      Is Valid CD C:
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
Drive & Path name 1712; Volume name ; Max #/chars in vol name 1750820; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1288672; Volume name ; Max #/chars in vol name 61; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = C:
FreeSpace in C: is 15840
DetectBackupFolder
IsBackupFolder C:\
GMT=-5
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=DPOPE2
ComputerName=DPOPE2
EnvUsername=Administrator
UserDomain=DPOPE2
UserInfoName=Administrator
UserProfileFolder=C:\Documents and Settings\Administrator
UserProfileName=Administrator 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name ; Max #/chars in vol name 1752900; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to C:
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
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
      GetDistroInfo distrofullname=Xubuntu-i386 distro=Xubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/xubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Xubuntu
Changing icon to Xubuntu.ico
LeaveMainPage
ChangeInstallationSize to 8
LeaveMainPage
ChangeInstallationSize to 10
LeaveMainPage
Locale=en_US.UTF-8
      GetDistroInfo distrofullname=Xubuntu-i386 distro=Xubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/xubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
CreateInstallationFolders
MakeUninstall
Created C:\ubuntu\Uninstall-Xubuntu.exe
Created reg key HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
CopyDistFolders
GetIso
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
No CD found
DetectIso
      GetDistroInfo distrofullname=Xubuntu-i386 distro=Xubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/xubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Checking/Downloading Xubuntu-8.04.1
retrieve_partial_files
check_internet_connection
Dialer online
connected
Trying remote metalink: [http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/xubuntu-8.04.1-desktop-i386.metalink](http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/xubuntu-8.04.1-desktop-i386.metalink)
get_md5 [http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/xubuntu-8.04.1-desktop-i386.metalink](http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/xubuntu-8.04.1-desktop-i386.metalink)
Downloading: trymefirst= url=http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/MD5SUMS-metalink.gpg md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink.gpg
Downloading: trymefirst= url=http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/MD5SUMS-metalink md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink
      Verifying signature C:\ubuntu\install\MD5SUMS-metalink.asc
2; gpgv: error loading `iconv.dll': The specified module could not be found.


gpgv: Signature made 07/17/08 09:02:08 Eastern Daylight Time using DSA key ID FBB75451
gpgv: key FBB75451 was created 157366221 seconds in the future (time warp or clock problem)
gpgv: key FBB75451 was created 157366221 seconds in the future (time warp or clock problem)
gpgv: Can't check signature: timestamp conflict
; ; ; 
Error verifying signature: 2
Trying remote metalink2: [http://cdimage.ubuntu.com/xubuntu/hardy/daily-live/current/hardy-desktop-i386.metalink](http://cdimage.ubuntu.com/xubuntu/hardy/daily-live/current/hardy-desktop-i386.metalink)
get_md5 [http://cdimage.ubuntu.com/xubuntu/hardy/daily-live/current/hardy-desktop-i386.metalink](http://cdimage.ubuntu.com/xubuntu/hardy/daily-live/current/hardy-desktop-i386.metalink)
Downloading: trymefirst= url=http://cdimage.ubuntu.com/xubuntu/hardy/daily-live/current/MD5SUMS-metalink.gpg md5=
Download status=The requested URL returned error: 404
Error downloading [http://cdimage.ubuntu.com/xubuntu/hardy/daily-live/current/MD5SUMS-metalink.gpg](http://cdimage.ubuntu.com/xubuntu/hardy/daily-live/current/MD5SUMS-metalink.gpg), The req
The download was interrupted with the error: 
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\nsc5E.tmp
detect_all
Parsing cmdline "C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\7zS5B.tmp\wubi.exe " 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=382 MB
arch=i386
DetectCD
      Is Valid CD C:
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
Drive & Path name 1712; Volume name ; Max #/chars in vol name 1750820; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1288672; Volume name ; Max #/chars in vol name 61; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = C:
FreeSpace in C: is 15840
DetectBackupFolder
IsBackupFolder C:\
GMT=-5
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=DPOPE2
ComputerName=DPOPE2
EnvUsername=Administrator
UserDomain=DPOPE2
UserInfoName=Administrator
UserProfileFolder=C:\Documents and Settings\Administrator
UserProfileName=Administrator 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name ; Max #/chars in vol name 1752900; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to C:
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
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
      GetDistroInfo distrofullname=Xubuntu-i386 distro=Xubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/xubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Xubuntu
Changing icon to Xubuntu.ico
LeaveMainPage
ChangeInstallationSize to 10
LeaveMainPage
Locale=en_US.UTF-8
      GetDistroInfo distrofullname=Xubuntu-i386 distro=Xubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/xubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
CreateInstallationFolders
MakeUninstall
Created C:\ubuntu\Uninstall-Xubuntu.exe
Created reg key HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
CopyDistFolders
GetIso
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
No CD found
DetectIso
      GetDistroInfo distrofullname=Xubuntu-i386 distro=Xubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/xubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Checking/Downloading Xubuntu-8.04.1
retrieve_partial_files
check_internet_connection
Dialer online
connected
Trying remote metalink: [http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/xubuntu-8.04.1-desktop-i386.metalink](http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/xubuntu-8.04.1-desktop-i386.metalink)
get_md5 [http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/xubuntu-8.04.1-desktop-i386.metalink](http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/xubuntu-8.04.1-desktop-i386.metalink)
Downloading: trymefirst= url=http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/MD5SUMS-metalink.gpg md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink.gpg
Downloading: trymefirst= url=http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/MD5SUMS-metalink md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink
      Verifying signature C:\ubuntu\install\MD5SUMS-metalink.asc
2; gpgv: error loading `iconv.dll': The specified module could not be found.


gpgv: Signature made 07/17/08 09:02:08 Eastern Daylight Time using DSA key ID FBB75451
gpgv: key FBB75451 was created 157366177 seconds in the future (time warp or clock problem)
gpgv: key FBB75451 was created 157366177 seconds in the future (time warp or clock problem)
gpgv: Can't check signature: timestamp conflict
; ; ; 
Error verifying signature: 2
Trying remote metalink2: [http://cdimage.ubuntu.com/xubuntu/hardy/daily-live/current/hardy-desktop-i386.metalink](http://cdimage.ubuntu.com/xubuntu/hardy/daily-live/current/hardy-desktop-i386.metalink)
get_md5 [http://cdimage.ubuntu.com/xubuntu/hardy/daily-live/current/hardy-desktop-i386.metalink](http://cdimage.ubuntu.com/xubuntu/hardy/daily-live/current/hardy-desktop-i386.metalink)
Downloading: trymefirst= url=http://cdimage.ubuntu.com/xubuntu/hardy/daily-live/current/MD5SUMS-metalink.gpg md5=
Download status=The requested URL returned error: 404
Error downloading [http://cdimage.ubuntu.com/xubuntu/hardy/daily-live/current/MD5SUMS-metalink.gpg](http://cdimage.ubuntu.com/xubuntu/hardy/daily-live/current/MD5SUMS-metalink.gpg), The req
The download was interrupted with the error: 
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\nsh65.tmp
detect_all
Parsing cmdline "C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\7zS62.tmp\wubi.exe " 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=382 MB
arch=i386
DetectCD
      Is Valid CD C:
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
Drive & Path name 1712; Volume name ; Max #/chars in vol name 1750820; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1288672; Volume name ; Max #/chars in vol name 63; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = C:
FreeSpace in C: is 15840
DetectBackupFolder
IsBackupFolder C:\
GMT=-5
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=DPOPE2
ComputerName=DPOPE2
EnvUsername=Administrator
UserDomain=DPOPE2
UserInfoName=Administrator
UserProfileFolder=C:\Documents and Settings\Administrator
UserProfileName=Administrator 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name ; Max #/chars in vol name 1752900; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to C:
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
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
ChangeInstallationSize to 10
LeaveMainPage
      GetDistroInfo distrofullname=Xubuntu-i386 distro=Xubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/xubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Xubuntu
Changing icon to Xubuntu.ico
LeaveMainPage
Locale=en_US.UTF-8
      GetDistroInfo distrofullname=Xubuntu-i386 distro=Xubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/xubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
CreateInstallationFolders
MakeUninstall
Created C:\ubuntu\Uninstall-Xubuntu.exe
Created reg key HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
CopyDistFolders
GetIso
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
No CD found
DetectIso
      GetDistroInfo distrofullname=Xubuntu-i386 distro=Xubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/xubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Checking/Downloading Xubuntu-8.04.1
retrieve_partial_files
check_internet_connection
Dialer online
connected
Trying remote metalink: [http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/xubuntu-8.04.1-desktop-i386.metalink](http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/xubuntu-8.04.1-desktop-i386.metalink)
get_md5 [http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/xubuntu-8.04.1-desktop-i386.metalink](http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/xubuntu-8.04.1-desktop-i386.metalink)
Downloading: trymefirst= url=http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/MD5SUMS-metalink.gpg md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink.gpg
Downloading: trymefirst= url=http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/MD5SUMS-metalink md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink
      Verifying signature C:\ubuntu\install\MD5SUMS-metalink.asc
2; gpgv: error loading `iconv.dll': The specified module could not be found.


gpgv: Signature made 07/17/08 09:02:08 Eastern Daylight Time using DSA key ID FBB75451
gpgv: key FBB75451 was created 157366033 seconds in the future (time warp or clock problem)
gpgv: key FBB75451 was created 157366033 seconds in the future (time warp or clock problem)
gpgv: Can't check signature: timestamp conflict
; ; ; 
Error verifying signature: 2
Trying remote metalink2: [http://cdimage.ubuntu.com/xubuntu/hardy/daily-live/current/hardy-desktop-i386.metalink](http://cdimage.ubuntu.com/xubuntu/hardy/daily-live/current/hardy-desktop-i386.metalink)
get_md5 [http://cdimage.ubuntu.com/xubuntu/hardy/daily-live/current/hardy-desktop-i386.metalink](http://cdimage.ubuntu.com/xubuntu/hardy/daily-live/current/hardy-desktop-i386.metalink)
Downloading: trymefirst= url=http://cdimage.ubuntu.com/xubuntu/hardy/daily-live/current/MD5SUMS-metalink.gpg md5=
Download status=The requested URL returned error: 404
Error downloading [http://cdimage.ubuntu.com/xubuntu/hardy/daily-live/current/MD5SUMS-metalink.gpg](http://cdimage.ubuntu.com/xubuntu/hardy/daily-live/current/MD5SUMS-metalink.gpg), The req
The download was interrupted with the error: 
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\nsp72.tmp
detect_all
Parsing cmdline "E:\Ubuntu Installer\wubi.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=382 MB
arch=i386
DetectCD
      Is Valid CD E:
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
Drive & Path name 1712; Volume name ; Max #/chars in vol name 1756300; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1288408; Volume name ; Max #/chars in vol name 60; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = C:
FreeSpace in C: is 15838
DetectBackupFolder
IsBackupFolder C:\
GMT=-5
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=DPOPE2
ComputerName=DPOPE2
EnvUsername=Administrator
UserDomain=DPOPE2
UserInfoName=Administrator
UserProfileFolder=C:\Documents and Settings\Administrator
UserProfileName=Administrator 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name ; Max #/chars in vol name 1752140; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to C:
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
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
ChangeInstallationSize to 10
LeaveMainPage
Locale=en_US.UTF-8
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
      Is Valid CD E:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
No CD found
DetectIso
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
2; gpgv: error loading `iconv.dll': The specified module could not be found.


gpgv: Signature made 07/03/08 17:36:17 Eastern Daylight Time using DSA key ID FBB75451
gpgv: key FBB75451 was created 157362708 seconds in the future (time warp or clock problem)
gpgv: key FBB75451 was created 157362708 seconds in the future (time warp or clock problem)
gpgv: Can't check signature: timestamp conflict
; ; ; 
Error verifying signature: 2
Trying remote metalink2: [http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-i386.metalink](http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-i386.metalink)
get_md5 [http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-i386.metalink](http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-i386.metalink)
Downloading: trymefirst= url=http://cdimage.ubuntu.com/hardy/daily-live/current/MD5SUMS-metalink.gpg md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink.gpg
Downloading: trymefirst= url=http://cdimage.ubuntu.com/hardy/daily-live/current/MD5SUMS-metalink md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink
      Verifying signature C:\ubuntu\install\MD5SUMS-metalink.asc
2; gpgv: error loading `iconv.dll': The specified module could not be found.


gpgv: Signature made 10/07/08 18:47:11 Eastern Daylight Time using DSA key ID FBB75451
gpgv: key FBB75451 was created 157362706 seconds in the future (time warp or clock problem)
gpgv: key FBB75451 was created 157362706 seconds in the future (time warp or clock problem)
gpgv: Can't check signature: timestamp conflict
; ; ; 
Error verifying signature: 2
The download was interrupted with the error: 
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\nss78.tmp
detect_all
Parsing cmdline "E:\Ubuntu Installer\wubi.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=382 MB
arch=i386
DetectCD
      Is Valid CD E:
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
Drive & Path name 1712; Volume name ; Max #/chars in vol name 1756300; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1288408; Volume name ; Max #/chars in vol name 59; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = C:
FreeSpace in C: is 15838
DetectBackupFolder
IsBackupFolder C:\
GMT=-5
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=DPOPE2
ComputerName=DPOPE2
EnvUsername=Administrator
UserDomain=DPOPE2
UserInfoName=Administrator
UserProfileFolder=C:\Documents and Settings\Administrator
UserProfileName=Administrator 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name ; Max #/chars in vol name 1752140; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to C:
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
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
      GetDistroInfo distrofullname=Xubuntu-i386 distro=Xubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/xubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Xubuntu
Changing icon to Xubuntu.ico
LeaveMainPage
ChangeInstallationSize to 10
============ Installer ============
Ubuntu is already running, quitting
LeaveMainPage
ChangeInstallationDrive to C:
ChangeInstallationSize to 10
LeaveMainPage
LeaveMainPage
Locale=en_US.UTF-8
      GetDistroInfo distrofullname=Xubuntu-i386 distro=Xubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/xubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
CreateInstallationFolders
MakeUninstall
Created C:\ubuntu\Uninstall-Xubuntu.exe
Created reg key HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
CopyDistFolders
GetIso
DetectCD
      Is Valid CD E:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
No CD found
DetectIso
      GetDistroInfo distrofullname=Xubuntu-i386 distro=Xubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/xubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Checking/Downloading Xubuntu-8.04.1
retrieve_partial_files
check_internet_connection
Dialer online
connected
Trying remote metalink: [http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/xubuntu-8.04.1-desktop-i386.metalink](http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/xubuntu-8.04.1-desktop-i386.metalink)
get_md5 [http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/xubuntu-8.04.1-desktop-i386.metalink](http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/xubuntu-8.04.1-desktop-i386.metalink)
Downloading: trymefirst= url=http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/MD5SUMS-metalink.gpg md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink.gpg
Downloading: trymefirst= url=http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/MD5SUMS-metalink md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink
      Verifying signature C:\ubuntu\install\MD5SUMS-metalink.asc
2; gpgv: error loading `iconv.dll': The specified module could not be found.


gpgv: Signature made 07/17/08 09:02:08 Eastern Daylight Time using DSA key ID FBB75451
gpgv: key FBB75451 was created 157362637 seconds in the future (time warp or clock problem)
gpgv: key FBB75451 was created 157362637 seconds in the future (time warp or clock problem)
gpgv: Can't check signature: timestamp conflict
; ; ; 
Error verifying signature: 2
Trying remote metalink2: [http://cdimage.ubuntu.com/xubuntu/hardy/daily-live/current/hardy-desktop-i386.metalink](http://cdimage.ubuntu.com/xubuntu/hardy/daily-live/current/hardy-desktop-i386.metalink)
get_md5 [http://cdimage.ubuntu.com/xubuntu/hardy/daily-live/current/hardy-desktop-i386.metalink](http://cdimage.ubuntu.com/xubuntu/hardy/daily-live/current/hardy-desktop-i386.metalink)
Downloading: trymefirst= url=http://cdimage.ubuntu.com/xubuntu/hardy/daily-live/current/MD5SUMS-metalink.gpg md5=
Download status=The requested URL returned error: 404
Error downloading [http://cdimage.ubuntu.com/xubuntu/hardy/daily-live/current/MD5SUMS-metalink.gpg](http://cdimage.ubuntu.com/xubuntu/hardy/daily-live/current/MD5SUMS-metalink.gpg), The req
The download was interrupted with the error: 
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\nsu80.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\Administrator\Desktop\wubi.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=382 MB
arch=i386
DetectCD
      Is Valid CD C:
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
Drive & Path name 1712; Volume name ; Max #/chars in vol name 1754516; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1285112; Volume name ; Max #/chars in vol name 59; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = C:
FreeSpace in C: is 15837
DetectBackupFolder
IsBackupFolder C:\
GMT=-5
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=DPOPE2
ComputerName=DPOPE2
EnvUsername=Administrator
UserDomain=DPOPE2
UserInfoName=Administrator
UserProfileFolder=C:\Documents and Settings\Administrator
UserProfileName=Administrator 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name ; Max #/chars in vol name 1759932; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to C:
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
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\nsc83.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\Administrator\Desktop\wubi.exe" "C:\Documents and Settings\Administrator\Desktop\ubuntu-8.04.1-desktop-i386.lnk"
debug=, 32bit=, cdboot=
User account type=Admin
Memory=382 MB
arch=i386
DetectCD
      Is Valid CD C:
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
Drive & Path name 1712; Volume name ; Max #/chars in vol name 1753972; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1285192; Volume name ; Max #/chars in vol name 59; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = C:
FreeSpace in C: is 15837
DetectBackupFolder
IsBackupFolder C:\
GMT=-5
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=DPOPE2
ComputerName=DPOPE2
EnvUsername=Administrator
UserDomain=DPOPE2
UserInfoName=Administrator
UserProfileFolder=C:\Documents and Settings\Administrator
UserProfileName=Administrator 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name ; Max #/chars in vol name 1762724; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to C:
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
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
Locale=en_US.UTF-8
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
      Is Valid CD C:
CDInfo cleared
No CD found
DetectIso
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
2; gpgv: error loading `iconv.dll': The specified module could not be found.


gpgv: Signature made 07/03/08 17:36:17 Eastern Daylight Time using DSA key ID FBB75451
gpgv: key FBB75451 was created 157361179 seconds in the future (time warp or clock problem)
gpgv: key FBB75451 was created 157361179 seconds in the future (time warp or clock problem)
gpgv: Can't check signature: timestamp conflict
; ; ; 
Error verifying signature: 2
Trying remote metalink2: [http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-i386.metalink](http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-i386.metalink)
get_md5 [http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-i386.metalink](http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-i386.metalink)
Downloading: trymefirst= url=http://cdimage.ubuntu.com/hardy/daily-live/current/MD5SUMS-metalink.gpg md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink.gpg
Downloading: trymefirst= url=http://cdimage.ubuntu.com/hardy/daily-live/current/MD5SUMS-metalink md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink
      Verifying signature C:\ubuntu\install\MD5SUMS-metalink.asc
2; gpgv: error loading `iconv.dll': The specified module could not be found.


gpgv: Signature made 10/07/08 18:47:11 Eastern Daylight Time using DSA key ID FBB75451
gpgv: key FBB75451 was created 157361177 seconds in the future (time warp or clock problem)
gpgv: key FBB75451 was created 157361177 seconds in the future (time warp or clock problem)
gpgv: Can't check signature: timestamp conflict
; ; ; 
Error verifying signature: 2
The download was interrupted with the error: 
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\nsp89.tmp
detect_all
Parsing cmdline "E:\Ubuntu Installer\wubi.exe" "E:\Ubuntu Installer\ubuntu-8.04.1-desktop-i386.lnk"
debug=, 32bit=, cdboot=
User account type=Admin
Memory=382 MB
arch=i386
DetectCD
      Is Valid CD E:
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
Drive & Path name 1712; Volume name ; Max #/chars in vol name 1753684; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1288456; Volume name ; Max #/chars in vol name 59; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = C:
FreeSpace in C: is 15837
DetectBackupFolder
IsBackupFolder C:\
GMT=-5
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=DPOPE2
ComputerName=DPOPE2
EnvUsername=Administrator
UserDomain=DPOPE2
UserInfoName=Administrator
UserProfileFolder=C:\Documents and Settings\Administrator
UserProfileName=Administrator 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name ; Max #/chars in vol name 1751604; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to C:
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
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\nsh8C.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\Administrator\Desktop\wubi.exe" "C:\Documents and Settings\Administrator\Desktop\ubuntu-8.04.1-desktop-i386.lnk"
debug=, 32bit=, cdboot=
User account type=Admin
Memory=382 MB
arch=i386
DetectCD
      Is Valid CD C:
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
Drive & Path name 1712; Volume name ; Max #/chars in vol name 1753972; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1285192; Volume name ; Max #/chars in vol name 59; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = C:
FreeSpace in C: is 15837
DetectBackupFolder
IsBackupFolder C:\
GMT=-5
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=DPOPE2
ComputerName=DPOPE2
EnvUsername=Administrator
UserDomain=DPOPE2
UserInfoName=Administrator
UserProfileFolder=C:\Documents and Settings\Administrator
UserProfileName=Administrator 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name ; Max #/chars in vol name 1762724; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to C:
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
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
ChangeInstallationSize to 10
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name ; Max #/chars in vol name 1832516; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to C:
ChangeInstallationSize to 10
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
Locale=en_US.UTF-8
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
      Is Valid CD C:
CDInfo cleared
No CD found
DetectIso
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
2; gpgv: error loading `iconv.dll': The specified module could not be found.


gpgv: Signature made 07/03/08 17:36:17 Eastern Daylight Time using DSA key ID FBB75451
gpgv: key FBB75451 was created 157340837 seconds in the future (time warp or clock problem)
gpgv: key FBB75451 was created 157340837 seconds in the future (time warp or clock problem)
gpgv: Can't check signature: timestamp conflict
; ; ; 
Error verifying signature: 2
Trying remote metalink2: [http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-i386.metalink](http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-i386.metalink)
get_md5 [http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-i386.metalink](http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-i386.metalink)
Downloading: trymefirst= url=http://cdimage.ubuntu.com/hardy/daily-live/current/MD5SUMS-metalink.gpg md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink.gpg
Downloading: trymefirst= url=http://cdimage.ubuntu.com/hardy/daily-live/current/MD5SUMS-metalink md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink
      Verifying signature C:\ubuntu\install\MD5SUMS-metalink.asc
2; gpgv: error loading `iconv.dll': The specified module could not be found.


gpgv: Signature made 10/07/08 18:47:11 Eastern Daylight Time using DSA key ID FBB75451
gpgv: key FBB75451 was created 157340835 seconds in the future (time warp or clock problem)
gpgv: key FBB75451 was created 157340835 seconds in the future (time warp or clock problem)
gpgv: Can't check signature: timestamp conflict
; ; ; 
Error verifying signature: 2
The download was interrupted with the error: 
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\nsz92.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\Administrator\Desktop\Ubuntu Installer\wubi.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=382 MB
arch=i386
DetectCD
      Is Valid CD C:
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
Drive & Path name 1712; Volume name ; Max #/chars in vol name 1756300; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1288776; Volume name ; Max #/chars in vol name 60; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = C:
FreeSpace in C: is 15837
DetectBackupFolder
IsBackupFolder C:\
GMT=-5
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=DPOPE2
ComputerName=DPOPE2
EnvUsername=Administrator
UserDomain=DPOPE2
UserInfoName=Administrator
UserProfileFolder=C:\Documents and Settings\Administrator
UserProfileName=Administrator 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name ; Max #/chars in vol name 1752140; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to C:
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
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
ChangeInstallationSize to 10
LeaveMainPage
Locale=en_US.UTF-8
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
      Is Valid CD C:
CDInfo cleared
No CD found
DetectIso
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
2; gpgv: error loading `iconv.dll': The specified module could not be found.


gpgv: Signature made 07/03/08 17:36:17 Eastern Daylight Time using DSA key ID FBB75451
gpgv: key FBB75451 was created 157340690 seconds in the future (time warp or clock problem)
gpgv: key FBB75451 was created 157340690 seconds in the future (time warp or clock problem)
gpgv: Can't check signature: timestamp conflict
; ; ; 
Error verifying signature: 2
Trying remote metalink2: [http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-i386.metalink](http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-i386.metalink)
get_md5 [http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-i386.metalink](http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-i386.metalink)
Downloading: trymefirst= url=http://cdimage.ubuntu.com/hardy/daily-live/current/MD5SUMS-metalink.gpg md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink.gpg
Downloading: trymefirst= url=http://cdimage.ubuntu.com/hardy/daily-live/current/MD5SUMS-metalink md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink
      Verifying signature C:\ubuntu\install\MD5SUMS-metalink.asc
2; gpgv: error loading `iconv.dll': The specified module could not be found.


gpgv: Signature made 10/07/08 18:47:11 Eastern Daylight Time using DSA key ID FBB75451
gpgv: key FBB75451 was created 157340688 seconds in the future (time warp or clock problem)
gpgv: key FBB75451 was created 157340688 seconds in the future (time warp or clock problem)
gpgv: Can't check signature: timestamp conflict
; ; ; 
Error verifying signature: 2
The download was interrupted with the error: 

and the other...

============ Installer ============
PLUGINSDIR=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\nst98.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\Administrator\Desktop\Ubuntu Installer\Wubi-8.04.1-rev506.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=382 MB
arch=i386
DetectCD
      Is Valid CD C:
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
Drive & Path name 1712; Volume name ; Max #/chars in vol name 1755988; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1288912; Volume name ; Max #/chars in vol name 60; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = C:
FreeSpace in C: is 15832
DetectBackupFolder
IsBackupFolder C:\
GMT=-5
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=DPOPE2
ComputerName=DPOPE2
EnvUsername=Administrator
UserDomain=DPOPE2
UserInfoName=Administrator
UserProfileFolder=C:\Documents and Settings\Administrator
UserProfileName=Administrator 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name ; Max #/chars in vol name 1758588; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to C:
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
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
Locale=en_US.UTF-8
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
      Is Valid CD C:
CDInfo cleared
No CD found
DetectIso
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
2; gpgv: error loading `iconv.dll': The specified module could not be found.


gpgv: Signature made 07/03/08 17:36:17 Eastern Daylight Time using DSA key ID FBB75451
gpgv: key FBB75451 was created 157340282 seconds in the future (time warp or clock problem)
gpgv: key FBB75451 was created 157340282 seconds in the future (time warp or clock problem)
gpgv: Can't check signature: timestamp conflict
; ; ; 
Error verifying signature: 2
Trying remote metalink2: [http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-i386.metalink](http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-i386.metalink)
get_md5 [http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-i386.metalink](http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-i386.metalink)
Downloading: trymefirst= url=http://cdimage.ubuntu.com/hardy/daily-live/current/MD5SUMS-metalink.gpg md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink.gpg
Downloading: trymefirst= url=http://cdimage.ubuntu.com/hardy/daily-live/current/MD5SUMS-metalink md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink
      Verifying signature C:\ubuntu\install\MD5SUMS-metalink.asc
2; gpgv: error loading `iconv.dll': The specified module could not be found.


gpgv: Signature made 10/07/08 18:47:11 Eastern Daylight Time using DSA key ID FBB75451
gpgv: key FBB75451 was created 157340280 seconds in the future (time warp or clock problem)
gpgv: key FBB75451 was created 157340280 seconds in the future (time warp or clock problem)
gpgv: Can't check signature: timestamp conflict
; ; ; 
Error verifying signature: 2
The download was interrupted with the error: 
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\nsg9E.tmp
detect_all
Parsing cmdline "C:\Ubuntu Installer\Wubi-8.04.1-rev506.exe" "C:\Ubuntu Installer\ubuntu-8.04.1-desktop-i386.lnk"
debug=, 32bit=, cdboot=
User account type=Admin
Memory=382 MB
arch=i386
DetectCD
      Is Valid CD C:
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
Drive & Path name 1712; Volume name ; Max #/chars in vol name 1753452; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1288512; Volume name ; Max #/chars in vol name 60; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = C:
FreeSpace in C: is 15828
DetectBackupFolder
IsBackupFolder C:\
GMT=-5
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=DPOPE2
ComputerName=DPOPE2
EnvUsername=Administrator
UserDomain=DPOPE2
UserInfoName=Administrator
UserProfileFolder=C:\Documents and Settings\Administrator
UserProfileName=Administrator 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name ; Max #/chars in vol name 1749292; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to C:
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
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
Locale=en_US.UTF-8
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
      Is Valid CD C:
CDInfo cleared
No CD found
DetectIso
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
2; gpgv: error loading `iconv.dll': The specified module could not be found.


gpgv: Signature made 07/03/08 17:36:17 Eastern Daylight Time using DSA key ID FBB75451
gpgv: key FBB75451 was created 157340119 seconds in the future (time warp or clock problem)
gpgv: key FBB75451 was created 157340119 seconds in the future (time warp or clock problem)
gpgv: Can't check signature: timestamp conflict
; ; ; 
Error verifying signature: 2
Trying remote metalink2: [http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-i386.metalink](http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-i386.metalink)
get_md5 [http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-i386.metalink](http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-i386.metalink)
Downloading: trymefirst= url=http://cdimage.ubuntu.com/hardy/daily-live/current/MD5SUMS-metalink.gpg md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink.gpg
Downloading: trymefirst= url=http://cdimage.ubuntu.com/hardy/daily-live/current/MD5SUMS-metalink md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink
      Verifying signature C:\ubuntu\install\MD5SUMS-metalink.asc
2; gpgv: error loading `iconv.dll': The specified module could not be found.


gpgv: Signature made 10/07/08 18:47:11 Eastern Daylight Time using DSA key ID FBB75451
gpgv: key FBB75451 was created 157340118 seconds in the future (time warp or clock problem)
gpgv: key FBB75451 was created 157340118 seconds in the future (time warp or clock problem)
gpgv: Can't check signature: timestamp conflict
; ; ; 
Error verifying signature: 2
The download was interrupted with the error: 
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\nswA4.tmp
detect_all
Parsing cmdline "C:\Ubuntu Installer\Wubi-8.04.1-rev506.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=382 MB
arch=i386
DetectCD
      Is Valid CD C:
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
Drive & Path name 1712; Volume name ; Max #/chars in vol name 1752748; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1288456; Volume name ; Max #/chars in vol name 60; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = C:
FreeSpace in C: is 15829
DetectBackupFolder
IsBackupFolder C:\
GMT=-5
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=DPOPE2
ComputerName=DPOPE2
EnvUsername=Administrator
UserDomain=DPOPE2
UserInfoName=Administrator
UserProfileFolder=C:\Documents and Settings\Administrator
UserProfileName=Administrator 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name ; Max #/chars in vol name 1749628; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to C:
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
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
Locale=en_US.UTF-8
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
      Is Valid CD C:
CDInfo cleared
No CD found
DetectIso
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
Download status=connect() timed out!
Error downloading [http://releases.ubuntu.com/8.04.1/MD5SUMS-metalink](http://releases.ubuntu.com/8.04.1/MD5SUMS-metalink), connect
Trying remote metalink2: [http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-i386.metalink](http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-i386.metalink)
get_md5 [http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-i386.metalink](http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-i386.metalink)
Downloading: trymefirst= url=http://cdimage.ubuntu.com/hardy/daily-live/current/MD5SUMS-metalink.gpg md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink.gpg
Downloading: trymefirst= url=http://cdimage.ubuntu.com/hardy/daily-live/current/MD5SUMS-metalink md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink
      Verifying signature C:\ubuntu\install\MD5SUMS-metalink.asc
2; gpgv: error loading `iconv.dll': The specified module could not be found.


gpgv: Signature made 10/07/08 18:47:11 Eastern Daylight Time using DSA key ID FBB75451
gpgv: key FBB75451 was created 157339516 seconds in the future (time warp or clock problem)
gpgv: key FBB75451 was created 157339516 seconds in the future (time warp or clock problem)
gpgv: Can't check signature: timestamp conflict
; ; ; 
Error verifying signature: 2
The download was interrupted with the error: 
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\nsyA9.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\Administrator\Desktop\Ubuntu Installer\Wubi-8.04.1-rev506.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=382 MB
arch=i386
DetectCD
      Is Valid CD C:
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
Drive & Path name 1712; Volume name ; Max #/chars in vol name 1755988; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1288912; Volume name ; Max #/chars in vol name 60; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = C:
FreeSpace in C: is 15828
DetectBackupFolder
IsBackupFolder C:\
GMT=-5
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=DPOPE2
ComputerName=DPOPE2
EnvUsername=Administrator
UserDomain=DPOPE2
UserInfoName=Administrator
UserProfileFolder=C:\Documents and Settings\Administrator
UserProfileName=Administrator 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name ; Max #/chars in vol name 1758588; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to C:
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
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
Locale=en_US.UTF-8
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
      Is Valid CD C:
CDInfo cleared
No CD found
DetectIso
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
2; gpgv: error loading `iconv.dll': The specified module could not be found.


gpgv: Signature made 07/03/08 17:36:17 Eastern Daylight Time using DSA key ID FBB75451
gpgv: key FBB75451 was created 157306301 seconds in the future (time warp or clock problem)
gpgv: key FBB75451 was created 157306301 seconds in the future (time warp or clock problem)
gpgv: Can't check signature: timestamp conflict
; ; ; 
Error verifying signature: 2
Trying remote metalink2: [http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-i386.metalink](http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-i386.metalink)
get_md5 [http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-i386.metalink](http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-i386.metalink)
Downloading: trymefirst= url=http://cdimage.ubuntu.com/hardy/daily-live/current/MD5SUMS-metalink.gpg md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink.gpg
Downloading: trymefirst= url=http://cdimage.ubuntu.com/hardy/daily-live/current/MD5SUMS-metalink md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink
      Verifying signature C:\ubuntu\install\MD5SUMS-metalink.asc
2; gpgv: error loading `iconv.dll': The specified module could not be found.


gpgv: Signature made 10/07/08 18:47:11 Eastern Daylight Time using DSA key ID FBB75451
gpgv: key FBB75451 was created 157306300 seconds in the future (time warp or clock problem)
gpgv: key FBB75451 was created 157306300 seconds in the future (time warp or clock problem)
gpgv: Can't check signature: timestamp conflict
; ; ; 
Error verifying signature: 2
The download was interrupted with the error: 
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\nswAF.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\Administrator\Desktop\Ubuntu Installer\Wubi-8.04.1-rev506.exe" "C:\Documents and Settings\Administrator\Desktop\Ubuntu Installer\ubuntu-8.04.1-desktop-i386.lnk"
debug=, 32bit=, cdboot=
User account type=Admin
Memory=382 MB
arch=i386
DetectCD
      Is Valid CD C:
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
Drive & Path name 1712; Volume name ; Max #/chars in vol name 1754548; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1289008; Volume name ; Max #/chars in vol name 60; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = C:
FreeSpace in C: is 15828
DetectBackupFolder
IsBackupFolder C:\
GMT=-5
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=DPOPE2
ComputerName=DPOPE2
EnvUsername=Administrator
UserDomain=DPOPE2
UserInfoName=Administrator
UserProfileFolder=C:\Documents and Settings\Administrator
UserProfileName=Administrator 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name ; Max #/chars in vol name 1761892; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to C:
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
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\nsaC9.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\Administrator\Desktop\Ubuntu Installer\Wubi-8.04.1-rev506.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=382 MB
arch=i386
DetectCD
      Is Valid CD C:
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
Drive & Path name 1712; Volume name ; Max #/chars in vol name 1755988; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1288912; Volume name ; Max #/chars in vol name 78; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = C:
FreeSpace in C: is 15750
DetectBackupFolder
IsBackupFolder C:\
GMT=-5
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=DPOPE2
ComputerName=DPOPE2
EnvUsername=Administrator
UserDomain=DPOPE2
UserInfoName=Administrator
UserProfileFolder=C:\Documents and Settings\Administrator
UserProfileName=Administrator 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name ; Max #/chars in vol name 1758588; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to C:
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
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
ChangeInstallationSize to 10
LeaveMainPage
Locale=en_US.UTF-8
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
      Is Valid CD C:
CDInfo cleared
No CD found
DetectIso
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
2; gpgv: error loading `iconv.dll': The specified module could not be found.


gpgv: Signature made 07/03/08 17:36:17 Eastern Daylight Time using DSA key ID FBB75451
gpgv: key FBB75451 was created 157304665 seconds in the future (time warp or clock problem)
gpgv: key FBB75451 was created 157304665 seconds in the future (time warp or clock problem)
gpgv: Can't check signature: timestamp conflict
; ; ; 
Error verifying signature: 2
Trying remote metalink2: [http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-i386.metalink](http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-i386.metalink)
get_md5 [http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-i386.metalink](http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-i386.metalink)
Downloading: trymefirst= url=http://cdimage.ubuntu.com/hardy/daily-live/current/MD5SUMS-metalink.gpg md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink.gpg
Downloading: trymefirst= url=http://cdimage.ubuntu.com/hardy/daily-live/current/MD5SUMS-metalink md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink
      Verifying signature C:\ubuntu\install\MD5SUMS-metalink.asc
2; gpgv: error loading `iconv.dll': The specified module could not be found.


gpgv: Signature made 10/07/08 18:47:11 Eastern Daylight Time using DSA key ID FBB75451
gpgv: key FBB75451 was created 157304663 seconds in the future (time warp or clock problem)
gpgv: key FBB75451 was created 157304663 seconds in the future (time warp or clock problem)
gpgv: Can't check signature: timestamp conflict
; ; ; 
Error verifying signature: 2
The download was interrupted with the error: 
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\nsaD8.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\Administrator\Desktop\Ubuntu Installer\Wubi-8.04.1-rev506.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=382 MB
arch=i386
DetectCD
      Is Valid CD C:
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
Drive & Path name 1712; Volume name ; Max #/chars in vol name 1755988; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1288912; Volume name ; Max #/chars in vol name 81; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = C:
FreeSpace in C: is 15758
DetectBackupFolder
IsBackupFolder C:\
GMT=-5
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=DPOPE2
ComputerName=DPOPE2
EnvUsername=Administrator
UserDomain=DPOPE2
UserInfoName=Administrator
UserProfileFolder=C:\Documents and Settings\Administrator
UserProfileName=Administrator 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name ; Max #/chars in vol name 1758588; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to C:
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
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\nsfDC.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\Administrator\Desktop\Ubuntu Installer\Wubi-8.04.1-rev506.exe" --skipmemorycheck
debug=, 32bit=, cdboot=
User account type=Admin
arch=i386
DetectCD
      Is Valid CD C:
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
Drive & Path name 1712; Volume name ; Max #/chars in vol name 1756004; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name Admin; Volume name ; Max #/chars in vol name ; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 
Drive c: has valid filesystem NTFS
Installation drive chosen = C:
FreeSpace in C: is 15757
DetectBackupFolder
IsBackupFolder C:\
GMT=-5
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=DPOPE2
ComputerName=DPOPE2
EnvUsername=Administrator
UserDomain=DPOPE2
UserInfoName=Administrator
UserProfileFolder=C:\Documents and Settings\Administrator
UserProfileName=Administrator 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name ; Max #/chars in vol name 1751844; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to C:
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
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
ChangeInstallationSize to 10
LeaveMainPage
Locale=en_US.UTF-8
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
      Is Valid CD C:
CDInfo cleared
No CD found
DetectIso
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
2; gpgv: error loading `iconv.dll': The specified module could not be found.


gpgv: Signature made 07/03/08 17:36:17 Eastern Daylight Time using DSA key ID FBB75451
gpgv: key FBB75451 was created 157304355 seconds in the future (time warp or clock problem)
gpgv: key FBB75451 was created 157304355 seconds in the future (time warp or clock problem)
gpgv: Can't check signature: timestamp conflict
; ; ; 
Error verifying signature: 2
Trying remote metalink2: [http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-i386.metalink](http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-i386.metalink)
get_md5 [http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-i386.metalink](http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-i386.metalink)
Downloading: trymefirst= url=http://cdimage.ubuntu.com/hardy/daily-live/current/MD5SUMS-metalink.gpg md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink.gpg
Downloading: trymefirst= url=http://cdimage.ubuntu.com/hardy/daily-live/current/MD5SUMS-metalink md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink
      Verifying signature C:\ubuntu\install\MD5SUMS-metalink.asc
2; gpgv: error loading `iconv.dll': The specified module could not be found.


gpgv: Signature made 10/07/08 18:47:11 Eastern Daylight Time using DSA key ID FBB75451
gpgv: key FBB75451 was created 157304354 seconds in the future (time warp or clock problem)
gpgv: key FBB75451 was created 157304354 seconds in the future (time warp or clock problem)
gpgv: Can't check signature: timestamp conflict
; ; ; 
Error verifying signature: 2
The download was interrupted with the error: 
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\nsxE6.tmp
detect_all
Parsing cmdline "C:\Ubuntu Installer\Wubi-8.04.1-rev506.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=382 MB
arch=i386
DetectCD
      Is Valid CD C:
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
Drive & Path name 1712; Volume name ; Max #/chars in vol name 1752748; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1288456; Volume name ; Max #/chars in vol name 83; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = C:
FreeSpace in C: is 15753
DetectBackupFolder
IsBackupFolder C:\
GMT=-5
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=DPOPE2
ComputerName=DPOPE2
EnvUsername=Administrator
UserDomain=DPOPE2
UserInfoName=Administrator
UserProfileFolder=C:\Documents and Settings\Administrator
UserProfileName=Administrator 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name ; Max #/chars in vol name 1749628; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to C:
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
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
Locale=en_US.UTF-8
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
      Is Valid CD C:
CDInfo cleared
No CD found
DetectIso
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
2; gpgv: error loading `iconv.dll': The specified module could not be found.


gpgv: Signature made 07/03/08 17:36:17 Eastern Daylight Time using DSA key ID FBB75451
gpgv: key FBB75451 was created 157304115 seconds in the future (time warp or clock problem)
gpgv: key FBB75451 was created 157304115 seconds in the future (time warp or clock problem)
gpgv: Can't check signature: timestamp conflict
; ; ; 
Error verifying signature: 2
Trying remote metalink2: [http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-i386.metalink](http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-i386.metalink)
get_md5 [http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-i386.metalink](http://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-i386.metalink)
Downloading: trymefirst= url=http://cdimage.ubuntu.com/hardy/daily-live/current/MD5SUMS-metalink.gpg md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink.gpg
Downloading: trymefirst= url=http://cdimage.ubuntu.com/hardy/daily-live/current/MD5SUMS-metalink md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink
      Verifying signature C:\ubuntu\install\MD5SUMS-metalink.asc
2; gpgv: error loading `iconv.dll': The specified module could not be found.


gpgv: Signature made 10/07/08 18:47:11 Eastern Daylight Time using DSA key ID FBB75451
gpgv: key FBB75451 was created 157304113 seconds in the future (time warp or clock problem)
gpgv: key FBB75451 was created 157304113 seconds in the future (time warp or clock problem)
gpgv: Can't check signature: timestamp conflict
; ; ; 
Error verifying signature: 2
The download was interrupted with the error: 
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\nsl22D.tmp
detect_all
Parsing cmdline Wubi-8.04.1-rev506.exe
debug=, 32bit=, cdboot=
User account type=Admin
Memory=382 MB
arch=i386
DetectCD
      Is Valid CD E:
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
Drive & Path name 1712; Volume name ; Max #/chars in vol name 1756780; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 1288632; Volume name ; Max #/chars in vol name 88; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = C:
FreeSpace in C: is 15747
DetectBackupFolder
IsBackupFolder C:\
GMT=-6
Country=US
Locale=en_US.UTF-8
TimeZone=America/Chicago
Domain=localdomain
HostName=DPOPE2
ComputerName=DPOPE2
EnvUsername=Administrator
UserDomain=DPOPE2
UserInfoName=Administrator
UserProfileFolder=C:\Documents and Settings\Administrator
UserProfileName=Administrator 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name ; Max #/chars in vol name 1752620; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to C:
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
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\nsg230.tmp
detect_all
Parsing cmdline Wubi-8.04.1-rev506.exe --skipmemorycheck
debug=, 32bit=, cdboot=
User account type=Admin
arch=i386
DetectCD
      Is Valid CD E:
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
Drive & Path name 1712; Volume name ; Max #/chars in vol name 1756820; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name Admin; Volume name ; Max #/chars in vol name ; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 
Drive c: has valid filesystem NTFS
Installation drive chosen = C:
FreeSpace in C: is 15747
DetectBackupFolder
IsBackupFolder C:\
GMT=-6
Country=US
Locale=en_US.UTF-8
TimeZone=America/Chicago
Domain=localdomain
HostName=DPOPE2
ComputerName=DPOPE2
EnvUsername=Administrator
UserDomain=DPOPE2
UserInfoName=Administrator
UserProfileFolder=C:\Documents and Settings\Administrator
UserProfileName=Administrator 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name ; Max #/chars in vol name 1752660; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to C:
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
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
ChangeInstallationSize to 10
LeaveMainPage
Locale=en_US.UTF-8
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
      Is Valid CD E:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
No CD found
DetectIso
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


gpgv: Signature made 07/03/08 16:36:17 Central Daylight Time using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
; ; ; 
      Parsing C:\ubuntu\install\MD5SUMS-metalink
Found md5 cde82e1566ad8a88e36138853c195b5f
Downloading: trymefirst= url=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink md5=cde82e1566ad8a88e36138853c195b5f
Download status=cancel
User cancelled download, quitting.
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\nst235.tmp
detect_all
Parsing cmdline Wubi-8.04.1-rev506.exe --skipmemorycheck
debug=, 32bit=, cdboot=
User account type=Admin
arch=i386
DetectCD
      Is Valid CD E:
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
Drive & Path name 1712; Volume name ; Max #/chars in vol name 1756820; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name Admin; Volume name ; Max #/chars in vol name ; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 
Drive c: has valid filesystem NTFS
Installation drive chosen = C:
FreeSpace in C: is 15677
DetectBackupFolder
IsBackupFolder C:\
GMT=-6
Country=US
Locale=en_US.UTF-8
TimeZone=America/Chicago
Domain=localdomain
HostName=DPOPE2
ComputerName=DPOPE2
EnvUsername=Administrator
UserDomain=DPOPE2
UserInfoName=Administrator
UserProfileFolder=C:\Documents and Settings\Administrator
UserProfileName=Administrator 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name ; Max #/chars in vol name 1752660; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to C:
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
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
ChangeInstallationSize to 10
LeaveMainPage
Locale=en_US.UTF-8
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
      Is Valid CD E:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
No CD found
DetectIso
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


gpgv: Signature made 07/03/08 16:36:17 Central Daylight Time using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
; ; ; 
      Parsing C:\ubuntu\install\MD5SUMS-metalink
Found md5 cde82e1566ad8a88e36138853c195b5f
Downloading: trymefirst= url=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink md5=cde82e1566ad8a88e36138853c195b5f
Download status=cancel
User cancelled download, quitting.
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\nss23F.tmp
detect_all
Parsing cmdline Wubi-8.04.1-rev506.exe --skipmemorycheck
debug=, 32bit=, cdboot=
User account type=Admin
arch=i386
DetectCD
      Is Valid CD C:
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
Drive & Path name 1712; Volume name ; Max #/chars in vol name 1755820; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name Admin; Volume name ; Max #/chars in vol name ; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size 
Drive c: has valid filesystem NTFS
Installation drive chosen = C:
FreeSpace in C: is 15670
DetectBackupFolder
IsBackupFolder C:\
GMT=-6
Country=US
Locale=en_US.UTF-8
TimeZone=America/Chicago
Domain=localdomain
HostName=DPOPE2
ComputerName=DPOPE2
EnvUsername=Administrator
UserDomain=DPOPE2
UserInfoName=Administrator
UserProfileFolder=C:\Documents and Settings\Administrator
UserProfileName=Administrator 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1778; Volume name ; Max #/chars in vol name 1754780; Volume Serial # -1602204316; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
Drive list = C:
ChangeInstallationDrive to C:
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
      GetDistroInfo distrofullname=Ubuntu-i386 distro=Ubuntu cddistro= cdarch= arch=i386
      ->metalinkURL=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04.1
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
ChangeInstallationSize to 10
LeaveMainPage
Locale=en_US.UTF-8
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
      Is Valid CD C:
CDInfo cleared
No CD found
DetectIso
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


gpgv: Signature made 07/03/08 16:36:17 Central Daylight Time using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
; ; ; 
      Parsing C:\ubuntu\install\MD5SUMS-metalink
Found md5 cde82e1566ad8a88e36138853c195b5f
Downloading: trymefirst= url=http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.metalink md5=cde82e1566ad8a88e36138853c195b5f
Download status=cancel
User cancelled download, quitting.

I actually did cancel the download because it slowed down to 1 kib a second.

---

