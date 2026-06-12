---
title: "Error installing Ubuntu 9.04 with wubi on windows XP, please help."
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by omgpop on 2009-04-26
Hi there, 

When I try to install Ubuntu 8.04 using Wubi, I get a text box saying;

An error occurred:

IOError: <urlopen <html>
>

For more information please see the log file: blaablaablaa

I looked at the log file and it meant nothing to me.
Before I downloaded and installed Wubi, I did not know how to install Ubuntu; I thought, in my Naiveté, that all I had to do was open the .iso file, but no such luck. I asked around and discovered Wubi and used it. I should note, that except from foolishly trying to install the .iso file by the method I previously described, I have done nothing to it at all.

EDIT: How is it that the file I downloaded is only a a disk image file? Have I downloaded the wrong thing? Mind you, at nearly 700Mb, it seems like a large disk image.

---

### Post by omgpop on 2009-04-26
I do hate to be a pest and bump, but I would rather that than not get an answer to be perfectly honest.

---

### Post by lisati on 2009-04-26
Please be patient: I'm looking into it, others may be doing so too. How did searching the forums go?

---

### Post by omgpop on 2009-04-26
Sorry for being impatient.
I searched urlopen with no other filters and found nothing relevant, although I'm not saying nothing's there of course.

---

### Post by lisati on 2009-04-26
Is there a wubi log file in your %temp% folder? Attaching it might help other forum users figure out what's going on.

---

### Post by omgpop on 2009-04-26
Sorry for taking so long to reply. I think so, is the answer, if I am on the same page as you. I will find it shortly.

---

