---
title: "Permission Denied during install"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by mckinleyalbert on 2009-04-30
Hi,
 
I'm trying to Install Ubuntu within Windows. However, once installation completes, I get the following error:
 
An error occurred:
 
Permission denied
 
For more information, please see the log file:
c:\users\owner\appdata\local\temp\wubi-9.04-rev128.log
 
However, there is no appdata folder within c:\users\owner on my computer. Please help! Thanks!

---

### Post by jklowden on 2009-05-02
I had a similar error.  The folder name was correct, and there was a long log message (which I saved, in case anyone wants it).  

The problem in my case turned out to have nothing to do with permissions at all.  The CD was bad.  I found out when I tried to switch to a full install.  A new CD fixed the issue completely.

---

### Post by locutis on 2009-05-19
Had them same problem, downloading the latest wubi fixed it for me. 

It's listed as one of the fixes.

---

### Post by abhi_284 on 2009-11-05
Facing the same problem
Can you tell me which version of wubi has the fix

---

### Post by abhi_284 on 2009-11-05
> **jklowden said:**
> 
The problem in my case turned out to have nothing to do with permissions at all.  The CD was bad.  I found out when I tried to switch to a full install.  A new CD fixed the issue completely.

My CD drive is suspect. 
I have used the same CD to install using wubi on a diff system.

---

### Post by fast-nu on 2009-12-17
hi every one i also got same problem while doing that.. if u got any rep then plz forward it to me @  [email]hassan.basri@hotmail.com[/email] okay.. thnx

---

### Post by Mark Phelps on 2009-12-17
To everyone experiencing this ...

The Appdata folder is "hidden" now -- it was not, if I recall, hidden under XP, and the default behaviour for Windows Explorer is to hide both system files and other hidden files (and folders) from view.

You will need to go into Windows Explorer and change it to show system files and hidden files -- then, you will see this folder.

---

### Post by pschwend on 2009-12-23
I got the same error after downloading directly to the hard drive (no CD involved) using Wubi installer.
 
I changed explorer to show hidden files however I don't know how that changes anything.
 
Apparently the boot record could not be updated because my PC still boots to Windows XP directly with no other options.
 
Anyone know what steps to take to correct this?
 
Thanks.

---

### Post by aiza on 2010-03-04
Tried installing wubi 9.10. It installs half way and then gives an error message saying permission denied. It says to check the log file which I found in C:\Documents and Settings\User\Local Settings\Temp. I don't understand much of this log file

I have Windows XP Professional with SP2. I un-installed wubi and tried to install it again twice but I still get the same error message. I have 2 hard disks. One is partitioned into 2 and the other HD is partitioned into 4. I tried installing on both hard disks but don't have any success. Plz proved me a solution for this as I keen to use ubuntu.

---

### Post by tona_107 on 2010-03-14
Any help on this issue? I know a lot of people are having this problem.

---

### Post by ON3i11S on 2010-03-22
I am having this problem as well.  I'm using the wubi installer to install ubuntu9.10 on my windows 7 machine.  After about an hour of installation (3/4ths of the way or so)  i get an error message saying the same thing

An error occurred:  Permission denied

For more information, please.... blah blah blah

I really want to put ubuntu on my machine but as of right now, it's been a hassle :(

---

### Post by Gregorybekkers on 2010-03-22
appdata is  hidden in winVista and 7...
it has no write permissions in it.
try vbox or install it from cd

---

### Post by pienyereye on 2010-04-03
I was having the same issue for a couple of weeks since I upgraded to Windows 7. Originally, I installed 9.10 from a CD after Windows Vista and had a dual boot situation - which was great.
 
I upgraded to Win7 and lost Grub. I expected this. However, I was getting the access denied error when trying to reload from the same CD that worked fine on my desktop machine. 

Here is what I did to fix this issue. I am not saying this is the perfect way to fix but it worked for me and it seems like folks are still having this problem so here it goes...
I downloaded Virtual CloneDrive (google it - its freeware) When I installed Virtual CloneDrive, I associated the .iso files with it and no others. I then ran the .iso file that I originally downloaded to make my disc, directly from my Program Files folder by double-clicking. It should be mounted and launch as a virtual drive and run like the disc but without using the disc. I think the access denied error has something to do with the disc drive but I was unable to fix it. 

Just follow your prompts to install as you normally would from the CD. Apparently, it saved all my settings from my previous Ubuntu install so I was psyched. :guitar:

Again, this may not be the best way to fix but I am more of a Windows geek than a Linux geek (but I am working on it ;P) Also, it may not fix your issue at all or make it worse so if that is the case, be sure to post back ASAP! My experience was good.
Good Luck

---

### Post by yoog on 2010-04-07
Method posted by pienyereye works very well. I think I faced the similar problem in the past trying to install from CD+RW and I end up burning ISO on teh CD-R and then installation went fine.
 
Kudos to pienyereye.

---

