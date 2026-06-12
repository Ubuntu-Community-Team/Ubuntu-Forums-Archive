---
title: "Installing Ubuntu 9.10 with Wubi.."
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by .Kai on 2009-04-21
Okay, I installed Ubuntu 9.04(the lastest beta before the RC release) then tried to uninstall(in windows) it got an error then I installed the old ubuntu then uninstalled it,then I deleted all the old folders to the 9.10 then when I tried to install it again on the RC1(I might've made some kind of mistake)
I get this error: 

---------------------------
Ubuntu Installer
---------------------------
An error occurred:

Permission denied

For more information, please see the log file: c:\docume~1\kyo\locals~1\temp\wubi-9.04-rev122.log
---------------------------
OK   
---------------------------

any ideas on how to solve this? thanks

---

### Post by .Kai on 2009-04-21
Anyone?

---

### Post by .Kai on 2009-04-22
Bump again.. =/

---

### Post by shark1997 on 2009-04-22
Did you know Ubuntu 9.10 isn't out yet? 9.04 is releasing April 23

---

### Post by .Kai on 2009-04-23
It's just released. =D I'll downloaded that to see if I have any problems

---

### Post by .Kai on 2009-04-23
Okay, I still can't install it. -___- 
this is my logfile on Windows:
```

04-23 09:21 INFO   root: === wubi 9.04 rev128 ===
04-23 09:21 DEBUG  root: Logfile is c:\docume~1\kyo\locals~1\temp\wubi-9.04-rev128.log
04-23 09:21 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
04-23 09:21 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Kyo\LOCALS~1\Temp\pylE.tmp\data
04-23 09:21 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Kyo\LOCALS~1\Temp\pylE.tmp\bin\7z.exe
04-23 09:21 DEBUG  CommonBackend: Fetching basic info...
04-23 09:21 DEBUG  CommonBackend: original_exe=D:\wubi.exe
04-23 09:21 DEBUG  CommonBackend: platform=win32
04-23 09:21 DEBUG  CommonBackend: osname=nt
04-23 09:21 DEBUG  CommonBackend: language=en_US
04-23 09:21 DEBUG  CommonBackend: encoding=cp1252
04-23 09:21 DEBUG  WindowsBackend: arch=i386
04-23 09:21 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Kyo\LOCALS~1\Temp\pylE.tmp\data\isolist.ini
04-23 09:21 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-23 09:21 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-23 09:21 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-23 09:21 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-23 09:21 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-23 09:21 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-23 09:21 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-23 09:21 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-23 09:21 DEBUG  WindowsBackend: Fetching host info...
04-23 09:21 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-23 09:21 DEBUG  WindowsBackend: windows version=xp
04-23 09:21 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-23 09:21 DEBUG  WindowsBackend: windows_sp=Service Pack 3
04-23 09:21 DEBUG  WindowsBackend: windows_build=2600
04-23 09:21 DEBUG  WindowsBackend: gmt=-8
04-23 09:21 DEBUG  WindowsBackend: country=US
04-23 09:21 DEBUG  WindowsBackend: timezone=America/Los_Angeles
04-23 09:21 DEBUG  WindowsBackend: windows_username=Kyo
04-23 09:21 DEBUG  WindowsBackend: user_full_name=Kyo
04-23 09:21 DEBUG  WindowsBackend: user_directory=Kyo
04-23 09:21 DEBUG  WindowsBackend: windows_language_code=1033
04-23 09:21 DEBUG  WindowsBackend: windows_language=English
04-23 09:21 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.20GHz
04-23 09:21 DEBUG  WindowsBackend: bootloader=xp
04-23 09:21 DEBUG  WindowsBackend: system_drive=Drive(C: hd 14577.4375 mb free )
04-23 09:21 DEBUG  WindowsBackend: drive=Drive(C: hd 14577.4375 mb free )
04-23 09:21 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
04-23 09:21 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-23 09:21 DEBUG  WindowsBackend: uninstaller_path=None
04-23 09:21 DEBUG  WindowsBackend: previous_target_dir=None
04-23 09:21 DEBUG  WindowsBackend: previous_distro_name=None
04-23 09:21 DEBUG  WindowsBackend: keyboard_id=67699721
04-23 09:21 DEBUG  WindowsBackend: keyboard_layout=us
04-23 09:21 DEBUG  WindowsBackend: keyboard_variant=
04-23 09:21 DEBUG  CommonBackend: locale=en_US.UTF-8
04-23 09:21 DEBUG  WindowsBackend: total_memory_mb=511.421875
04-23 09:21 DEBUG  CommonBackend: Searching ISOs on USB devices
04-23 09:21 DEBUG  CommonBackend: Searching for local CDs
04-23 09:21 DEBUG  Distro:   checking whether C:\DOCUME~1\Kyo\LOCALS~1\Temp\pylE.tmp is a valid Ubuntu CD
04-23 09:21 DEBUG  Distro:     does not contain C:\DOCUME~1\Kyo\LOCALS~1\Temp\pylE.tmp\casper\filesystem.squashfs
04-23 09:21 DEBUG  Distro:   checking whether C:\DOCUME~1\Kyo\LOCALS~1\Temp\pylE.tmp is a valid Ubuntu CD
04-23 09:21 DEBUG  Distro:     does not contain C:\DOCUME~1\Kyo\LOCALS~1\Temp\pylE.tmp\casper\filesystem.squashfs
04-23 09:21 DEBUG  Distro:   checking whether C:\DOCUME~1\Kyo\LOCALS~1\Temp\pylE.tmp is a valid Kubuntu CD
04-23 09:21 DEBUG  Distro:     does not contain C:\DOCUME~1\Kyo\LOCALS~1\Temp\pylE.tmp\casper\filesystem.squashfs
04-23 09:21 DEBUG  Distro:   checking whether C:\DOCUME~1\Kyo\LOCALS~1\Temp\pylE.tmp is a valid Kubuntu CD
04-23 09:21 DEBUG  Distro:     does not contain C:\DOCUME~1\Kyo\LOCALS~1\Temp\pylE.tmp\casper\filesystem.squashfs
04-23 09:21 DEBUG  Distro:   checking whether C:\DOCUME~1\Kyo\LOCALS~1\Temp\pylE.tmp is a valid Xubuntu CD
04-23 09:21 DEBUG  Distro:     does not contain C:\DOCUME~1\Kyo\LOCALS~1\Temp\pylE.tmp\casper\filesystem.squashfs
04-23 09:21 DEBUG  Distro:   checking whether C:\DOCUME~1\Kyo\LOCALS~1\Temp\pylE.tmp is a valid Xubuntu CD
04-23 09:21 DEBUG  Distro:     does not contain C:\DOCUME~1\Kyo\LOCALS~1\Temp\pylE.tmp\casper\filesystem.squashfs
04-23 09:21 DEBUG  Distro:   checking whether C:\DOCUME~1\Kyo\LOCALS~1\Temp\pylE.tmp is a valid Mythbuntu CD
04-23 09:21 DEBUG  Distro:     does not contain C:\DOCUME~1\Kyo\LOCALS~1\Temp\pylE.tmp\casper\filesystem.squashfs
04-23 09:21 DEBUG  Distro:   checking whether C:\DOCUME~1\Kyo\LOCALS~1\Temp\pylE.tmp is a valid Mythbuntu CD
04-23 09:21 DEBUG  Distro:     does not contain C:\DOCUME~1\Kyo\LOCALS~1\Temp\pylE.tmp\casper\filesystem.squashfs
04-23 09:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-23 09:21 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
04-23 09:21 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
04-23 09:21 DEBUG  Distro: wrong arch: i386 != amd64
04-23 09:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-23 09:21 INFO   Distro: Found a valid CD for Ubuntu: D:\
04-23 09:21 INFO   root: Running the CD menu...
04-23 09:21 DEBUG  WindowsFrontend: __init__...
04-23 09:21 DEBUG  WindowsFrontend: on_init...
04-23 09:22 INFO   root: CD menu finished
04-23 09:22 INFO   root: Running the installer...
04-23 09:22 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=8000MB, distro_name=Ubuntu, language=English, username=kyo
04-23 09:22 INFO   root: Received settings
04-23 09:22 DEBUG  TaskList: # Running tasklist...
04-23 09:22 DEBUG  TaskList: ## Running select_target_dir...
04-23 09:22 INFO   WindowsBackend: Installing into C:\ubuntu
04-23 09:22 DEBUG  TaskList: ## Finished select_target_dir
04-23 09:22 DEBUG  TaskList: ## Running create_dir_structure...
04-23 09:22 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-23 09:22 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-23 09:22 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-23 09:22 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-23 09:22 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-23 09:22 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-23 09:22 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-23 09:22 DEBUG  TaskList: ## Finished create_dir_structure
04-23 09:22 DEBUG  TaskList: ## Running uncompress_target_dir...
04-23 09:22 DEBUG  TaskList: ## Finished uncompress_target_dir
04-23 09:22 DEBUG  TaskList: ## Running create_uninstaller...
04-23 09:22 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-23 09:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-23 09:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-23 09:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-23 09:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-23 09:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
04-23 09:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-23 09:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-23 09:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-23 09:22 DEBUG  TaskList: ## Finished create_uninstaller
04-23 09:22 DEBUG  TaskList: ## Running copy_installation_files...
04-23 09:22 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Kyo\LOCALS~1\Temp\pylE.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-23 09:22 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Kyo\LOCALS~1\Temp\pylE.tmp\winboot -> C:\ubuntu\winboot
04-23 09:22 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Kyo\LOCALS~1\Temp\pylE.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-23 09:22 DEBUG  TaskList: ## Finished copy_installation_files
04-23 09:22 DEBUG  TaskList: ## Running get_iso...
04-23 09:22 DEBUG  TaskList: New task copy_file
04-23 09:22 DEBUG  TaskList: ### Running copy_file...
04-23 09:22 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 13] Permission denied
04-23 09:22 DEBUG  TaskList: # Cancelling tasklist
04-23 09:22 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 13] Permission denied
04-23 09:22 DEBUG  TaskList: New task check_iso
04-23 09:22 DEBUG  CommonBackend: Searching for local ISO
04-23 09:22 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
04-23 09:22 DEBUG  TaskList: New task get_metalink
04-23 09:22 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
04-23 09:22 DEBUG  TaskList: # Cancelling tasklist
04-23 09:22 DEBUG  TaskList: # Finished tasklist

```

---

### Post by .Kai on 2009-04-23
Still need help here.... >_< I've been trying to install Ubuntu 9.10 for awhile [on CD] and still no luck

---

### Post by zanos on 2009-04-24
Hi. I had the same problem however I couldnt install at all. I had windows 7 (32bit) running and I was trying to install ubuntu 64bit. Then I tried ubuntu 32bit and now im writing you this reply under Linux. I hope that helps.Z

---

### Post by _sleeper on 2009-04-24
just a hint here. 9.10 is not released yet. it will be on october.
and another hint. it is preferable to put code tags between outputs, commands, etc. ;)