### Post by omgpop on 2009-04-26
Okay. I am currently trying to install Ubuntu so that I can get the address to that log file, however, where it usually pops up with that error message, (downloading information on installation files, it took longer then came up with a different message: cannot download the metalink and therefore the ISO.

---

### Post by omgpop on 2009-04-26
I just realized I may have deleted the temp folder, which is what I think is causing the new error. I saw the word temp in the log address, and assumed that was part of the reason for the error; you see I used to have an account called temp, but I deleted it except from its files, leaving a folder called temp. I really should have thought about why there might be two temp folders in hindsight.

---

### Post by omgpop on 2009-04-26
EDIT: current problem.

04-26 11:42 INFO   root: === wubi 9.04 rev129 ===
04-26 11:42 DEBUG  root: Logfile is c:\docume~1\jordan\locals~1\temp\wubi-9.04-rev129.log
04-26 11:42 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\DOCUME~1\\Jordan\\LOCALS~1\\Temp\\6lup8p0t.tmp\\wubi.exe"']
04-26 11:42 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl7F.tmp\data
04-26 11:42 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl7F.tmp\bin\7z.exe
04-26 11:42 DEBUG  CommonBackend: Fetching basic info...
04-26 11:42 DEBUG  CommonBackend: original_exe=C:\DOCUME~1\Jordan\LOCALS~1\Temp\6lup8p0t.tmp\wubi.exe
04-26 11:42 DEBUG  CommonBackend: platform=win32
04-26 11:42 DEBUG  CommonBackend: osname=nt
04-26 11:42 DEBUG  CommonBackend: language=en_GB
04-26 11:42 DEBUG  CommonBackend: encoding=cp1252
04-26 11:42 DEBUG  WindowsBackend: arch=i386
04-26 11:42 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl7F.tmp\data\isolist.ini
04-26 11:42 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-26 11:42 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-26 11:42 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-26 11:42 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-26 11:42 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-26 11:42 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-26 11:42 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-26 11:42 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-26 11:42 DEBUG  WindowsBackend: Fetching host info...
04-26 11:42 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-26 11:42 DEBUG  WindowsBackend: windows version=xp
04-26 11:42 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-26 11:42 DEBUG  WindowsBackend: windows_sp=Service Pack 3
04-26 11:42 DEBUG  WindowsBackend: windows_build=2600
04-26 11:42 DEBUG  WindowsBackend: gmt=0
04-26 11:42 DEBUG  WindowsBackend: country=GB
04-26 11:42 DEBUG  WindowsBackend: timezone=Europe/London
04-26 11:42 DEBUG  WindowsBackend: windows_username=Jordan
04-26 11:42 DEBUG  WindowsBackend: user_full_name=Jordan
04-26 11:42 DEBUG  WindowsBackend: user_directory=Jordan
04-26 11:42 DEBUG  WindowsBackend: windows_language_code=1033
04-26 11:42 DEBUG  WindowsBackend: windows_language=English
04-26 11:42 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
04-26 11:42 DEBUG  WindowsBackend: bootloader=xp
04-26 11:42 DEBUG  WindowsBackend: system_drive=Drive(C: hd 33148.4570313 mb free )
04-26 11:42 DEBUG  WindowsBackend: drive=Drive(C: hd 33148.4570313 mb free )
04-26 11:42 DEBUG  WindowsBackend: drive=Drive(D: hd 44576.3476563 mb free ntfs)
04-26 11:42 DEBUG  WindowsBackend: drive=Drive(E: hd 6121.09375 mb free fat32)
04-26 11:42 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free udf)
04-26 11:42 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
04-26 11:42 DEBUG  WindowsBackend: uninstaller_path=None
04-26 11:42 DEBUG  WindowsBackend: previous_target_dir=None
04-26 11:42 DEBUG  WindowsBackend: previous_distro_name=None
04-26 11:42 DEBUG  WindowsBackend: keyboard_id=134809609
04-26 11:42 DEBUG  WindowsBackend: keyboard_layout=gb
04-26 11:42 DEBUG  WindowsBackend: keyboard_variant=
04-26 11:42 DEBUG  CommonBackend: locale=en_GB.UTF-8
04-26 11:42 DEBUG  WindowsBackend: total_memory_mb=511.484375
04-26 11:42 DEBUG  CommonBackend: Searching ISOs on USB devices
04-26 11:42 DEBUG  CommonBackend: Searching for local CDs
04-26 11:42 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl7F.tmp is a valid Ubuntu CD
04-26 11:42 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl7F.tmp\casper\filesystem.squashfs
04-26 11:42 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl7F.tmp is a valid Ubuntu CD
04-26 11:42 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl7F.tmp\casper\filesystem.squashfs
04-26 11:42 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl7F.tmp is a valid Kubuntu CD
04-26 11:42 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl7F.tmp\casper\filesystem.squashfs
04-26 11:42 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl7F.tmp is a valid Kubuntu CD
04-26 11:42 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl7F.tmp\casper\filesystem.squashfs
04-26 11:42 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl7F.tmp is a valid Xubuntu CD
04-26 11:42 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl7F.tmp\casper\filesystem.squashfs
04-26 11:42 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl7F.tmp is a valid Xubuntu CD
04-26 11:42 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl7F.tmp\casper\filesystem.squashfs
04-26 11:42 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl7F.tmp is a valid Mythbuntu CD
04-26 11:42 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl7F.tmp\casper\filesystem.squashfs
04-26 11:42 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl7F.tmp is a valid Mythbuntu CD
04-26 11:42 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl7F.tmp\casper\filesystem.squashfs
04-26 11:42 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 11:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 11:42 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 11:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 11:42 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 11:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 11:42 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 11:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 11:42 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 11:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 11:42 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 11:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 11:42 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 11:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 11:42 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 11:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 11:42 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-26 11:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 11:42 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-26 11:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 11:42 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-26 11:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 11:42 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-26 11:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 11:42 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-26 11:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 11:42 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-26 11:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 11:42 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-26 11:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 11:42 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-26 11:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 11:42 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-26 11:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 11:42 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-26 11:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 11:42 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-26 11:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 11:42 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-26 11:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 11:42 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-26 11:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 11:42 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-26 11:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 11:42 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-26 11:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 11:42 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-26 11:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 11:42 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-26 11:42 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 11:42 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-26 11:42 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 11:42 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-26 11:42 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 11:42 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-26 11:42 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 11:42 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-26 11:42 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 11:42 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-26 11:42 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 11:42 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-26 11:42 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 11:42 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-26 11:42 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 11:42 INFO   root: Running the installer...
04-26 11:42 DEBUG  WindowsFrontend: __init__...
04-26 11:42 DEBUG  WindowsFrontend: on_init...
04-26 11:42 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=English, username=omgpop
04-26 11:42 INFO   root: Received settings
04-26 11:42 DEBUG  TaskList: # Running tasklist...
04-26 11:42 DEBUG  TaskList: ## Running select_target_dir...
04-26 11:42 INFO   WindowsBackend: Installing into C:\ubuntu
04-26 11:42 DEBUG  TaskList: ## Finished select_target_dir
04-26 11:42 DEBUG  TaskList: ## Running create_dir_structure...
04-26 11:42 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-26 11:42 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-26 11:42 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-26 11:42 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-26 11:42 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-26 11:42 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-26 11:42 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-26 11:42 DEBUG  TaskList: ## Finished create_dir_structure
04-26 11:42 DEBUG  TaskList: ## Running uncompress_target_dir...
04-26 11:42 DEBUG  TaskList: ## Finished uncompress_target_dir
04-26 11:42 DEBUG  TaskList: ## Running create_uninstaller...
04-26 11:42 DEBUG  WindowsBackend: Copying uninstaller C:\DOCUME~1\Jordan\LOCALS~1\Temp\6lup8p0t.tmp\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-26 11:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-26 11:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-26 11:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-26 11:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-26 11:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev129
04-26 11:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-26 11:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-26 11:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-26 11:42 DEBUG  TaskList: ## Finished create_uninstaller
04-26 11:42 DEBUG  TaskList: ## Running copy_installation_files...
04-26 11:42 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl7F.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-26 11:42 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl7F.tmp\winboot -> C:\ubuntu\winboot
04-26 11:42 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl7F.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-26 11:42 DEBUG  TaskList: ## Finished copy_installation_files
04-26 11:42 DEBUG  TaskList: ## Running get_iso...
04-26 11:42 DEBUG  CommonBackend: Searching for local CD
04-26 11:42 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl7F.tmp is a valid Ubuntu CD
04-26 11:42 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl7F.tmp\casper\filesystem.squashfs
04-26 11:42 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 11:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 11:42 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-26 11:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 11:42 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-26 11:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 11:42 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-26 11:42 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 11:42 DEBUG  CommonBackend: Searching for local ISO
04-26 11:42 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
04-26 11:42 DEBUG  TaskList: New task get_metalink
04-26 11:42 DEBUG  TaskList: ### Running get_metalink...
04-26 11:42 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink](http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink) > C:\ubuntu\install
04-26 11:43 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-9.04-desktop-i386.metalink, url=http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink, basename=ubuntu-9.04-desktop-i386.metalink, length=19438, text=None
04-26 11:43 DEBUG  downloader: download finished (read 19438 bytes)
04-26 11:43 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.04/MD5SUMS-metalink](http://releases.ubuntu.com/9.04/MD5SUMS-metalink) > C:\ubuntu\install
04-26 11:43 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/9.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=413, text=None
04-26 11:43 DEBUG  downloader: download finished (read 413 bytes)
04-26 11:43 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/9.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
04-26 11:43 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/9.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
04-26 11:43 DEBUG  downloader: download finished (read 189 bytes)
04-26 11:43 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
04-26 11:43 INFO   saplog: Checking block bindings..
04-26 11:43 INFO   saplog: Key verified successfully.
04-26 11:43 DEBUG  CommonBackend: metalink md5sums:
1ec553ada3a4a18fb977816ccac02dfc  ubuntu-9.04-alternate-amd64.metalink
5daf9cb57325672f0eb768d6c11888e8  ubuntu-9.04-alternate-i386.metalink
3df58e889d3613abc2347a6b0e8f4d04  ubuntu-9.04-desktop-amd64.metalink
542bc6d7988f1d2967d419c089b08f57  ubuntu-9.04-desktop-i386.metalink
ea0b13f00711ef4b2e5c772482033a1f  ubuntu-9.04-server-amd64.metalink
88e47c579eb587c8aae1a7d7737ab3f0  ubuntu-9.04-server-i386.metalink

04-26 11:43 DEBUG  TaskList: ### Finished get_metalink
04-26 11:43 DEBUG  TaskList: New task download
04-26 11:43 DEBUG  TaskList: ### Running download...
04-26 11:43 DEBUG  downloader: downloading [http://de.archive.ubuntu.com/ubuntu-releases/9.04/ubuntu-9.04-desktop-i386.iso](http://de.archive.ubuntu.com/ubuntu-releases/9.04/ubuntu-9.04-desktop-i386.iso) > C:\ubuntu\install\ubuntu-9.04-desktop-i386.iso
04-26 11:43 ERROR  TaskList: [Errno 4] IOError: <urlopen error <html>

>
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\downloader.py", line 79, in download
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\urlgrabber\grabber.py", line 845, in _retry
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\urlgrabber\grabber.py", line 913, in retryfunc
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\urlgrabber\grabber.py", line 1001, in __init__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\urlgrabber\grabber.py", line 1072, in _do_open
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\urlgrabber\grabber.py", line 1188, in _make_request
URLGrabError: [Errno 4] IOError: <urlopen error <html>

>
04-26 11:43 DEBUG  TaskList: # Cancelling tasklist
04-26 11:43 ERROR  root: [Errno 4] IOError: <urlopen error <html>

>
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 129, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
URLGrabError: [Errno 4] IOError: <urlopen error <html>

>
04-26 11:43 DEBUG  TaskList: New task download
04-26 11:43 DEBUG  TaskList: New task download
04-26 11:43 DEBUG  TaskList: New task download
04-26 11:43 DEBUG  TaskList: New task download
04-26 11:43 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 487, in get_iso
Exception: Could not retrieve the required installation files
04-26 11:43 DEBUG  TaskList: # Cancelling tasklist
04-26 11:43 DEBUG  TaskList: # Finished tasklist
04-26 11:44 INFO   root: === wubi 9.04 rev129 ===
04-26 11:44 DEBUG  root: Logfile is c:\docume~1\jordan\locals~1\temp\wubi-9.04-rev129.log
04-26 11:44 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\DOCUME~1\\Jordan\\LOCALS~1\\Temp\\6lup8p0t.tmp\\wubi.exe"']
04-26 11:44 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl80.tmp\data
04-26 11:44 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl80.tmp\bin\7z.exe
04-26 11:44 DEBUG  CommonBackend: Fetching basic info...
04-26 11:44 DEBUG  CommonBackend: original_exe=C:\DOCUME~1\Jordan\LOCALS~1\Temp\6lup8p0t.tmp\wubi.exe
04-26 11:44 DEBUG  CommonBackend: platform=win32
04-26 11:44 DEBUG  CommonBackend: osname=nt
04-26 11:44 DEBUG  CommonBackend: language=en_GB
04-26 11:44 DEBUG  CommonBackend: encoding=cp1252
04-26 11:44 DEBUG  WindowsBackend: arch=i386
04-26 11:44 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl80.tmp\data\isolist.ini
04-26 11:44 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-26 11:44 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-26 11:44 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-26 11:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-26 11:44 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-26 11:44 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-26 11:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-26 11:44 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-26 11:44 DEBUG  WindowsBackend: Fetching host info...
04-26 11:44 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-26 11:44 DEBUG  WindowsBackend: windows version=xp
04-26 11:44 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-26 11:44 DEBUG  WindowsBackend: windows_sp=Service Pack 3
04-26 11:44 DEBUG  WindowsBackend: windows_build=2600
04-26 11:44 DEBUG  WindowsBackend: gmt=0
04-26 11:44 DEBUG  WindowsBackend: country=GB
04-26 11:44 DEBUG  WindowsBackend: timezone=Europe/London
04-26 11:44 DEBUG  WindowsBackend: windows_username=Jordan
04-26 11:44 DEBUG  WindowsBackend: user_full_name=Jordan
04-26 11:44 DEBUG  WindowsBackend: user_directory=Jordan
04-26 11:44 DEBUG  WindowsBackend: windows_language_code=1033
04-26 11:44 DEBUG  WindowsBackend: windows_language=English
04-26 11:44 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
04-26 11:44 DEBUG  WindowsBackend: bootloader=xp
04-26 11:44 DEBUG  WindowsBackend: system_drive=Drive(C: hd 33146.2265625 mb free )
04-26 11:44 DEBUG  WindowsBackend: drive=Drive(C: hd 33146.2265625 mb free )
04-26 11:44 DEBUG  WindowsBackend: drive=Drive(D: hd 44576.3476563 mb free ntfs)
04-26 11:44 DEBUG  WindowsBackend: drive=Drive(E: hd 6121.09375 mb free fat32)
04-26 11:44 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free udf)
04-26 11:44 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
04-26 11:44 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-26 11:44 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-26 11:44 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-26 11:44 DEBUG  WindowsBackend: keyboard_id=134809609
04-26 11:44 DEBUG  WindowsBackend: keyboard_layout=gb
04-26 11:44 DEBUG  WindowsBackend: keyboard_variant=
04-26 11:44 DEBUG  CommonBackend: locale=en_GB.UTF-8
04-26 11:44 DEBUG  WindowsBackend: total_memory_mb=511.484375
04-26 11:44 DEBUG  CommonBackend: Searching ISOs on USB devices
04-26 11:44 DEBUG  CommonBackend: Searching for local CDs
04-26 11:44 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl80.tmp is a valid Ubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl80.tmp\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl80.tmp is a valid Ubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl80.tmp\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl80.tmp is a valid Kubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl80.tmp\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl80.tmp is a valid Kubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl80.tmp\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl80.tmp is a valid Xubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl80.tmp\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl80.tmp is a valid Xubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl80.tmp\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl80.tmp is a valid Mythbuntu CD
04-26 11:44 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl80.tmp\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl80.tmp is a valid Mythbuntu CD
04-26 11:44 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl80.tmp\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 11:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 11:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-26 11:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-26 11:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-26 11:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-26 11:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-26 11:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-26 11:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 11:44 INFO   root: Already installed, running the uninstaller...
04-26 11:44 INFO   root: Running the uninstaller...
04-26 11:44 INFO   CommonBackend: This is the uninstaller running
04-26 11:44 DEBUG  WindowsFrontend: __init__...
04-26 11:44 DEBUG  WindowsFrontend: on_init...
04-26 11:44 INFO   root: Received settings
04-26 11:44 DEBUG  TaskList: # Running tasklist...
04-26 11:44 DEBUG  TaskList: ## Running Backup ISO...
04-26 11:44 DEBUG  TaskList: ## Finished Backup ISO
04-26 11:44 DEBUG  TaskList: ## Running Remove bootloader entry...
04-26 11:44 ERROR  WindowsBackend: Cannot find bcdedit
04-26 11:44 DEBUG  WindowsBackend: undo_bootini C:
04-26 11:44 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 33146.2265625 mb free )
04-26 11:44 DEBUG  WindowsBackend: undo_bootini D:
04-26 11:44 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 44576.3476563 mb free ntfs)
04-26 11:44 DEBUG  WindowsBackend: undo_bootini E:
04-26 11:44 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 6121.09375 mb free fat32)
04-26 11:44 DEBUG  TaskList: ## Finished Remove bootloader entry
04-26 11:44 DEBUG  TaskList: ## Running Remove target dir...
04-26 11:44 DEBUG  CommonBackend: Deleting C:\ubuntu
04-26 11:44 DEBUG  TaskList: ## Finished Remove target dir
04-26 11:44 DEBUG  TaskList: ## Running Remove registry key...
04-26 11:44 DEBUG  TaskList: ## Finished Remove registry key
04-26 11:44 DEBUG  TaskList: # Finished tasklist
04-26 11:44 INFO   root: Almost finished uninstalling
04-26 11:44 INFO   root: Finished uninstallation
04-26 11:44 DEBUG  CommonBackend: Fetching basic info...
04-26 11:44 DEBUG  CommonBackend: original_exe=C:\DOCUME~1\Jordan\LOCALS~1\Temp\6lup8p0t.tmp\wubi.exe
04-26 11:44 DEBUG  CommonBackend: platform=win32
04-26 11:44 DEBUG  CommonBackend: osname=nt
04-26 11:44 DEBUG  CommonBackend: language=en_GB
04-26 11:44 DEBUG  CommonBackend: encoding=cp1252
04-26 11:44 DEBUG  WindowsBackend: arch=i386
04-26 11:44 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl80.tmp\data\isolist.ini
04-26 11:44 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-26 11:44 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-26 11:44 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-26 11:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-26 11:44 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-26 11:44 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-26 11:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-26 11:44 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-26 11:44 DEBUG  WindowsBackend: Fetching host info...
04-26 11:44 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-26 11:44 DEBUG  WindowsBackend: windows version=xp
04-26 11:44 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-26 11:44 DEBUG  WindowsBackend: windows_sp=Service Pack 3
04-26 11:44 DEBUG  WindowsBackend: windows_build=2600
04-26 11:44 DEBUG  WindowsBackend: gmt=0
04-26 11:44 DEBUG  WindowsBackend: country=GB
04-26 11:44 DEBUG  WindowsBackend: timezone=Europe/London
04-26 11:44 DEBUG  WindowsBackend: windows_username=Jordan
04-26 11:44 DEBUG  WindowsBackend: user_full_name=Jordan
04-26 11:44 DEBUG  WindowsBackend: user_directory=Jordan
04-26 11:44 DEBUG  WindowsBackend: windows_language_code=1033
04-26 11:44 DEBUG  WindowsBackend: windows_language=English
04-26 11:44 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
04-26 11:44 DEBUG  WindowsBackend: bootloader=xp
04-26 11:44 DEBUG  WindowsBackend: system_drive=Drive(C: hd 33148.0664063 mb free )
04-26 11:44 DEBUG  WindowsBackend: drive=Drive(C: hd 33148.0664063 mb free )
04-26 11:44 DEBUG  WindowsBackend: drive=Drive(D: hd 44576.3476563 mb free ntfs)
04-26 11:44 DEBUG  WindowsBackend: drive=Drive(E: hd 6121.09375 mb free fat32)
04-26 11:44 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free udf)
04-26 11:44 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
04-26 11:44 DEBUG  WindowsBackend: uninstaller_path=None
04-26 11:44 DEBUG  WindowsBackend: previous_target_dir=None
04-26 11:44 DEBUG  WindowsBackend: previous_distro_name=None
04-26 11:44 DEBUG  WindowsBackend: keyboard_id=134809609
04-26 11:44 DEBUG  WindowsBackend: keyboard_layout=gb
04-26 11:44 DEBUG  WindowsBackend: keyboard_variant=
04-26 11:44 DEBUG  CommonBackend: locale=en_GB.UTF-8
04-26 11:44 DEBUG  WindowsBackend: total_memory_mb=511.484375
04-26 11:44 DEBUG  CommonBackend: Searching ISOs on USB devices
04-26 11:44 DEBUG  CommonBackend: Searching for local CDs
04-26 11:44 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl80.tmp is a valid Ubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl80.tmp\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl80.tmp is a valid Ubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl80.tmp\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl80.tmp is a valid Kubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl80.tmp\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl80.tmp is a valid Kubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl80.tmp\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl80.tmp is a valid Xubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl80.tmp\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl80.tmp is a valid Xubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl80.tmp\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl80.tmp is a valid Mythbuntu CD
04-26 11:44 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl80.tmp\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl80.tmp is a valid Mythbuntu CD
04-26 11:44 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl80.tmp\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 11:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 11:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-26 11:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-26 11:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-26 11:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-26 11:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-26 11:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-26 11:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 11:44 INFO   root: Running the installer...
04-26 11:44 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=English, username=jordan
04-26 11:44 INFO   root: Received settings
04-26 11:44 DEBUG  TaskList: # Running tasklist...
04-26 11:44 DEBUG  TaskList: ## Running select_target_dir...
04-26 11:44 INFO   WindowsBackend: Installing into C:\ubuntu
04-26 11:44 DEBUG  TaskList: ## Finished select_target_dir
04-26 11:44 DEBUG  TaskList: ## Running create_dir_structure...
04-26 11:44 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-26 11:44 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-26 11:44 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-26 11:44 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-26 11:44 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-26 11:44 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-26 11:44 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-26 11:44 DEBUG  TaskList: ## Finished create_dir_structure
04-26 11:44 DEBUG  TaskList: ## Running uncompress_target_dir...
04-26 11:44 DEBUG  TaskList: ## Finished uncompress_target_dir
04-26 11:44 DEBUG  TaskList: ## Running create_uninstaller...
04-26 11:44 DEBUG  WindowsBackend: Copying uninstaller C:\DOCUME~1\Jordan\LOCALS~1\Temp\6lup8p0t.tmp\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-26 11:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-26 11:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-26 11:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-26 11:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-26 11:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev129
04-26 11:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-26 11:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-26 11:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-26 11:44 DEBUG  TaskList: ## Finished create_uninstaller
04-26 11:44 DEBUG  TaskList: ## Running copy_installation_files...
04-26 11:44 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl80.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-26 11:44 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl80.tmp\winboot -> C:\ubuntu\winboot
04-26 11:44 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl80.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-26 11:44 DEBUG  TaskList: ## Finished copy_installation_files
04-26 11:44 DEBUG  TaskList: ## Running get_iso...
04-26 11:44 DEBUG  CommonBackend: Searching for local CD
04-26 11:44 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl80.tmp is a valid Ubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl80.tmp\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 11:44 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-26 11:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 11:44 DEBUG  CommonBackend: Searching for local ISO
04-26 11:44 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
04-26 11:44 DEBUG  TaskList: New task get_metalink
04-26 11:44 DEBUG  TaskList: ### Running get_metalink...
04-26 11:44 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink](http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink) > C:\ubuntu\install
04-26 11:44 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-9.04-desktop-i386.metalink, url=http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink, basename=ubuntu-9.04-desktop-i386.metalink, length=19438, text=None
04-26 11:44 DEBUG  downloader: download finished (read 19438 bytes)
04-26 11:44 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.04/MD5SUMS-metalink](http://releases.ubuntu.com/9.04/MD5SUMS-metalink) > C:\ubuntu\install
04-26 11:44 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/9.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=413, text=None
04-26 11:44 DEBUG  downloader: download finished (read 413 bytes)
04-26 11:44 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/9.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
04-26 11:44 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/9.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
04-26 11:44 DEBUG  downloader: download finished (read 189 bytes)
04-26 11:44 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
04-26 11:44 INFO   saplog: Checking block bindings..
04-26 11:44 INFO   saplog: Key verified successfully.
04-26 11:44 DEBUG  CommonBackend: metalink md5sums:
1ec553ada3a4a18fb977816ccac02dfc  ubuntu-9.04-alternate-amd64.metalink
5daf9cb57325672f0eb768d6c11888e8  ubuntu-9.04-alternate-i386.metalink
3df58e889d3613abc2347a6b0e8f4d04  ubuntu-9.04-desktop-amd64.metalink
542bc6d7988f1d2967d419c089b08f57  ubuntu-9.04-desktop-i386.metalink
ea0b13f00711ef4b2e5c772482033a1f  ubuntu-9.04-server-amd64.metalink
88e47c579eb587c8aae1a7d7737ab3f0  ubuntu-9.04-server-i386.metalink

04-26 11:44 DEBUG  TaskList: ### Finished get_metalink
04-26 11:44 DEBUG  TaskList: New task download
04-26 11:44 DEBUG  TaskList: ### Running download...
04-26 11:44 DEBUG  downloader: downloading [http://de.archive.ubuntu.com/ubuntu-releases/9.04/ubuntu-9.04-desktop-i386.iso](http://de.archive.ubuntu.com/ubuntu-releases/9.04/ubuntu-9.04-desktop-i386.iso) > C:\ubuntu\install\ubuntu-9.04-desktop-i386.iso
04-26 11:45 ERROR  TaskList: [Errno 4] IOError: <urlopen error <html>

>
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\downloader.py", line 79, in download
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\urlgrabber\grabber.py", line 845, in _retry
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\urlgrabber\grabber.py", line 913, in retryfunc
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\urlgrabber\grabber.py", line 1001, in __init__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\urlgrabber\grabber.py", line 1072, in _do_open
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\urlgrabber\grabber.py", line 1188, in _make_request
URLGrabError: [Errno 4] IOError: <urlopen error <html>

>
04-26 11:45 DEBUG  TaskList: # Cancelling tasklist
04-26 11:45 ERROR  root: [Errno 4] IOError: <urlopen error <html>

>
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 129, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
URLGrabError: [Errno 4] IOError: <urlopen error <html>

>
04-26 11:45 DEBUG  TaskList: New task download
04-26 11:45 DEBUG  TaskList: New task download
04-26 11:45 DEBUG  TaskList: New task download
04-26 11:45 DEBUG  TaskList: New task download
04-26 11:45 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 487, in get_iso
Exception: Could not retrieve the required installation files
04-26 11:45 DEBUG  TaskList: # Cancelling tasklist
04-26 11:45 DEBUG  TaskList: # Finished tasklist
04-26 12:05 INFO   root: === wubi 9.04 rev129 ===
04-26 12:05 DEBUG  root: Logfile is c:\docume~1\jordan\locals~1\temp\wubi-9.04-rev129.log
04-26 12:05 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\DOCUME~1\\Jordan\\LOCALS~1\\Temp\\6lup8p0t.tmp\\wubi.exe"']
04-26 12:05 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8A.tmp\data
04-26 12:05 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8A.tmp\bin\7z.exe
04-26 12:05 DEBUG  CommonBackend: Fetching basic info...
04-26 12:05 DEBUG  CommonBackend: original_exe=C:\DOCUME~1\Jordan\LOCALS~1\Temp\6lup8p0t.tmp\wubi.exe
04-26 12:05 DEBUG  CommonBackend: platform=win32
04-26 12:05 DEBUG  CommonBackend: osname=nt
04-26 12:05 DEBUG  CommonBackend: language=en_GB
04-26 12:05 DEBUG  CommonBackend: encoding=cp1252
04-26 12:05 DEBUG  WindowsBackend: arch=i386
04-26 12:05 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8A.tmp\data\isolist.ini
04-26 12:05 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-26 12:05 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-26 12:05 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-26 12:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-26 12:05 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-26 12:05 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-26 12:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-26 12:05 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-26 12:05 DEBUG  WindowsBackend: Fetching host info...
04-26 12:05 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-26 12:05 DEBUG  WindowsBackend: windows version=xp
04-26 12:05 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-26 12:05 DEBUG  WindowsBackend: windows_sp=Service Pack 3
04-26 12:05 DEBUG  WindowsBackend: windows_build=2600
04-26 12:05 DEBUG  WindowsBackend: gmt=0
04-26 12:05 DEBUG  WindowsBackend: country=GB
04-26 12:05 DEBUG  WindowsBackend: timezone=Europe/London
04-26 12:05 DEBUG  WindowsBackend: windows_username=Jordan
04-26 12:05 DEBUG  WindowsBackend: user_full_name=Jordan
04-26 12:05 DEBUG  WindowsBackend: user_directory=Jordan
04-26 12:05 DEBUG  WindowsBackend: windows_language_code=1033
04-26 12:05 DEBUG  WindowsBackend: windows_language=English
04-26 12:05 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
04-26 12:05 DEBUG  WindowsBackend: bootloader=xp
04-26 12:05 DEBUG  WindowsBackend: system_drive=Drive(C: hd 33060.0117188 mb free )
04-26 12:05 DEBUG  WindowsBackend: drive=Drive(C: hd 33060.0117188 mb free )
04-26 12:05 DEBUG  WindowsBackend: drive=Drive(D: hd 44576.3476563 mb free ntfs)
04-26 12:05 DEBUG  WindowsBackend: drive=Drive(E: hd 6121.09375 mb free fat32)
04-26 12:05 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free udf)
04-26 12:05 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
04-26 12:05 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-26 12:05 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-26 12:05 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-26 12:05 DEBUG  WindowsBackend: keyboard_id=134809609
04-26 12:05 DEBUG  WindowsBackend: keyboard_layout=gb
04-26 12:05 DEBUG  WindowsBackend: keyboard_variant=
04-26 12:05 DEBUG  CommonBackend: locale=en_GB.UTF-8
04-26 12:05 DEBUG  WindowsBackend: total_memory_mb=511.484375
04-26 12:05 DEBUG  CommonBackend: Searching ISOs on USB devices
04-26 12:05 DEBUG  CommonBackend: Searching for local CDs
04-26 12:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8A.tmp is a valid Ubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8A.tmp\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8A.tmp is a valid Ubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8A.tmp\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8A.tmp is a valid Kubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8A.tmp\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8A.tmp is a valid Kubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8A.tmp\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8A.tmp is a valid Xubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8A.tmp\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8A.tmp is a valid Xubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8A.tmp\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8A.tmp is a valid Mythbuntu CD
04-26 12:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8A.tmp\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8A.tmp is a valid Mythbuntu CD
04-26 12:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8A.tmp\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 12:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 12:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-26 12:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-26 12:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-26 12:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-26 12:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-26 12:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-26 12:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 12:05 INFO   root: Already installed, running the uninstaller...
04-26 12:05 INFO   root: Running the uninstaller...
04-26 12:05 INFO   CommonBackend: This is the uninstaller running
04-26 12:05 DEBUG  WindowsFrontend: __init__...
04-26 12:05 DEBUG  WindowsFrontend: on_init...
04-26 12:05 INFO   root: Received settings
04-26 12:05 DEBUG  TaskList: # Running tasklist...
04-26 12:05 DEBUG  TaskList: ## Running Backup ISO...
04-26 12:05 DEBUG  TaskList: ## Finished Backup ISO
04-26 12:05 DEBUG  TaskList: ## Running Remove bootloader entry...
04-26 12:05 ERROR  WindowsBackend: Cannot find bcdedit
04-26 12:05 DEBUG  WindowsBackend: undo_bootini C:
04-26 12:05 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 33060.0117188 mb free )
04-26 12:05 DEBUG  WindowsBackend: undo_bootini D:
04-26 12:05 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 44576.3476563 mb free ntfs)
04-26 12:05 DEBUG  WindowsBackend: undo_bootini E:
04-26 12:05 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 6121.09375 mb free fat32)
04-26 12:05 DEBUG  TaskList: ## Finished Remove bootloader entry
04-26 12:05 DEBUG  TaskList: ## Running Remove target dir...
04-26 12:05 DEBUG  CommonBackend: Deleting C:\ubuntu
04-26 12:05 DEBUG  TaskList: ## Finished Remove target dir
04-26 12:05 DEBUG  TaskList: ## Running Remove registry key...
04-26 12:05 DEBUG  TaskList: ## Finished Remove registry key
04-26 12:05 DEBUG  TaskList: # Finished tasklist
04-26 12:05 INFO   root: Almost finished uninstalling
04-26 12:05 INFO   root: Finished uninstallation
04-26 12:05 DEBUG  CommonBackend: Fetching basic info...
04-26 12:05 DEBUG  CommonBackend: original_exe=C:\DOCUME~1\Jordan\LOCALS~1\Temp\6lup8p0t.tmp\wubi.exe
04-26 12:05 DEBUG  CommonBackend: platform=win32
04-26 12:05 DEBUG  CommonBackend: osname=nt
04-26 12:05 DEBUG  CommonBackend: language=en_GB
04-26 12:05 DEBUG  CommonBackend: encoding=cp1252
04-26 12:05 DEBUG  WindowsBackend: arch=i386
04-26 12:05 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8A.tmp\data\isolist.ini
04-26 12:05 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-26 12:05 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-26 12:05 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-26 12:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-26 12:05 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-26 12:05 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-26 12:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-26 12:05 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-26 12:05 DEBUG  WindowsBackend: Fetching host info...
04-26 12:05 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-26 12:05 DEBUG  WindowsBackend: windows version=xp
04-26 12:05 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-26 12:05 DEBUG  WindowsBackend: windows_sp=Service Pack 3
04-26 12:05 DEBUG  WindowsBackend: windows_build=2600
04-26 12:05 DEBUG  WindowsBackend: gmt=0
04-26 12:05 DEBUG  WindowsBackend: country=GB
04-26 12:05 DEBUG  WindowsBackend: timezone=Europe/London
04-26 12:05 DEBUG  WindowsBackend: windows_username=Jordan
04-26 12:05 DEBUG  WindowsBackend: user_full_name=Jordan
04-26 12:05 DEBUG  WindowsBackend: user_directory=Jordan
04-26 12:05 DEBUG  WindowsBackend: windows_language_code=1033
04-26 12:05 DEBUG  WindowsBackend: windows_language=English
04-26 12:05 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
04-26 12:05 DEBUG  WindowsBackend: bootloader=xp
04-26 12:05 DEBUG  WindowsBackend: system_drive=Drive(C: hd 33061.9414063 mb free )
04-26 12:05 DEBUG  WindowsBackend: drive=Drive(C: hd 33061.9414063 mb free )
04-26 12:05 DEBUG  WindowsBackend: drive=Drive(D: hd 44576.3476563 mb free ntfs)
04-26 12:05 DEBUG  WindowsBackend: drive=Drive(E: hd 6121.09375 mb free fat32)
04-26 12:05 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free udf)
04-26 12:05 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
04-26 12:05 DEBUG  WindowsBackend: uninstaller_path=None
04-26 12:05 DEBUG  WindowsBackend: previous_target_dir=None
04-26 12:05 DEBUG  WindowsBackend: previous_distro_name=None
04-26 12:05 DEBUG  WindowsBackend: keyboard_id=134809609
04-26 12:05 DEBUG  WindowsBackend: keyboard_layout=gb
04-26 12:05 DEBUG  WindowsBackend: keyboard_variant=
04-26 12:05 DEBUG  CommonBackend: locale=en_GB.UTF-8
04-26 12:05 DEBUG  WindowsBackend: total_memory_mb=511.484375
04-26 12:05 DEBUG  CommonBackend: Searching ISOs on USB devices
04-26 12:05 DEBUG  CommonBackend: Searching for local CDs
04-26 12:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8A.tmp is a valid Ubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8A.tmp\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8A.tmp is a valid Ubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8A.tmp\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8A.tmp is a valid Kubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8A.tmp\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8A.tmp is a valid Kubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8A.tmp\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8A.tmp is a valid Xubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8A.tmp\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8A.tmp is a valid Xubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8A.tmp\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8A.tmp is a valid Mythbuntu CD
04-26 12:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8A.tmp\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8A.tmp is a valid Mythbuntu CD
04-26 12:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8A.tmp\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 12:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 12:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-26 12:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-26 12:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-26 12:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-26 12:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-26 12:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-26 12:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 12:05 INFO   root: Running the installer...
04-26 12:05 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=17000MB, distro_name=Ubuntu, language=English, username=jordan
04-26 12:05 INFO   root: Received settings
04-26 12:05 DEBUG  TaskList: # Running tasklist...
04-26 12:05 DEBUG  TaskList: ## Running select_target_dir...
04-26 12:05 INFO   WindowsBackend: Installing into D:\ubuntu
04-26 12:05 DEBUG  TaskList: ## Finished select_target_dir
04-26 12:05 DEBUG  TaskList: ## Running create_dir_structure...
04-26 12:05 DEBUG  CommonBackend: Creating dir D:\ubuntu
04-26 12:05 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
04-26 12:05 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
04-26 12:05 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
04-26 12:05 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
04-26 12:05 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
04-26 12:05 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
04-26 12:05 DEBUG  TaskList: ## Finished create_dir_structure
04-26 12:05 DEBUG  TaskList: ## Running uncompress_target_dir...
04-26 12:05 DEBUG  TaskList: ## Finished uncompress_target_dir
04-26 12:05 DEBUG  TaskList: ## Running create_uninstaller...
04-26 12:05 DEBUG  WindowsBackend: Copying uninstaller C:\DOCUME~1\Jordan\LOCALS~1\Temp\6lup8p0t.tmp\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
04-26 12:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
04-26 12:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
04-26 12:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-26 12:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
04-26 12:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev129
04-26 12:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-26 12:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-26 12:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-26 12:05 DEBUG  TaskList: ## Finished create_uninstaller
04-26 12:05 DEBUG  TaskList: ## Running copy_installation_files...
04-26 12:05 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8A.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
04-26 12:05 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8A.tmp\winboot -> D:\ubuntu\winboot
04-26 12:05 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8A.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
04-26 12:05 DEBUG  TaskList: ## Finished copy_installation_files
04-26 12:05 DEBUG  TaskList: ## Running get_iso...
04-26 12:05 DEBUG  CommonBackend: Searching for local CD
04-26 12:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8A.tmp is a valid Ubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8A.tmp\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 12:05 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-26 12:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 12:05 DEBUG  CommonBackend: Searching for local ISO
04-26 12:05 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
04-26 12:05 DEBUG  TaskList: New task get_metalink
04-26 12:05 DEBUG  TaskList: ### Running get_metalink...
04-26 12:05 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink](http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink) > D:\ubuntu\install
04-26 12:05 DEBUG  downloader: Download start filename=D:\ubuntu\install\ubuntu-9.04-desktop-i386.metalink, url=http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink, basename=ubuntu-9.04-desktop-i386.metalink, length=19438, text=None
04-26 12:05 DEBUG  downloader: download finished (read 19438 bytes)
04-26 12:05 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.04/MD5SUMS-metalink](http://releases.ubuntu.com/9.04/MD5SUMS-metalink) > D:\ubuntu\install
04-26 12:05 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/9.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=487, text=None
04-26 12:05 DEBUG  downloader: download finished (read 487 bytes)
04-26 12:05 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/9.04/MD5SUMS-metalink.gpg) > D:\ubuntu\install
04-26 12:05 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/9.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
04-26 12:05 DEBUG  downloader: download finished (read 189 bytes)
04-26 12:05 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
04-26 12:05 INFO   saplog: Checking block bindings..
04-26 12:05 INFO   saplog: Key verified successfully.
04-26 12:05 DEBUG  CommonBackend: metalink md5sums:
1ec553ada3a4a18fb977816ccac02dfc  ubuntu-9.04-alternate-amd64.metalink
5daf9cb57325672f0eb768d6c11888e8  ubuntu-9.04-alternate-i386.metalink
3df58e889d3613abc2347a6b0e8f4d04  ubuntu-9.04-desktop-amd64.metalink
542bc6d7988f1d2967d419c089b08f57  ubuntu-9.04-desktop-i386.metalink
ffd21294d807046e22589b966b134d2d  ubuntu-9.04-netbook-remix-i386.metalink
ea0b13f00711ef4b2e5c772482033a1f  ubuntu-9.04-server-amd64.metalink
88e47c579eb587c8aae1a7d7737ab3f0  ubuntu-9.04-server-i386.metalink