### Post by pseudocube on 2010-05-04
Aaah, same error here. Installing 10.04 with Wubi installer (no CD) in Vista:
```
05-03 17:43 INFO   root: === wubi 10.04 rev189 ===
05-03 17:43 DEBUG  root: Logfile is c:\users\andrew\appdata\local\temp\wubi-10.04-rev189.log
05-03 17:43 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Andrew\\Desktop\\wubi.exe"']
05-03 17:43 DEBUG  CommonBackend: data_dir=C:\Users\Andrew\AppData\Local\Temp\pyl448E.tmp\data
05-03 17:43 DEBUG  WindowsBackend: 7z=C:\Users\Andrew\AppData\Local\Temp\pyl448E.tmp\bin\7z.exe
05-03 17:43 DEBUG  CommonBackend: Fetching basic info...
05-03 17:43 DEBUG  CommonBackend: original_exe=C:\Users\Andrew\Desktop\wubi.exe
05-03 17:43 DEBUG  CommonBackend: platform=win32
05-03 17:43 DEBUG  CommonBackend: osname=nt
05-03 17:43 DEBUG  CommonBackend: language=en_US
05-03 17:43 DEBUG  CommonBackend: encoding=cp1252
05-03 17:43 DEBUG  WindowsBackend: arch=i386
05-03 17:43 DEBUG  CommonBackend: Parsing isolist=C:\Users\Andrew\AppData\Local\Temp\pyl448E.tmp\data\isolist.ini
05-03 17:43 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-03 17:43 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-03 17:43 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-03 17:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-03 17:43 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-03 17:43 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-03 17:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-03 17:43 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-03 17:43 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
05-03 17:43 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-03 17:43 DEBUG  WindowsBackend: Fetching host info...
05-03 17:43 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-03 17:43 DEBUG  WindowsBackend: windows version=vista
05-03 17:43 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Business
05-03 17:43 DEBUG  WindowsBackend: windows_sp=None
05-03 17:43 DEBUG  WindowsBackend: windows_build=6000
05-03 17:43 DEBUG  WindowsBackend: gmt=-8
05-03 17:43 DEBUG  WindowsBackend: country=US
05-03 17:43 DEBUG  WindowsBackend: timezone=America/Los_Angeles
05-03 17:43 DEBUG  WindowsBackend: windows_username=Andrew
05-03 17:43 DEBUG  WindowsBackend: user_full_name=Andrew
05-03 17:43 DEBUG  WindowsBackend: user_directory=C:\Users\Andrew
05-03 17:43 DEBUG  WindowsBackend: windows_language_code=1033
05-03 17:43 DEBUG  WindowsBackend: windows_language=English
05-03 17:43 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) Duo CPU      T2400  @ 1.83GHz
05-03 17:43 DEBUG  WindowsBackend: bootloader=vista
05-03 17:43 DEBUG  WindowsBackend: system_drive=Drive(C: hd 45699.9648438 mb free ntfs)
05-03 17:43 DEBUG  WindowsBackend: drive=Drive(C: hd 45699.9648438 mb free ntfs)
05-03 17:43 DEBUG  WindowsBackend: drive=Drive(D: hd 767.421875 mb free ntfs)
05-03 17:43 DEBUG  WindowsBackend: drive=Drive(E: hd 1347.55859375 mb free ntfs)
05-03 17:43 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
05-03 17:43 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-03 17:43 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-03 17:43 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-03 17:43 DEBUG  WindowsBackend: keyboard_id=67699721
05-03 17:43 DEBUG  WindowsBackend: keyboard_layout=us
05-03 17:43 DEBUG  WindowsBackend: keyboard_variant=
05-03 17:43 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-03 17:43 DEBUG  CommonBackend: locale=en_US.UTF-8
05-03 17:43 DEBUG  WindowsBackend: total_memory_mb=1014.8125
05-03 17:43 DEBUG  CommonBackend: Searching ISOs on USB devices
05-03 17:43 DEBUG  CommonBackend: Searching for local CDs
05-03 17:43 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pyl448E.tmp is a valid Ubuntu CD
05-03 17:43 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pyl448E.tmp\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pyl448E.tmp is a valid Ubuntu CD
05-03 17:43 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pyl448E.tmp\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pyl448E.tmp is a valid Ubuntu Netbook CD
05-03 17:43 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pyl448E.tmp\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pyl448E.tmp is a valid Kubuntu CD
05-03 17:43 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pyl448E.tmp\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pyl448E.tmp is a valid Kubuntu CD
05-03 17:43 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pyl448E.tmp\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pyl448E.tmp is a valid Kubuntu Netbook CD
05-03 17:43 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pyl448E.tmp\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pyl448E.tmp is a valid Xubuntu CD
05-03 17:43 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pyl448E.tmp\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pyl448E.tmp is a valid Xubuntu CD
05-03 17:43 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pyl448E.tmp\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pyl448E.tmp is a valid Mythbuntu CD
05-03 17:43 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pyl448E.tmp\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pyl448E.tmp is a valid Mythbuntu CD
05-03 17:43 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pyl448E.tmp\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-03 17:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-03 17:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-03 17:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-03 17:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-03 17:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
05-03 17:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-03 17:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-03 17:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-03 17:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-03 17:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-03 17:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-03 17:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-03 17:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-03 17:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-03 17:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
05-03 17:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-03 17:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-03 17:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-03 17:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-03 17:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-03 17:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-03 17:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
05-03 17:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-03 17:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-03 17:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
05-03 17:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-03 17:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-03 17:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-03 17:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-03 17:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 17:43 INFO   root: Already installed, running the uninstaller...
05-03 17:43 INFO   root: Running the uninstaller...
05-03 17:43 INFO   CommonBackend: Launching previous uninestaller C:\ubuntu\uninstall-wubi.exe
05-03 17:44 DEBUG  root: application.quit
05-03 17:44 DEBUG  root: application.on_quit
05-03 17:44 INFO   root: sys.exit
05-03 17:44 INFO   root: Quitting application
05-03 17:45 INFO   root: === wubi 10.04 rev189 ===
05-03 17:45 DEBUG  root: Logfile is c:\users\andrew\appdata\local\temp\wubi-10.04-rev189.log
05-03 17:45 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Andrew\\Desktop\\wubi.exe"']
05-03 17:45 DEBUG  CommonBackend: data_dir=C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp\data
05-03 17:45 DEBUG  WindowsBackend: 7z=C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp\bin\7z.exe
05-03 17:45 DEBUG  CommonBackend: Fetching basic info...
05-03 17:45 DEBUG  CommonBackend: original_exe=C:\Users\Andrew\Desktop\wubi.exe
05-03 17:45 DEBUG  CommonBackend: platform=win32
05-03 17:45 DEBUG  CommonBackend: osname=nt
05-03 17:45 DEBUG  CommonBackend: language=en_US
05-03 17:45 DEBUG  CommonBackend: encoding=cp1252
05-03 17:45 DEBUG  WindowsBackend: arch=i386
05-03 17:45 DEBUG  CommonBackend: Parsing isolist=C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp\data\isolist.ini
05-03 17:45 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-03 17:45 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-03 17:45 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-03 17:45 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-03 17:45 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-03 17:45 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-03 17:45 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-03 17:45 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-03 17:45 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
05-03 17:45 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-03 17:45 DEBUG  WindowsBackend: Fetching host info...
05-03 17:45 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-03 17:45 DEBUG  WindowsBackend: windows version=vista
05-03 17:45 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Business
05-03 17:45 DEBUG  WindowsBackend: windows_sp=None
05-03 17:45 DEBUG  WindowsBackend: windows_build=6000
05-03 17:45 DEBUG  WindowsBackend: gmt=-8
05-03 17:45 DEBUG  WindowsBackend: country=US
05-03 17:45 DEBUG  WindowsBackend: timezone=America/Los_Angeles
05-03 17:45 DEBUG  WindowsBackend: windows_username=Andrew
05-03 17:45 DEBUG  WindowsBackend: user_full_name=Andrew
05-03 17:45 DEBUG  WindowsBackend: user_directory=C:\Users\Andrew
05-03 17:45 DEBUG  WindowsBackend: windows_language_code=1033
05-03 17:45 DEBUG  WindowsBackend: windows_language=English
05-03 17:45 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) Duo CPU      T2400  @ 1.83GHz
05-03 17:45 DEBUG  WindowsBackend: bootloader=vista
05-03 17:45 DEBUG  WindowsBackend: system_drive=Drive(C: hd 63390.53125 mb free ntfs)
05-03 17:45 DEBUG  WindowsBackend: drive=Drive(C: hd 63390.53125 mb free ntfs)
05-03 17:45 DEBUG  WindowsBackend: drive=Drive(D: hd 767.421875 mb free ntfs)
05-03 17:45 DEBUG  WindowsBackend: drive=Drive(E: hd 1347.55859375 mb free ntfs)
05-03 17:45 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
05-03 17:45 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-03 17:45 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-03 17:45 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-03 17:45 DEBUG  WindowsBackend: keyboard_id=67699721
05-03 17:45 DEBUG  WindowsBackend: keyboard_layout=us
05-03 17:45 DEBUG  WindowsBackend: keyboard_variant=
05-03 17:45 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-03 17:45 DEBUG  CommonBackend: locale=en_US.UTF-8
05-03 17:45 DEBUG  WindowsBackend: total_memory_mb=1014.8125
05-03 17:45 DEBUG  CommonBackend: Searching ISOs on USB devices
05-03 17:45 DEBUG  CommonBackend: Searching for local CDs
05-03 17:45 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp is a valid Ubuntu CD
05-03 17:45 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp is a valid Ubuntu CD
05-03 17:45 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp is a valid Ubuntu Netbook CD
05-03 17:45 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp is a valid Kubuntu CD
05-03 17:45 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp is a valid Kubuntu CD
05-03 17:45 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp is a valid Kubuntu Netbook CD
05-03 17:45 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp is a valid Xubuntu CD
05-03 17:45 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp is a valid Xubuntu CD
05-03 17:45 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp is a valid Mythbuntu CD
05-03 17:45 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp is a valid Mythbuntu CD
05-03 17:45 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-03 17:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-03 17:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-03 17:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-03 17:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-03 17:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
05-03 17:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-03 17:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-03 17:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-03 17:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-03 17:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-03 17:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-03 17:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-03 17:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-03 17:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-03 17:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
05-03 17:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-03 17:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-03 17:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-03 17:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-03 17:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-03 17:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-03 17:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
05-03 17:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-03 17:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-03 17:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
05-03 17:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-03 17:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-03 17:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-03 17:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-03 17:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 17:45 INFO   root: Running the installer...
05-03 17:45 DEBUG  WindowsFrontend: __init__...
05-03 17:45 DEBUG  WindowsFrontend: on_init...
05-03 17:45 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp\translations, languages=['en_US', 'en']
05-03 17:45 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp\translations, languages=['en_US', 'en']
05-03 17:46 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=andrew
05-03 17:46 INFO   root: Received settings
05-03 17:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp\translations, languages=['en_US', 'en']
05-03 17:46 DEBUG  TaskList: # Running tasklist...
05-03 17:46 DEBUG  TaskList: ## Running select_target_dir...
05-03 17:46 INFO   WindowsBackend: Installing into C:\ubuntu
05-03 17:46 DEBUG  TaskList: ## Finished select_target_dir
05-03 17:46 DEBUG  TaskList: ## Running create_dir_structure...
05-03 17:46 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-03 17:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-03 17:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-03 17:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-03 17:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-03 17:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-03 17:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-03 17:46 DEBUG  TaskList: ## Finished create_dir_structure
05-03 17:46 DEBUG  TaskList: ## Running uncompress_target_dir...
05-03 17:46 DEBUG  TaskList: ## Finished uncompress_target_dir
05-03 17:46 DEBUG  TaskList: ## Running create_uninstaller...
05-03 17:46 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Andrew\Desktop\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
05-03 17:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-03 17:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-03 17:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-03 17:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
05-03 17:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
05-03 17:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-03 17:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
05-03 17:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
05-03 17:46 DEBUG  TaskList: ## Finished create_uninstaller
05-03 17:46 DEBUG  TaskList: ## Running copy_installation_files...
05-03 17:46 DEBUG  WindowsBackend: Copying C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-03 17:46 DEBUG  WindowsBackend: Copying C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp\winboot -> C:\ubuntu\winboot
05-03 17:46 DEBUG  WindowsBackend: Copying C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
05-03 17:46 DEBUG  TaskList: ## Finished copy_installation_files
05-03 17:46 DEBUG  TaskList: ## Running get_iso...
05-03 17:46 DEBUG  CommonBackend: Searching for local CD
05-03 17:46 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp is a valid Ubuntu CD
05-03 17:46 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp\casper\filesystem.squashfs
05-03 17:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-03 17:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 17:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-03 17:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 17:46 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-03 17:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 17:46 DEBUG  CommonBackend: Searching for local ISO
05-03 17:46 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-03 17:46 DEBUG  TaskList: New task get_metalink
05-03 17:46 DEBUG  TaskList: ### Running get_metalink...
05-03 17:46 DEBUG  downloader: downloading http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink > C:\ubuntu\install
05-03 17:46 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-10.04-desktop-i386.metalink, url=http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink, basename=ubuntu-10.04-desktop-i386.metalink, length=7420, text=None
05-03 17:46 DEBUG  downloader: download finished (read 7420 bytes)
05-03 17:46 DEBUG  downloader: downloading http://releases.ubuntu.com/10.04/MD5SUMS-metalink > C:\ubuntu\install
05-03 17:46 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=639, text=None
05-03 17:46 DEBUG  downloader: download finished (read 639 bytes)
05-03 17:46 DEBUG  downloader: downloading http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg > C:\ubuntu\install
05-03 17:46 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
05-03 17:46 DEBUG  downloader: download finished (read 189 bytes)
05-03 17:46 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
05-03 17:46 INFO   saplog: Checking block bindings..
05-03 17:46 INFO   saplog: Key verified successfully.
05-03 17:46 DEBUG  CommonBackend: metalink md5sums:
63592a82b86f25a2b75ec10e75fba8f5  ubuntu-10.04-alternate-amd64.metalink
1ad74973481704af353be8dce13b8a83  ubuntu-10.04-alternate-i386.metalink
999542213cd64cabdca682c080a7227a  ubuntu-10.04-desktop-amd64.metalink
0b3f5975f84933431267f1be5daf0882  ubuntu-10.04-desktop-i386.metalink
d57239ea96a3e3c7ac3d03672de0596e  ubuntu-10.04-netbook-armel+dove.metalink
fecad822acacbf0d5763eab4b21c7bef  ubuntu-10.04-netbook-armel+imx51.metalink
a92079601c82c2c8b60c2e2d43df09b6  ubuntu-10.04-netbook-i386.metalink
4804fa76f01904b80847e06ff159f4b5  ubuntu-10.04-server-amd64.metalink
4cb4790703d19ac401e10de456e643f0  ubuntu-10.04-server-i386.metalink

05-03 17:46 DEBUG  TaskList: ### Finished get_metalink
05-03 17:46 DEBUG  TaskList: New task download
05-03 17:46 DEBUG  TaskList: ### Running download...
05-03 17:46 DEBUG  btdownloader: downloading http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.iso.torrent > C:\ubuntu\install\ubuntu-10.04-desktop-i386.iso
05-03 19:46 ERROR  TaskList: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\btdownloader.py", line 79, in download
  File "\lib\bittorrent\download.py", line 303, in download
  File "\lib\bittorrent\RawServer.py", line 256, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request


05-03 19:46 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

 in task download
05-03 19:46 DEBUG  TaskList: ### Finished download
05-03 19:46 ERROR  TaskList: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04-desktop-i386.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04-desktop-i386.iso'
05-03 19:46 DEBUG  TaskList: # Cancelling tasklist
05-03 19:46 DEBUG  TaskList: # Finished tasklist
05-03 19:46 ERROR  root: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04-desktop-i386.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04-desktop-i386.iso'
05-03 21:05 INFO   root: === wubi 10.04 rev189 ===
05-03 21:05 DEBUG  root: Logfile is c:\users\andrew\appdata\local\temp\wubi-10.04-rev189.log
05-03 21:05 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Andrew\\Desktop\\wubi.exe"']
05-03 21:05 DEBUG  CommonBackend: data_dir=C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp\data
05-03 21:05 DEBUG  WindowsBackend: 7z=C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp\bin\7z.exe
05-03 21:05 DEBUG  CommonBackend: Fetching basic info...
05-03 21:05 DEBUG  CommonBackend: original_exe=C:\Users\Andrew\Desktop\wubi.exe
05-03 21:05 DEBUG  CommonBackend: platform=win32
05-03 21:05 DEBUG  CommonBackend: osname=nt
05-03 21:05 DEBUG  CommonBackend: language=en_US
05-03 21:05 DEBUG  CommonBackend: encoding=cp1252
05-03 21:05 DEBUG  WindowsBackend: arch=i386
05-03 21:05 DEBUG  CommonBackend: Parsing isolist=C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp\data\isolist.ini
05-03 21:05 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-03 21:05 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-03 21:05 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-03 21:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-03 21:05 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-03 21:05 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-03 21:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-03 21:05 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-03 21:05 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
05-03 21:05 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-03 21:05 DEBUG  WindowsBackend: Fetching host info...
05-03 21:05 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-03 21:05 DEBUG  WindowsBackend: windows version=vista
05-03 21:05 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Business
05-03 21:05 DEBUG  WindowsBackend: windows_sp=None
05-03 21:05 DEBUG  WindowsBackend: windows_build=6000
05-03 21:05 DEBUG  WindowsBackend: gmt=-8
05-03 21:05 DEBUG  WindowsBackend: country=US
05-03 21:05 DEBUG  WindowsBackend: timezone=America/Los_Angeles
05-03 21:05 DEBUG  WindowsBackend: windows_username=Andrew
05-03 21:05 DEBUG  WindowsBackend: user_full_name=Andrew
05-03 21:05 DEBUG  WindowsBackend: user_directory=C:\Users\Andrew
05-03 21:05 DEBUG  WindowsBackend: windows_language_code=1033
05-03 21:05 DEBUG  WindowsBackend: windows_language=English
05-03 21:05 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) Duo CPU      T2400  @ 1.83GHz
05-03 21:05 DEBUG  WindowsBackend: bootloader=vista
05-03 21:05 DEBUG  WindowsBackend: system_drive=Drive(C: hd 63464.7421875 mb free ntfs)
05-03 21:05 DEBUG  WindowsBackend: drive=Drive(C: hd 63464.7421875 mb free ntfs)
05-03 21:05 DEBUG  WindowsBackend: drive=Drive(D: hd 767.421875 mb free ntfs)
05-03 21:05 DEBUG  WindowsBackend: drive=Drive(E: hd 1347.55859375 mb free ntfs)
05-03 21:05 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
05-03 21:05 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-03 21:05 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-03 21:05 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-03 21:05 DEBUG  WindowsBackend: keyboard_id=67699721
05-03 21:05 DEBUG  WindowsBackend: keyboard_layout=us
05-03 21:05 DEBUG  WindowsBackend: keyboard_variant=
05-03 21:05 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-03 21:05 DEBUG  CommonBackend: locale=en_US.UTF-8
05-03 21:05 DEBUG  WindowsBackend: total_memory_mb=1014.8125
05-03 21:05 DEBUG  CommonBackend: Searching ISOs on USB devices
05-03 21:05 DEBUG  CommonBackend: Searching for local CDs
05-03 21:05 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp is a valid Ubuntu CD
05-03 21:05 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp is a valid Ubuntu CD
05-03 21:05 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp is a valid Ubuntu Netbook CD
05-03 21:05 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp is a valid Kubuntu CD
05-03 21:05 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp is a valid Kubuntu CD
05-03 21:05 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp is a valid Kubuntu Netbook CD
05-03 21:05 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp is a valid Xubuntu CD
05-03 21:05 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp is a valid Xubuntu CD
05-03 21:05 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp is a valid Mythbuntu CD
05-03 21:05 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp is a valid Mythbuntu CD
05-03 21:05 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-03 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-03 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-03 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-03 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-03 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
05-03 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-03 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-03 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-03 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-03 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-03 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-03 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-03 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-03 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-03 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
05-03 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-03 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-03 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-03 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-03 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-03 21:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-03 21:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
05-03 21:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-03 21:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-03 21:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
05-03 21:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-03 21:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-03 21:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-03 21:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-03 21:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 21:05 INFO   root: Already installed, running the uninstaller...
05-03 21:05 INFO   root: Running the uninstaller...
05-03 21:05 INFO   CommonBackend: This is the uninstaller running
05-03 21:05 DEBUG  WindowsFrontend: __init__...
05-03 21:05 DEBUG  WindowsFrontend: on_init...
05-03 21:05 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp\translations, languages=['en_US', 'en']
05-03 21:05 INFO   root: Received settings
05-03 21:05 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp\translations, languages=['en_US', 'en']
05-03 21:05 DEBUG  TaskList: # Running tasklist...
05-03 21:05 DEBUG  TaskList: ## Running Backup ISO...
05-03 21:05 DEBUG  TaskList: ## Finished Backup ISO
05-03 21:05 DEBUG  TaskList: ## Running Remove bootloader entry...
05-03 21:05 DEBUG  WindowsBackend: Could not find bcd id
05-03 21:05 DEBUG  WindowsBackend: undo_bootini C:
05-03 21:05 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 63464.7421875 mb free ntfs)
05-03 21:05 ERROR  TaskList: [Errno 13] Permission denied: 'C:\\config.sys'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 506, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 599, in undo_configsys
  File "\lib\wubi\backends\common\utils.py", line 246, in write_file
IOError: [Errno 13] Permission denied: 'C:\\config.sys'
05-03 21:05 DEBUG  TaskList: # Cancelling tasklist
05-03 21:05 DEBUG  TaskList: # Finished tasklist
05-03 21:05 ERROR  root: [Errno 13] Permission denied: 'C:\\config.sys'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 143, in run_installer
  File "\lib\wubi\application.py", line 177, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 506, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 599, in undo_configsys
  File "\lib\wubi\backends\common\utils.py", line 246, in write_file
IOError: [Errno 13] Permission denied: 'C:\\config.sys'
05-03 21:06 INFO   root: === wubi 10.04 rev189 ===
05-03 21:06 DEBUG  root: Logfile is c:\users\andrew\appdata\local\temp\wubi-10.04-rev189.log
05-03 21:06 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Andrew\\Desktop\\wubi.exe"']
05-03 21:06 DEBUG  CommonBackend: data_dir=C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp\data
05-03 21:06 DEBUG  WindowsBackend: 7z=C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp\bin\7z.exe
05-03 21:06 DEBUG  CommonBackend: Fetching basic info...
05-03 21:06 DEBUG  CommonBackend: original_exe=C:\Users\Andrew\Desktop\wubi.exe
05-03 21:06 DEBUG  CommonBackend: platform=win32
05-03 21:06 DEBUG  CommonBackend: osname=nt
05-03 21:06 DEBUG  CommonBackend: language=en_US
05-03 21:06 DEBUG  CommonBackend: encoding=cp1252
05-03 21:06 DEBUG  WindowsBackend: arch=i386
05-03 21:06 DEBUG  CommonBackend: Parsing isolist=C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp\data\isolist.ini
05-03 21:06 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-03 21:06 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-03 21:06 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-03 21:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-03 21:06 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-03 21:06 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-03 21:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-03 21:06 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-03 21:06 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
05-03 21:06 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-03 21:06 DEBUG  WindowsBackend: Fetching host info...
05-03 21:06 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-03 21:06 DEBUG  WindowsBackend: windows version=vista
05-03 21:06 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Business
05-03 21:06 DEBUG  WindowsBackend: windows_sp=None
05-03 21:06 DEBUG  WindowsBackend: windows_build=6000
05-03 21:06 DEBUG  WindowsBackend: gmt=-8
05-03 21:06 DEBUG  WindowsBackend: country=US
05-03 21:06 DEBUG  WindowsBackend: timezone=America/Los_Angeles
05-03 21:06 DEBUG  WindowsBackend: windows_username=Andrew
05-03 21:06 DEBUG  WindowsBackend: user_full_name=Andrew
05-03 21:06 DEBUG  WindowsBackend: user_directory=C:\Users\Andrew
05-03 21:06 DEBUG  WindowsBackend: windows_language_code=1033
05-03 21:06 DEBUG  WindowsBackend: windows_language=English
05-03 21:06 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) Duo CPU      T2400  @ 1.83GHz
05-03 21:06 DEBUG  WindowsBackend: bootloader=vista
05-03 21:06 DEBUG  WindowsBackend: system_drive=Drive(C: hd 63464.4453125 mb free ntfs)
05-03 21:06 DEBUG  WindowsBackend: drive=Drive(C: hd 63464.4453125 mb free ntfs)
05-03 21:06 DEBUG  WindowsBackend: drive=Drive(D: hd 767.421875 mb free ntfs)
05-03 21:06 DEBUG  WindowsBackend: drive=Drive(E: hd 1347.55859375 mb free ntfs)
05-03 21:06 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
05-03 21:06 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-03 21:06 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-03 21:06 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-03 21:06 DEBUG  WindowsBackend: keyboard_id=67699721
05-03 21:06 DEBUG  WindowsBackend: keyboard_layout=us
05-03 21:06 DEBUG  WindowsBackend: keyboard_variant=
05-03 21:06 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-03 21:06 DEBUG  CommonBackend: locale=en_US.UTF-8
05-03 21:06 DEBUG  WindowsBackend: total_memory_mb=1014.8125
05-03 21:06 DEBUG  CommonBackend: Searching ISOs on USB devices
05-03 21:06 DEBUG  CommonBackend: Searching for local CDs
05-03 21:06 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp is a valid Ubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp is a valid Ubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp is a valid Ubuntu Netbook CD
05-03 21:06 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp is a valid Kubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp is a valid Kubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp is a valid Kubuntu Netbook CD
05-03 21:06 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp is a valid Xubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp is a valid Xubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp is a valid Mythbuntu CD
05-03 21:06 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp is a valid Mythbuntu CD
05-03 21:06 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-03 21:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
05-03 21:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-03 21:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-03 21:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-03 21:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
05-03 21:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-03 21:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-03 21:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
05-03 21:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
05-03 21:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-03 21:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-03 21:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 21:06 INFO   root: Running the installer...
05-03 21:06 DEBUG  WindowsFrontend: __init__...
05-03 21:06 DEBUG  WindowsFrontend: on_init...
05-03 21:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp\translations, languages=['en_US', 'en']
05-03 21:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp\translations, languages=['en_US', 'en']
05-03 21:06 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=andrew
05-03 21:06 INFO   root: Received settings
05-03 21:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp\translations, languages=['en_US', 'en']
05-03 21:06 DEBUG  TaskList: # Running tasklist...
05-03 21:06 DEBUG  TaskList: ## Running select_target_dir...
05-03 21:06 INFO   WindowsBackend: Installing into C:\ubuntu
05-03 21:06 DEBUG  TaskList: ## Finished select_target_dir
05-03 21:06 DEBUG  TaskList: ## Running create_dir_structure...
05-03 21:06 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-03 21:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-03 21:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-03 21:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-03 21:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-03 21:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-03 21:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-03 21:06 DEBUG  TaskList: ## Finished create_dir_structure
05-03 21:06 DEBUG  TaskList: ## Running uncompress_target_dir...
05-03 21:06 DEBUG  TaskList: ## Finished uncompress_target_dir
05-03 21:06 DEBUG  TaskList: ## Running create_uninstaller...
05-03 21:06 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Andrew\Desktop\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
05-03 21:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-03 21:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-03 21:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-03 21:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
05-03 21:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
05-03 21:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-03 21:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
05-03 21:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
05-03 21:06 DEBUG  TaskList: ## Finished create_uninstaller
05-03 21:06 DEBUG  TaskList: ## Running copy_installation_files...
05-03 21:06 DEBUG  WindowsBackend: Copying C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-03 21:06 DEBUG  WindowsBackend: Copying C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp\winboot -> C:\ubuntu\winboot
05-03 21:06 DEBUG  WindowsBackend: Copying C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
05-03 21:06 DEBUG  TaskList: ## Finished copy_installation_files
05-03 21:06 DEBUG  TaskList: ## Running get_iso...
05-03 21:06 DEBUG  CommonBackend: Searching for local CD
05-03 21:06 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp is a valid Ubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 21:06 DEBUG  CommonBackend: Searching for local ISO
05-03 21:06 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-03 21:06 DEBUG  TaskList: New task get_metalink
05-03 21:06 DEBUG  TaskList: ### Running get_metalink...
05-03 21:06 DEBUG  downloader: downloading http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink > C:\ubuntu\install
05-03 21:06 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-10.04-desktop-i386.metalink, url=http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink, basename=ubuntu-10.04-desktop-i386.metalink, length=7420, text=None
05-03 21:06 DEBUG  downloader: download finished (read 7420 bytes)
05-03 21:06 DEBUG  downloader: downloading http://releases.ubuntu.com/10.04/MD5SUMS-metalink > C:\ubuntu\install
05-03 21:06 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=639, text=None
05-03 21:06 DEBUG  downloader: download finished (read 639 bytes)
05-03 21:06 DEBUG  downloader: downloading http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg > C:\ubuntu\install
05-03 21:06 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
05-03 21:06 DEBUG  downloader: download finished (read 189 bytes)
05-03 21:06 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
05-03 21:06 INFO   saplog: Checking block bindings..
05-03 21:06 INFO   saplog: Key verified successfully.
05-03 21:06 DEBUG  CommonBackend: metalink md5sums:
63592a82b86f25a2b75ec10e75fba8f5  ubuntu-10.04-alternate-amd64.metalink
1ad74973481704af353be8dce13b8a83  ubuntu-10.04-alternate-i386.metalink
999542213cd64cabdca682c080a7227a  ubuntu-10.04-desktop-amd64.metalink
0b3f5975f84933431267f1be5daf0882  ubuntu-10.04-desktop-i386.metalink
d57239ea96a3e3c7ac3d03672de0596e  ubuntu-10.04-netbook-armel+dove.metalink
fecad822acacbf0d5763eab4b21c7bef  ubuntu-10.04-netbook-armel+imx51.metalink
a92079601c82c2c8b60c2e2d43df09b6  ubuntu-10.04-netbook-i386.metalink
4804fa76f01904b80847e06ff159f4b5  ubuntu-10.04-server-amd64.metalink
4cb4790703d19ac401e10de456e643f0  ubuntu-10.04-server-i386.metalink

05-03 21:06 DEBUG  TaskList: ### Finished get_metalink
05-03 21:06 DEBUG  TaskList: New task download
05-03 21:06 DEBUG  TaskList: ### Running download...
05-03 21:06 DEBUG  btdownloader: downloading http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.iso.torrent > C:\ubuntu\install\ubuntu-10.04-desktop-i386.iso
05-03 22:36 ERROR  TaskList: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\btdownloader.py", line 79, in download
  File "\lib\bittorrent\download.py", line 303, in download
  File "\lib\bittorrent\RawServer.py", line 256, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request


05-03 22:36 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

 in task download
05-03 22:36 DEBUG  TaskList: ### Finished download
05-03 22:36 ERROR  TaskList: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04-desktop-i386.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04-desktop-i386.iso'
05-03 22:36 DEBUG  TaskList: # Cancelling tasklist
05-03 22:36 DEBUG  TaskList: # Finished tasklist
05-03 22:36 ERROR  root: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04-desktop-i386.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04-desktop-i386.iso'

```

