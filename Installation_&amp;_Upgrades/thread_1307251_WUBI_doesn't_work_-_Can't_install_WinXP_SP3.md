---
title: "WUBI doesn't work - Can't install WinXP SP3"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by byros on 2009-10-30
WUBI install fails no matter what, I'm trying within Windows XP SP3, I'm using the 9.10 CD.

After the WUBI installer inside Windows reaches 100% I get the following error
message:

An error occurred:
Invalid Argument
For more information please see the log file: C.\temp\wubi-9.10ubuntu1-rev1.60.log

[IMG]http://img503.imageshack.us/img503/5765/wubi.jpg[/IMG]

---See log at end of post---

I always had the same error with 9.04 and was never able to install it,
tried multiple versions of WUBI after the official release and none fixed the issue,
I never experienced this problem with 8.10 Intrepid Ibex, hell I even
got the creative drivers working on the 1st try for my X-fi xtreme gamer card
on 8.10 so I'm not that lost...

I've already downloaded and & burned 3 times the CD so it's not
 a corrupt ISO file. I can boot up 9.10 via Live Cd and then install & boot
 to a USB flash drive with no problems it's just the damned wubi installer
 that's not working well.

WUBI has become so frustrating that I'm tempted to go out and buy a copy of Windows 7 (vista that sort of works) and just forget about ubuntu once and for all.
 
 My specs:
 Intel Q6600
 2GB RAM
 250GB SATA HDD
 Nvidia 6800GS


------------------
Here's the log
------------------