04-26 12:05 DEBUG  TaskList: ### Finished get_metalink
04-26 12:05 DEBUG  TaskList: New task download
04-26 12:05 DEBUG  TaskList: ### Running download...
04-26 12:05 DEBUG  downloader: downloading [http://de.archive.ubuntu.com/ubuntu-releases/9.04/ubuntu-9.04-desktop-i386.iso](http://de.archive.ubuntu.com/ubuntu-releases/9.04/ubuntu-9.04-desktop-i386.iso) > D:\ubuntu\install\ubuntu-9.04-desktop-i386.iso
04-26 12:05 ERROR  TaskList: [Errno 4] IOError: <urlopen error <html>

>
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\downloader.py", line 79, in download
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\urlgrabber\grabber.py", line 845, in _retry
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\urlgrabber\grabber.py", line 913, in retryfunc
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\urlgrabber\grabber.py", line 1001, in __init__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\urlgrabber\grabber.py", line 1072, in _do_open
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\urlgrabber\grabber.py", line 1188, in _make_request
URLGrabError: [Errno 4] IOError: <urlopen error <html>

>
04-26 12:05 DEBUG  TaskList: # Cancelling tasklist
04-26 12:05 ERROR  root: [Errno 4] IOError: <urlopen error <html>

>
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 129, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
URLGrabError: [Errno 4] IOError: <urlopen error <html>

>
04-26 12:05 DEBUG  TaskList: New task download
04-26 12:05 DEBUG  TaskList: New task download
04-26 12:05 DEBUG  TaskList: New task download
04-26 12:05 DEBUG  TaskList: New task download
04-26 12:05 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 487, in get_iso
Exception: Could not retrieve the required installation files
04-26 12:05 DEBUG  TaskList: # Cancelling tasklist
04-26 12:05 DEBUG  TaskList: # Finished tasklist
04-26 12:12 INFO   root: === wubi 9.04 rev129 ===
04-26 12:12 DEBUG  root: Logfile is c:\docume~1\jordan\locals~1\temp\wubi-9.04-rev129.log
04-26 12:12 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\DOCUME~1\\Jordan\\LOCALS~1\\Temp\\6lup8p0t.tmp\\wubi.exe"']
04-26 12:12 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8B.tmp\data
04-26 12:12 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8B.tmp\bin\7z.exe
04-26 12:12 DEBUG  CommonBackend: Fetching basic info...
04-26 12:12 DEBUG  CommonBackend: original_exe=C:\DOCUME~1\Jordan\LOCALS~1\Temp\6lup8p0t.tmp\wubi.exe
04-26 12:12 DEBUG  CommonBackend: platform=win32
04-26 12:12 DEBUG  CommonBackend: osname=nt
04-26 12:12 DEBUG  CommonBackend: language=en_GB
04-26 12:12 DEBUG  CommonBackend: encoding=cp1252
04-26 12:12 DEBUG  WindowsBackend: arch=i386
04-26 12:12 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8B.tmp\data\isolist.ini
04-26 12:12 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-26 12:12 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-26 12:12 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-26 12:12 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-26 12:12 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-26 12:12 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-26 12:12 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-26 12:12 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-26 12:12 DEBUG  WindowsBackend: Fetching host info...
04-26 12:12 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-26 12:12 DEBUG  WindowsBackend: windows version=xp
04-26 12:12 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-26 12:12 DEBUG  WindowsBackend: windows_sp=Service Pack 3
04-26 12:12 DEBUG  WindowsBackend: windows_build=2600
04-26 12:12 DEBUG  WindowsBackend: gmt=0
04-26 12:12 DEBUG  WindowsBackend: country=GB
04-26 12:12 DEBUG  WindowsBackend: timezone=Europe/London
04-26 12:12 DEBUG  WindowsBackend: windows_username=Jordan
04-26 12:12 DEBUG  WindowsBackend: user_full_name=Jordan
04-26 12:12 DEBUG  WindowsBackend: user_directory=Jordan
04-26 12:12 DEBUG  WindowsBackend: windows_language_code=1033
04-26 12:12 DEBUG  WindowsBackend: windows_language=English
04-26 12:12 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
04-26 12:12 DEBUG  WindowsBackend: bootloader=xp
04-26 12:12 DEBUG  WindowsBackend: system_drive=Drive(C: hd 33070.578125 mb free )
04-26 12:12 DEBUG  WindowsBackend: drive=Drive(C: hd 33070.578125 mb free )
04-26 12:12 DEBUG  WindowsBackend: drive=Drive(D: hd 44574.390625 mb free ntfs)
04-26 12:12 DEBUG  WindowsBackend: drive=Drive(E: hd 6121.09375 mb free fat32)
04-26 12:12 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free udf)
04-26 12:12 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
04-26 12:12 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
04-26 12:12 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
04-26 12:12 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-26 12:12 DEBUG  WindowsBackend: keyboard_id=134809609
04-26 12:12 DEBUG  WindowsBackend: keyboard_layout=gb
04-26 12:12 DEBUG  WindowsBackend: keyboard_variant=
04-26 12:12 DEBUG  CommonBackend: locale=en_GB.UTF-8
04-26 12:12 DEBUG  WindowsBackend: total_memory_mb=511.484375
04-26 12:12 DEBUG  CommonBackend: Searching ISOs on USB devices
04-26 12:12 DEBUG  CommonBackend: Searching for local CDs
04-26 12:12 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8B.tmp is a valid Ubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8B.tmp\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8B.tmp is a valid Ubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8B.tmp\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8B.tmp is a valid Kubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8B.tmp\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8B.tmp is a valid Kubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8B.tmp\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8B.tmp is a valid Xubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8B.tmp\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8B.tmp is a valid Xubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8B.tmp\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8B.tmp is a valid Mythbuntu CD
04-26 12:12 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8B.tmp\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8B.tmp is a valid Mythbuntu CD
04-26 12:12 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8B.tmp\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 12:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 12:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-26 12:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-26 12:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-26 12:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-26 12:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-26 12:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-26 12:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 12:12 INFO   root: Already installed, running the uninstaller...
04-26 12:12 INFO   root: Running the uninstaller...
04-26 12:12 INFO   CommonBackend: This is the uninstaller running
04-26 12:12 DEBUG  WindowsFrontend: __init__...
04-26 12:12 DEBUG  WindowsFrontend: on_init...
04-26 12:12 INFO   root: Received settings
04-26 12:12 DEBUG  TaskList: # Running tasklist...
04-26 12:12 DEBUG  TaskList: ## Running Backup ISO...
04-26 12:12 DEBUG  TaskList: ## Finished Backup ISO
04-26 12:12 DEBUG  TaskList: ## Running Remove bootloader entry...
04-26 12:12 ERROR  WindowsBackend: Cannot find bcdedit
04-26 12:12 DEBUG  WindowsBackend: undo_bootini C:
04-26 12:12 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 33070.578125 mb free )
04-26 12:12 DEBUG  WindowsBackend: undo_bootini D:
04-26 12:12 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 44574.390625 mb free ntfs)
04-26 12:12 DEBUG  WindowsBackend: undo_bootini E:
04-26 12:12 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 6121.09375 mb free fat32)
04-26 12:12 DEBUG  TaskList: ## Finished Remove bootloader entry
04-26 12:12 DEBUG  TaskList: ## Running Remove target dir...
04-26 12:12 DEBUG  CommonBackend: Deleting D:\ubuntu
04-26 12:12 DEBUG  TaskList: ## Finished Remove target dir
04-26 12:12 DEBUG  TaskList: ## Running Remove registry key...
04-26 12:12 DEBUG  TaskList: ## Finished Remove registry key
04-26 12:12 DEBUG  TaskList: # Finished tasklist
04-26 12:12 INFO   root: Almost finished uninstalling
04-26 12:12 INFO   root: Finished uninstallation
04-26 12:12 DEBUG  CommonBackend: Fetching basic info...
04-26 12:12 DEBUG  CommonBackend: original_exe=C:\DOCUME~1\Jordan\LOCALS~1\Temp\6lup8p0t.tmp\wubi.exe
04-26 12:12 DEBUG  CommonBackend: platform=win32
04-26 12:12 DEBUG  CommonBackend: osname=nt
04-26 12:12 DEBUG  CommonBackend: language=en_GB
04-26 12:12 DEBUG  CommonBackend: encoding=cp1252
04-26 12:12 DEBUG  WindowsBackend: arch=i386
04-26 12:12 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8B.tmp\data\isolist.ini
04-26 12:12 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-26 12:12 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-26 12:12 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-26 12:12 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-26 12:12 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-26 12:12 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-26 12:12 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-26 12:12 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-26 12:12 DEBUG  WindowsBackend: Fetching host info...
04-26 12:12 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-26 12:12 DEBUG  WindowsBackend: windows version=xp
04-26 12:12 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-26 12:12 DEBUG  WindowsBackend: windows_sp=Service Pack 3
04-26 12:12 DEBUG  WindowsBackend: windows_build=2600
04-26 12:12 DEBUG  WindowsBackend: gmt=0
04-26 12:12 DEBUG  WindowsBackend: country=GB
04-26 12:12 DEBUG  WindowsBackend: timezone=Europe/London
04-26 12:12 DEBUG  WindowsBackend: windows_username=Jordan
04-26 12:12 DEBUG  WindowsBackend: user_full_name=Jordan
04-26 12:12 DEBUG  WindowsBackend: user_directory=Jordan
04-26 12:12 DEBUG  WindowsBackend: windows_language_code=1033
04-26 12:12 DEBUG  WindowsBackend: windows_language=English
04-26 12:12 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
04-26 12:12 DEBUG  WindowsBackend: bootloader=xp
04-26 12:12 DEBUG  WindowsBackend: system_drive=Drive(C: hd 33070.5664063 mb free )
04-26 12:12 DEBUG  WindowsBackend: drive=Drive(C: hd 33070.5664063 mb free )
04-26 12:12 DEBUG  WindowsBackend: drive=Drive(D: hd 44576.3320313 mb free ntfs)
04-26 12:12 DEBUG  WindowsBackend: drive=Drive(E: hd 6121.09375 mb free fat32)
04-26 12:12 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free udf)
04-26 12:12 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
04-26 12:12 DEBUG  WindowsBackend: uninstaller_path=None
04-26 12:12 DEBUG  WindowsBackend: previous_target_dir=None
04-26 12:12 DEBUG  WindowsBackend: previous_distro_name=None
04-26 12:12 DEBUG  WindowsBackend: keyboard_id=134809609
04-26 12:12 DEBUG  WindowsBackend: keyboard_layout=gb
04-26 12:12 DEBUG  WindowsBackend: keyboard_variant=
04-26 12:12 DEBUG  CommonBackend: locale=en_GB.UTF-8
04-26 12:12 DEBUG  WindowsBackend: total_memory_mb=511.484375
04-26 12:12 DEBUG  CommonBackend: Searching ISOs on USB devices
04-26 12:12 DEBUG  CommonBackend: Searching for local CDs
04-26 12:12 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8B.tmp is a valid Ubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8B.tmp\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8B.tmp is a valid Ubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8B.tmp\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8B.tmp is a valid Kubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8B.tmp\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8B.tmp is a valid Kubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8B.tmp\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8B.tmp is a valid Xubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8B.tmp\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8B.tmp is a valid Xubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8B.tmp\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8B.tmp is a valid Mythbuntu CD
04-26 12:12 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8B.tmp\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8B.tmp is a valid Mythbuntu CD
04-26 12:12 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8B.tmp\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 12:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 12:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-26 12:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-26 12:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-26 12:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-26 12:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-26 12:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-26 12:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 12:12 INFO   root: Running the installer...
04-26 12:12 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=English, username=jordan
04-26 12:12 INFO   root: Received settings
04-26 12:12 DEBUG  TaskList: # Running tasklist...
04-26 12:12 DEBUG  TaskList: ## Running select_target_dir...
04-26 12:12 INFO   WindowsBackend: Installing into C:\ubuntu
04-26 12:12 DEBUG  TaskList: ## Finished select_target_dir
04-26 12:12 DEBUG  TaskList: ## Running create_dir_structure...
04-26 12:12 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-26 12:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-26 12:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-26 12:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-26 12:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-26 12:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-26 12:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-26 12:12 DEBUG  TaskList: ## Finished create_dir_structure
04-26 12:12 DEBUG  TaskList: ## Running uncompress_target_dir...
04-26 12:12 DEBUG  TaskList: ## Finished uncompress_target_dir
04-26 12:12 DEBUG  TaskList: ## Running create_uninstaller...
04-26 12:12 DEBUG  WindowsBackend: Copying uninstaller C:\DOCUME~1\Jordan\LOCALS~1\Temp\6lup8p0t.tmp\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-26 12:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-26 12:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-26 12:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-26 12:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-26 12:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev129
04-26 12:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-26 12:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-26 12:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-26 12:12 DEBUG  TaskList: ## Finished create_uninstaller
04-26 12:12 DEBUG  TaskList: ## Running copy_installation_files...
04-26 12:12 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8B.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-26 12:12 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8B.tmp\winboot -> C:\ubuntu\winboot
04-26 12:12 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8B.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-26 12:12 DEBUG  TaskList: ## Finished copy_installation_files
04-26 12:12 DEBUG  TaskList: ## Running get_iso...
04-26 12:12 DEBUG  CommonBackend: Searching for local CD
04-26 12:12 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8B.tmp is a valid Ubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl8B.tmp\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 12:12 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-26 12:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 12:12 DEBUG  CommonBackend: Searching for local ISO
04-26 12:12 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
04-26 12:12 DEBUG  TaskList: New task get_metalink
04-26 12:12 DEBUG  TaskList: ### Running get_metalink...
04-26 12:12 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink](http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink) > C:\ubuntu\install
04-26 12:12 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-9.04-desktop-i386.metalink, url=http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink, basename=ubuntu-9.04-desktop-i386.metalink, length=19438, text=None
04-26 12:12 DEBUG  downloader: download finished (read 19438 bytes)
04-26 12:12 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.04/MD5SUMS-metalink](http://releases.ubuntu.com/9.04/MD5SUMS-metalink) > C:\ubuntu\install
04-26 12:12 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/9.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=487, text=None
04-26 12:12 DEBUG  downloader: download finished (read 487 bytes)
04-26 12:12 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/9.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
04-26 12:12 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/9.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
04-26 12:12 DEBUG  downloader: download finished (read 189 bytes)
04-26 12:12 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
04-26 12:12 INFO   saplog: Checking block bindings..
04-26 12:12 INFO   saplog: Key verified successfully.
04-26 12:12 DEBUG  CommonBackend: metalink md5sums:
1ec553ada3a4a18fb977816ccac02dfc  ubuntu-9.04-alternate-amd64.metalink
5daf9cb57325672f0eb768d6c11888e8  ubuntu-9.04-alternate-i386.metalink
3df58e889d3613abc2347a6b0e8f4d04  ubuntu-9.04-desktop-amd64.metalink
542bc6d7988f1d2967d419c089b08f57  ubuntu-9.04-desktop-i386.metalink
ffd21294d807046e22589b966b134d2d  ubuntu-9.04-netbook-remix-i386.metalink
ea0b13f00711ef4b2e5c772482033a1f  ubuntu-9.04-server-amd64.metalink
88e47c579eb587c8aae1a7d7737ab3f0  ubuntu-9.04-server-i386.metalink

04-26 12:12 DEBUG  TaskList: ### Finished get_metalink
04-26 12:12 DEBUG  TaskList: New task download
04-26 12:12 DEBUG  TaskList: ### Running download...
04-26 12:12 DEBUG  downloader: downloading [http://de.archive.ubuntu.com/ubuntu-releases/9.04/ubuntu-9.04-desktop-i386.iso](http://de.archive.ubuntu.com/ubuntu-releases/9.04/ubuntu-9.04-desktop-i386.iso) > C:\ubuntu\install\ubuntu-9.04-desktop-i386.iso
04-26 12:12 ERROR  TaskList: [Errno 4] IOError: <urlopen error <html>

>
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\downloader.py", line 79, in download
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\urlgrabber\grabber.py", line 845, in _retry
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\urlgrabber\grabber.py", line 913, in retryfunc
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\urlgrabber\grabber.py", line 1001, in __init__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\urlgrabber\grabber.py", line 1072, in _do_open
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\urlgrabber\grabber.py", line 1188, in _make_request
URLGrabError: [Errno 4] IOError: <urlopen error <html>

>
04-26 12:12 DEBUG  TaskList: # Cancelling tasklist
04-26 12:12 ERROR  root: [Errno 4] IOError: <urlopen error <html>

>
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 129, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
URLGrabError: [Errno 4] IOError: <urlopen error <html>

>
04-26 12:12 DEBUG  TaskList: New task download
04-26 12:12 DEBUG  TaskList: New task download
04-26 12:12 DEBUG  TaskList: New task download
04-26 12:12 DEBUG  TaskList: New task download
04-26 12:12 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 487, in get_iso
Exception: Could not retrieve the required installation files
04-26 12:12 DEBUG  TaskList: # Cancelling tasklist
04-26 12:12 DEBUG  TaskList: # Finished tasklist
04-26 13:15 INFO   root: === wubi 9.04 rev129 ===
04-26 13:15 DEBUG  root: Logfile is c:\docume~1\jordan\locals~1\temp\wubi-9.04-rev129.log
04-26 13:15 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\DOCUME~1\\Jordan\\LOCALS~1\\Temp\\6lup8p0t.tmp\\wubi.exe"']
04-26 13:15 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF4.tmp\data
04-26 13:15 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF4.tmp\bin\7z.exe
04-26 13:15 DEBUG  CommonBackend: Fetching basic info...
04-26 13:15 DEBUG  CommonBackend: original_exe=C:\DOCUME~1\Jordan\LOCALS~1\Temp\6lup8p0t.tmp\wubi.exe
04-26 13:15 DEBUG  CommonBackend: platform=win32
04-26 13:15 DEBUG  CommonBackend: osname=nt
04-26 13:15 DEBUG  CommonBackend: language=en_GB
04-26 13:15 DEBUG  CommonBackend: encoding=cp1252
04-26 13:15 DEBUG  WindowsBackend: arch=i386
04-26 13:15 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF4.tmp\data\isolist.ini
04-26 13:15 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-26 13:15 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-26 13:15 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-26 13:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-26 13:15 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-26 13:15 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-26 13:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-26 13:15 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-26 13:15 DEBUG  WindowsBackend: Fetching host info...
04-26 13:15 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-26 13:15 DEBUG  WindowsBackend: windows version=xp
04-26 13:15 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-26 13:15 DEBUG  WindowsBackend: windows_sp=Service Pack 3
04-26 13:15 DEBUG  WindowsBackend: windows_build=2600
04-26 13:15 DEBUG  WindowsBackend: gmt=0
04-26 13:15 DEBUG  WindowsBackend: country=GB
04-26 13:15 DEBUG  WindowsBackend: timezone=Europe/London
04-26 13:15 DEBUG  WindowsBackend: windows_username=Jordan
04-26 13:15 DEBUG  WindowsBackend: user_full_name=Jordan
04-26 13:15 DEBUG  WindowsBackend: user_directory=Jordan
04-26 13:15 DEBUG  WindowsBackend: windows_language_code=1033
04-26 13:15 DEBUG  WindowsBackend: windows_language=English
04-26 13:15 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
04-26 13:15 DEBUG  WindowsBackend: bootloader=xp
04-26 13:15 DEBUG  WindowsBackend: system_drive=Drive(C: hd 33005.828125 mb free )
04-26 13:15 DEBUG  WindowsBackend: drive=Drive(C: hd 33005.828125 mb free )
04-26 13:15 DEBUG  WindowsBackend: drive=Drive(D: hd 44576.3320313 mb free ntfs)
04-26 13:15 DEBUG  WindowsBackend: drive=Drive(E: hd 6121.09375 mb free fat32)
04-26 13:15 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free udf)
04-26 13:15 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
04-26 13:15 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-26 13:15 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-26 13:15 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-26 13:15 DEBUG  WindowsBackend: keyboard_id=134809609
04-26 13:15 DEBUG  WindowsBackend: keyboard_layout=gb
04-26 13:15 DEBUG  WindowsBackend: keyboard_variant=
04-26 13:15 DEBUG  CommonBackend: locale=en_GB.UTF-8
04-26 13:15 DEBUG  WindowsBackend: total_memory_mb=511.484375
04-26 13:15 DEBUG  CommonBackend: Searching ISOs on USB devices
04-26 13:15 DEBUG  CommonBackend: Searching for local CDs
04-26 13:15 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF4.tmp is a valid Ubuntu CD
04-26 13:15 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF4.tmp\casper\filesystem.squashfs
04-26 13:15 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF4.tmp is a valid Ubuntu CD
04-26 13:15 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF4.tmp\casper\filesystem.squashfs
04-26 13:15 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF4.tmp is a valid Kubuntu CD
04-26 13:15 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF4.tmp\casper\filesystem.squashfs
04-26 13:15 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF4.tmp is a valid Kubuntu CD
04-26 13:15 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF4.tmp\casper\filesystem.squashfs
04-26 13:15 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF4.tmp is a valid Xubuntu CD
04-26 13:15 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF4.tmp\casper\filesystem.squashfs
04-26 13:15 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF4.tmp is a valid Xubuntu CD
04-26 13:15 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF4.tmp\casper\filesystem.squashfs
04-26 13:15 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF4.tmp is a valid Mythbuntu CD
04-26 13:15 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF4.tmp\casper\filesystem.squashfs
04-26 13:15 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF4.tmp is a valid Mythbuntu CD
04-26 13:15 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF4.tmp\casper\filesystem.squashfs
04-26 13:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 13:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 13:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:15 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 13:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:15 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 13:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:15 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 13:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:15 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 13:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:15 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 13:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:15 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 13:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:15 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-26 13:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:15 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-26 13:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:15 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-26 13:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:15 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-26 13:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:15 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-26 13:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:15 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-26 13:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:15 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-26 13:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:15 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-26 13:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:15 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-26 13:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:15 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-26 13:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:15 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-26 13:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:15 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-26 13:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:15 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-26 13:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:15 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-26 13:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:15 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-26 13:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:15 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-26 13:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:15 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-26 13:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:15 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-26 13:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:15 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-26 13:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:15 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-26 13:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:15 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-26 13:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:15 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-26 13:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:15 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-26 13:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:15 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-26 13:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:15 INFO   root: Already installed, running the uninstaller...
04-26 13:15 INFO   root: Running the uninstaller...
04-26 13:15 INFO   CommonBackend: This is the uninstaller running
04-26 13:15 DEBUG  WindowsFrontend: __init__...
04-26 13:15 DEBUG  WindowsFrontend: on_init...
04-26 13:15 INFO   root: Received settings
04-26 13:15 DEBUG  TaskList: # Running tasklist...
04-26 13:15 DEBUG  TaskList: ## Running Backup ISO...
04-26 13:15 DEBUG  TaskList: ## Finished Backup ISO
04-26 13:15 DEBUG  TaskList: ## Running Remove bootloader entry...
04-26 13:15 ERROR  WindowsBackend: Cannot find bcdedit
04-26 13:15 DEBUG  WindowsBackend: undo_bootini C:
04-26 13:15 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 33005.828125 mb free )
04-26 13:15 DEBUG  WindowsBackend: undo_bootini D:
04-26 13:15 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 44576.3320313 mb free ntfs)
04-26 13:15 DEBUG  WindowsBackend: undo_bootini E:
04-26 13:15 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 6121.09375 mb free fat32)
04-26 13:15 DEBUG  TaskList: ## Finished Remove bootloader entry
04-26 13:15 DEBUG  TaskList: ## Running Remove target dir...
04-26 13:15 DEBUG  CommonBackend: Deleting C:\ubuntu
04-26 13:16 DEBUG  TaskList: ## Finished Remove target dir
04-26 13:16 DEBUG  TaskList: ## Running Remove registry key...
04-26 13:16 DEBUG  TaskList: ## Finished Remove registry key
04-26 13:16 DEBUG  TaskList: # Finished tasklist
04-26 13:16 INFO   root: Almost finished uninstalling
04-26 13:16 INFO   root: Finished uninstallation
04-26 13:16 DEBUG  CommonBackend: Fetching basic info...
04-26 13:16 DEBUG  CommonBackend: original_exe=C:\DOCUME~1\Jordan\LOCALS~1\Temp\6lup8p0t.tmp\wubi.exe
04-26 13:16 DEBUG  CommonBackend: platform=win32
04-26 13:16 DEBUG  CommonBackend: osname=nt
04-26 13:16 DEBUG  CommonBackend: language=en_GB
04-26 13:16 DEBUG  CommonBackend: encoding=cp1252
04-26 13:16 DEBUG  WindowsBackend: arch=i386
04-26 13:16 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF4.tmp\data\isolist.ini
04-26 13:16 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-26 13:16 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-26 13:16 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-26 13:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-26 13:16 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-26 13:16 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-26 13:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-26 13:16 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-26 13:16 DEBUG  WindowsBackend: Fetching host info...
04-26 13:16 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-26 13:16 DEBUG  WindowsBackend: windows version=xp
04-26 13:16 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-26 13:16 DEBUG  WindowsBackend: windows_sp=Service Pack 3
04-26 13:16 DEBUG  WindowsBackend: windows_build=2600
04-26 13:16 DEBUG  WindowsBackend: gmt=0
04-26 13:16 DEBUG  WindowsBackend: country=GB
04-26 13:16 DEBUG  WindowsBackend: timezone=Europe/London
04-26 13:16 DEBUG  WindowsBackend: windows_username=Jordan
04-26 13:16 DEBUG  WindowsBackend: user_full_name=Jordan
04-26 13:16 DEBUG  WindowsBackend: user_directory=Jordan
04-26 13:16 DEBUG  WindowsBackend: windows_language_code=1033
04-26 13:16 DEBUG  WindowsBackend: windows_language=English
04-26 13:16 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
04-26 13:16 DEBUG  WindowsBackend: bootloader=xp
04-26 13:16 DEBUG  WindowsBackend: system_drive=Drive(C: hd 33007.7539063 mb free )
04-26 13:16 DEBUG  WindowsBackend: drive=Drive(C: hd 33007.7539063 mb free )
04-26 13:16 DEBUG  WindowsBackend: drive=Drive(D: hd 44576.3320313 mb free ntfs)
04-26 13:16 DEBUG  WindowsBackend: drive=Drive(E: hd 6121.09375 mb free fat32)
04-26 13:16 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free udf)
04-26 13:16 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
04-26 13:16 DEBUG  WindowsBackend: uninstaller_path=None
04-26 13:16 DEBUG  WindowsBackend: previous_target_dir=None
04-26 13:16 DEBUG  WindowsBackend: previous_distro_name=None
04-26 13:16 DEBUG  WindowsBackend: keyboard_id=134809609
04-26 13:16 DEBUG  WindowsBackend: keyboard_layout=gb
04-26 13:16 DEBUG  WindowsBackend: keyboard_variant=
04-26 13:16 DEBUG  CommonBackend: locale=en_GB.UTF-8
04-26 13:16 DEBUG  WindowsBackend: total_memory_mb=511.484375
04-26 13:16 DEBUG  CommonBackend: Searching ISOs on USB devices
04-26 13:16 DEBUG  CommonBackend: Searching for local CDs
04-26 13:16 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF4.tmp is a valid Ubuntu CD
04-26 13:16 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF4.tmp\casper\filesystem.squashfs
04-26 13:16 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF4.tmp is a valid Ubuntu CD
04-26 13:16 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF4.tmp\casper\filesystem.squashfs
04-26 13:16 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF4.tmp is a valid Kubuntu CD
04-26 13:16 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF4.tmp\casper\filesystem.squashfs
04-26 13:16 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF4.tmp is a valid Kubuntu CD
04-26 13:16 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF4.tmp\casper\filesystem.squashfs
04-26 13:16 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF4.tmp is a valid Xubuntu CD
04-26 13:16 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF4.tmp\casper\filesystem.squashfs
04-26 13:16 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF4.tmp is a valid Xubuntu CD
04-26 13:16 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF4.tmp\casper\filesystem.squashfs
04-26 13:16 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF4.tmp is a valid Mythbuntu CD
04-26 13:16 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF4.tmp\casper\filesystem.squashfs
04-26 13:16 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF4.tmp is a valid Mythbuntu CD
04-26 13:16 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF4.tmp\casper\filesystem.squashfs
04-26 13:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 13:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 13:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 13:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 13:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:16 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 13:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:16 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 13:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:16 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 13:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:16 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 13:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-26 13:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-26 13:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:16 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-26 13:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:16 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-26 13:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:16 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-26 13:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:16 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-26 13:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:16 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-26 13:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:16 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-26 13:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:16 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-26 13:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:16 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-26 13:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:16 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-26 13:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:16 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-26 13:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:16 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-26 13:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:16 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-26 13:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:16 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-26 13:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:16 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-26 13:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:16 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-26 13:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:16 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-26 13:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:16 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-26 13:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:16 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-26 13:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:16 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-26 13:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:16 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-26 13:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:16 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-26 13:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:16 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-26 13:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:16 INFO   root: Running the installer...
04-26 13:19 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=English, username=jordan
04-26 13:19 INFO   root: Received settings
04-26 13:19 DEBUG  TaskList: # Running tasklist...
04-26 13:19 DEBUG  TaskList: ## Running select_target_dir...
04-26 13:19 INFO   WindowsBackend: Installing into C:\ubuntu
04-26 13:19 DEBUG  TaskList: ## Finished select_target_dir
04-26 13:19 DEBUG  TaskList: ## Running create_dir_structure...
04-26 13:19 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-26 13:19 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-26 13:19 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-26 13:19 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-26 13:19 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-26 13:19 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-26 13:19 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-26 13:19 DEBUG  TaskList: ## Finished create_dir_structure
04-26 13:19 DEBUG  TaskList: ## Running uncompress_target_dir...
04-26 13:19 DEBUG  TaskList: ## Finished uncompress_target_dir
04-26 13:19 DEBUG  TaskList: ## Running create_uninstaller...
04-26 13:19 DEBUG  WindowsBackend: Copying uninstaller C:\DOCUME~1\Jordan\LOCALS~1\Temp\6lup8p0t.tmp\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-26 13:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-26 13:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-26 13:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-26 13:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-26 13:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev129
04-26 13:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-26 13:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-26 13:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-26 13:19 DEBUG  TaskList: ## Finished create_uninstaller
04-26 13:19 DEBUG  TaskList: ## Running copy_installation_files...
04-26 13:19 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF4.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-26 13:19 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF4.tmp\winboot -> C:\ubuntu\winboot
04-26 13:19 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF4.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-26 13:19 DEBUG  TaskList: ## Finished copy_installation_files
04-26 13:19 DEBUG  TaskList: ## Running get_iso...
04-26 13:19 DEBUG  CommonBackend: Searching for local CD
04-26 13:19 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF4.tmp is a valid Ubuntu CD
04-26 13:19 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF4.tmp\casper\filesystem.squashfs
04-26 13:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 13:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-26 13:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:19 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-26 13:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:19 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-26 13:19 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:19 DEBUG  CommonBackend: Searching for local ISO
04-26 13:19 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
04-26 13:19 DEBUG  TaskList: New task get_metalink
04-26 13:19 DEBUG  TaskList: ### Running get_metalink...
04-26 13:19 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink](http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink) > C:\ubuntu\install
04-26 13:20 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink](http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (10061, 'Connection refused')>
04-26 13:20 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/jaunty-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/jaunty-desktop-i386.metalink) > C:\ubuntu\install
04-26 13:20 DEBUG  downloader: Download start filename=C:\ubuntu\install\jaunty-desktop-i386.metalink, url=http://cdimage.ubuntu.com/daily-live/current/jaunty-desktop-i386.metalink, basename=jaunty-desktop-i386.metalink, length=999, text=None
04-26 13:20 DEBUG  downloader: download finished (read 999 bytes)
04-26 13:20 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink](http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink) > C:\ubuntu\install
04-26 13:20 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=127, text=None
04-26 13:20 DEBUG  downloader: download finished (read 127 bytes)
04-26 13:20 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink.gpg](http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink.gpg) > C:\ubuntu\install
04-26 13:21 ERROR  TaskList: [Errno 4] IOError: <urlopen error (10061, 'Connection refused')>
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 373, in get_metalink
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 242, in check_metalink
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\downloader.py", line 79, in download
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\urlgrabber\grabber.py", line 845, in _retry
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\urlgrabber\grabber.py", line 913, in retryfunc
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\urlgrabber\grabber.py", line 1001, in __init__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\urlgrabber\grabber.py", line 1072, in _do_open
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\urlgrabber\grabber.py", line 1188, in _make_request
URLGrabError: [Errno 4] IOError: <urlopen error (10061, 'Connection refused')>
04-26 13:21 DEBUG  TaskList: # Cancelling tasklist
04-26 13:21 ERROR  root: [Errno 4] IOError: <urlopen error (10061, 'Connection refused')>
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 129, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
URLGrabError: [Errno 4] IOError: <urlopen error (10061, 'Connection refused')>
04-26 13:21 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
04-26 13:21 DEBUG  TaskList: # Cancelling tasklist
04-26 13:21 DEBUG  TaskList: # Finished tasklist
04-26 13:22 INFO   root: === wubi 9.04 rev129 ===
04-26 13:22 DEBUG  root: Logfile is c:\docume~1\jordan\locals~1\temp\wubi-9.04-rev129.log
04-26 13:22 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\DOCUME~1\\Jordan\\LOCALS~1\\Temp\\6lup8p0t.tmp\\wubi.exe"']
04-26 13:22 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF9.tmp\data
04-26 13:22 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF9.tmp\bin\7z.exe
04-26 13:22 DEBUG  CommonBackend: Fetching basic info...
04-26 13:22 DEBUG  CommonBackend: original_exe=C:\DOCUME~1\Jordan\LOCALS~1\Temp\6lup8p0t.tmp\wubi.exe
04-26 13:22 DEBUG  CommonBackend: platform=win32
04-26 13:22 DEBUG  CommonBackend: osname=nt
04-26 13:22 DEBUG  CommonBackend: language=en_GB
04-26 13:22 DEBUG  CommonBackend: encoding=cp1252
04-26 13:22 DEBUG  WindowsBackend: arch=i386
04-26 13:22 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF9.tmp\data\isolist.ini
04-26 13:22 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-26 13:22 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-26 13:22 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-26 13:22 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-26 13:22 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-26 13:22 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-26 13:22 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-26 13:22 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-26 13:22 DEBUG  WindowsBackend: Fetching host info...
04-26 13:22 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-26 13:22 DEBUG  WindowsBackend: windows version=xp
04-26 13:22 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-26 13:22 DEBUG  WindowsBackend: windows_sp=Service Pack 3
04-26 13:22 DEBUG  WindowsBackend: windows_build=2600
04-26 13:22 DEBUG  WindowsBackend: gmt=0
04-26 13:22 DEBUG  WindowsBackend: country=GB
04-26 13:22 DEBUG  WindowsBackend: timezone=Europe/London
04-26 13:22 DEBUG  WindowsBackend: windows_username=Jordan
04-26 13:22 DEBUG  WindowsBackend: user_full_name=Jordan
04-26 13:22 DEBUG  WindowsBackend: user_directory=Jordan
04-26 13:22 DEBUG  WindowsBackend: windows_language_code=1033
04-26 13:22 DEBUG  WindowsBackend: windows_language=English
04-26 13:22 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
04-26 13:22 DEBUG  WindowsBackend: bootloader=xp
04-26 13:22 DEBUG  WindowsBackend: system_drive=Drive(C: hd 33005.1914063 mb free )
04-26 13:22 DEBUG  WindowsBackend: drive=Drive(C: hd 33005.1914063 mb free )
04-26 13:22 DEBUG  WindowsBackend: drive=Drive(D: hd 44576.3320313 mb free ntfs)
04-26 13:22 DEBUG  WindowsBackend: drive=Drive(E: hd 6121.09375 mb free fat32)
04-26 13:22 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free udf)
04-26 13:22 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
04-26 13:22 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-26 13:22 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-26 13:22 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-26 13:22 DEBUG  WindowsBackend: keyboard_id=134809609
04-26 13:22 DEBUG  WindowsBackend: keyboard_layout=gb
04-26 13:22 DEBUG  WindowsBackend: keyboard_variant=
04-26 13:22 DEBUG  CommonBackend: locale=en_GB.UTF-8
04-26 13:22 DEBUG  WindowsBackend: total_memory_mb=511.484375
04-26 13:22 DEBUG  CommonBackend: Searching ISOs on USB devices
04-26 13:22 DEBUG  CommonBackend: Searching for local CDs
04-26 13:22 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF9.tmp is a valid Ubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF9.tmp\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF9.tmp is a valid Ubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF9.tmp\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF9.tmp is a valid Kubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF9.tmp\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF9.tmp is a valid Kubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF9.tmp\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF9.tmp is a valid Xubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF9.tmp\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF9.tmp is a valid Xubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF9.tmp\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF9.tmp is a valid Mythbuntu CD
04-26 13:22 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF9.tmp\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF9.tmp is a valid Mythbuntu CD
04-26 13:22 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF9.tmp\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 13:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 13:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-26 13:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-26 13:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-26 13:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-26 13:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-26 13:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-26 13:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:22 INFO   root: Already installed, running the uninstaller...
04-26 13:22 INFO   root: Running the uninstaller...
04-26 13:22 INFO   CommonBackend: This is the uninstaller running
04-26 13:22 DEBUG  WindowsFrontend: __init__...
04-26 13:22 DEBUG  WindowsFrontend: on_init...
04-26 13:22 INFO   root: Received settings
04-26 13:22 DEBUG  TaskList: # Running tasklist...
04-26 13:22 DEBUG  TaskList: ## Running Backup ISO...
04-26 13:22 DEBUG  TaskList: ## Finished Backup ISO
04-26 13:22 DEBUG  TaskList: ## Running Remove bootloader entry...
04-26 13:22 ERROR  WindowsBackend: Cannot find bcdedit
04-26 13:22 DEBUG  WindowsBackend: undo_bootini C:
04-26 13:22 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 33005.1914063 mb free )
04-26 13:22 DEBUG  WindowsBackend: undo_bootini D:
04-26 13:22 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 44576.3320313 mb free ntfs)
04-26 13:22 DEBUG  WindowsBackend: undo_bootini E:
04-26 13:22 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 6121.09375 mb free fat32)
04-26 13:22 DEBUG  TaskList: ## Finished Remove bootloader entry
04-26 13:22 DEBUG  TaskList: ## Running Remove target dir...
04-26 13:22 DEBUG  CommonBackend: Deleting C:\ubuntu
04-26 13:22 DEBUG  TaskList: ## Finished Remove target dir
04-26 13:22 DEBUG  TaskList: ## Running Remove registry key...
04-26 13:22 DEBUG  TaskList: ## Finished Remove registry key
04-26 13:22 DEBUG  TaskList: # Finished tasklist
04-26 13:22 INFO   root: Almost finished uninstalling
04-26 13:22 INFO   root: Finished uninstallation
04-26 13:22 DEBUG  CommonBackend: Fetching basic info...
04-26 13:22 DEBUG  CommonBackend: original_exe=C:\DOCUME~1\Jordan\LOCALS~1\Temp\6lup8p0t.tmp\wubi.exe
04-26 13:22 DEBUG  CommonBackend: platform=win32
04-26 13:22 DEBUG  CommonBackend: osname=nt
04-26 13:22 DEBUG  CommonBackend: language=en_GB
04-26 13:22 DEBUG  CommonBackend: encoding=cp1252
04-26 13:22 DEBUG  WindowsBackend: arch=i386
04-26 13:22 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF9.tmp\data\isolist.ini
04-26 13:22 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-26 13:22 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-26 13:22 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-26 13:22 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-26 13:22 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-26 13:22 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-26 13:22 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-26 13:22 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-26 13:22 DEBUG  WindowsBackend: Fetching host info...
04-26 13:22 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-26 13:22 DEBUG  WindowsBackend: windows version=xp
04-26 13:22 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-26 13:22 DEBUG  WindowsBackend: windows_sp=Service Pack 3
04-26 13:22 DEBUG  WindowsBackend: windows_build=2600
04-26 13:22 DEBUG  WindowsBackend: gmt=0
04-26 13:22 DEBUG  WindowsBackend: country=GB
04-26 13:22 DEBUG  WindowsBackend: timezone=Europe/London
04-26 13:22 DEBUG  WindowsBackend: windows_username=Jordan
04-26 13:22 DEBUG  WindowsBackend: user_full_name=Jordan
04-26 13:22 DEBUG  WindowsBackend: user_directory=Jordan
04-26 13:22 DEBUG  WindowsBackend: windows_language_code=1033
04-26 13:22 DEBUG  WindowsBackend: windows_language=English
04-26 13:22 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
04-26 13:22 DEBUG  WindowsBackend: bootloader=xp
04-26 13:22 DEBUG  WindowsBackend: system_drive=Drive(C: hd 33007.09375 mb free )
04-26 13:22 DEBUG  WindowsBackend: drive=Drive(C: hd 33007.09375 mb free )
04-26 13:22 DEBUG  WindowsBackend: drive=Drive(D: hd 44576.3320313 mb free ntfs)
04-26 13:22 DEBUG  WindowsBackend: drive=Drive(E: hd 6121.09375 mb free fat32)
04-26 13:22 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free udf)
04-26 13:22 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
04-26 13:22 DEBUG  WindowsBackend: uninstaller_path=None
04-26 13:22 DEBUG  WindowsBackend: previous_target_dir=None
04-26 13:22 DEBUG  WindowsBackend: previous_distro_name=None
04-26 13:22 DEBUG  WindowsBackend: keyboard_id=134809609
04-26 13:22 DEBUG  WindowsBackend: keyboard_layout=gb
04-26 13:22 DEBUG  WindowsBackend: keyboard_variant=
04-26 13:22 DEBUG  CommonBackend: locale=en_GB.UTF-8
04-26 13:22 DEBUG  WindowsBackend: total_memory_mb=511.484375
04-26 13:22 DEBUG  CommonBackend: Searching ISOs on USB devices
04-26 13:22 DEBUG  CommonBackend: Searching for local CDs
04-26 13:22 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF9.tmp is a valid Ubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF9.tmp\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF9.tmp is a valid Ubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF9.tmp\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF9.tmp is a valid Kubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF9.tmp\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF9.tmp is a valid Kubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF9.tmp\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF9.tmp is a valid Xubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF9.tmp\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF9.tmp is a valid Xubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF9.tmp\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF9.tmp is a valid Mythbuntu CD
04-26 13:22 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF9.tmp\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF9.tmp is a valid Mythbuntu CD
04-26 13:22 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF9.tmp\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 13:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 13:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-26 13:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-26 13:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-26 13:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-26 13:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-26 13:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-26 13:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:22 INFO   root: Running the installer...
04-26 13:22 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=English, username=jordan
04-26 13:22 INFO   root: Received settings
04-26 13:22 DEBUG  TaskList: # Running tasklist...
04-26 13:22 DEBUG  TaskList: ## Running select_target_dir...
04-26 13:22 INFO   WindowsBackend: Installing into C:\ubuntu
04-26 13:22 DEBUG  TaskList: ## Finished select_target_dir
04-26 13:22 DEBUG  TaskList: ## Running create_dir_structure...
04-26 13:22 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-26 13:22 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-26 13:22 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-26 13:22 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-26 13:22 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-26 13:22 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-26 13:22 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-26 13:22 DEBUG  TaskList: ## Finished create_dir_structure
04-26 13:22 DEBUG  TaskList: ## Running uncompress_target_dir...
04-26 13:22 DEBUG  TaskList: ## Finished uncompress_target_dir
04-26 13:22 DEBUG  TaskList: ## Running create_uninstaller...
04-26 13:22 DEBUG  WindowsBackend: Copying uninstaller C:\DOCUME~1\Jordan\LOCALS~1\Temp\6lup8p0t.tmp\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-26 13:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-26 13:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-26 13:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-26 13:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-26 13:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev129
04-26 13:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-26 13:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-26 13:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-26 13:22 DEBUG  TaskList: ## Finished create_uninstaller
04-26 13:22 DEBUG  TaskList: ## Running copy_installation_files...
04-26 13:22 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF9.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-26 13:22 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF9.tmp\winboot -> C:\ubuntu\winboot
04-26 13:22 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF9.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-26 13:22 DEBUG  TaskList: ## Finished copy_installation_files
04-26 13:22 DEBUG  TaskList: ## Running get_iso...
04-26 13:22 DEBUG  CommonBackend: Searching for local CD
04-26 13:22 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF9.tmp is a valid Ubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylF9.tmp\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:22 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-26 13:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:22 DEBUG  CommonBackend: Searching for local ISO
04-26 13:22 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
04-26 13:22 DEBUG  TaskList: New task get_metalink
04-26 13:22 DEBUG  TaskList: ### Running get_metalink...
04-26 13:22 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink](http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink) > C:\ubuntu\install
04-26 13:22 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink](http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (10061, 'Connection refused')>
04-26 13:22 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/jaunty-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/jaunty-desktop-i386.metalink) > C:\ubuntu\install
04-26 13:23 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/daily-live/current/jaunty-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/jaunty-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (10061, 'Connection refused')>
04-26 13:23 DEBUG  TaskList: ### Finished get_metalink
04-26 13:23 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
04-26 13:23 DEBUG  TaskList: # Cancelling tasklist
04-26 13:23 ERROR  root: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 129, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
Exception: Cannot download the metalink and therefore the ISO
04-26 13:23 DEBUG  TaskList: # Finished tasklist
04-26 13:25 INFO   root: === wubi 9.04 rev129 ===
04-26 13:25 DEBUG  root: Logfile is c:\docume~1\jordan\locals~1\temp\wubi-9.04-rev129.log
04-26 13:25 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\DOCUME~1\\Jordan\\LOCALS~1\\Temp\\6lup8p0t.tmp\\wubi.exe"']
04-26 13:25 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylFC.tmp\data
04-26 13:25 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylFC.tmp\bin\7z.exe
04-26 13:25 DEBUG  CommonBackend: Fetching basic info...
04-26 13:25 DEBUG  CommonBackend: original_exe=C:\DOCUME~1\Jordan\LOCALS~1\Temp\6lup8p0t.tmp\wubi.exe
04-26 13:25 DEBUG  CommonBackend: platform=win32
04-26 13:25 DEBUG  CommonBackend: osname=nt
04-26 13:25 DEBUG  CommonBackend: language=en_GB
04-26 13:25 DEBUG  CommonBackend: encoding=cp1252
04-26 13:25 DEBUG  WindowsBackend: arch=i386
04-26 13:25 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylFC.tmp\data\isolist.ini
04-26 13:25 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-26 13:25 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-26 13:25 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-26 13:25 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-26 13:25 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-26 13:25 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-26 13:25 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-26 13:25 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-26 13:25 DEBUG  WindowsBackend: Fetching host info...
04-26 13:25 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-26 13:25 DEBUG  WindowsBackend: windows version=xp
04-26 13:25 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-26 13:25 DEBUG  WindowsBackend: windows_sp=Service Pack 3
04-26 13:25 DEBUG  WindowsBackend: windows_build=2600
04-26 13:25 DEBUG  WindowsBackend: gmt=0
04-26 13:25 DEBUG  WindowsBackend: country=GB
04-26 13:25 DEBUG  WindowsBackend: timezone=Europe/London
04-26 13:25 DEBUG  WindowsBackend: windows_username=Jordan
04-26 13:25 DEBUG  WindowsBackend: user_full_name=Jordan
04-26 13:25 DEBUG  WindowsBackend: user_directory=Jordan
04-26 13:25 DEBUG  WindowsBackend: windows_language_code=1033
04-26 13:25 DEBUG  WindowsBackend: windows_language=English
04-26 13:25 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
04-26 13:25 DEBUG  WindowsBackend: bootloader=xp
04-26 13:25 DEBUG  WindowsBackend: system_drive=Drive(C: hd 33040.8398438 mb free )
04-26 13:25 DEBUG  WindowsBackend: drive=Drive(C: hd 33040.8398438 mb free )
04-26 13:25 DEBUG  WindowsBackend: drive=Drive(D: hd 44576.3320313 mb free ntfs)
04-26 13:25 DEBUG  WindowsBackend: drive=Drive(E: hd 6121.09375 mb free fat32)
04-26 13:25 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free udf)
04-26 13:25 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
04-26 13:25 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-26 13:25 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-26 13:25 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-26 13:25 DEBUG  WindowsBackend: keyboard_id=134809609
04-26 13:25 DEBUG  WindowsBackend: keyboard_layout=gb
04-26 13:25 DEBUG  WindowsBackend: keyboard_variant=
04-26 13:25 DEBUG  CommonBackend: locale=en_GB.UTF-8
04-26 13:25 DEBUG  WindowsBackend: total_memory_mb=511.484375
04-26 13:25 DEBUG  CommonBackend: Searching ISOs on USB devices
04-26 13:25 DEBUG  CommonBackend: Searching for local CDs
04-26 13:25 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylFC.tmp is a valid Ubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylFC.tmp\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylFC.tmp is a valid Ubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylFC.tmp\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylFC.tmp is a valid Kubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylFC.tmp\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylFC.tmp is a valid Kubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylFC.tmp\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylFC.tmp is a valid Xubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylFC.tmp\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylFC.tmp is a valid Xubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylFC.tmp\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylFC.tmp is a valid Mythbuntu CD
04-26 13:25 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylFC.tmp\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylFC.tmp is a valid Mythbuntu CD
04-26 13:25 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylFC.tmp\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 13:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 13:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-26 13:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-26 13:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-26 13:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-26 13:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-26 13:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-26 13:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:25 INFO   root: Already installed, running the uninstaller...
04-26 13:25 INFO   root: Running the uninstaller...
04-26 13:25 INFO   CommonBackend: This is the uninstaller running
04-26 13:25 DEBUG  WindowsFrontend: __init__...
04-26 13:25 DEBUG  WindowsFrontend: on_init...
04-26 13:25 INFO   root: Received settings
04-26 13:25 DEBUG  TaskList: # Running tasklist...
04-26 13:25 DEBUG  TaskList: ## Running Backup ISO...
04-26 13:25 DEBUG  TaskList: ## Finished Backup ISO
04-26 13:25 DEBUG  TaskList: ## Running Remove bootloader entry...
04-26 13:25 ERROR  WindowsBackend: Cannot find bcdedit
04-26 13:25 DEBUG  WindowsBackend: undo_bootini C:
04-26 13:25 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 33040.8398438 mb free )
04-26 13:25 DEBUG  WindowsBackend: undo_bootini D:
04-26 13:25 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 44576.3320313 mb free ntfs)
04-26 13:25 DEBUG  WindowsBackend: undo_bootini E:
04-26 13:25 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 6121.09375 mb free fat32)
04-26 13:25 DEBUG  TaskList: ## Finished Remove bootloader entry
04-26 13:25 DEBUG  TaskList: ## Running Remove target dir...
04-26 13:25 DEBUG  CommonBackend: Deleting C:\ubuntu
04-26 13:25 DEBUG  TaskList: ## Finished Remove target dir
04-26 13:25 DEBUG  TaskList: ## Running Remove registry key...
04-26 13:25 DEBUG  TaskList: ## Finished Remove registry key
04-26 13:25 DEBUG  TaskList: # Finished tasklist
04-26 13:25 INFO   root: Almost finished uninstalling
04-26 13:25 INFO   root: Finished uninstallation
04-26 13:25 DEBUG  CommonBackend: Fetching basic info...
04-26 13:25 DEBUG  CommonBackend: original_exe=C:\DOCUME~1\Jordan\LOCALS~1\Temp\6lup8p0t.tmp\wubi.exe
04-26 13:25 DEBUG  CommonBackend: platform=win32
04-26 13:25 DEBUG  CommonBackend: osname=nt
04-26 13:25 DEBUG  CommonBackend: language=en_GB
04-26 13:25 DEBUG  CommonBackend: encoding=cp1252
04-26 13:25 DEBUG  WindowsBackend: arch=i386
04-26 13:25 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylFC.tmp\data\isolist.ini
04-26 13:25 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-26 13:25 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-26 13:25 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-26 13:25 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-26 13:25 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-26 13:25 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-26 13:25 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-26 13:25 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-26 13:25 DEBUG  WindowsBackend: Fetching host info...
04-26 13:25 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-26 13:25 DEBUG  WindowsBackend: windows version=xp
04-26 13:25 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-26 13:25 DEBUG  WindowsBackend: windows_sp=Service Pack 3
04-26 13:25 DEBUG  WindowsBackend: windows_build=2600
04-26 13:25 DEBUG  WindowsBackend: gmt=0
04-26 13:25 DEBUG  WindowsBackend: country=GB
04-26 13:25 DEBUG  WindowsBackend: timezone=Europe/London
04-26 13:25 DEBUG  WindowsBackend: windows_username=Jordan
04-26 13:25 DEBUG  WindowsBackend: user_full_name=Jordan
04-26 13:25 DEBUG  WindowsBackend: user_directory=Jordan
04-26 13:25 DEBUG  WindowsBackend: windows_language_code=1033
04-26 13:25 DEBUG  WindowsBackend: windows_language=English
04-26 13:25 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
04-26 13:25 DEBUG  WindowsBackend: bootloader=xp
04-26 13:25 DEBUG  WindowsBackend: system_drive=Drive(C: hd 33042.7460938 mb free )
04-26 13:25 DEBUG  WindowsBackend: drive=Drive(C: hd 33042.7460938 mb free )
04-26 13:25 DEBUG  WindowsBackend: drive=Drive(D: hd 44576.3320313 mb free ntfs)
04-26 13:25 DEBUG  WindowsBackend: drive=Drive(E: hd 6121.09375 mb free fat32)
04-26 13:25 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free udf)
04-26 13:25 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
04-26 13:25 DEBUG  WindowsBackend: uninstaller_path=None
04-26 13:25 DEBUG  WindowsBackend: previous_target_dir=None
04-26 13:25 DEBUG  WindowsBackend: previous_distro_name=None
04-26 13:25 DEBUG  WindowsBackend: keyboard_id=134809609
04-26 13:25 DEBUG  WindowsBackend: keyboard_layout=gb
04-26 13:25 DEBUG  WindowsBackend: keyboard_variant=
04-26 13:25 DEBUG  CommonBackend: locale=en_GB.UTF-8
04-26 13:25 DEBUG  WindowsBackend: total_memory_mb=511.484375
04-26 13:25 DEBUG  CommonBackend: Searching ISOs on USB devices
04-26 13:25 DEBUG  CommonBackend: Searching for local CDs
04-26 13:25 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylFC.tmp is a valid Ubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylFC.tmp\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylFC.tmp is a valid Ubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylFC.tmp\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylFC.tmp is a valid Kubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylFC.tmp\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylFC.tmp is a valid Kubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylFC.tmp\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylFC.tmp is a valid Xubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylFC.tmp\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylFC.tmp is a valid Xubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylFC.tmp\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylFC.tmp is a valid Mythbuntu CD
04-26 13:25 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylFC.tmp\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylFC.tmp is a valid Mythbuntu CD
04-26 13:25 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylFC.tmp\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 13:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 13:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-26 13:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-26 13:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-26 13:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-26 13:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-26 13:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-26 13:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:25 INFO   root: Running the installer...
04-26 13:25 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=English, username=jordan
04-26 13:25 INFO   root: Received settings
04-26 13:25 DEBUG  TaskList: # Running tasklist...
04-26 13:25 DEBUG  TaskList: ## Running select_target_dir...
04-26 13:25 INFO   WindowsBackend: Installing into C:\ubuntu
04-26 13:25 DEBUG  TaskList: ## Finished select_target_dir
04-26 13:25 DEBUG  TaskList: ## Running create_dir_structure...
04-26 13:25 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-26 13:25 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-26 13:25 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-26 13:25 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-26 13:25 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-26 13:25 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-26 13:25 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-26 13:25 DEBUG  TaskList: ## Finished create_dir_structure
04-26 13:25 DEBUG  TaskList: ## Running uncompress_target_dir...
04-26 13:25 DEBUG  TaskList: ## Finished uncompress_target_dir
04-26 13:25 DEBUG  TaskList: ## Running create_uninstaller...
04-26 13:25 DEBUG  WindowsBackend: Copying uninstaller C:\DOCUME~1\Jordan\LOCALS~1\Temp\6lup8p0t.tmp\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-26 13:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-26 13:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-26 13:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-26 13:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-26 13:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev129
04-26 13:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-26 13:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-26 13:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-26 13:25 DEBUG  TaskList: ## Finished create_uninstaller
04-26 13:25 DEBUG  TaskList: ## Running copy_installation_files...
04-26 13:25 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylFC.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-26 13:25 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylFC.tmp\winboot -> C:\ubuntu\winboot
04-26 13:25 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylFC.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-26 13:25 DEBUG  TaskList: ## Finished copy_installation_files
04-26 13:25 DEBUG  TaskList: ## Running get_iso...
04-26 13:25 DEBUG  CommonBackend: Searching for local CD
04-26 13:25 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylFC.tmp is a valid Ubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pylFC.tmp\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:25 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-26 13:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:25 DEBUG  CommonBackend: Searching for local ISO
04-26 13:25 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
04-26 13:25 DEBUG  TaskList: New task get_metalink
04-26 13:25 DEBUG  TaskList: ### Running get_metalink...
04-26 13:25 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink](http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink) > C:\ubuntu\install
04-26 13:25 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink](http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (10061, 'Connection refused')>
04-26 13:25 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/jaunty-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/jaunty-desktop-i386.metalink) > C:\ubuntu\install
04-26 13:26 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/daily-live/current/jaunty-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/jaunty-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (10061, 'Connection refused')>
04-26 13:26 DEBUG  TaskList: ### Finished get_metalink
04-26 13:26 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
04-26 13:26 DEBUG  TaskList: # Cancelling tasklist
04-26 13:26 ERROR  root: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 129, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
Exception: Cannot download the metalink and therefore the ISO
04-26 13:26 DEBUG  TaskList: # Finished tasklist
04-26 13:37 INFO   root: === wubi 9.04 rev129 ===
04-26 13:37 DEBUG  root: Logfile is c:\docume~1\jordan\locals~1\temp\wubi-9.04-rev129.log
04-26 13:37 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Jordan\\Local Settings\\Temp\\6lup8p0t.tmp\\wubi.exe"']
04-26 13:37 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl9.tmp\data
04-26 13:37 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl9.tmp\bin\7z.exe
04-26 13:37 DEBUG  CommonBackend: Fetching basic info...
04-26 13:37 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Jordan\Local Settings\Temp\6lup8p0t.tmp\wubi.exe
04-26 13:37 DEBUG  CommonBackend: platform=win32
04-26 13:37 DEBUG  CommonBackend: osname=nt
04-26 13:37 DEBUG  CommonBackend: language=en_GB
04-26 13:37 DEBUG  CommonBackend: encoding=cp1252
04-26 13:37 DEBUG  WindowsBackend: arch=i386
04-26 13:37 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl9.tmp\data\isolist.ini
04-26 13:37 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-26 13:37 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-26 13:37 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-26 13:37 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-26 13:37 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-26 13:37 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-26 13:37 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-26 13:37 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-26 13:37 DEBUG  WindowsBackend: Fetching host info...
04-26 13:37 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-26 13:37 DEBUG  WindowsBackend: windows version=xp
04-26 13:37 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-26 13:37 DEBUG  WindowsBackend: windows_sp=Service Pack 3
04-26 13:37 DEBUG  WindowsBackend: windows_build=2600
04-26 13:37 DEBUG  WindowsBackend: gmt=0
04-26 13:37 DEBUG  WindowsBackend: country=GB
04-26 13:37 DEBUG  WindowsBackend: timezone=Europe/London
04-26 13:37 DEBUG  WindowsBackend: windows_username=Jordan
04-26 13:37 DEBUG  WindowsBackend: user_full_name=Jordan
04-26 13:37 DEBUG  WindowsBackend: user_directory=Jordan
04-26 13:37 DEBUG  WindowsBackend: windows_language_code=1033
04-26 13:37 DEBUG  WindowsBackend: windows_language=English
04-26 13:37 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
04-26 13:37 DEBUG  WindowsBackend: bootloader=xp
04-26 13:37 DEBUG  WindowsBackend: system_drive=Drive(C: hd 33040.1484375 mb free )
04-26 13:37 DEBUG  WindowsBackend: drive=Drive(C: hd 33040.1484375 mb free )
04-26 13:37 DEBUG  WindowsBackend: drive=Drive(D: hd 44576.3398438 mb free ntfs)
04-26 13:37 DEBUG  WindowsBackend: drive=Drive(E: hd 6121.09375 mb free fat32)
04-26 13:37 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free udf)
04-26 13:38 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
04-26 13:38 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
04-26 13:38 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
04-26 13:38 DEBUG  WindowsBackend: drive=Drive(J: removable 0.0 mb free )
04-26 13:38 DEBUG  WindowsBackend: drive=Drive(K: removable 0.0 mb free )
04-26 13:38 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-26 13:38 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-26 13:38 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-26 13:38 DEBUG  WindowsBackend: keyboard_id=134809609
04-26 13:38 DEBUG  WindowsBackend: keyboard_layout=gb
04-26 13:38 DEBUG  WindowsBackend: keyboard_variant=
04-26 13:38 DEBUG  CommonBackend: locale=en_GB.UTF-8
04-26 13:38 DEBUG  WindowsBackend: total_memory_mb=511.484375
04-26 13:38 DEBUG  CommonBackend: Searching ISOs on USB devices
04-26 13:38 DEBUG  CommonBackend: Searching for local CDs
04-26 13:38 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl9.tmp is a valid Ubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl9.tmp is a valid Ubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl9.tmp is a valid Kubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl9.tmp is a valid Kubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl9.tmp is a valid Xubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl9.tmp is a valid Xubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl9.tmp is a valid Mythbuntu CD
04-26 13:38 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl9.tmp is a valid Mythbuntu CD
04-26 13:38 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 13:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 13:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-26 13:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-26 13:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-26 13:38 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-26 13:38 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-26 13:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-26 13:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
04-26 13:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
04-26 13:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
04-26 13:38 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
04-26 13:38 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
04-26 13:38 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
04-26 13:38 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
04-26 13:38 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
04-26 13:38 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-26 13:38 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
04-26 13:38 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-26 13:38 INFO   root: Already installed, running the uninstaller...
04-26 13:38 INFO   root: Running the uninstaller...
04-26 13:38 INFO   CommonBackend: This is the uninstaller running
04-26 13:38 DEBUG  WindowsFrontend: __init__...
04-26 13:38 DEBUG  WindowsFrontend: on_init...
04-26 13:39 INFO   root: Received settings
04-26 13:39 DEBUG  TaskList: # Running tasklist...
04-26 13:39 DEBUG  TaskList: ## Running Backup ISO...
04-26 13:39 DEBUG  TaskList: ## Finished Backup ISO
04-26 13:39 DEBUG  TaskList: ## Running Remove bootloader entry...
04-26 13:39 ERROR  WindowsBackend: Cannot find bcdedit
04-26 13:39 DEBUG  WindowsBackend: undo_bootini C:
04-26 13:39 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 33040.1484375 mb free )
04-26 13:39 DEBUG  WindowsBackend: undo_bootini D:
04-26 13:39 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 44576.3398438 mb free ntfs)
04-26 13:39 DEBUG  WindowsBackend: undo_bootini E:
04-26 13:39 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 6121.09375 mb free fat32)
04-26 13:39 DEBUG  WindowsBackend: undo_bootini H:
04-26 13:39 DEBUG  WindowsBackend: undo_configsys Drive(H: removable 0.0 mb free )
04-26 13:39 DEBUG  WindowsBackend: undo_bootini I:
04-26 13:39 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 0.0 mb free )
04-26 13:39 DEBUG  WindowsBackend: undo_bootini J:
04-26 13:39 DEBUG  WindowsBackend: undo_configsys Drive(J: removable 0.0 mb free )
04-26 13:39 DEBUG  WindowsBackend: undo_bootini K:
04-26 13:39 DEBUG  WindowsBackend: undo_configsys Drive(K: removable 0.0 mb free )
04-26 13:39 DEBUG  TaskList: ## Finished Remove bootloader entry
04-26 13:39 DEBUG  TaskList: ## Running Remove target dir...
04-26 13:39 DEBUG  CommonBackend: Deleting C:\ubuntu
04-26 13:39 DEBUG  TaskList: ## Finished Remove target dir
04-26 13:39 DEBUG  TaskList: ## Running Remove registry key...
04-26 13:39 DEBUG  TaskList: ## Finished Remove registry key
04-26 13:39 DEBUG  TaskList: # Finished tasklist
04-26 13:39 INFO   root: Almost finished uninstalling
04-26 13:39 INFO   root: Finished uninstallation
04-26 13:39 DEBUG  CommonBackend: Fetching basic info...
04-26 13:39 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Jordan\Local Settings\Temp\6lup8p0t.tmp\wubi.exe
04-26 13:39 DEBUG  CommonBackend: platform=win32
04-26 13:39 DEBUG  CommonBackend: osname=nt
04-26 13:39 DEBUG  CommonBackend: language=en_GB
04-26 13:39 DEBUG  CommonBackend: encoding=cp1252
04-26 13:39 DEBUG  WindowsBackend: arch=i386
04-26 13:39 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl9.tmp\data\isolist.ini
04-26 13:39 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-26 13:39 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-26 13:39 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-26 13:39 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-26 13:39 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-26 13:39 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-26 13:39 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-26 13:39 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-26 13:39 DEBUG  WindowsBackend: Fetching host info...
04-26 13:39 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-26 13:39 DEBUG  WindowsBackend: windows version=xp
04-26 13:39 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-26 13:39 DEBUG  WindowsBackend: windows_sp=Service Pack 3
04-26 13:39 DEBUG  WindowsBackend: windows_build=2600
04-26 13:39 DEBUG  WindowsBackend: gmt=0
04-26 13:39 DEBUG  WindowsBackend: country=GB
04-26 13:39 DEBUG  WindowsBackend: timezone=Europe/London
04-26 13:39 DEBUG  WindowsBackend: windows_username=Jordan
04-26 13:39 DEBUG  WindowsBackend: user_full_name=Jordan
04-26 13:39 DEBUG  WindowsBackend: user_directory=Jordan
04-26 13:39 DEBUG  WindowsBackend: windows_language_code=1033
04-26 13:39 DEBUG  WindowsBackend: windows_language=English
04-26 13:39 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
04-26 13:39 DEBUG  WindowsBackend: bootloader=xp
04-26 13:39 DEBUG  WindowsBackend: system_drive=Drive(C: hd 33040.1367188 mb free )
04-26 13:39 DEBUG  WindowsBackend: drive=Drive(C: hd 33040.1367188 mb free )
04-26 13:39 DEBUG  WindowsBackend: drive=Drive(D: hd 44576.3398438 mb free ntfs)
04-26 13:39 DEBUG  WindowsBackend: drive=Drive(E: hd 6121.09375 mb free fat32)
04-26 13:39 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free udf)
04-26 13:39 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
04-26 13:39 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
04-26 13:39 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
04-26 13:39 DEBUG  WindowsBackend: drive=Drive(J: removable 0.0 mb free )
04-26 13:39 DEBUG  WindowsBackend: drive=Drive(K: removable 0.0 mb free )
04-26 13:39 DEBUG  WindowsBackend: uninstaller_path=None
04-26 13:39 DEBUG  WindowsBackend: previous_target_dir=None
04-26 13:39 DEBUG  WindowsBackend: previous_distro_name=None
04-26 13:39 DEBUG  WindowsBackend: keyboard_id=134809609
04-26 13:39 DEBUG  WindowsBackend: keyboard_layout=gb
04-26 13:39 DEBUG  WindowsBackend: keyboard_variant=
04-26 13:39 DEBUG  CommonBackend: locale=en_GB.UTF-8
04-26 13:39 DEBUG  WindowsBackend: total_memory_mb=511.484375
04-26 13:39 DEBUG  CommonBackend: Searching ISOs on USB devices
04-26 13:39 DEBUG  CommonBackend: Searching for local CDs
04-26 13:39 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl9.tmp is a valid Ubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl9.tmp is a valid Ubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl9.tmp is a valid Kubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl9.tmp is a valid Kubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl9.tmp is a valid Xubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl9.tmp is a valid Xubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl9.tmp is a valid Mythbuntu CD
04-26 13:39 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl9.tmp is a valid Mythbuntu CD
04-26 13:39 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 13:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 13:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-26 13:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-26 13:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-26 13:39 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-26 13:39 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-26 13:39 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-26 13:39 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
04-26 13:39 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
04-26 13:39 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
04-26 13:39 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
04-26 13:39 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
04-26 13:39 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
04-26 13:39 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
04-26 13:39 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
04-26 13:39 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-26 13:39 INFO   root: Running the installer...
04-26 13:39 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=English, username=jordan
04-26 13:39 INFO   root: Received settings
04-26 13:39 DEBUG  TaskList: # Running tasklist...
04-26 13:39 DEBUG  TaskList: ## Running select_target_dir...
04-26 13:39 INFO   WindowsBackend: Installing into C:\ubuntu
04-26 13:39 DEBUG  TaskList: ## Finished select_target_dir
04-26 13:39 DEBUG  TaskList: ## Running create_dir_structure...
04-26 13:39 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-26 13:39 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-26 13:39 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-26 13:39 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-26 13:39 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-26 13:39 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-26 13:39 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-26 13:39 DEBUG  TaskList: ## Finished create_dir_structure
04-26 13:39 DEBUG  TaskList: ## Running uncompress_target_dir...
04-26 13:39 DEBUG  TaskList: ## Finished uncompress_target_dir
04-26 13:39 DEBUG  TaskList: ## Running create_uninstaller...
04-26 13:39 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\Jordan\Local Settings\Temp\6lup8p0t.tmp\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-26 13:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-26 13:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-26 13:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-26 13:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-26 13:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev129
04-26 13:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-26 13:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-26 13:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-26 13:39 DEBUG  TaskList: ## Finished create_uninstaller
04-26 13:39 DEBUG  TaskList: ## Running copy_installation_files...
04-26 13:39 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl9.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-26 13:39 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl9.tmp\winboot -> C:\ubuntu\winboot
04-26 13:39 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl9.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-26 13:39 DEBUG  TaskList: ## Finished copy_installation_files
04-26 13:39 DEBUG  TaskList: ## Running get_iso...
04-26 13:39 DEBUG  CommonBackend: Searching for local CD
04-26 13:39 DEBUG  Distro:   checking whether C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl9.tmp is a valid Ubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain C:\DOCUME~1\Jordan\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-26 13:39 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
04-26 13:39 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-26 13:39 DEBUG  CommonBackend: Searching for local ISO
04-26 13:39 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
04-26 13:39 DEBUG  TaskList: New task get_metalink
04-26 13:39 DEBUG  TaskList: ### Running get_metalink...
04-26 13:39 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink](http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink) > C:\ubuntu\install
04-26 13:39 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-9.04-desktop-i386.metalink, url=http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink, basename=ubuntu-9.04-desktop-i386.metalink, length=19438, text=None
04-26 13:39 DEBUG  downloader: download finished (read 19438 bytes)
04-26 13:39 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.04/MD5SUMS-metalink](http://releases.ubuntu.com/9.04/MD5SUMS-metalink) > C:\ubuntu\install
04-26 13:39 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/9.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=413, text=None
04-26 13:39 DEBUG  downloader: download finished (read 413 bytes)
04-26 13:39 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/9.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
04-26 13:39 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/9.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
04-26 13:39 DEBUG  downloader: download finished (read 189 bytes)
04-26 13:39 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
04-26 13:39 INFO   saplog: Checking block bindings..
04-26 13:39 INFO   saplog: Key verified successfully.
04-26 13:39 DEBUG  CommonBackend: metalink md5sums:
1ec553ada3a4a18fb977816ccac02dfc  ubuntu-9.04-alternate-amd64.metalink
5daf9cb57325672f0eb768d6c11888e8  ubuntu-9.04-alternate-i386.metalink
3df58e889d3613abc2347a6b0e8f4d04  ubuntu-9.04-desktop-amd64.metalink
542bc6d7988f1d2967d419c089b08f57  ubuntu-9.04-desktop-i386.metalink
ea0b13f00711ef4b2e5c772482033a1f  ubuntu-9.04-server-amd64.metalink
88e47c579eb587c8aae1a7d7737ab3f0  ubuntu-9.04-server-i386.metalink

04-26 13:39 DEBUG  TaskList: ### Finished get_metalink
04-26 13:39 DEBUG  TaskList: New task download
04-26 13:39 DEBUG  TaskList: ### Running download...
04-26 13:39 DEBUG  downloader: downloading [http://de.archive.ubuntu.com/ubuntu-releases/9.04/ubuntu-9.04-desktop-i386.iso](http://de.archive.ubuntu.com/ubuntu-releases/9.04/ubuntu-9.04-desktop-i386.iso) > C:\ubuntu\install\ubuntu-9.04-desktop-i386.iso
04-26 13:39 ERROR  TaskList: [Errno 4] IOError: <urlopen error <html>

>
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\downloader.py", line 79, in download
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\urlgrabber\grabber.py", line 845, in _retry
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\urlgrabber\grabber.py", line 913, in retryfunc
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\urlgrabber\grabber.py", line 1001, in __init__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\urlgrabber\grabber.py", line 1072, in _do_open
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\urlgrabber\grabber.py", line 1188, in _make_request
URLGrabError: [Errno 4] IOError: <urlopen error <html>

>
04-26 13:39 DEBUG  TaskList: # Cancelling tasklist
04-26 13:39 ERROR  root: [Errno 4] IOError: <urlopen error <html>

>
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 129, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
URLGrabError: [Errno 4] IOError: <urlopen error <html>

>
04-26 13:39 DEBUG  TaskList: New task download
04-26 13:39 DEBUG  TaskList: New task download
04-26 13:39 DEBUG  TaskList: New task download
04-26 13:39 DEBUG  TaskList: New task download
04-26 13:39 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 487, in get_iso
Exception: Could not retrieve the required installation files
04-26 13:39 DEBUG  TaskList: # Cancelling tasklist
04-26 13:39 DEBUG  TaskList: # Finished tasklist

---

### Post by omgpop on 2009-04-26
I restarted my computer and now its back to the old problem (which is surprisingly a relief). I will try and find a log of that and will just replace the last log with that one.

---

### Post by omgpop on 2009-04-26
This is odd. I cannot run wubi if a disk is not in drive G:. Why is that?

---

### Post by omgpop on 2009-04-26
Hi there. Sorry to have wasted anyones time, but I have found a solution. I just needed to put the ISO and wubi in the same directory. But never mind, knowing my luck I will be posting again with another problem. Thank you for attempting to help me.

---

### Post by abq911 on 2009-05-16
I have the same problem, and I am a noob at this stuff. Could some of the more advanced people explain to me simply what is a:
ISO
Directory

What do I do with Wubi.exe and the ISO, I know you have to put them in a directory, but what is that. 

I have the same error as omgpop, and here is my log file:
I only put in the 23:05 but there is A LOT MORE.

05-15 23:05 DEBUG  root: Logfile is c:\docume~1\adel\locals~1\temp\wubi-9.04-rev129.log
05-15 23:05 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Adel\\Desktop\\wubi.exe"']
05-15 23:05 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Adel\LOCALS~1\Temp\pyl2.tmp\data
05-15 23:05 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Adel\LOCALS~1\Temp\pyl2.tmp\bin\7z.exe
05-15 23:05 DEBUG  CommonBackend: Fetching basic info...
05-15 23:05 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Adel\Desktop\wubi.exe
05-15 23:05 DEBUG  CommonBackend: platform=win32
05-15 23:05 DEBUG  CommonBackend: osname=nt
05-15 23:05 DEBUG  CommonBackend: language=en_US
05-15 23:05 DEBUG  CommonBackend: encoding=cp1252
05-15 23:05 DEBUG  WindowsBackend: arch=i386
05-15 23:05 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Adel\LOCALS~1\Temp\pyl2.tmp\data\isolist.ini
05-15 23:05 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-15 23:05 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-15 23:05 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-15 23:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-15 23:05 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-15 23:05 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-15 23:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-15 23:05 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-15 23:05 DEBUG  WindowsBackend: Fetching host info...
05-15 23:05 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-15 23:05 DEBUG  WindowsBackend: windows version=xp
05-15 23:05 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
05-15 23:05 DEBUG  WindowsBackend: windows_sp=Service Pack 3
05-15 23:05 DEBUG  WindowsBackend: windows_build=2600
05-15 23:05 DEBUG  WindowsBackend: gmt=-5
05-15 23:05 DEBUG  WindowsBackend: country=US
05-15 23:05 DEBUG  WindowsBackend: timezone=America/New_York
05-15 23:05 DEBUG  WindowsBackend: windows_username=Adel
05-15 23:05 DEBUG  WindowsBackend: user_full_name=Adel
05-15 23:05 DEBUG  WindowsBackend: user_directory=Adel
05-15 23:05 DEBUG  WindowsBackend: windows_language_code=1033
05-15 23:05 DEBUG  WindowsBackend: windows_language=English
05-15 23:05 DEBUG  WindowsBackend: processor_name=        Intel(R) Pentium(R) M processor 1.73GHz
05-15 23:05 DEBUG  WindowsBackend: bootloader=xp
05-15 23:05 DEBUG  WindowsBackend: system_drive=Drive(C: hd 80356.8710938 mb free )
05-15 23:05 DEBUG  WindowsBackend: drive=Drive(C: hd 80356.8710938 mb free )
05-15 23:05 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
05-15 23:05 DEBUG  WindowsBackend: uninstaller_path=None
05-15 23:05 DEBUG  WindowsBackend: previous_target_dir=None
05-15 23:05 DEBUG  WindowsBackend: previous_distro_name=None
05-15 23:05 DEBUG  WindowsBackend: keyboard_id=67699721
05-15 23:05 DEBUG  WindowsBackend: keyboard_layout=us
05-15 23:05 DEBUG  WindowsBackend: keyboard_variant=
05-15 23:05 DEBUG  CommonBackend: locale=en_US.UTF-8
05-15 23:05 DEBUG  WindowsBackend: total_memory_mb=2039.41796875
05-15 23:05 DEBUG  CommonBackend: Searching ISOs on USB devices
05-15 23:05 DEBUG  CommonBackend: Searching for local CDs
05-15 23:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Adel\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu CD
05-15 23:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Adel\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
05-15 23:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Adel\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu CD
05-15 23:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Adel\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
05-15 23:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Adel\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu CD
05-15 23:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Adel\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
05-15 23:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Adel\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu CD
05-15 23:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Adel\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
05-15 23:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Adel\LOCALS~1\Temp\pyl2.tmp is a valid Xubuntu CD
05-15 23:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Adel\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
05-15 23:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Adel\LOCALS~1\Temp\pyl2.tmp is a valid Xubuntu CD
05-15 23:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Adel\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
05-15 23:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Adel\LOCALS~1\Temp\pyl2.tmp is a valid Mythbuntu CD
05-15 23:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Adel\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
05-15 23:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Adel\LOCALS~1\Temp\pyl2.tmp is a valid Mythbuntu CD
05-15 23:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Adel\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
05-15 23:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-15 23:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 23:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-15 23:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 23:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-15 23:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 23:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-15 23:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 23:05 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-15 23:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 23:05 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-15 23:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 23:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-15 23:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 23:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-15 23:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 23:05 INFO   root: Running the installer...
05-15 23:05 DEBUG  WindowsFrontend: __init__...
05-15 23:05 DEBUG  WindowsFrontend: on_init...
05-15 23:05 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=English, username=adelq
05-15 23:05 INFO   root: Received settings
05-15 23:05 DEBUG  TaskList: # Running tasklist...
05-15 23:05 DEBUG  TaskList: ## Running select_target_dir...
05-15 23:05 INFO   WindowsBackend: Installing into C:\ubuntu
05-15 23:05 DEBUG  TaskList: ## Finished select_target_dir
05-15 23:05 DEBUG  TaskList: ## Running create_dir_structure...
05-15 23:05 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-15 23:05 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-15 23:05 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-15 23:05 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-15 23:05 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-15 23:05 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-15 23:05 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-15 23:05 DEBUG  TaskList: ## Finished create_dir_structure
05-15 23:05 DEBUG  TaskList: ## Running uncompress_target_dir...
05-15 23:05 DEBUG  TaskList: ## Finished uncompress_target_dir
05-15 23:05 DEBUG  TaskList: ## Running create_uninstaller...
05-15 23:05 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\Adel\Desktop\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
05-15 23:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-15 23:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-15 23:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-15 23:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
05-15 23:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev129
05-15 23:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-15 23:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-15 23:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-15 23:05 DEBUG  TaskList: ## Finished create_uninstaller
05-15 23:05 DEBUG  TaskList: ## Running copy_installation_files...
05-15 23:05 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Adel\LOCALS~1\Temp\pyl2.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-15 23:05 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Adel\LOCALS~1\Temp\pyl2.tmp\winboot -> C:\ubuntu\winboot
05-15 23:05 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Adel\LOCALS~1\Temp\pyl2.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
05-15 23:05 DEBUG  TaskList: ## Finished copy_installation_files
05-15 23:05 DEBUG  TaskList: ## Running get_iso...
05-15 23:05 DEBUG  CommonBackend: Searching for local CD
05-15 23:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Adel\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu CD
05-15 23:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Adel\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
05-15 23:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-15 23:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 23:05 DEBUG  CommonBackend: Searching for local ISO
05-15 23:05 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-15 23:05 DEBUG  TaskList: New task get_metalink
05-15 23:05 DEBUG  TaskList: ### Running get_metalink...
05-15 23:05 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink](http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink) > C:\ubuntu\install
05-15 23:05 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-9.04-desktop-i386.metalink, url=http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink, basename=ubuntu-9.04-desktop-i386.metalink, length=19438, text=None
05-15 23:05 DEBUG  downloader: download finished (read 19438 bytes)
05-15 23:05 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.04/MD5SUMS-metalink](http://releases.ubuntu.com/9.04/MD5SUMS-metalink) > C:\ubuntu\install
05-15 23:05 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/9.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=413, text=None
05-15 23:05 DEBUG  downloader: download finished (read 413 bytes)
05-15 23:05 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/9.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
05-15 23:05 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/9.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
05-15 23:05 DEBUG  downloader: download finished (read 189 bytes)
05-15 23:05 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
05-15 23:05 INFO   saplog: Checking block bindings..
05-15 23:05 INFO   saplog: Key verified successfully.
05-15 23:05 DEBUG  CommonBackend: metalink md5sums:
1ec553ada3a4a18fb977816ccac02dfc  ubuntu-9.04-alternate-amd64.metalink
5daf9cb57325672f0eb768d6c11888e8  ubuntu-9.04-alternate-i386.metalink
3df58e889d3613abc2347a6b0e8f4d04  ubuntu-9.04-desktop-amd64.metalink
542bc6d7988f1d2967d419c089b08f57  ubuntu-9.04-desktop-i386.metalink
ea0b13f00711ef4b2e5c772482033a1f  ubuntu-9.04-server-amd64.metalink
88e47c579eb587c8aae1a7d7737ab3f0  ubuntu-9.04-server-i386.metalink

05-15 23:05 DEBUG  TaskList: ### Finished get_metalink
05-15 23:05 DEBUG  TaskList: New task download
05-15 23:05 DEBUG  TaskList: ### Running download...
05-15 23:05 DEBUG  downloader: downloading [http://de.archive.ubuntu.com/ubuntu-releases/9.04/ubuntu-9.04-desktop-i386.iso](http://de.archive.ubuntu.com/ubuntu-releases/9.04/ubuntu-9.04-desktop-i386.iso) > C:\ubuntu\install\ubuntu-9.04-desktop-i386.iso
05-15 23:05 ERROR  TaskList: [Errno 4] IOError: <urlopen error <html>

>
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\downloader.py", line 79, in download
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\urlgrabber\grabber.py", line 845, in _retry
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\urlgrabber\grabber.py", line 913, in retryfunc
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\urlgrabber\grabber.py", line 1001, in __init__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\urlgrabber\grabber.py", line 1072, in _do_open
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\urlgrabber\grabber.py", line 1188, in _make_request
URLGrabError: [Errno 4] IOError: <urlopen error <html>

>
05-15 23:05 DEBUG  TaskList: # Cancelling tasklist
05-15 23:05 ERROR  root: [Errno 4] IOError: <urlopen error <html>

>
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 129, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
URLGrabError: [Errno 4] IOError: <urlopen error <html>

>
05-15 23:05 DEBUG  TaskList: New task download
05-15 23:05 DEBUG  TaskList: New task download
05-15 23:05 DEBUG  TaskList: New task download
05-15 23:05 DEBUG  TaskList: New task download
05-15 23:05 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 487, in get_iso
Exception: Could not retrieve the required installation files
05-15 23:05 DEBUG  TaskList: # Cancelling tasklist
05-15 23:05 DEBUG  TaskList: # Finished tasklist

---