---

### Post by mihdih on 2010-05-18
Hi

As stated by Mark Phelps and Gregorybekkers, Application Data is 'Hidden" by default. Hence 'Permission denied'. 

To resolve the issue, this is what I did:

Note: Done in Windows XP SP3, dunno if this works in Vista or in Windows 7

1. Open C:\Documents and Settings
2. Show hidden files and folders in Tools > Folder Options > View
3. Under the user (e.g. Administrator) folder find 'Application Data' folder
[INDENT]Example: C:\Documents and Settings\Administrator [/INDENT]
4. Modify its properties, uncheck 'Hidden' option, then save
5. Under 'User\Local Settings' find 'Application Data' folder
[INDENT]Example: C:\Documents and Settings\Administrator\Local Settings[/INDENT]
6. Modify its properties, uncheck 'Hidden' option, then save
7. Then finally install Ubuntu 10.04 via Wubi

Basically you'll just have to unhide 'Application Data' folder

Hope this helps...

Cheers

> **pseudocube said:**
> Aaah, same error here. Installing 10.04 with Wubi installer (no CD) in Vista:
```
05-03 17:43 INFO   root: === wubi 10.04 rev189 ===
05-03 17:43 DEBUG  root: Logfile is c:\users\andrew\appdata\local\temp\wubi-10.04-rev189.log
05-03 17:43 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Andrew\\Desktop\\wubi.exe"']
05-03 17:43 DEBUG  CommonBackend: data_dir=C:\Users\Andrew\AppData\Local\Temp\pyl448E.tmp\data
05-03 17:43 DEBUG  WindowsBackend: 7z=C:\Users\Andrew\AppData\Local\Temp\pyl448E.tmp\bin\7z.exe
05-03 17:43 DEBUG  CommonBackend: Fetching basic info...
05-03 17:43 DEBUG  CommonBackend: original_exe=C:\Users\Andrew\Desktop\wubi.exe
05-03 17:43 DEBUG  CommonBackend: platform=win32
05-03 17:43 DEBUG  CommonBackend: osname=nt
05-03 17:43 DEBUG  CommonBackend: language=en_US
05-03 17:43 DEBUG  CommonBackend: encoding=cp1252
05-03 17:43 DEBUG  WindowsBackend: arch=i386
05-03 17:43 DEBUG  CommonBackend: Parsing isolist=C:\Users\Andrew\AppData\Local\Temp\pyl448E.tmp\data\isolist.ini
05-03 17:43 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-03 17:43 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-03 17:43 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-03 17:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-03 17:43 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-03 17:43 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-03 17:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-03 17:43 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-03 17:43 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
05-03 17:43 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-03 17:43 DEBUG  WindowsBackend: Fetching host info...
05-03 17:43 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-03 17:43 DEBUG  WindowsBackend: windows version=vista
05-03 17:43 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Business
05-03 17:43 DEBUG  WindowsBackend: windows_sp=None
05-03 17:43 DEBUG  WindowsBackend: windows_build=6000
05-03 17:43 DEBUG  WindowsBackend: gmt=-8
05-03 17:43 DEBUG  WindowsBackend: country=US
05-03 17:43 DEBUG  WindowsBackend: timezone=America/Los_Angeles
05-03 17:43 DEBUG  WindowsBackend: windows_username=Andrew
05-03 17:43 DEBUG  WindowsBackend: user_full_name=Andrew
05-03 17:43 DEBUG  WindowsBackend: user_directory=C:\Users\Andrew
05-03 17:43 DEBUG  WindowsBackend: windows_language_code=1033
05-03 17:43 DEBUG  WindowsBackend: windows_language=English
05-03 17:43 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) Duo CPU      T2400  @ 1.83GHz
05-03 17:43 DEBUG  WindowsBackend: bootloader=vista
05-03 17:43 DEBUG  WindowsBackend: system_drive=Drive(C: hd 45699.9648438 mb free ntfs)
05-03 17:43 DEBUG  WindowsBackend: drive=Drive(C: hd 45699.9648438 mb free ntfs)
05-03 17:43 DEBUG  WindowsBackend: drive=Drive(D: hd 767.421875 mb free ntfs)
05-03 17:43 DEBUG  WindowsBackend: drive=Drive(E: hd 1347.55859375 mb free ntfs)
05-03 17:43 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
05-03 17:43 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-03 17:43 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-03 17:43 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-03 17:43 DEBUG  WindowsBackend: keyboard_id=67699721
05-03 17:43 DEBUG  WindowsBackend: keyboard_layout=us
05-03 17:43 DEBUG  WindowsBackend: keyboard_variant=
05-03 17:43 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-03 17:43 DEBUG  CommonBackend: locale=en_US.UTF-8
05-03 17:43 DEBUG  WindowsBackend: total_memory_mb=1014.8125
05-03 17:43 DEBUG  CommonBackend: Searching ISOs on USB devices
05-03 17:43 DEBUG  CommonBackend: Searching for local CDs
05-03 17:43 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pyl448E.tmp is a valid Ubuntu CD
05-03 17:43 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pyl448E.tmp\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pyl448E.tmp is a valid Ubuntu CD
05-03 17:43 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pyl448E.tmp\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pyl448E.tmp is a valid Ubuntu Netbook CD
05-03 17:43 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pyl448E.tmp\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pyl448E.tmp is a valid Kubuntu CD
05-03 17:43 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pyl448E.tmp\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pyl448E.tmp is a valid Kubuntu CD
05-03 17:43 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pyl448E.tmp\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pyl448E.tmp is a valid Kubuntu Netbook CD
05-03 17:43 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pyl448E.tmp\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pyl448E.tmp is a valid Xubuntu CD
05-03 17:43 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pyl448E.tmp\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pyl448E.tmp is a valid Xubuntu CD
05-03 17:43 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pyl448E.tmp\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pyl448E.tmp is a valid Mythbuntu CD
05-03 17:43 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pyl448E.tmp\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pyl448E.tmp is a valid Mythbuntu CD
05-03 17:43 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pyl448E.tmp\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-03 17:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-03 17:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-03 17:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-03 17:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-03 17:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
05-03 17:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-03 17:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-03 17:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-03 17:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-03 17:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-03 17:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-03 17:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-03 17:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-03 17:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-03 17:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
05-03 17:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-03 17:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-03 17:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-03 17:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-03 17:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-03 17:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-03 17:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
05-03 17:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-03 17:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-03 17:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
05-03 17:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-03 17:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-03 17:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-03 17:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 17:43 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-03 17:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 17:43 INFO   root: Already installed, running the uninstaller...
05-03 17:43 INFO   root: Running the uninstaller...
05-03 17:43 INFO   CommonBackend: Launching previous uninestaller C:\ubuntu\uninstall-wubi.exe
05-03 17:44 DEBUG  root: application.quit
05-03 17:44 DEBUG  root: application.on_quit
05-03 17:44 INFO   root: sys.exit
05-03 17:44 INFO   root: Quitting application
05-03 17:45 INFO   root: === wubi 10.04 rev189 ===
05-03 17:45 DEBUG  root: Logfile is c:\users\andrew\appdata\local\temp\wubi-10.04-rev189.log
05-03 17:45 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Andrew\\Desktop\\wubi.exe"']
05-03 17:45 DEBUG  CommonBackend: data_dir=C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp\data
05-03 17:45 DEBUG  WindowsBackend: 7z=C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp\bin\7z.exe
05-03 17:45 DEBUG  CommonBackend: Fetching basic info...
05-03 17:45 DEBUG  CommonBackend: original_exe=C:\Users\Andrew\Desktop\wubi.exe
05-03 17:45 DEBUG  CommonBackend: platform=win32
05-03 17:45 DEBUG  CommonBackend: osname=nt
05-03 17:45 DEBUG  CommonBackend: language=en_US
05-03 17:45 DEBUG  CommonBackend: encoding=cp1252
05-03 17:45 DEBUG  WindowsBackend: arch=i386
05-03 17:45 DEBUG  CommonBackend: Parsing isolist=C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp\data\isolist.ini
05-03 17:45 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-03 17:45 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-03 17:45 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-03 17:45 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-03 17:45 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-03 17:45 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-03 17:45 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-03 17:45 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-03 17:45 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
05-03 17:45 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-03 17:45 DEBUG  WindowsBackend: Fetching host info...
05-03 17:45 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-03 17:45 DEBUG  WindowsBackend: windows version=vista
05-03 17:45 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Business
05-03 17:45 DEBUG  WindowsBackend: windows_sp=None
05-03 17:45 DEBUG  WindowsBackend: windows_build=6000
05-03 17:45 DEBUG  WindowsBackend: gmt=-8
05-03 17:45 DEBUG  WindowsBackend: country=US
05-03 17:45 DEBUG  WindowsBackend: timezone=America/Los_Angeles
05-03 17:45 DEBUG  WindowsBackend: windows_username=Andrew
05-03 17:45 DEBUG  WindowsBackend: user_full_name=Andrew
05-03 17:45 DEBUG  WindowsBackend: user_directory=C:\Users\Andrew
05-03 17:45 DEBUG  WindowsBackend: windows_language_code=1033
05-03 17:45 DEBUG  WindowsBackend: windows_language=English
05-03 17:45 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) Duo CPU      T2400  @ 1.83GHz
05-03 17:45 DEBUG  WindowsBackend: bootloader=vista
05-03 17:45 DEBUG  WindowsBackend: system_drive=Drive(C: hd 63390.53125 mb free ntfs)
05-03 17:45 DEBUG  WindowsBackend: drive=Drive(C: hd 63390.53125 mb free ntfs)
05-03 17:45 DEBUG  WindowsBackend: drive=Drive(D: hd 767.421875 mb free ntfs)
05-03 17:45 DEBUG  WindowsBackend: drive=Drive(E: hd 1347.55859375 mb free ntfs)
05-03 17:45 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
05-03 17:45 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-03 17:45 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-03 17:45 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-03 17:45 DEBUG  WindowsBackend: keyboard_id=67699721
05-03 17:45 DEBUG  WindowsBackend: keyboard_layout=us
05-03 17:45 DEBUG  WindowsBackend: keyboard_variant=
05-03 17:45 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-03 17:45 DEBUG  CommonBackend: locale=en_US.UTF-8
05-03 17:45 DEBUG  WindowsBackend: total_memory_mb=1014.8125
05-03 17:45 DEBUG  CommonBackend: Searching ISOs on USB devices
05-03 17:45 DEBUG  CommonBackend: Searching for local CDs
05-03 17:45 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp is a valid Ubuntu CD
05-03 17:45 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp is a valid Ubuntu CD
05-03 17:45 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp is a valid Ubuntu Netbook CD
05-03 17:45 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp is a valid Kubuntu CD
05-03 17:45 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp is a valid Kubuntu CD
05-03 17:45 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp is a valid Kubuntu Netbook CD
05-03 17:45 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp is a valid Xubuntu CD
05-03 17:45 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp is a valid Xubuntu CD
05-03 17:45 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp is a valid Mythbuntu CD
05-03 17:45 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp is a valid Mythbuntu CD
05-03 17:45 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-03 17:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-03 17:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-03 17:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-03 17:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-03 17:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
05-03 17:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-03 17:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-03 17:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-03 17:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-03 17:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-03 17:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-03 17:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-03 17:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-03 17:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-03 17:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
05-03 17:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-03 17:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-03 17:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-03 17:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-03 17:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-03 17:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-03 17:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
05-03 17:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-03 17:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-03 17:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
05-03 17:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-03 17:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-03 17:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-03 17:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 17:45 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-03 17:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 17:45 INFO   root: Running the installer...
05-03 17:45 DEBUG  WindowsFrontend: __init__...
05-03 17:45 DEBUG  WindowsFrontend: on_init...
05-03 17:45 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp\translations, languages=['en_US', 'en']
05-03 17:45 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp\translations, languages=['en_US', 'en']
05-03 17:46 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=andrew
05-03 17:46 INFO   root: Received settings
05-03 17:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp\translations, languages=['en_US', 'en']
05-03 17:46 DEBUG  TaskList: # Running tasklist...
05-03 17:46 DEBUG  TaskList: ## Running select_target_dir...
05-03 17:46 INFO   WindowsBackend: Installing into C:\ubuntu
05-03 17:46 DEBUG  TaskList: ## Finished select_target_dir
05-03 17:46 DEBUG  TaskList: ## Running create_dir_structure...
05-03 17:46 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-03 17:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-03 17:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-03 17:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-03 17:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-03 17:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-03 17:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-03 17:46 DEBUG  TaskList: ## Finished create_dir_structure
05-03 17:46 DEBUG  TaskList: ## Running uncompress_target_dir...
05-03 17:46 DEBUG  TaskList: ## Finished uncompress_target_dir
05-03 17:46 DEBUG  TaskList: ## Running create_uninstaller...
05-03 17:46 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Andrew\Desktop\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
05-03 17:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-03 17:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-03 17:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-03 17:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
05-03 17:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
05-03 17:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-03 17:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
05-03 17:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
05-03 17:46 DEBUG  TaskList: ## Finished create_uninstaller
05-03 17:46 DEBUG  TaskList: ## Running copy_installation_files...
05-03 17:46 DEBUG  WindowsBackend: Copying C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-03 17:46 DEBUG  WindowsBackend: Copying C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp\winboot -> C:\ubuntu\winboot
05-03 17:46 DEBUG  WindowsBackend: Copying C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
05-03 17:46 DEBUG  TaskList: ## Finished copy_installation_files
05-03 17:46 DEBUG  TaskList: ## Running get_iso...
05-03 17:46 DEBUG  CommonBackend: Searching for local CD
05-03 17:46 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp is a valid Ubuntu CD
05-03 17:46 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pylC8DA.tmp\casper\filesystem.squashfs
05-03 17:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-03 17:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 17:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-03 17:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 17:46 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-03 17:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 17:46 DEBUG  CommonBackend: Searching for local ISO
05-03 17:46 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-03 17:46 DEBUG  TaskList: New task get_metalink
05-03 17:46 DEBUG  TaskList: ### Running get_metalink...
05-03 17:46 DEBUG  downloader: downloading http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink > C:\ubuntu\install
05-03 17:46 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-10.04-desktop-i386.metalink, url=http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink, basename=ubuntu-10.04-desktop-i386.metalink, length=7420, text=None
05-03 17:46 DEBUG  downloader: download finished (read 7420 bytes)
05-03 17:46 DEBUG  downloader: downloading http://releases.ubuntu.com/10.04/MD5SUMS-metalink > C:\ubuntu\install
05-03 17:46 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=639, text=None
05-03 17:46 DEBUG  downloader: download finished (read 639 bytes)
05-03 17:46 DEBUG  downloader: downloading http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg > C:\ubuntu\install
05-03 17:46 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
05-03 17:46 DEBUG  downloader: download finished (read 189 bytes)
05-03 17:46 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
05-03 17:46 INFO   saplog: Checking block bindings..
05-03 17:46 INFO   saplog: Key verified successfully.
05-03 17:46 DEBUG  CommonBackend: metalink md5sums:
63592a82b86f25a2b75ec10e75fba8f5  ubuntu-10.04-alternate-amd64.metalink
1ad74973481704af353be8dce13b8a83  ubuntu-10.04-alternate-i386.metalink
999542213cd64cabdca682c080a7227a  ubuntu-10.04-desktop-amd64.metalink
0b3f5975f84933431267f1be5daf0882  ubuntu-10.04-desktop-i386.metalink
d57239ea96a3e3c7ac3d03672de0596e  ubuntu-10.04-netbook-armel+dove.metalink
fecad822acacbf0d5763eab4b21c7bef  ubuntu-10.04-netbook-armel+imx51.metalink
a92079601c82c2c8b60c2e2d43df09b6  ubuntu-10.04-netbook-i386.metalink
4804fa76f01904b80847e06ff159f4b5  ubuntu-10.04-server-amd64.metalink
4cb4790703d19ac401e10de456e643f0  ubuntu-10.04-server-i386.metalink

05-03 17:46 DEBUG  TaskList: ### Finished get_metalink
05-03 17:46 DEBUG  TaskList: New task download
05-03 17:46 DEBUG  TaskList: ### Running download...
05-03 17:46 DEBUG  btdownloader: downloading http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.iso.torrent > C:\ubuntu\install\ubuntu-10.04-desktop-i386.iso
05-03 19:46 ERROR  TaskList: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\btdownloader.py", line 79, in download
  File "\lib\bittorrent\download.py", line 303, in download
  File "\lib\bittorrent\RawServer.py", line 256, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request


05-03 19:46 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

 in task download
05-03 19:46 DEBUG  TaskList: ### Finished download
05-03 19:46 ERROR  TaskList: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04-desktop-i386.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04-desktop-i386.iso'
05-03 19:46 DEBUG  TaskList: # Cancelling tasklist
05-03 19:46 DEBUG  TaskList: # Finished tasklist
05-03 19:46 ERROR  root: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04-desktop-i386.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04-desktop-i386.iso'
05-03 21:05 INFO   root: === wubi 10.04 rev189 ===
05-03 21:05 DEBUG  root: Logfile is c:\users\andrew\appdata\local\temp\wubi-10.04-rev189.log
05-03 21:05 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Andrew\\Desktop\\wubi.exe"']
05-03 21:05 DEBUG  CommonBackend: data_dir=C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp\data
05-03 21:05 DEBUG  WindowsBackend: 7z=C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp\bin\7z.exe
05-03 21:05 DEBUG  CommonBackend: Fetching basic info...
05-03 21:05 DEBUG  CommonBackend: original_exe=C:\Users\Andrew\Desktop\wubi.exe
05-03 21:05 DEBUG  CommonBackend: platform=win32
05-03 21:05 DEBUG  CommonBackend: osname=nt
05-03 21:05 DEBUG  CommonBackend: language=en_US
05-03 21:05 DEBUG  CommonBackend: encoding=cp1252
05-03 21:05 DEBUG  WindowsBackend: arch=i386
05-03 21:05 DEBUG  CommonBackend: Parsing isolist=C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp\data\isolist.ini
05-03 21:05 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-03 21:05 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-03 21:05 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-03 21:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-03 21:05 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-03 21:05 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-03 21:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-03 21:05 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-03 21:05 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
05-03 21:05 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-03 21:05 DEBUG  WindowsBackend: Fetching host info...
05-03 21:05 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-03 21:05 DEBUG  WindowsBackend: windows version=vista
05-03 21:05 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Business
05-03 21:05 DEBUG  WindowsBackend: windows_sp=None
05-03 21:05 DEBUG  WindowsBackend: windows_build=6000
05-03 21:05 DEBUG  WindowsBackend: gmt=-8
05-03 21:05 DEBUG  WindowsBackend: country=US
05-03 21:05 DEBUG  WindowsBackend: timezone=America/Los_Angeles
05-03 21:05 DEBUG  WindowsBackend: windows_username=Andrew
05-03 21:05 DEBUG  WindowsBackend: user_full_name=Andrew
05-03 21:05 DEBUG  WindowsBackend: user_directory=C:\Users\Andrew
05-03 21:05 DEBUG  WindowsBackend: windows_language_code=1033
05-03 21:05 DEBUG  WindowsBackend: windows_language=English
05-03 21:05 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) Duo CPU      T2400  @ 1.83GHz
05-03 21:05 DEBUG  WindowsBackend: bootloader=vista
05-03 21:05 DEBUG  WindowsBackend: system_drive=Drive(C: hd 63464.7421875 mb free ntfs)
05-03 21:05 DEBUG  WindowsBackend: drive=Drive(C: hd 63464.7421875 mb free ntfs)
05-03 21:05 DEBUG  WindowsBackend: drive=Drive(D: hd 767.421875 mb free ntfs)
05-03 21:05 DEBUG  WindowsBackend: drive=Drive(E: hd 1347.55859375 mb free ntfs)
05-03 21:05 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
05-03 21:05 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-03 21:05 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-03 21:05 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-03 21:05 DEBUG  WindowsBackend: keyboard_id=67699721
05-03 21:05 DEBUG  WindowsBackend: keyboard_layout=us
05-03 21:05 DEBUG  WindowsBackend: keyboard_variant=
05-03 21:05 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-03 21:05 DEBUG  CommonBackend: locale=en_US.UTF-8
05-03 21:05 DEBUG  WindowsBackend: total_memory_mb=1014.8125
05-03 21:05 DEBUG  CommonBackend: Searching ISOs on USB devices
05-03 21:05 DEBUG  CommonBackend: Searching for local CDs
05-03 21:05 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp is a valid Ubuntu CD
05-03 21:05 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp is a valid Ubuntu CD
05-03 21:05 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp is a valid Ubuntu Netbook CD
05-03 21:05 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp is a valid Kubuntu CD
05-03 21:05 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp is a valid Kubuntu CD
05-03 21:05 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp is a valid Kubuntu Netbook CD
05-03 21:05 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp is a valid Xubuntu CD
05-03 21:05 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp is a valid Xubuntu CD
05-03 21:05 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp is a valid Mythbuntu CD
05-03 21:05 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp is a valid Mythbuntu CD
05-03 21:05 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-03 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-03 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-03 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-03 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-03 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
05-03 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-03 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-03 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-03 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-03 21:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-03 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-03 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-03 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-03 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-03 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
05-03 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-03 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-03 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-03 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-03 21:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-03 21:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-03 21:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
05-03 21:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-03 21:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-03 21:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
05-03 21:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-03 21:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-03 21:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-03 21:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 21:05 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-03 21:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 21:05 INFO   root: Already installed, running the uninstaller...
05-03 21:05 INFO   root: Running the uninstaller...
05-03 21:05 INFO   CommonBackend: This is the uninstaller running
05-03 21:05 DEBUG  WindowsFrontend: __init__...
05-03 21:05 DEBUG  WindowsFrontend: on_init...
05-03 21:05 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp\translations, languages=['en_US', 'en']
05-03 21:05 INFO   root: Received settings
05-03 21:05 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Andrew\AppData\Local\Temp\pyl4088.tmp\translations, languages=['en_US', 'en']
05-03 21:05 DEBUG  TaskList: # Running tasklist...
05-03 21:05 DEBUG  TaskList: ## Running Backup ISO...
05-03 21:05 DEBUG  TaskList: ## Finished Backup ISO
05-03 21:05 DEBUG  TaskList: ## Running Remove bootloader entry...
05-03 21:05 DEBUG  WindowsBackend: Could not find bcd id
05-03 21:05 DEBUG  WindowsBackend: undo_bootini C:
05-03 21:05 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 63464.7421875 mb free ntfs)
05-03 21:05 ERROR  TaskList: [Errno 13] Permission denied: 'C:\\config.sys'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 506, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 599, in undo_configsys
  File "\lib\wubi\backends\common\utils.py", line 246, in write_file
IOError: [Errno 13] Permission denied: 'C:\\config.sys'
05-03 21:05 DEBUG  TaskList: # Cancelling tasklist
05-03 21:05 DEBUG  TaskList: # Finished tasklist
05-03 21:05 ERROR  root: [Errno 13] Permission denied: 'C:\\config.sys'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 143, in run_installer
  File "\lib\wubi\application.py", line 177, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 506, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 599, in undo_configsys
  File "\lib\wubi\backends\common\utils.py", line 246, in write_file
IOError: [Errno 13] Permission denied: 'C:\\config.sys'
05-03 21:06 INFO   root: === wubi 10.04 rev189 ===
05-03 21:06 DEBUG  root: Logfile is c:\users\andrew\appdata\local\temp\wubi-10.04-rev189.log
05-03 21:06 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Andrew\\Desktop\\wubi.exe"']
05-03 21:06 DEBUG  CommonBackend: data_dir=C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp\data
05-03 21:06 DEBUG  WindowsBackend: 7z=C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp\bin\7z.exe
05-03 21:06 DEBUG  CommonBackend: Fetching basic info...
05-03 21:06 DEBUG  CommonBackend: original_exe=C:\Users\Andrew\Desktop\wubi.exe
05-03 21:06 DEBUG  CommonBackend: platform=win32
05-03 21:06 DEBUG  CommonBackend: osname=nt
05-03 21:06 DEBUG  CommonBackend: language=en_US
05-03 21:06 DEBUG  CommonBackend: encoding=cp1252
05-03 21:06 DEBUG  WindowsBackend: arch=i386
05-03 21:06 DEBUG  CommonBackend: Parsing isolist=C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp\data\isolist.ini
05-03 21:06 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-03 21:06 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-03 21:06 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-03 21:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-03 21:06 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-03 21:06 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-03 21:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-03 21:06 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-03 21:06 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
05-03 21:06 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-03 21:06 DEBUG  WindowsBackend: Fetching host info...
05-03 21:06 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-03 21:06 DEBUG  WindowsBackend: windows version=vista
05-03 21:06 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Business
05-03 21:06 DEBUG  WindowsBackend: windows_sp=None
05-03 21:06 DEBUG  WindowsBackend: windows_build=6000
05-03 21:06 DEBUG  WindowsBackend: gmt=-8
05-03 21:06 DEBUG  WindowsBackend: country=US
05-03 21:06 DEBUG  WindowsBackend: timezone=America/Los_Angeles
05-03 21:06 DEBUG  WindowsBackend: windows_username=Andrew
05-03 21:06 DEBUG  WindowsBackend: user_full_name=Andrew
05-03 21:06 DEBUG  WindowsBackend: user_directory=C:\Users\Andrew
05-03 21:06 DEBUG  WindowsBackend: windows_language_code=1033
05-03 21:06 DEBUG  WindowsBackend: windows_language=English
05-03 21:06 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) Duo CPU      T2400  @ 1.83GHz
05-03 21:06 DEBUG  WindowsBackend: bootloader=vista
05-03 21:06 DEBUG  WindowsBackend: system_drive=Drive(C: hd 63464.4453125 mb free ntfs)
05-03 21:06 DEBUG  WindowsBackend: drive=Drive(C: hd 63464.4453125 mb free ntfs)
05-03 21:06 DEBUG  WindowsBackend: drive=Drive(D: hd 767.421875 mb free ntfs)
05-03 21:06 DEBUG  WindowsBackend: drive=Drive(E: hd 1347.55859375 mb free ntfs)
05-03 21:06 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
05-03 21:06 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-03 21:06 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-03 21:06 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-03 21:06 DEBUG  WindowsBackend: keyboard_id=67699721
05-03 21:06 DEBUG  WindowsBackend: keyboard_layout=us
05-03 21:06 DEBUG  WindowsBackend: keyboard_variant=
05-03 21:06 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-03 21:06 DEBUG  CommonBackend: locale=en_US.UTF-8
05-03 21:06 DEBUG  WindowsBackend: total_memory_mb=1014.8125
05-03 21:06 DEBUG  CommonBackend: Searching ISOs on USB devices
05-03 21:06 DEBUG  CommonBackend: Searching for local CDs
05-03 21:06 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp is a valid Ubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp is a valid Ubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp is a valid Ubuntu Netbook CD
05-03 21:06 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp is a valid Kubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp is a valid Kubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp is a valid Kubuntu Netbook CD
05-03 21:06 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp is a valid Xubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp is a valid Xubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp is a valid Mythbuntu CD
05-03 21:06 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp is a valid Mythbuntu CD
05-03 21:06 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-03 21:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
05-03 21:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-03 21:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-03 21:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-03 21:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
05-03 21:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-03 21:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-03 21:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
05-03 21:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
05-03 21:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-03 21:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-03 21:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 21:06 INFO   root: Running the installer...
05-03 21:06 DEBUG  WindowsFrontend: __init__...
05-03 21:06 DEBUG  WindowsFrontend: on_init...
05-03 21:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp\translations, languages=['en_US', 'en']
05-03 21:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp\translations, languages=['en_US', 'en']
05-03 21:06 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=andrew
05-03 21:06 INFO   root: Received settings
05-03 21:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp\translations, languages=['en_US', 'en']
05-03 21:06 DEBUG  TaskList: # Running tasklist...
05-03 21:06 DEBUG  TaskList: ## Running select_target_dir...
05-03 21:06 INFO   WindowsBackend: Installing into C:\ubuntu
05-03 21:06 DEBUG  TaskList: ## Finished select_target_dir
05-03 21:06 DEBUG  TaskList: ## Running create_dir_structure...
05-03 21:06 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-03 21:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-03 21:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-03 21:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-03 21:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-03 21:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-03 21:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-03 21:06 DEBUG  TaskList: ## Finished create_dir_structure
05-03 21:06 DEBUG  TaskList: ## Running uncompress_target_dir...
05-03 21:06 DEBUG  TaskList: ## Finished uncompress_target_dir
05-03 21:06 DEBUG  TaskList: ## Running create_uninstaller...
05-03 21:06 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Andrew\Desktop\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
05-03 21:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-03 21:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-03 21:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-03 21:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
05-03 21:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
05-03 21:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-03 21:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
05-03 21:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
05-03 21:06 DEBUG  TaskList: ## Finished create_uninstaller
05-03 21:06 DEBUG  TaskList: ## Running copy_installation_files...
05-03 21:06 DEBUG  WindowsBackend: Copying C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-03 21:06 DEBUG  WindowsBackend: Copying C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp\winboot -> C:\ubuntu\winboot
05-03 21:06 DEBUG  WindowsBackend: Copying C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
05-03 21:06 DEBUG  TaskList: ## Finished copy_installation_files
05-03 21:06 DEBUG  TaskList: ## Running get_iso...
05-03 21:06 DEBUG  CommonBackend: Searching for local CD
05-03 21:06 DEBUG  Distro:   checking whether C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp is a valid Ubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain C:\Users\Andrew\AppData\Local\Temp\pylB099.tmp\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-03 21:06 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-03 21:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-03 21:06 DEBUG  CommonBackend: Searching for local ISO
05-03 21:06 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-03 21:06 DEBUG  TaskList: New task get_metalink
05-03 21:06 DEBUG  TaskList: ### Running get_metalink...
05-03 21:06 DEBUG  downloader: downloading http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink > C:\ubuntu\install
05-03 21:06 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-10.04-desktop-i386.metalink, url=http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink, basename=ubuntu-10.04-desktop-i386.metalink, length=7420, text=None
05-03 21:06 DEBUG  downloader: download finished (read 7420 bytes)
05-03 21:06 DEBUG  downloader: downloading http://releases.ubuntu.com/10.04/MD5SUMS-metalink > C:\ubuntu\install
05-03 21:06 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=639, text=None
05-03 21:06 DEBUG  downloader: download finished (read 639 bytes)
05-03 21:06 DEBUG  downloader: downloading http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg > C:\ubuntu\install
05-03 21:06 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
05-03 21:06 DEBUG  downloader: download finished (read 189 bytes)
05-03 21:06 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
05-03 21:06 INFO   saplog: Checking block bindings..
05-03 21:06 INFO   saplog: Key verified successfully.
05-03 21:06 DEBUG  CommonBackend: metalink md5sums:
63592a82b86f25a2b75ec10e75fba8f5  ubuntu-10.04-alternate-amd64.metalink
1ad74973481704af353be8dce13b8a83  ubuntu-10.04-alternate-i386.metalink
999542213cd64cabdca682c080a7227a  ubuntu-10.04-desktop-amd64.metalink
0b3f5975f84933431267f1be5daf0882  ubuntu-10.04-desktop-i386.metalink
d57239ea96a3e3c7ac3d03672de0596e  ubuntu-10.04-netbook-armel+dove.metalink
fecad822acacbf0d5763eab4b21c7bef  ubuntu-10.04-netbook-armel+imx51.metalink
a92079601c82c2c8b60c2e2d43df09b6  ubuntu-10.04-netbook-i386.metalink
4804fa76f01904b80847e06ff159f4b5  ubuntu-10.04-server-amd64.metalink
4cb4790703d19ac401e10de456e643f0  ubuntu-10.04-server-i386.metalink

05-03 21:06 DEBUG  TaskList: ### Finished get_metalink
05-03 21:06 DEBUG  TaskList: New task download
05-03 21:06 DEBUG  TaskList: ### Running download...
05-03 21:06 DEBUG  btdownloader: downloading http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.iso.torrent > C:\ubuntu\install\ubuntu-10.04-desktop-i386.iso
05-03 22:36 ERROR  TaskList: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\btdownloader.py", line 79, in download
  File "\lib\bittorrent\download.py", line 303, in download
  File "\lib\bittorrent\RawServer.py", line 256, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request


05-03 22:36 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

 in task download
05-03 22:36 DEBUG  TaskList: ### Finished download
05-03 22:36 ERROR  TaskList: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04-desktop-i386.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04-desktop-i386.iso'
05-03 22:36 DEBUG  TaskList: # Cancelling tasklist
05-03 22:36 DEBUG  TaskList: # Finished tasklist
05-03 22:36 ERROR  root: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04-desktop-i386.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04-desktop-i386.iso'

```