as for wubi, in the log file it keeps repeating that you do not have enough permissions. check your account settings and your permissions.

---

### Post by .Kai on 2009-04-24
> **_sleeper said:**
> just a hint here. 9.10 is not released yet. it will be on october.
and another hint. it is preferable to put code tags between outputs, commands, etc. ;)


as for wubi, in the log file it keeps repeating that you do not have enough permissions. check your account settings and your permissions.
Yeah I like testing stuff. =o code box added I was in a hurry to do something else then.
and my I'm already a Computer administrator and it still wont allow me to install it and I don't know any other settings to change. so I still kinda need up.

Thanks for your reply so far!


@zanos I don't know how can I tell which -bit it is. =o

---

### Post by .Kai on 2009-04-24
Help please. :/

---

### Post by buntunub on 2009-04-25
Same problem here. I get a continuous stream of exception processing errors when trying to install Jaunty Kubuntu Wubi 32 bit and it will not install at all. I click through all those and then get the Wubi Installer, but after getting to the download section it finally pops another error, " An error occurred: IOError: <urlopen error (10060, 'Operation timed out')>"

---

### Post by buntunub on 2009-04-25
I finally found the wubi log and it dumped the following errors - 

```
04-25 01:25 DEBUG  Distro:   checking whether C:\DOCUME~1\user\LOCALS~1\Temp\pylE.tmp is a valid Kubuntu CD
04-25 01:25 DEBUG  Distro:     does not contain C:\DOCUME~1\user\LOCALS~1\Temp\pylE.tmp\casper\filesystem.squashfs
04-25 01:25 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-25 01:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-25 01:25 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-25 01:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-25 01:25 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-25 01:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-25 01:25 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-25 01:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-25 01:25 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
04-25 01:25 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-25 01:25 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
04-25 01:25 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-25 01:25 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
04-25 01:25 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-25 01:25 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
04-25 01:25 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-25 01:25 DEBUG  Distro:   checking whether Y:\ is a valid Kubuntu CD
04-25 01:25 DEBUG  Distro:     does not contain Y:\casper\filesystem.squashfs
04-25 01:25 DEBUG  Distro:   checking whether Z:\ is a valid Kubuntu CD
04-25 01:25 DEBUG  Distro:     does not contain Z:\casper\filesystem.squashfs
04-25 01:25 DEBUG  CommonBackend: Searching for local ISO
04-25 01:25 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
04-25 01:25 DEBUG  TaskList: New task get_metalink
04-25 01:25 DEBUG  TaskList: ### Running get_metalink...
04-25 01:25 DEBUG  downloader: downloading releases.ubuntu.com/kubuntu/9.04/kubuntu-9.04-desktop-i386.metalink > C:\ubuntu\install
04-25 01:25 ERROR  CommonBackend: Cannot download metalink file releases.ubuntu.com/kubuntu/9.04/kubuntu-9.04-desktop-i386.metalink err=[Errno 2] Local file does not exist: C:\DOCUME~1\user\LOCALS~1\Temp\pylE.tmp\releases.ubuntu.com\kubuntu\9.04\kubuntu-9.04-desktop-i386.metalink
04-25 01:25 DEBUG  downloader: downloading http://cdimage.ubuntu.com/kubuntu/daily-live/current/jaunty-desktop-amd64.metalink > C:\ubuntu\install
04-25 01:25 DEBUG  downloader: Download start filename=C:\ubuntu\install\jaunty-desktop-amd64.metalink, url=http://cdimage.ubuntu.com/kubuntu/daily-live/current/jaunty-desktop-amd64.metalink, basename=jaunty-desktop-amd64.metalink, length=1018, text=None
04-25 01:25 DEBUG  downloader: download finished (read 1018 bytes)
04-25 01:25 DEBUG  downloader: downloading http://cdimage.ubuntu.com/kubuntu/daily-live/current/MD5SUMS-metalink > C:\ubuntu\install
04-25 01:25 ERROR  TaskList: [Errno 4] IOError: <urlopen error (10060, 'Operation timed out')>
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 373, in get_metalink
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 240, in check_metalink
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\downloader.py", line 79, in download
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\urlgrabber\grabber.py", line 845, in _retry
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\urlgrabber\grabber.py", line 913, in retryfunc
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\urlgrabber\grabber.py", line 1001, in __init__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\urlgrabber\grabber.py", line 1072, in _do_open
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\urlgrabber\grabber.py", line 1188, in _make_request
URLGrabError: [Errno 4] IOError: <urlopen error (10060, 'Operation timed out')>
04-25 01:25 DEBUG  TaskList: # Cancelling tasklist
04-25 01:25 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
04-25 01:25 ERROR  root: [Errno 4] IOError: <urlopen error (10060, 'Operation timed out')>
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 129, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
URLGrabError: [Errno 4] IOError: <urlopen error (10060, 'Operation timed out')>
04-25 01:25 DEBUG  TaskList: # Cancelling tasklist
04-25 01:25 DEBUG  TaskList: # Finished tasklist

```