10-31 02:55 INFO   root: === wubi 9.10ubuntu1 rev160 ===
10-31 02:55 DEBUG  root: Logfile is c:\temp\wubi-9.10ubuntu1-rev160.log
10-31 02:55 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
10-31 02:55 DEBUG  CommonBackend: data_dir=C:\Temp\pyl4.tmp\data
10-31 02:55 DEBUG  WindowsBackend: 7z=C:\Temp\pyl4.tmp\bin\7z.exe
10-31 02:55 DEBUG  CommonBackend: Fetching basic info...
10-31 02:55 DEBUG  CommonBackend: original_exe=D:\wubi.exe
10-31 02:55 DEBUG  CommonBackend: platform=win32
10-31 02:55 DEBUG  CommonBackend: osname=nt
10-31 02:55 DEBUG  CommonBackend: language=en_US
10-31 02:55 DEBUG  CommonBackend: encoding=cp1252
10-31 02:55 DEBUG  WindowsBackend: arch=amd64
10-31 02:55 DEBUG  CommonBackend: Parsing isolist=C:\Temp\pyl4.tmp\data\isolist.ini
10-31 02:55 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-31 02:55 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-31 02:55 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-31 02:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-31 02:55 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-31 02:55 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-31 02:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-31 02:55 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-31 02:55 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
10-31 02:55 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
10-31 02:55 DEBUG  WindowsBackend: Fetching host info...
10-31 02:55 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-31 02:55 DEBUG  WindowsBackend: windows version=xp
10-31 02:55 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
10-31 02:55 DEBUG  WindowsBackend: windows_sp=Service Pack 3
10-31 02:55 DEBUG  WindowsBackend: windows_build=2600
10-31 02:55 DEBUG  WindowsBackend: gmt=-6
10-31 02:55 DEBUG  WindowsBackend: country=US
10-31 02:55 DEBUG  WindowsBackend: timezone=America/Chicago
10-31 02:55 DEBUG  WindowsBackend: windows_username=Default
10-31 02:55 DEBUG  WindowsBackend: user_full_name=Default
10-31 02:55 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Default
10-31 02:55 DEBUG  WindowsBackend: windows_language_code=1033
10-31 02:55 DEBUG  WindowsBackend: windows_language=English
10-31 02:55 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
10-31 02:55 DEBUG  WindowsBackend: bootloader=xp
10-31 02:55 DEBUG  WindowsBackend: system_drive=Drive(C: hd 66671.21875 mb free fat32)
10-31 02:55 DEBUG  WindowsBackend: drive=Drive(C: hd 66671.21875 mb free fat32)
10-31 02:55 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
10-31 02:55 DEBUG  WindowsBackend: drive=Drive(E: hd 65248.46875 mb free fat32)
10-31 02:55 DEBUG  WindowsBackend: drive=Drive(F: hd 823473.96875 mb free fat32)
10-31 02:55 DEBUG  WindowsBackend: uninstaller_path=None
10-31 02:55 DEBUG  WindowsBackend: previous_target_dir=None
10-31 02:55 DEBUG  WindowsBackend: previous_distro_name=None
10-31 02:55 DEBUG  WindowsBackend: keyboard_id=67765258
10-31 02:55 DEBUG  WindowsBackend: keyboard_layout=us
10-31 02:55 DEBUG  WindowsBackend: keyboard_variant=
10-31 02:55 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-31 02:55 DEBUG  CommonBackend: locale=en_US.UTF-8
10-31 02:55 DEBUG  WindowsBackend: total_memory_mb=2046.79296875
10-31 02:55 DEBUG  CommonBackend: Searching ISOs on USB devices
10-31 02:55 DEBUG  CommonBackend: Searching for local CDs
10-31 02:55 DEBUG  Distro:   checking whether C:\Temp\pyl4.tmp is a valid Ubuntu CD
10-31 02:55 DEBUG  Distro:     does not contain C:\Temp\pyl4.tmp\casper\filesystem.squashfs
10-31 02:55 DEBUG  Distro:   checking whether C:\Temp\pyl4.tmp is a valid Ubuntu CD
10-31 02:55 DEBUG  Distro:     does not contain C:\Temp\pyl4.tmp\casper\filesystem.squashfs
10-31 02:55 DEBUG  Distro:   checking whether C:\Temp\pyl4.tmp is a valid Ubuntu Netbook Remix CD
10-31 02:55 DEBUG  Distro:     does not contain C:\Temp\pyl4.tmp\casper\filesystem.squashfs
10-31 02:55 DEBUG  Distro:   checking whether C:\Temp\pyl4.tmp is a valid Kubuntu CD
10-31 02:55 DEBUG  Distro:     does not contain C:\Temp\pyl4.tmp\casper\filesystem.squashfs
10-31 02:55 DEBUG  Distro:   checking whether C:\Temp\pyl4.tmp is a valid Kubuntu CD
10-31 02:55 DEBUG  Distro:     does not contain C:\Temp\pyl4.tmp\casper\filesystem.squashfs
10-31 02:55 DEBUG  Distro:   checking whether C:\Temp\pyl4.tmp is a valid Kubuntu Netbook CD
10-31 02:55 DEBUG  Distro:     does not contain C:\Temp\pyl4.tmp\casper\filesystem.squashfs
10-31 02:55 DEBUG  Distro:   checking whether C:\Temp\pyl4.tmp is a valid Xubuntu CD
10-31 02:55 DEBUG  Distro:     does not contain C:\Temp\pyl4.tmp\casper\filesystem.squashfs
10-31 02:55 DEBUG  Distro:   checking whether C:\Temp\pyl4.tmp is a valid Xubuntu CD
10-31 02:55 DEBUG  Distro:     does not contain C:\Temp\pyl4.tmp\casper\filesystem.squashfs
10-31 02:55 DEBUG  Distro:   checking whether C:\Temp\pyl4.tmp is a valid Mythbuntu CD
10-31 02:55 DEBUG  Distro:     does not contain C:\Temp\pyl4.tmp\casper\filesystem.squashfs
10-31 02:55 DEBUG  Distro:   checking whether C:\Temp\pyl4.tmp is a valid Mythbuntu CD
10-31 02:55 DEBUG  Distro:     does not contain C:\Temp\pyl4.tmp\casper\filesystem.squashfs
10-31 02:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-31 02:55 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
10-31 02:55 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
10-31 02:55 INFO   Distro: Found a valid CD for Ubuntu: D:\
10-31 02:55 INFO   root: Running the CD menu...
10-31 02:55 DEBUG  WindowsFrontend: __init__...
10-31 02:55 DEBUG  WindowsFrontend: on_init...
10-31 02:55 INFO   WinuiPage: appname=wubi, localedir=C:\Temp\pyl4.tmp\translations, languages=['en_US', 'en']
10-31 02:55 INFO   WinuiPage: appname=wubi, localedir=C:\Temp\pyl4.tmp\translations, languages=['en_US', 'en']
10-31 02:55 INFO   root: CD menu finished
10-31 02:55 INFO   root: Running the installer...
10-31 02:55 INFO   WinuiPage: appname=wubi, localedir=C:\Temp\pyl4.tmp\translations, languages=['en_US', 'en']
10-31 02:55 INFO   WinuiPage: appname=wubi, localedir=C:\Temp\pyl4.tmp\translations, languages=['en_US', 'en']
10-31 02:56 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=6000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=default
10-31 02:56 INFO   root: Received settings
10-31 02:56 INFO   WinuiPage: appname=wubi, localedir=C:\Temp\pyl4.tmp\translations, languages=['en_US', 'en']
10-31 02:56 DEBUG  TaskList: # Running tasklist...
10-31 02:56 DEBUG  TaskList: ## Running select_target_dir...
10-31 02:56 INFO   WindowsBackend: Installing into C:\ubuntu
10-31 02:56 DEBUG  TaskList: ## Finished select_target_dir
10-31 02:56 DEBUG  TaskList: ## Running create_dir_structure...
10-31 02:56 DEBUG  CommonBackend: Creating dir C:\ubuntu
10-31 02:56 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
10-31 02:56 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
10-31 02:56 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
10-31 02:56 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
10-31 02:56 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
10-31 02:56 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
10-31 02:56 DEBUG  TaskList: ## Finished create_dir_structure
10-31 02:56 DEBUG  TaskList: ## Running uncompress_target_dir...
10-31 02:56 DEBUG  TaskList: ## Finished uncompress_target_dir
10-31 02:56 DEBUG  TaskList: ## Running create_uninstaller...
10-31 02:56 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
10-31 02:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
10-31 02:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
10-31 02:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-31 02:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
10-31 02:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
10-31 02:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-31 02:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
10-31 02:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
10-31 02:56 DEBUG  TaskList: ## Finished create_uninstaller
10-31 02:56 DEBUG  TaskList: ## Running copy_installation_files...
10-31 02:56 DEBUG  WindowsBackend: Copying C:\Temp\pyl4.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
10-31 02:56 DEBUG  WindowsBackend: Copying C:\Temp\pyl4.tmp\winboot -> C:\ubuntu\winboot
10-31 02:56 DEBUG  WindowsBackend: Copying C:\Temp\pyl4.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
10-31 02:56 DEBUG  TaskList: ## Finished copy_installation_files
10-31 02:56 DEBUG  TaskList: ## Running get_iso...
10-31 02:56 DEBUG  TaskList: New task copy_file
10-31 02:56 DEBUG  TaskList: ### Running copy_file...
10-31 02:59 DEBUG  TaskList: ### Finished copy_file
10-31 02:59 ERROR  TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 22] Invalid argument
10-31 02:59 DEBUG  TaskList: # Cancelling tasklist
10-31 02:59 DEBUG  TaskList: New task check_iso
10-31 02:59 ERROR  root: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 126, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 22] Invalid argument
10-31 02:59 DEBUG  CommonBackend: Searching for local ISO
10-31 02:59 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
10-31 02:59 DEBUG  TaskList: New task get_metalink
10-31 02:59 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
10-31 02:59 DEBUG  TaskList: # Cancelling tasklist
10-31 02:59 DEBUG  TaskList: # Finished tasklist
10-31 03:01 INFO   root: === wubi 9.10ubuntu1 rev160 ===
10-31 03:01 DEBUG  root: Logfile is c:\temp\wubi-9.10ubuntu1-rev160.log
10-31 03:01 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
10-31 03:01 DEBUG  CommonBackend: data_dir=C:\Temp\pyl32.tmp\data
10-31 03:01 DEBUG  WindowsBackend: 7z=C:\Temp\pyl32.tmp\bin\7z.exe
10-31 03:01 DEBUG  CommonBackend: Fetching basic info...
10-31 03:01 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
10-31 03:01 DEBUG  CommonBackend: platform=win32
10-31 03:01 DEBUG  CommonBackend: osname=nt
10-31 03:01 DEBUG  CommonBackend: language=en_US
10-31 03:01 DEBUG  CommonBackend: encoding=cp1252
10-31 03:01 DEBUG  WindowsBackend: arch=amd64
10-31 03:01 DEBUG  CommonBackend: Parsing isolist=C:\Temp\pyl32.tmp\data\isolist.ini
10-31 03:01 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-31 03:01 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-31 03:01 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-31 03:01 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-31 03:01 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-31 03:01 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-31 03:01 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-31 03:01 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-31 03:01 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
10-31 03:01 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
10-31 03:01 DEBUG  WindowsBackend: Fetching host info...
10-31 03:01 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-31 03:01 DEBUG  WindowsBackend: windows version=xp
10-31 03:01 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
10-31 03:01 DEBUG  WindowsBackend: windows_sp=Service Pack 3
10-31 03:01 DEBUG  WindowsBackend: windows_build=2600
10-31 03:01 DEBUG  WindowsBackend: gmt=-6
10-31 03:01 DEBUG  WindowsBackend: country=US
10-31 03:01 DEBUG  WindowsBackend: timezone=America/Chicago
10-31 03:01 DEBUG  WindowsBackend: windows_username=Default
10-31 03:01 DEBUG  WindowsBackend: user_full_name=Default
10-31 03:01 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Default
10-31 03:01 DEBUG  WindowsBackend: windows_language_code=1033
10-31 03:01 DEBUG  WindowsBackend: windows_language=English
10-31 03:01 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
10-31 03:01 DEBUG  WindowsBackend: bootloader=xp
10-31 03:01 DEBUG  WindowsBackend: system_drive=Drive(C: hd 66001.0625 mb free fat32)
10-31 03:01 DEBUG  WindowsBackend: drive=Drive(C: hd 66001.0625 mb free fat32)
10-31 03:01 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
10-31 03:01 DEBUG  WindowsBackend: drive=Drive(E: hd 65248.46875 mb free fat32)
10-31 03:01 DEBUG  WindowsBackend: drive=Drive(F: hd 823473.96875 mb free fat32)
10-31 03:01 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
10-31 03:01 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
10-31 03:01 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
10-31 03:01 DEBUG  WindowsBackend: keyboard_id=67765258
10-31 03:01 DEBUG  WindowsBackend: keyboard_layout=us
10-31 03:01 DEBUG  WindowsBackend: keyboard_variant=
10-31 03:01 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-31 03:01 DEBUG  CommonBackend: locale=en_US.UTF-8
10-31 03:01 DEBUG  WindowsBackend: total_memory_mb=2046.79296875
10-31 03:01 DEBUG  CommonBackend: Searching ISOs on USB devices
10-31 03:01 DEBUG  CommonBackend: Searching for local CDs
10-31 03:01 DEBUG  Distro:   checking whether C:\Temp\pyl32.tmp is a valid Ubuntu CD
10-31 03:01 DEBUG  Distro:     does not contain C:\Temp\pyl32.tmp\casper\filesystem.squashfs
10-31 03:01 DEBUG  Distro:   checking whether C:\Temp\pyl32.tmp is a valid Ubuntu CD
10-31 03:01 DEBUG  Distro:     does not contain C:\Temp\pyl32.tmp\casper\filesystem.squashfs
10-31 03:01 DEBUG  Distro:   checking whether C:\Temp\pyl32.tmp is a valid Ubuntu Netbook Remix CD
10-31 03:01 DEBUG  Distro:     does not contain C:\Temp\pyl32.tmp\casper\filesystem.squashfs
10-31 03:01 DEBUG  Distro:   checking whether C:\Temp\pyl32.tmp is a valid Kubuntu CD
10-31 03:01 DEBUG  Distro:     does not contain C:\Temp\pyl32.tmp\casper\filesystem.squashfs
10-31 03:01 DEBUG  Distro:   checking whether C:\Temp\pyl32.tmp is a valid Kubuntu CD
10-31 03:01 DEBUG  Distro:     does not contain C:\Temp\pyl32.tmp\casper\filesystem.squashfs
10-31 03:01 DEBUG  Distro:   checking whether C:\Temp\pyl32.tmp is a valid Kubuntu Netbook CD
10-31 03:01 DEBUG  Distro:     does not contain C:\Temp\pyl32.tmp\casper\filesystem.squashfs
10-31 03:01 DEBUG  Distro:   checking whether C:\Temp\pyl32.tmp is a valid Xubuntu CD
10-31 03:01 DEBUG  Distro:     does not contain C:\Temp\pyl32.tmp\casper\filesystem.squashfs
10-31 03:01 DEBUG  Distro:   checking whether C:\Temp\pyl32.tmp is a valid Xubuntu CD
10-31 03:01 DEBUG  Distro:     does not contain C:\Temp\pyl32.tmp\casper\filesystem.squashfs
10-31 03:01 DEBUG  Distro:   checking whether C:\Temp\pyl32.tmp is a valid Mythbuntu CD
10-31 03:01 DEBUG  Distro:     does not contain C:\Temp\pyl32.tmp\casper\filesystem.squashfs
10-31 03:01 DEBUG  Distro:   checking whether C:\Temp\pyl32.tmp is a valid Mythbuntu CD
10-31 03:01 DEBUG  Distro:     does not contain C:\Temp\pyl32.tmp\casper\filesystem.squashfs
10-31 03:01 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-31 03:01 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
10-31 03:01 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
10-31 03:01 INFO   Distro: Found a valid CD for Ubuntu: D:\
10-31 03:01 INFO   root: Running the uninstaller...
10-31 03:01 INFO   CommonBackend: This is the uninstaller running
10-31 03:01 DEBUG  WindowsFrontend: __init__...
10-31 03:01 DEBUG  WindowsFrontend: on_init...
10-31 03:01 INFO   WinuiPage: appname=wubi, localedir=C:\Temp\pyl32.tmp\translations, languages=['en_US', 'en']
10-31 03:01 INFO   WindowsFrontend: Operation cancelled
10-31 03:01 DEBUG  WindowsFrontend: frontend.quit
10-31 03:01 DEBUG  WindowsFrontend: frontend.on_quit
10-31 03:01 DEBUG  root: application.on_quit
10-31 03:01 INFO   root: sys.exit
10-31 03:11 INFO   root: === wubi 9.10ubuntu1 rev160 ===
10-31 03:11 DEBUG  root: Logfile is c:\temp\wubi-9.10ubuntu1-rev160.log
10-31 03:11 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
10-31 03:11 DEBUG  CommonBackend: data_dir=C:\Temp\pyl5E.tmp\data
10-31 03:11 DEBUG  WindowsBackend: 7z=C:\Temp\pyl5E.tmp\bin\7z.exe
10-31 03:11 DEBUG  CommonBackend: Fetching basic info...
10-31 03:11 DEBUG  CommonBackend: original_exe=D:\wubi.exe
10-31 03:11 DEBUG  CommonBackend: platform=win32
10-31 03:11 DEBUG  CommonBackend: osname=nt
10-31 03:11 DEBUG  CommonBackend: language=en_US
10-31 03:11 DEBUG  CommonBackend: encoding=cp1252
10-31 03:11 DEBUG  WindowsBackend: arch=amd64
10-31 03:11 DEBUG  CommonBackend: Parsing isolist=C:\Temp\pyl5E.tmp\data\isolist.ini
10-31 03:11 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-31 03:11 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-31 03:11 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-31 03:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-31 03:11 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-31 03:11 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-31 03:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-31 03:11 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-31 03:11 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
10-31 03:11 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
10-31 03:11 DEBUG  WindowsBackend: Fetching host info...
10-31 03:11 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-31 03:11 DEBUG  WindowsBackend: windows version=xp
10-31 03:11 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
10-31 03:11 DEBUG  WindowsBackend: windows_sp=Service Pack 3
10-31 03:11 DEBUG  WindowsBackend: windows_build=2600
10-31 03:11 DEBUG  WindowsBackend: gmt=-6
10-31 03:11 DEBUG  WindowsBackend: country=US
10-31 03:11 DEBUG  WindowsBackend: timezone=America/Chicago
10-31 03:11 DEBUG  WindowsBackend: windows_username=Default
10-31 03:11 DEBUG  WindowsBackend: user_full_name=Default
10-31 03:11 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Default
10-31 03:11 DEBUG  WindowsBackend: windows_language_code=1033
10-31 03:11 DEBUG  WindowsBackend: windows_language=English
10-31 03:11 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
10-31 03:11 DEBUG  WindowsBackend: bootloader=xp
10-31 03:11 DEBUG  WindowsBackend: system_drive=Drive(C: hd 65994.25 mb free fat32)
10-31 03:11 DEBUG  WindowsBackend: drive=Drive(C: hd 65994.25 mb free fat32)
10-31 03:11 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
10-31 03:11 DEBUG  WindowsBackend: drive=Drive(E: hd 65248.46875 mb free fat32)
10-31 03:11 DEBUG  WindowsBackend: drive=Drive(F: hd 823473.96875 mb free fat32)
10-31 03:11 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
10-31 03:11 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
10-31 03:11 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
10-31 03:11 DEBUG  WindowsBackend: keyboard_id=67765258
10-31 03:11 DEBUG  WindowsBackend: keyboard_layout=us
10-31 03:11 DEBUG  WindowsBackend: keyboard_variant=
10-31 03:11 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-31 03:11 DEBUG  CommonBackend: locale=en_US.UTF-8
10-31 03:11 DEBUG  WindowsBackend: total_memory_mb=2046.79296875
10-31 03:11 DEBUG  CommonBackend: Searching ISOs on USB devices
10-31 03:11 DEBUG  CommonBackend: Searching for local CDs
10-31 03:11 DEBUG  Distro:   checking whether C:\Temp\pyl5E.tmp is a valid Ubuntu CD
10-31 03:11 DEBUG  Distro:     does not contain C:\Temp\pyl5E.tmp\casper\filesystem.squashfs
10-31 03:11 DEBUG  Distro:   checking whether C:\Temp\pyl5E.tmp is a valid Ubuntu CD
10-31 03:11 DEBUG  Distro:     does not contain C:\Temp\pyl5E.tmp\casper\filesystem.squashfs
10-31 03:11 DEBUG  Distro:   checking whether C:\Temp\pyl5E.tmp is a valid Ubuntu Netbook Remix CD
10-31 03:11 DEBUG  Distro:     does not contain C:\Temp\pyl5E.tmp\casper\filesystem.squashfs
10-31 03:11 DEBUG  Distro:   checking whether C:\Temp\pyl5E.tmp is a valid Kubuntu CD
10-31 03:11 DEBUG  Distro:     does not contain C:\Temp\pyl5E.tmp\casper\filesystem.squashfs
10-31 03:11 DEBUG  Distro:   checking whether C:\Temp\pyl5E.tmp is a valid Kubuntu CD
10-31 03:11 DEBUG  Distro:     does not contain C:\Temp\pyl5E.tmp\casper\filesystem.squashfs
10-31 03:11 DEBUG  Distro:   checking whether C:\Temp\pyl5E.tmp is a valid Kubuntu Netbook CD
10-31 03:11 DEBUG  Distro:     does not contain C:\Temp\pyl5E.tmp\casper\filesystem.squashfs
10-31 03:11 DEBUG  Distro:   checking whether C:\Temp\pyl5E.tmp is a valid Xubuntu CD
10-31 03:11 DEBUG  Distro:     does not contain C:\Temp\pyl5E.tmp\casper\filesystem.squashfs
10-31 03:11 DEBUG  Distro:   checking whether C:\Temp\pyl5E.tmp is a valid Xubuntu CD
10-31 03:11 DEBUG  Distro:     does not contain C:\Temp\pyl5E.tmp\casper\filesystem.squashfs
10-31 03:11 DEBUG  Distro:   checking whether C:\Temp\pyl5E.tmp is a valid Mythbuntu CD
10-31 03:11 DEBUG  Distro:     does not contain C:\Temp\pyl5E.tmp\casper\filesystem.squashfs
10-31 03:11 DEBUG  Distro:   checking whether C:\Temp\pyl5E.tmp is a valid Mythbuntu CD
10-31 03:11 DEBUG  Distro:     does not contain C:\Temp\pyl5E.tmp\casper\filesystem.squashfs
10-31 03:11 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-31 03:11 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
10-31 03:11 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
10-31 03:11 INFO   Distro: Found a valid CD for Ubuntu: D:\
10-31 03:11 INFO   root: Running the CD menu...
10-31 03:11 DEBUG  WindowsFrontend: __init__...
10-31 03:11 DEBUG  WindowsFrontend: on_init...
10-31 03:11 INFO   WinuiPage: appname=wubi, localedir=C:\Temp\pyl5E.tmp\translations, languages=['en_US', 'en']
10-31 03:11 INFO   WinuiPage: appname=wubi, localedir=C:\Temp\pyl5E.tmp\translations, languages=['en_US', 'en']
10-31 03:11 INFO   root: CD menu finished
10-31 03:11 INFO   root: Already installed, running the uninstaller...
10-31 03:11 INFO   root: Running the uninstaller...
10-31 03:11 INFO   CommonBackend: This is the uninstaller running
10-31 03:11 INFO   WinuiPage: appname=wubi, localedir=C:\Temp\pyl5E.tmp\translations, languages=['en_US', 'en']
10-31 03:11 INFO   root: Received settings
10-31 03:11 INFO   WinuiPage: appname=wubi, localedir=C:\Temp\pyl5E.tmp\translations, languages=['en_US', 'en']
10-31 03:11 DEBUG  TaskList: # Running tasklist...
10-31 03:11 DEBUG  TaskList: ## Running Backup ISO...
10-31 03:11 DEBUG  TaskList: ## Finished Backup ISO
10-31 03:11 DEBUG  TaskList: ## Running Remove bootloader entry...
10-31 03:11 ERROR  WindowsBackend: Cannot find bcdedit
10-31 03:11 DEBUG  WindowsBackend: undo_bootini C:
10-31 03:11 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 65994.25 mb free fat32)
10-31 03:11 DEBUG  WindowsBackend: undo_bootini E:
10-31 03:11 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 65248.46875 mb free fat32)
10-31 03:11 DEBUG  WindowsBackend: undo_bootini F:
10-31 03:11 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 823473.96875 mb free fat32)
10-31 03:11 DEBUG  TaskList: ## Finished Remove bootloader entry
10-31 03:11 DEBUG  TaskList: ## Running Remove target dir...
10-31 03:11 DEBUG  CommonBackend: Deleting C:\ubuntu
10-31 03:11 DEBUG  TaskList: ## Finished Remove target dir
10-31 03:11 DEBUG  TaskList: ## Running Remove registry key...
10-31 03:11 DEBUG  TaskList: ## Finished Remove registry key
10-31 03:11 DEBUG  TaskList: # Finished tasklist
10-31 03:11 INFO   root: Almost finished uninstalling
10-31 03:11 INFO   root: Finished uninstallation
10-31 03:11 DEBUG  CommonBackend: Fetching basic info...
10-31 03:11 DEBUG  CommonBackend: original_exe=D:\wubi.exe
10-31 03:11 DEBUG  CommonBackend: platform=win32
10-31 03:11 DEBUG  CommonBackend: osname=nt
10-31 03:11 DEBUG  WindowsBackend: arch=amd64
10-31 03:11 DEBUG  CommonBackend: Parsing isolist=C:\Temp\pyl5E.tmp\data\isolist.ini
10-31 03:11 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-31 03:11 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-31 03:11 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-31 03:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-31 03:11 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-31 03:11 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-31 03:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-31 03:11 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-31 03:11 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
10-31 03:11 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
10-31 03:11 DEBUG  WindowsBackend: Fetching host info...
10-31 03:11 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-31 03:11 DEBUG  WindowsBackend: windows version=xp
10-31 03:11 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
10-31 03:11 DEBUG  WindowsBackend: windows_sp=Service Pack 3
10-31 03:11 DEBUG  WindowsBackend: windows_build=2600
10-31 03:11 DEBUG  WindowsBackend: gmt=-6
10-31 03:11 DEBUG  WindowsBackend: country=US
10-31 03:11 DEBUG  WindowsBackend: timezone=America/Chicago
10-31 03:11 DEBUG  WindowsBackend: windows_username=Default
10-31 03:11 DEBUG  WindowsBackend: user_full_name=Default
10-31 03:11 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Default
10-31 03:11 DEBUG  WindowsBackend: windows_language_code=1033
10-31 03:11 DEBUG  WindowsBackend: windows_language=English
10-31 03:11 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
10-31 03:11 DEBUG  WindowsBackend: bootloader=xp
10-31 03:11 DEBUG  WindowsBackend: system_drive=Drive(C: hd 66685.3125 mb free fat32)
10-31 03:11 DEBUG  WindowsBackend: drive=Drive(C: hd 66685.3125 mb free fat32)
10-31 03:11 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
10-31 03:11 DEBUG  WindowsBackend: drive=Drive(E: hd 65248.46875 mb free fat32)
10-31 03:11 DEBUG  WindowsBackend: drive=Drive(F: hd 823473.96875 mb free fat32)
10-31 03:11 DEBUG  WindowsBackend: uninstaller_path=None
10-31 03:11 DEBUG  WindowsBackend: previous_target_dir=None
10-31 03:11 DEBUG  WindowsBackend: previous_distro_name=None
10-31 03:11 DEBUG  WindowsBackend: keyboard_id=67765258
10-31 03:11 DEBUG  WindowsBackend: keyboard_layout=us
10-31 03:11 DEBUG  WindowsBackend: keyboard_variant=
10-31 03:11 DEBUG  WindowsBackend: total_memory_mb=2046.79296875
10-31 03:11 DEBUG  CommonBackend: Searching ISOs on USB devices
10-31 03:11 DEBUG  CommonBackend: Searching for local CDs
10-31 03:11 DEBUG  Distro:   checking whether C:\Temp\pyl5E.tmp is a valid Ubuntu CD
10-31 03:11 DEBUG  Distro:     does not contain C:\Temp\pyl5E.tmp\casper\filesystem.squashfs
10-31 03:11 DEBUG  Distro:   checking whether C:\Temp\pyl5E.tmp is a valid Ubuntu CD
10-31 03:11 DEBUG  Distro:     does not contain C:\Temp\pyl5E.tmp\casper\filesystem.squashfs
10-31 03:11 DEBUG  Distro:   checking whether C:\Temp\pyl5E.tmp is a valid Ubuntu Netbook Remix CD
10-31 03:11 DEBUG  Distro:     does not contain C:\Temp\pyl5E.tmp\casper\filesystem.squashfs
10-31 03:11 DEBUG  Distro:   checking whether C:\Temp\pyl5E.tmp is a valid Kubuntu CD
10-31 03:11 DEBUG  Distro:     does not contain C:\Temp\pyl5E.tmp\casper\filesystem.squashfs
10-31 03:11 DEBUG  Distro:   checking whether C:\Temp\pyl5E.tmp is a valid Kubuntu CD
10-31 03:11 DEBUG  Distro:     does not contain C:\Temp\pyl5E.tmp\casper\filesystem.squashfs
10-31 03:11 DEBUG  Distro:   checking whether C:\Temp\pyl5E.tmp is a valid Kubuntu Netbook CD
10-31 03:11 DEBUG  Distro:     does not contain C:\Temp\pyl5E.tmp\casper\filesystem.squashfs
10-31 03:11 DEBUG  Distro:   checking whether C:\Temp\pyl5E.tmp is a valid Xubuntu CD
10-31 03:11 DEBUG  Distro:     does not contain C:\Temp\pyl5E.tmp\casper\filesystem.squashfs
10-31 03:11 DEBUG  Distro:   checking whether C:\Temp\pyl5E.tmp is a valid Xubuntu CD
10-31 03:11 DEBUG  Distro:     does not contain C:\Temp\pyl5E.tmp\casper\filesystem.squashfs
10-31 03:11 DEBUG  Distro:   checking whether C:\Temp\pyl5E.tmp is a valid Mythbuntu CD
10-31 03:11 DEBUG  Distro:     does not contain C:\Temp\pyl5E.tmp\casper\filesystem.squashfs
10-31 03:11 DEBUG  Distro:   checking whether C:\Temp\pyl5E.tmp is a valid Mythbuntu CD
10-31 03:11 DEBUG  Distro:     does not contain C:\Temp\pyl5E.tmp\casper\filesystem.squashfs
10-31 03:11 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-31 03:11 INFO   Distro: Found a valid CD for Ubuntu: D:\
10-31 03:11 INFO   root: Running the installer...
10-31 03:11 INFO   WinuiPage: appname=wubi, localedir=C:\Temp\pyl5E.tmp\translations, languages=['en_US', 'en']
10-31 03:11 INFO   WinuiPage: appname=wubi, localedir=C:\Temp\pyl5E.tmp\translations, languages=['en_US', 'en']
10-31 03:12 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=6000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=default
10-31 03:12 INFO   root: Received settings
10-31 03:12 INFO   WinuiPage: appname=wubi, localedir=C:\Temp\pyl5E.tmp\translations, languages=['en_US', 'en']
10-31 03:12 DEBUG  TaskList: # Running tasklist...
10-31 03:12 DEBUG  TaskList: ## Running select_target_dir...
10-31 03:12 INFO   WindowsBackend: Installing into C:\ubuntu
10-31 03:12 DEBUG  TaskList: ## Finished select_target_dir
10-31 03:12 DEBUG  TaskList: ## Running create_dir_structure...
10-31 03:12 DEBUG  CommonBackend: Creating dir C:\ubuntu
10-31 03:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
10-31 03:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
10-31 03:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
10-31 03:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
10-31 03:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
10-31 03:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
10-31 03:12 DEBUG  TaskList: ## Finished create_dir_structure
10-31 03:12 DEBUG  TaskList: ## Running uncompress_target_dir...
10-31 03:12 DEBUG  TaskList: ## Finished uncompress_target_dir
10-31 03:12 DEBUG  TaskList: ## Running create_uninstaller...
10-31 03:12 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
10-31 03:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
10-31 03:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
10-31 03:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-31 03:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
10-31 03:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
10-31 03:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-31 03:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
10-31 03:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
10-31 03:12 DEBUG  TaskList: ## Finished create_uninstaller
10-31 03:12 DEBUG  TaskList: ## Running copy_installation_files...
10-31 03:12 DEBUG  WindowsBackend: Copying C:\Temp\pyl5E.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
10-31 03:12 DEBUG  WindowsBackend: Copying C:\Temp\pyl5E.tmp\winboot -> C:\ubuntu\winboot
10-31 03:12 DEBUG  WindowsBackend: Copying C:\Temp\pyl5E.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
10-31 03:12 DEBUG  TaskList: ## Finished copy_installation_files
10-31 03:12 DEBUG  TaskList: ## Running get_iso...
10-31 03:12 DEBUG  TaskList: New task copy_file
10-31 03:12 DEBUG  TaskList: ### Running copy_file...
10-31 03:14 DEBUG  TaskList: ### Finished copy_file
10-31 03:14 ERROR  TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 22] Invalid argument
10-31 03:14 DEBUG  TaskList: # Cancelling tasklist
10-31 03:14 DEBUG  TaskList: New task check_iso
10-31 03:14 ERROR  root: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 126, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 22] Invalid argument
10-31 03:14 DEBUG  CommonBackend: Searching for local ISO
10-31 03:14 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
10-31 03:14 DEBUG  TaskList: New task get_metalink
10-31 03:14 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
10-31 03:14 DEBUG  TaskList: # Cancelling tasklist
10-31 03:14 DEBUG  TaskList: # Finished tasklist
10-31 03:27 INFO   root: === wubi 9.10ubuntu1 rev160 ===
10-31 03:27 DEBUG  root: Logfile is c:\temp\wubi-9.10ubuntu1-rev160.log
10-31 03:27 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
10-31 03:27 DEBUG  CommonBackend: data_dir=C:\Temp\pyl9D.tmp\data
10-31 03:27 DEBUG  WindowsBackend: 7z=C:\Temp\pyl9D.tmp\bin\7z.exe
10-31 03:27 DEBUG  CommonBackend: Fetching basic info...
10-31 03:27 DEBUG  CommonBackend: original_exe=D:\wubi.exe
10-31 03:27 DEBUG  CommonBackend: platform=win32
10-31 03:27 DEBUG  CommonBackend: osname=nt
10-31 03:27 DEBUG  CommonBackend: language=en_US
10-31 03:27 DEBUG  CommonBackend: encoding=cp1252
10-31 03:27 DEBUG  WindowsBackend: arch=amd64
10-31 03:27 DEBUG  CommonBackend: Parsing isolist=C:\Temp\pyl9D.tmp\data\isolist.ini
10-31 03:27 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-31 03:27 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-31 03:27 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-31 03:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-31 03:27 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-31 03:27 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-31 03:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-31 03:27 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-31 03:27 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
10-31 03:27 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
10-31 03:27 DEBUG  WindowsBackend: Fetching host info...
10-31 03:27 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-31 03:27 DEBUG  WindowsBackend: windows version=xp
10-31 03:27 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
10-31 03:27 DEBUG  WindowsBackend: windows_sp=Service Pack 3
10-31 03:27 DEBUG  WindowsBackend: windows_build=2600
10-31 03:27 DEBUG  WindowsBackend: gmt=-6
10-31 03:27 DEBUG  WindowsBackend: country=US
10-31 03:27 DEBUG  WindowsBackend: timezone=America/Chicago
10-31 03:27 DEBUG  WindowsBackend: windows_username=Default
10-31 03:27 DEBUG  WindowsBackend: user_full_name=Default
10-31 03:27 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Default
10-31 03:27 DEBUG  WindowsBackend: windows_language_code=1033
10-31 03:27 DEBUG  WindowsBackend: windows_language=English
10-31 03:27 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
10-31 03:27 DEBUG  WindowsBackend: bootloader=xp
10-31 03:27 DEBUG  WindowsBackend: system_drive=Drive(C: hd 65984.1875 mb free fat32)
10-31 03:27 DEBUG  WindowsBackend: drive=Drive(C: hd 65984.1875 mb free fat32)
10-31 03:27 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
10-31 03:27 DEBUG  WindowsBackend: drive=Drive(E: hd 65248.46875 mb free fat32)
10-31 03:27 DEBUG  WindowsBackend: drive=Drive(F: hd 823473.96875 mb free fat32)
10-31 03:27 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
10-31 03:27 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
10-31 03:27 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
10-31 03:27 DEBUG  WindowsBackend: keyboard_id=67765258
10-31 03:27 DEBUG  WindowsBackend: keyboard_layout=us
10-31 03:27 DEBUG  WindowsBackend: keyboard_variant=
10-31 03:27 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-31 03:27 DEBUG  CommonBackend: locale=en_US.UTF-8
10-31 03:27 DEBUG  WindowsBackend: total_memory_mb=2046.79296875
10-31 03:27 DEBUG  CommonBackend: Searching ISOs on USB devices
10-31 03:27 DEBUG  CommonBackend: Searching for local CDs
10-31 03:27 DEBUG  Distro:   checking whether C:\Temp\pyl9D.tmp is a valid Ubuntu CD
10-31 03:27 DEBUG  Distro:     does not contain C:\Temp\pyl9D.tmp\casper\filesystem.squashfs
10-31 03:27 DEBUG  Distro:   checking whether C:\Temp\pyl9D.tmp is a valid Ubuntu CD
10-31 03:27 DEBUG  Distro:     does not contain C:\Temp\pyl9D.tmp\casper\filesystem.squashfs
10-31 03:27 DEBUG  Distro:   checking whether C:\Temp\pyl9D.tmp is a valid Ubuntu Netbook Remix CD
10-31 03:27 DEBUG  Distro:     does not contain C:\Temp\pyl9D.tmp\casper\filesystem.squashfs
10-31 03:27 DEBUG  Distro:   checking whether C:\Temp\pyl9D.tmp is a valid Kubuntu CD
10-31 03:27 DEBUG  Distro:     does not contain C:\Temp\pyl9D.tmp\casper\filesystem.squashfs
10-31 03:27 DEBUG  Distro:   checking whether C:\Temp\pyl9D.tmp is a valid Kubuntu CD
10-31 03:27 DEBUG  Distro:     does not contain C:\Temp\pyl9D.tmp\casper\filesystem.squashfs
10-31 03:27 DEBUG  Distro:   checking whether C:\Temp\pyl9D.tmp is a valid Kubuntu Netbook CD
10-31 03:27 DEBUG  Distro:     does not contain C:\Temp\pyl9D.tmp\casper\filesystem.squashfs
10-31 03:27 DEBUG  Distro:   checking whether C:\Temp\pyl9D.tmp is a valid Xubuntu CD
10-31 03:27 DEBUG  Distro:     does not contain C:\Temp\pyl9D.tmp\casper\filesystem.squashfs
10-31 03:27 DEBUG  Distro:   checking whether C:\Temp\pyl9D.tmp is a valid Xubuntu CD
10-31 03:27 DEBUG  Distro:     does not contain C:\Temp\pyl9D.tmp\casper\filesystem.squashfs
10-31 03:27 DEBUG  Distro:   checking whether C:\Temp\pyl9D.tmp is a valid Mythbuntu CD
10-31 03:27 DEBUG  Distro:     does not contain C:\Temp\pyl9D.tmp\casper\filesystem.squashfs
10-31 03:27 DEBUG  Distro:   checking whether C:\Temp\pyl9D.tmp is a valid Mythbuntu CD
10-31 03:27 DEBUG  Distro:     does not contain C:\Temp\pyl9D.tmp\casper\filesystem.squashfs
10-31 03:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-31 03:27 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
10-31 03:27 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
10-31 03:27 INFO   Distro: Found a valid CD for Ubuntu: D:\
10-31 03:27 INFO   root: Running the CD menu...
10-31 03:27 DEBUG  WindowsFrontend: __init__...
10-31 03:27 DEBUG  WindowsFrontend: on_init...
10-31 03:27 INFO   WinuiPage: appname=wubi, localedir=C:\Temp\pyl9D.tmp\translations, languages=['en_US', 'en']
10-31 03:27 INFO   WinuiPage: appname=wubi, localedir=C:\Temp\pyl9D.tmp\translations, languages=['en_US', 'en']
10-31 03:27 INFO   root: CD menu finished
10-31 03:27 INFO   root: Already installed, running the uninstaller...
10-31 03:27 INFO   root: Running the uninstaller...
10-31 03:27 INFO   CommonBackend: This is the uninstaller running
10-31 03:27 INFO   WinuiPage: appname=wubi, localedir=C:\Temp\pyl9D.tmp\translations, languages=['en_US', 'en']
10-31 03:28 INFO   root: Received settings
10-31 03:28 INFO   WinuiPage: appname=wubi, localedir=C:\Temp\pyl9D.tmp\translations, languages=['en_US', 'en']
10-31 03:28 DEBUG  TaskList: # Running tasklist...
10-31 03:28 DEBUG  TaskList: ## Running Backup ISO...
10-31 03:28 DEBUG  TaskList: ## Finished Backup ISO
10-31 03:28 DEBUG  TaskList: ## Running Remove bootloader entry...
10-31 03:28 ERROR  WindowsBackend: Cannot find bcdedit
10-31 03:28 DEBUG  WindowsBackend: undo_bootini C:
10-31 03:28 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 65984.1875 mb free fat32)
10-31 03:28 DEBUG  WindowsBackend: undo_bootini E:
10-31 03:28 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 65248.46875 mb free fat32)
10-31 03:28 DEBUG  WindowsBackend: undo_bootini F:
10-31 03:28 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 823473.96875 mb free fat32)
10-31 03:28 DEBUG  TaskList: ## Finished Remove bootloader entry
10-31 03:28 DEBUG  TaskList: ## Running Remove target dir...
10-31 03:28 DEBUG  CommonBackend: Deleting C:\ubuntu
10-31 03:28 DEBUG  TaskList: ## Finished Remove target dir
10-31 03:28 DEBUG  TaskList: ## Running Remove registry key...
10-31 03:28 DEBUG  TaskList: ## Finished Remove registry key
10-31 03:28 DEBUG  TaskList: # Finished tasklist
10-31 03:28 INFO   root: Almost finished uninstalling
10-31 03:28 INFO   root: Finished uninstallation
10-31 03:28 DEBUG  CommonBackend: Fetching basic info...
10-31 03:28 DEBUG  CommonBackend: original_exe=D:\wubi.exe
10-31 03:28 DEBUG  CommonBackend: platform=win32
10-31 03:28 DEBUG  CommonBackend: osname=nt
10-31 03:28 DEBUG  WindowsBackend: arch=amd64
10-31 03:28 DEBUG  CommonBackend: Parsing isolist=C:\Temp\pyl9D.tmp\data\isolist.ini
10-31 03:28 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-31 03:28 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-31 03:28 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-31 03:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-31 03:28 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-31 03:28 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-31 03:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-31 03:28 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-31 03:28 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
10-31 03:28 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
10-31 03:28 DEBUG  WindowsBackend: Fetching host info...
10-31 03:28 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-31 03:28 DEBUG  WindowsBackend: windows version=xp
10-31 03:28 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
10-31 03:28 DEBUG  WindowsBackend: windows_sp=Service Pack 3
10-31 03:28 DEBUG  WindowsBackend: windows_build=2600
10-31 03:28 DEBUG  WindowsBackend: gmt=-6
10-31 03:28 DEBUG  WindowsBackend: country=US
10-31 03:28 DEBUG  WindowsBackend: timezone=America/Chicago
10-31 03:28 DEBUG  WindowsBackend: windows_username=Default
10-31 03:28 DEBUG  WindowsBackend: user_full_name=Default
10-31 03:28 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Default
10-31 03:28 DEBUG  WindowsBackend: windows_language_code=1033
10-31 03:28 DEBUG  WindowsBackend: windows_language=English
10-31 03:28 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
10-31 03:28 DEBUG  WindowsBackend: bootloader=xp
10-31 03:28 DEBUG  WindowsBackend: system_drive=Drive(C: hd 66675.28125 mb free fat32)
10-31 03:28 DEBUG  WindowsBackend: drive=Drive(C: hd 66675.28125 mb free fat32)
10-31 03:28 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
10-31 03:28 DEBUG  WindowsBackend: drive=Drive(E: hd 65248.46875 mb free fat32)
10-31 03:28 DEBUG  WindowsBackend: drive=Drive(F: hd 823473.96875 mb free fat32)
10-31 03:28 DEBUG  WindowsBackend: uninstaller_path=None
10-31 03:28 DEBUG  WindowsBackend: previous_target_dir=None
10-31 03:28 DEBUG  WindowsBackend: previous_distro_name=None
10-31 03:28 DEBUG  WindowsBackend: keyboard_id=67765258
10-31 03:28 DEBUG  WindowsBackend: keyboard_layout=us
10-31 03:28 DEBUG  WindowsBackend: keyboard_variant=
10-31 03:28 DEBUG  WindowsBackend: total_memory_mb=2046.79296875
10-31 03:28 DEBUG  CommonBackend: Searching ISOs on USB devices
10-31 03:28 DEBUG  CommonBackend: Searching for local CDs
10-31 03:28 DEBUG  Distro:   checking whether C:\Temp\pyl9D.tmp is a valid Ubuntu CD
10-31 03:28 DEBUG  Distro:     does not contain C:\Temp\pyl9D.tmp\casper\filesystem.squashfs
10-31 03:28 DEBUG  Distro:   checking whether C:\Temp\pyl9D.tmp is a valid Ubuntu CD
10-31 03:28 DEBUG  Distro:     does not contain C:\Temp\pyl9D.tmp\casper\filesystem.squashfs
10-31 03:28 DEBUG  Distro:   checking whether C:\Temp\pyl9D.tmp is a valid Ubuntu Netbook Remix CD
10-31 03:28 DEBUG  Distro:     does not contain C:\Temp\pyl9D.tmp\casper\filesystem.squashfs
10-31 03:28 DEBUG  Distro:   checking whether C:\Temp\pyl9D.tmp is a valid Kubuntu CD
10-31 03:28 DEBUG  Distro:     does not contain C:\Temp\pyl9D.tmp\casper\filesystem.squashfs
10-31 03:28 DEBUG  Distro:   checking whether C:\Temp\pyl9D.tmp is a valid Kubuntu CD
10-31 03:28 DEBUG  Distro:     does not contain C:\Temp\pyl9D.tmp\casper\filesystem.squashfs
10-31 03:28 DEBUG  Distro:   checking whether C:\Temp\pyl9D.tmp is a valid Kubuntu Netbook CD
10-31 03:28 DEBUG  Distro:     does not contain C:\Temp\pyl9D.tmp\casper\filesystem.squashfs
10-31 03:28 DEBUG  Distro:   checking whether C:\Temp\pyl9D.tmp is a valid Xubuntu CD
10-31 03:28 DEBUG  Distro:     does not contain C:\Temp\pyl9D.tmp\casper\filesystem.squashfs
10-31 03:28 DEBUG  Distro:   checking whether C:\Temp\pyl9D.tmp is a valid Xubuntu CD
10-31 03:28 DEBUG  Distro:     does not contain C:\Temp\pyl9D.tmp\casper\filesystem.squashfs
10-31 03:28 DEBUG  Distro:   checking whether C:\Temp\pyl9D.tmp is a valid Mythbuntu CD
10-31 03:28 DEBUG  Distro:     does not contain C:\Temp\pyl9D.tmp\casper\filesystem.squashfs
10-31 03:28 DEBUG  Distro:   checking whether C:\Temp\pyl9D.tmp is a valid Mythbuntu CD
10-31 03:28 DEBUG  Distro:     does not contain C:\Temp\pyl9D.tmp\casper\filesystem.squashfs
10-31 03:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-31 03:28 INFO   Distro: Found a valid CD for Ubuntu: D:\
10-31 03:28 INFO   root: Running the installer...
10-31 03:28 INFO   WinuiPage: appname=wubi, localedir=C:\Temp\pyl9D.tmp\translations, languages=['en_US', 'en']
10-31 03:28 INFO   WinuiPage: appname=wubi, localedir=C:\Temp\pyl9D.tmp\translations, languages=['en_US', 'en']
10-30 21:33 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=6000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=default
10-30 21:33 INFO   root: Received settings
10-30 21:33 INFO   WinuiPage: appname=wubi, localedir=C:\Temp\pyl9D.tmp\translations, languages=['en_US', 'en']
10-30 21:33 DEBUG  TaskList: # Running tasklist...
10-30 21:33 DEBUG  TaskList: ## Running select_target_dir...
10-30 21:33 INFO   WindowsBackend: Installing into C:\ubuntu
10-30 21:33 DEBUG  TaskList: ## Finished select_target_dir
10-30 21:33 DEBUG  TaskList: ## Running create_dir_structure...
10-30 21:33 DEBUG  CommonBackend: Creating dir C:\ubuntu
10-30 21:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
10-30 21:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
10-30 21:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
10-30 21:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
10-30 21:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
10-30 21:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
10-30 21:33 DEBUG  TaskList: ## Finished create_dir_structure
10-30 21:33 DEBUG  TaskList: ## Running uncompress_target_dir...
10-30 21:33 DEBUG  TaskList: ## Finished uncompress_target_dir
10-30 21:33 DEBUG  TaskList: ## Running create_uninstaller...
10-30 21:33 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
10-30 21:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
10-30 21:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
10-30 21:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-30 21:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
10-30 21:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
10-30 21:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-30 21:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
10-30 21:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
10-30 21:33 DEBUG  TaskList: ## Finished create_uninstaller
10-30 21:33 DEBUG  TaskList: ## Running copy_installation_files...
10-30 21:33 DEBUG  WindowsBackend: Copying C:\Temp\pyl9D.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
10-30 21:33 DEBUG  WindowsBackend: Copying C:\Temp\pyl9D.tmp\winboot -> C:\ubuntu\winboot
10-30 21:33 DEBUG  WindowsBackend: Copying C:\Temp\pyl9D.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
10-30 21:33 DEBUG  TaskList: ## Finished copy_installation_files
10-30 21:33 DEBUG  TaskList: ## Running get_iso...
10-30 21:33 DEBUG  TaskList: New task copy_file
10-30 21:33 DEBUG  TaskList: ### Running copy_file...
10-30 21:36 DEBUG  TaskList: ### Finished copy_file
10-30 21:36 ERROR  TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 22] Invalid argument
10-30 21:36 DEBUG  TaskList: # Cancelling tasklist
10-30 21:36 DEBUG  TaskList: New task check_iso
10-30 21:36 ERROR  root: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 126, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 22] Invalid argument
10-30 21:36 DEBUG  CommonBackend: Searching for local ISO
10-30 21:36 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
10-30 21:36 DEBUG  TaskList: New task get_metalink
10-30 21:36 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
10-30 21:36 DEBUG  TaskList: # Cancelling tasklist
10-30 21:36 DEBUG  TaskList: # Finished tasklist

---

### Post by madhuperiasamy on 2009-11-13
byros pl see this link

[https://bugs.launchpad.net/wubi/+bug/383752](https://bugs.launchpad.net/wubi/+bug/383752)

had pretty much the same prob
was solved

---

### Post by surfzombie on 2009-11-13
I was having a similar problem trying to install using wubi on the burnt cd I have of Ubuntu 9.10.  I caame searching for help and found this thread.  I followed the link that was posted and in that link was another link [http://wubi-installer.org/](http://wubi-installer.org/) at which you can download the latest copy of wubi.exe which i did.  I still had my cd in the drive and launched the new wubi I had just downloaded and it worked like a charm.  Smooth as a baby's bottom.  I just want to say thanks for the help.:P

---