---

### Post by julie_bholu on 2010-08-11
TRY with IIS Enable

I Solved by Enable IIS in XP;)

---

### Post by bsubbudu on 2010-08-16
I have XP with sp2. Tried to unhide the folders as mentioned above. Didn't work. Still get the same permission denied message.
 
Any help would be appreciated.

---

### Post by Callaleia on 2010-08-19
pienyereye's solution solved this for me, under Windows 7. Thanks!  I had been beginning to get pretty frustrated.
 
* Note that the installer demanded that there be a CD in the drive (any CD). In fact, it won't work if said CD is actually the Live CD, because then it tries to read the files off of the disc in the drive, and you're back to "Permission Denied."
 
I also had to unplug my wireless adaptor, or it would try to download the ISO file again during the install, which wasn't desirable because a) I already had it, and b) we have limited bandwidth here.

---

### Post by Regardt on 2010-09-02
I have tried all of these solutions and not one of them have helped me. I have the latest version of Wubi, so then I try to install Ubuntu on Windows 7. Then it says Permission Denied, view log etc etc. Help please?

---

### Post by bcbc on 2010-09-02
> **Regardt said:**
> I have tried all of these solutions and not one of them have helped me. I have the latest version of Wubi, so then I try to install Ubuntu on Windows 7. Then it says Permission Denied, view log etc etc. Help please?