---

### Post by .Kai on 2009-04-25
>_< Atleast I'm not the only one but yeah we still need help! XD

---

### Post by buntunub on 2009-04-25
There seems to be some major issues with all versions of Wubi right now. I guess this function was not properly beta/alpha tested and fixed prior to Jaunty launch. Pity, because this is one of the most important functions from a new users perspective and is what most windows users will try out first before making the big switch to Linux and it fails to work entirely -- sure to make a big impression in an incredibly negative way!

Anyway, this [thread]("http://ubuntuforums.org/showthread.php?t=1134709&highlight=wubi") is promising and the fix worked for me. Lots of hoops to jump through and a hack job and Wubi sort of works -- at least it now installs but Nvidia/xorg fails to work. This is on Kubuntu, which so far looks like a gigantic pile of dung for Jaunty. At least Ubuntu 9.04 is fantastic!

---

### Post by antrunner85 on 2009-05-29
Hi everyone, 

I had the same problem but I think I found a solution.
Installing Ubuntu 9.04 from CD did not work and prompted the same error. However downloading wubi and place it under the same folder with the iso image seemed to work. I am just about restarting my computer to confirm.

---

### Post by minglis on 2009-06-07
Hi, I had the same problem, and as suggested by antrunner85, I simply placed the iso in the same dir as the wubi.exe and it worked fine.