What are the contents of said log file? As alluded to above, you might need to change your settings to view hidden folders to find this file - it doesn't cause permission errors if it's hidden, but it makes it harder to find it.

I normally enter %temp% in the explorer address bar and it will take you to it. It will be called something like wubi-10.04-rev.log.

Also, what flavour of Ubuntu are you trying to install. The netbook edition isn't working right now as it's still at 10.04 whereas the wubi.exe is at 10.04.1 and it doesn't work across releases. You need an older wubi.exe to get that.
You also need to run as an administrator and have access to the internet.

---

### Post by markjreed on 2010-09-02
OK, having this trouble with Win XP.  No idea why everyone's talking about the hidden folder in Windows 7 as if that were the problem.  The problem is that the install is failing.  This is the error message, looks like it's having trouble copying the ISO image, but I don't know where it's copying from or to or how to fix it:


09-02 20:28 DEBUG  TaskList: New task copy_file
09-02 20:28 DEBUG  TaskList: ### Running copy_file...
09-02 20:32 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
09-02 20:32 DEBUG  TaskList: # Cancelling tasklist
09-02 20:32 DEBUG  TaskList: New task check_iso
09-02 20:32 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
09-02 20:32 DEBUG  CommonBackend: Searching for local ISO
09-02 20:32 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
09-02 20:32 DEBUG  TaskList: New task get_metalink
09-02 20:32 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
09-02 20:32 DEBUG  TaskList: # Cancelling tasklist
09-02 20:32 DEBUG  TaskList: # Finished tasklist

---

### Post by bcbc on 2010-09-02
> **markjreed said:**
> OK, having this trouble with Win XP.  No idea why everyone's talking about the hidden folder in Windows 7 as if that were the problem.  The problem is that the install is failing.  This is the error message, looks like it's having trouble copying the ISO image, but I don't know where it's copying from or to or how to fix it:


It's hard to tell from the log snippet... if you rename the current .log file and run it again, then cut and paste the lot between [[SIZE="1"] [/SIZE]CODE][/CODE] tags. There's a little identifying info (location and windows user name) that you can remove if you wish.

---

### Post by krivosh on 2010-09-03
Found a very ellegant solution to "permission denied" problem on Windows7:

All you have to do is to download the .iso file of desired ubuntu installation from regular ubuntu download site, then put it to the same directory as wubi installer(wubi.exe?) is and run it - the installer finds out that the .iso is already there and uses it.

This is the how-to that helped me to get this idea:
[http://technomosh.blogspot.com/2009/11/using-wubi-without-torrent.html](http://technomosh.blogspot.com/2009/11/using-wubi-without-torrent.html)

---

### Post by tlacaelelrl on 2010-09-12
First, for all those trying to fix the issue by "unhiding" the system files in windows stop trying, that is only so you can review the log file that is mentioned by the error message.

Now about the error, I dont know much but many software in windows 7, not talking about any other versions of windows although it might work, if the windows firewall service is disabled then the software will not install, that might be the case for some of you, I usually disable it since i dont like using it, and i just reenable when I need to install software that is failing the install, which happened to me on the wubi

hope this helps some of you

---

### Post by Malph on 2010-10-02
> **tlacaelelrl said:**
> First, for all those trying to fix the issue by "unhiding" the system files in windows stop trying, that is only so you can review the log file that is mentioned by the error message.

Now about the error, I dont know much but many software in windows 7, not talking about any other versions of windows although it might work, if the windows firewall service is disabled then the software will not install, that might be the case for some of you, I usually disable it since i dont like using it, and i just reenable when I need to install software that is failing the install, which happened to me on the wubi

hope this helps some of you

Well, for me this didn't work. Still struggling with this!:(

---

### Post by Malph on 2010-10-02
> **pienyereye said:**
> I was having the same issue for a couple of weeks since I upgraded to Windows 7. Originally, I installed 9.10 from a CD after Windows Vista and had a dual boot situation - which was great.
 
I upgraded to Win7 and lost Grub. I expected this. However, I was getting the access denied error when trying to reload from the same CD that worked fine on my desktop machine. 

Here is what I did to fix this issue. I am not saying this is the perfect way to fix but it worked for me and it seems like folks are still having this problem so here it goes...
I downloaded Virtual CloneDrive (google it - its freeware) When I installed Virtual CloneDrive, I associated the .iso files with it and no others. I then ran the .iso file that I originally downloaded to make my disc, directly from my Program Files folder by double-clicking. It should be mounted and launch as a virtual drive and run like the disc but without using the disc. I think the access denied error has something to do with the disc drive but I was unable to fix it. 

Just follow your prompts to install as you normally would from the CD. Apparently, it saved all my settings from my previous Ubuntu install so I was psyched. :guitar:

Again, this may not be the best way to fix but I am more of a Windows geek than a Linux geek (but I am working on it ;P) Also, it may not fix your issue at all or make it worse so if that is the case, be sure to post back ASAP! My experience was good.
Good Luck

THANKS! THIS RESOLVED THE PROBLEM AND WORKED WELL FOR WINDOWS XP SP3! I suspect my CD drive has a problem because the disk is OK (I used it succesfully on my laptop previously to install Ubuntu). 

By the way, an error occurred several times while running the iso file on the virtual clone cd. I resolved that by clicking "continue" upon the error message (other option was to cancel or retry). Again, thanks for helping, it resolved hours of struggling.

---

### Post by erkanbostanci on 2011-01-24
> **krivosh said:**
> Found a very ellegant solution to "permission denied" problem on Windows7:

All you have to do is to download the .iso file of desired ubuntu installation from regular ubuntu download site, then put it to the same directory as wubi installer(wubi.exe?) is and run it - the installer finds out that the .iso is already there and uses it.

This is the how-to that helped me to get this idea:
[http://technomosh.blogspot.com/2009/11/using-wubi-without-torrent.html](http://technomosh.blogspot.com/2009/11/using-wubi-without-torrent.html)


Similarly if you download the iso file and wite the contents into a CD or you can use a daemon to read the contents of the iso file, then you can run wubi and select windows installation. It warns about reduced performance for disk operations but I did not notice this from my previous experience.

---

### Post by PeterDavis on 2011-01-31
Many thanks to Krivosh for the elegant solution at post #24, which worked for me on xp.  I'd never have found this by myself.

I actually discovered wubi.exe to be in my Download file, where the WUBI "one-click" procedure had presumably put it - before crashing with all those permissions denied (leading, in my case to AVG then declaring the installer to be Malware!).  

Since I'd also previously downloaded the 10.10 .iso file, it was conveniently next door in the Download file to wubi.exe, so a double-click on the latter was all I needed to install Ubuntu (which looks lovely).  Hooray!  :KS

---

### Post by srinivasjinde on 2011-03-09
Before running wubi, make sure the ubuntu iso image is present in the same folder, then everything would work fine.If you dont have iso file, google it and download the latest version.

---

### Post by maherman on 2011-05-28
I am running windows xp sp3 and have been unable to install ubuntu using wubi.exe and continue to get a permission denied error.  I have tried the suggestion in post#24 without success.   I've attached the error log, but I'm unable to parse this myself as I'm new to all of this.  Any help would be appreciated.

---

### Post by anders_r_r on 2011-06-14
> **krivosh said:**
> 
All you have to do is to download the .iso file of desired ubuntu installation from regular ubuntu download site, then put it to the same directory as wubi installer(wubi.exe?) is and run it - the installer finds out that the .iso is already there and uses it.


Thanks! That solved the problem for me on windowsXP.

---

### Post by SugoiDesu on 2011-08-08
Having the same problem on my sister's Windows 7 Ultimate machine...
This is a list of documented log problems:

```

08-08 20:16 DEBUG  TaskList: ### Finished get_metalink
08-08 20:16 DEBUG  TaskList: New task download
08-08 20:16 DEBUG  TaskList: ### Running download...
08-08 20:16 DEBUG  btdownloader: downloading http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent > D:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
08-08 20:16 ERROR  TaskList: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - <urlopen error (10060, 'Operation timed out')>

Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\btdownloader.py", line 79, in download
  File "\lib\bittorrent\download.py", line 303, in download
  File "\lib\bittorrent\RawServer.py", line 256, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - <urlopen error (10060, 'Operation timed out')>


08-08 20:16 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - <urlopen error (10060, 'Operation timed out')>

 in task download
08-08 20:16 DEBUG  TaskList: ### Finished download
08-08 20:16 ERROR  TaskList: [Errno 13] Permission denied: u'D:\\ubuntu\\install\\ubuntu-11.04-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'D:\\ubuntu\\install\\ubuntu-11.04-desktop-amd64.iso'
08-08 20:16 DEBUG  TaskList: # Cancelling tasklist
08-08 20:16 DEBUG  TaskList: # Finished tasklist
08-08 20:16 ERROR  root: [Errno 13] Permission denied: u'D:\\ubuntu\\install\\ubuntu-11.04-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'D:\\ubuntu\\install\\ubuntu-11.04-desktop-amd64.iso'

```

---

### Post by bcbc on 2011-08-08
> **SugoiDesu said:**
> Having the same problem on my sister's Windows 7 Ultimate machine...
This is a list of documented log problems:

```

08-08 20:16 DEBUG  TaskList: ### Finished get_metalink
08-08 20:16 DEBUG  TaskList: New task download
08-08 20:16 DEBUG  TaskList: ### Running download...
08-08 20:16 DEBUG  btdownloader: downloading http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent > D:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
08-08 20:16 ERROR  TaskList: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - <urlopen error (10060, 'Operation timed out')>

```
Problem is the bittorrent client that Wubi uses is being blocked. You should have seen a popup to allow pyrun.exe (python runtime) access to the windows firewall. If you allowed it, then it may be an upstream firewall.

You can download the desktop CD ISO yourself through your browser instead from here: [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
Save it in the same older as wubi.exe and then wubi will find and use it.

---

### Post by SugoiDesu on 2011-08-08
Turns out that I just didn't see uTorrent asking me for an access ficure.
Thanks!
Edit: The installation is still malfunctioning

---

### Post by rams_123 on 2011-08-11
08-11 21:00 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
08-11 21:00 DEBUG  TaskList: # Cancelling tasklist
08-11 21:00 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 129, in select_task
  File "\lib\wubi\application.py", line 195, in run_cd_menu
  File "\lib\wubi\application.py", line 119, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
08-11 21:00 DEBUG  TaskList: New task check_iso
08-11 21:00 DEBUG  CommonBackend: Searching for local ISO
08-11 21:00 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
08-11 21:00 DEBUG  TaskList: New task get_metalink
08-11 21:00 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
08-11 21:00 DEBUG  TaskList: # Cancelling tasklist
08-11 21:00 DEBUG  TaskList: # Finished tasklist

---

### Post by Lorenzo Rubbo on 2011-10-14
I got this problem installing Ubuntu 11.10 on Windows 7. Here's what worked for me:

1. **Turn off ALL virtual drives**. I had two virtual drives from two separate software - naughty I know.

2. **Download Ubuntu ISO.**

3. **Download Wubi Installer into the same folder as your ISO.**

4. **Run Wubi.**

Worked a treat for me! Must have been drive issues.

---

### Post by oreilly123 on 2011-11-11
> **Lorenzo Rubbo said:**
> I got this problem installing Ubuntu 11.10 on Windows 7. Here's what worked for me:

1. **Turn off ALL virtual drives**. I had two virtual drives from two separate software - naughty I know.

2. **Download Ubuntu ISO.**

3. **Download Wubi Installer into the same folder as your ISO.**

4. **Run Wubi.**

Worked a treat for me! Must have been drive issues.

For what it's worth this is what got me around the permission error that comes up during install. I downloaded the ISO into the same folder as the installer's executable and it went right through install and gave me the reboot prompt. This is on Windows 7.

---

### Post by skrogager on 2012-02-27
I got the same permission error. I saw in the log it was pointing to F: which were in use by a SD card reader. I just removed the drive letter via diskmgmt and everything went well...

---

### Post by wavebreak on 2012-03-13
> **pienyereye said:**
> I was having the same issue for a couple of weeks since I upgraded to Windows 7. Originally, I installed 9.10 from a CD after Windows Vista and had a dual boot situation - which was great.
 
I upgraded to Win7 and lost Grub. I expected this. However, I was getting the access denied error when trying to reload from the same CD that worked fine on my desktop machine. 

Here is what I did to fix this issue. I am not saying this is the perfect way to fix but it worked for me and it seems like folks are still having this problem so here it goes...
I downloaded Virtual CloneDrive (google it - its freeware) When I installed Virtual CloneDrive, I associated the .iso files with it and no others. I then ran the .iso file that I originally downloaded to make my disc, directly from my Program Files folder by double-clicking. It should be mounted and launch as a virtual drive and run like the disc but without using the disc. I think the access denied error has something to do with the disc drive but I was unable to fix it. 

Just follow your prompts to install as you normally would from the CD. Apparently, it saved all my settings from my previous Ubuntu install so I was psyched. :guitar:

Again, this may not be the best way to fix but I am more of a Windows geek than a Linux geek (but I am working on it ;P) Also, it may not fix your issue at all or make it worse so if that is the case, be sure to post back ASAP! My experience was good.
Good Luck
Got the same problem and would like to try your virtual clonedrive solution but have a few questions first. Please note that if I have put something that does not make sense that may be due to my lack of computer skills or I may have missed something obvious, please point out any problems :).

Info:
I have Vista the 64 bit one
I have downloaded and installed virtual conedrive.
I do not have a ubuntu file per say. 
I have the wubi file ([source ubuntu website]("http://www.ubuntu.com/download/ubuntu/windows-installer")) both on my computer and on cd disk do I need a ubuntu file as well?

The wubi file I have does not come with an image/ios file and I have looked at []("http://www.ubuntu.com/download/ubuntu/windows-installer")[_http://releases.ubuntu.com/11.10/ _]("http://releases.ubuntu.com/11.10/")but do not know which files to download and then mount. 

Also what do I do when they are mounted? Which file should I run presumably from the virtual cd drive.

If someone could help out that would be great I really want to give ubuntu a go and cannot do a dual operating system as my windows op/ms office backups are at home and I am curently at university. So other than running it from a disk which I have yet to try (heard it is slow and cant imagine how you can save things?) I have no other option. 

Trust me I did try playing around with installing wubi for quite some time before posting here but I seem to be going round in circles. Thanks in advance although you will be thanked again if you manage to help me :).

---