---

### Post by sintroge on 2009-08-03
yes i had the same problem. downloading an iso and putting it in the dir worked for me as well (be sure you run it in admin mode in windows). additionalyl i recall i had to disable internet to avoid wubi from checking md5 sums online (the daily builds go out of date quickly).

---

### Post by chinasteve2000 on 2009-09-19
YES! That's it. Download the iso file and put it in the same folder as the wubi.exe application. 

Thanks everyone. 

BTW, my problem was that I forgot the password I gave for the installation. Ha! So wubi for some reason has troubles reinstalling without the iso right there. My error was this:

[INDENT]an error occurred

IOError: <urlopen error>

For more info, please see log file....
[/INDENT]

Thanks community,
Steve

---

### Post by clarke0iitg on 2010-05-02
it works! ... just kept the wubi installer and the iso in the same folder ... tried it on 10.01 lucid lynx (which is awesome btw)

---

### Post by gtd on 2010-09-27
I tried the suggestions several times. However, it fails trying to find the CD, the iso, etc. I deleted the user/temp/log file wubi creates. I started wubi again and it begins a download of an iso from the internet. I disabled the network and wubi fails. Nothing's perfect : ) I'll go with wubi downloading the iso. My fingers are crossed. For all you newbies Ubuntu is probably one of the best products you'll see. I began with slackware about 15 years ago. So I have a little linux experience.

---

