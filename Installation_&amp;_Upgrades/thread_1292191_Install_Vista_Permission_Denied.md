---
title: "Install Vista Permission Denied"
date: 2009-10-15
forum: Installation &amp; Upgrades
---

### Post by Snow.Envi on 2009-10-15
Ubuntu 9.04
Windows Vista: Installation within Windows. 
Almost full installation then this error 
PERMISSION DENIED: 

C:\users\snow~1.env\appdata\local\temp\wubi-9.04-rev128.log

*also, i'm kinda new to all of this*
FILE LOG BELOW: 

10-15 14:46 INFO   root: === wubi 9.04 rev128 ===
10-15 14:46 DEBUG  root: Logfile is c:\users\snow~1.env\appdata\local\temp\wubi-9.04-rev128.log
10-15 14:46 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
10-15 14:46 DEBUG  CommonBackend: data_dir=C:\Users\SNOW~1.ENV\AppData\Local\Temp\pyl13CE.tmp\data
10-15 14:46 DEBUG  WindowsBackend: 7z=C:\Users\SNOW~1.ENV\AppData\Local\Temp\pyl13CE.tmp\bin\7z.exe
10-15 14:46 DEBUG  CommonBackend: Fetching basic info...
10-15 14:46 DEBUG  CommonBackend: original_exe=D:\wubi.exe
10-15 14:46 DEBUG  CommonBackend: platform=win32
10-15 14:46 DEBUG  CommonBackend: osname=nt
10-15 14:46 DEBUG  CommonBackend: language=en_US
10-15 14:46 DEBUG  CommonBackend: encoding=cp1252
10-15 14:46 DEBUG  WindowsBackend: arch=amd64
10-15 14:46 DEBUG  CommonBackend: Parsing isolist=C:\Users\SNOW~1.ENV\AppData\Local\Temp\pyl13CE.tmp\data\isolist.ini
10-15 14:46 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-15 14:46 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-15 14:46 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-15 14:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-15 14:46 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-15 14:46 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-15 14:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-15 14:46 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-15 14:46 DEBUG  WindowsBackend: Fetching host info...
10-15 14:46 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-15 14:46 DEBUG  WindowsBackend: windows version=vista
10-15 14:46 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Ultimate
10-15 14:46 DEBUG  WindowsBackend: windows_sp=None
10-15 14:46 DEBUG  WindowsBackend: windows_build=6000
10-15 14:46 DEBUG  WindowsBackend: gmt=-5
10-15 14:46 DEBUG  WindowsBackend: country=US
10-15 14:46 DEBUG  WindowsBackend: timezone=America/New_York
10-15 14:46 DEBUG  WindowsBackend: windows_username=Snow.Envi
10-15 14:46 DEBUG  WindowsBackend: user_full_name=Snow.Envi
10-15 14:46 DEBUG  WindowsBackend: user_directory=Snow.Envi
10-15 14:46 DEBUG  WindowsBackend: windows_language_code=1033
10-15 14:46 DEBUG  WindowsBackend: windows_language=English
10-15 14:46 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     E7200  @ 2.53GHz
10-15 14:46 DEBUG  WindowsBackend: bootloader=vista
10-15 14:46 DEBUG  WindowsBackend: system_drive=Drive(C: hd 176537.589844 mb free )
10-15 14:46 DEBUG  WindowsBackend: drive=Drive(C: hd 176537.589844 mb free )
10-15 14:46 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
10-15 14:46 DEBUG  WindowsBackend: drive=Drive(E: removable 0.0 mb free )
10-15 14:46 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
10-15 14:46 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
10-15 14:46 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
10-15 14:46 DEBUG  WindowsBackend: uninstaller_path=None
10-15 14:46 DEBUG  WindowsBackend: previous_target_dir=None
10-15 14:46 DEBUG  WindowsBackend: previous_distro_name=None
10-15 14:46 DEBUG  WindowsBackend: keyboard_id=67699721
10-15 14:46 DEBUG  WindowsBackend: keyboard_layout=us
10-15 14:46 DEBUG  WindowsBackend: keyboard_variant=
10-15 14:46 DEBUG  CommonBackend: locale=en_US.UTF-8
10-15 14:46 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
10-15 14:46 DEBUG  CommonBackend: Searching ISOs on USB devices
10-15 14:46 DEBUG  CommonBackend: Searching for local CDs
10-15 14:46 DEBUG  Distro:   checking whether C:\Users\SNOW~1.ENV\AppData\Local\Temp\pyl13CE.tmp is a valid Ubuntu CD
10-15 14:46 DEBUG  Distro:     does not contain C:\Users\SNOW~1.ENV\AppData\Local\Temp\pyl13CE.tmp\casper\filesystem.squashfs
10-15 14:46 DEBUG  Distro:   checking whether C:\Users\SNOW~1.ENV\AppData\Local\Temp\pyl13CE.tmp is a valid Ubuntu CD
10-15 14:46 DEBUG  Distro:     does not contain C:\Users\SNOW~1.ENV\AppData\Local\Temp\pyl13CE.tmp\casper\filesystem.squashfs
10-15 14:46 DEBUG  Distro:   checking whether C:\Users\SNOW~1.ENV\AppData\Local\Temp\pyl13CE.tmp is a valid Kubuntu CD
10-15 14:46 DEBUG  Distro:     does not contain C:\Users\SNOW~1.ENV\AppData\Local\Temp\pyl13CE.tmp\casper\filesystem.squashfs
10-15 14:46 DEBUG  Distro:   checking whether C:\Users\SNOW~1.ENV\AppData\Local\Temp\pyl13CE.tmp is a valid Kubuntu CD
10-15 14:46 DEBUG  Distro:     does not contain C:\Users\SNOW~1.ENV\AppData\Local\Temp\pyl13CE.tmp\casper\filesystem.squashfs
10-15 14:46 DEBUG  Distro:   checking whether C:\Users\SNOW~1.ENV\AppData\Local\Temp\pyl13CE.tmp is a valid Xubuntu CD
10-15 14:46 DEBUG  Distro:     does not contain C:\Users\SNOW~1.ENV\AppData\Local\Temp\pyl13CE.tmp\casper\filesystem.squashfs
10-15 14:46 DEBUG  Distro:   checking whether C:\Users\SNOW~1.ENV\AppData\Local\Temp\pyl13CE.tmp is a valid Xubuntu CD
10-15 14:46 DEBUG  Distro:     does not contain C:\Users\SNOW~1.ENV\AppData\Local\Temp\pyl13CE.tmp\casper\filesystem.squashfs
10-15 14:46 DEBUG  Distro:   checking whether C:\Users\SNOW~1.ENV\AppData\Local\Temp\pyl13CE.tmp is a valid Mythbuntu CD
10-15 14:46 DEBUG  Distro:     does not contain C:\Users\SNOW~1.ENV\AppData\Local\Temp\pyl13CE.tmp\casper\filesystem.squashfs
10-15 14:46 DEBUG  Distro:   checking whether C:\Users\SNOW~1.ENV\AppData\Local\Temp\pyl13CE.tmp is a valid Mythbuntu CD
10-15 14:46 DEBUG  Distro:     does not contain C:\Users\SNOW~1.ENV\AppData\Local\Temp\pyl13CE.tmp\casper\filesystem.squashfs
10-15 14:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-15 14:46 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
10-15 14:46 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
10-15 14:46 INFO   Distro: Found a valid CD for Ubuntu: D:\
10-15 14:46 INFO   root: Running the CD menu...
10-15 14:46 DEBUG  WindowsFrontend: __init__...
10-15 14:46 DEBUG  WindowsFrontend: on_init...
10-15 14:46 INFO   root: CD menu finished
10-15 14:46 INFO   root: Running the installer...
10-15 14:47 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=English, username=snowenvi
10-15 14:47 INFO   root: Received settings
10-15 14:47 DEBUG  TaskList: # Running tasklist...
10-15 14:47 DEBUG  TaskList: ## Running select_target_dir...
10-15 14:47 INFO   WindowsBackend: Installing into C:\ubuntu
10-15 14:47 DEBUG  TaskList: ## Finished select_target_dir
10-15 14:47 DEBUG  TaskList: ## Running create_dir_structure...
10-15 14:47 DEBUG  CommonBackend: Creating dir C:\ubuntu
10-15 14:47 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
10-15 14:47 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
10-15 14:47 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
10-15 14:47 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
10-15 14:47 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
10-15 14:47 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
10-15 14:47 DEBUG  TaskList: ## Finished create_dir_structure
10-15 14:47 DEBUG  TaskList: ## Running uncompress_target_dir...
10-15 14:47 DEBUG  TaskList: ## Finished uncompress_target_dir
10-15 14:47 DEBUG  TaskList: ## Running create_uninstaller...
10-15 14:47 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
10-15 14:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
10-15 14:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
10-15 14:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-15 14:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
10-15 14:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
10-15 14:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-15 14:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
10-15 14:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
10-15 14:47 DEBUG  TaskList: ## Finished create_uninstaller
10-15 14:47 DEBUG  TaskList: ## Running copy_installation_files...
10-15 14:47 DEBUG  WindowsBackend: Copying C:\Users\SNOW~1.ENV\AppData\Local\Temp\pyl13CE.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
10-15 14:47 DEBUG  WindowsBackend: Copying C:\Users\SNOW~1.ENV\AppData\Local\Temp\pyl13CE.tmp\winboot -> C:\ubuntu\winboot
10-15 14:47 DEBUG  WindowsBackend: Copying C:\Users\SNOW~1.ENV\AppData\Local\Temp\pyl13CE.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
10-15 14:47 DEBUG  TaskList: ## Finished copy_installation_files
10-15 14:47 DEBUG  TaskList: ## Running get_iso...
10-15 14:47 DEBUG  TaskList: New task copy_file
10-15 14:47 DEBUG  TaskList: ### Running copy_file...
10-15 14:50 DEBUG  TaskList: ### Finished copy_file
10-15 14:50 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 13] Permission denied
10-15 14:50 DEBUG  TaskList: # Cancelling tasklist
10-15 14:50 DEBUG  TaskList: New task check_iso
10-15 14:50 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 13] Permission denied
10-15 14:50 DEBUG  CommonBackend: Searching for local ISO
10-15 14:50 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
10-15 14:50 DEBUG  TaskList: New task get_metalink
10-15 14:50 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
10-15 14:50 DEBUG  TaskList: # Cancelling tasklist
10-15 14:50 DEBUG  TaskList: # Finished tasklist
10-15 14:52 INFO   root: === wubi 9.04 rev128 ===
10-15 14:52 DEBUG  root: Logfile is c:\users\snow~1.env\appdata\local\temp\wubi-9.04-rev128.log
10-15 14:52 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
10-15 14:52 DEBUG  CommonBackend: data_dir=C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylACB3.tmp\data
10-15 14:52 DEBUG  WindowsBackend: 7z=C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylACB3.tmp\bin\7z.exe
10-15 14:52 DEBUG  CommonBackend: Fetching basic info...
10-15 14:52 DEBUG  CommonBackend: original_exe=D:\wubi.exe
10-15 14:52 DEBUG  CommonBackend: platform=win32
10-15 14:52 DEBUG  CommonBackend: osname=nt
10-15 14:52 DEBUG  CommonBackend: language=en_US
10-15 14:52 DEBUG  CommonBackend: encoding=cp1252
10-15 14:52 DEBUG  WindowsBackend: arch=amd64
10-15 14:52 DEBUG  CommonBackend: Parsing isolist=C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylACB3.tmp\data\isolist.ini
10-15 14:52 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-15 14:52 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-15 14:52 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-15 14:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-15 14:52 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-15 14:52 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-15 14:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-15 14:52 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-15 14:52 DEBUG  WindowsBackend: Fetching host info...
10-15 14:52 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-15 14:52 DEBUG  WindowsBackend: windows version=vista
10-15 14:52 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Ultimate
10-15 14:52 DEBUG  WindowsBackend: windows_sp=None
10-15 14:52 DEBUG  WindowsBackend: windows_build=6000
10-15 14:52 DEBUG  WindowsBackend: gmt=-5
10-15 14:52 DEBUG  WindowsBackend: country=US
10-15 14:52 DEBUG  WindowsBackend: timezone=America/New_York
10-15 14:52 DEBUG  WindowsBackend: windows_username=Snow.Envi
10-15 14:52 DEBUG  WindowsBackend: user_full_name=Snow.Envi
10-15 14:52 DEBUG  WindowsBackend: user_directory=Snow.Envi
10-15 14:52 DEBUG  WindowsBackend: windows_language_code=1033
10-15 14:52 DEBUG  WindowsBackend: windows_language=English
10-15 14:52 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     E7200  @ 2.53GHz
10-15 14:52 DEBUG  WindowsBackend: bootloader=vista
10-15 14:52 DEBUG  WindowsBackend: system_drive=Drive(C: hd 175837.351563 mb free )
10-15 14:52 DEBUG  WindowsBackend: drive=Drive(C: hd 175837.351563 mb free )
10-15 14:52 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
10-15 14:52 DEBUG  WindowsBackend: drive=Drive(E: removable 0.0 mb free )
10-15 14:52 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
10-15 14:52 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
10-15 14:52 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
10-15 14:52 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
10-15 14:52 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
10-15 14:52 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
10-15 14:52 DEBUG  WindowsBackend: keyboard_id=67699721
10-15 14:52 DEBUG  WindowsBackend: keyboard_layout=us
10-15 14:52 DEBUG  WindowsBackend: keyboard_variant=
10-15 14:52 DEBUG  CommonBackend: locale=en_US.UTF-8
10-15 14:52 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
10-15 14:52 DEBUG  CommonBackend: Searching ISOs on USB devices
10-15 14:52 DEBUG  CommonBackend: Searching for local CDs
10-15 14:52 DEBUG  Distro:   checking whether C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylACB3.tmp is a valid Ubuntu CD
10-15 14:52 DEBUG  Distro:     does not contain C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylACB3.tmp\casper\filesystem.squashfs
10-15 14:52 DEBUG  Distro:   checking whether C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylACB3.tmp is a valid Ubuntu CD
10-15 14:52 DEBUG  Distro:     does not contain C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylACB3.tmp\casper\filesystem.squashfs
10-15 14:52 DEBUG  Distro:   checking whether C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylACB3.tmp is a valid Kubuntu CD
10-15 14:52 DEBUG  Distro:     does not contain C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylACB3.tmp\casper\filesystem.squashfs
10-15 14:52 DEBUG  Distro:   checking whether C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylACB3.tmp is a valid Kubuntu CD
10-15 14:52 DEBUG  Distro:     does not contain C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylACB3.tmp\casper\filesystem.squashfs
10-15 14:52 DEBUG  Distro:   checking whether C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylACB3.tmp is a valid Xubuntu CD
10-15 14:52 DEBUG  Distro:     does not contain C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylACB3.tmp\casper\filesystem.squashfs
10-15 14:52 DEBUG  Distro:   checking whether C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylACB3.tmp is a valid Xubuntu CD
10-15 14:52 DEBUG  Distro:     does not contain C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylACB3.tmp\casper\filesystem.squashfs
10-15 14:52 DEBUG  Distro:   checking whether C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylACB3.tmp is a valid Mythbuntu CD
10-15 14:52 DEBUG  Distro:     does not contain C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylACB3.tmp\casper\filesystem.squashfs
10-15 14:52 DEBUG  Distro:   checking whether C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylACB3.tmp is a valid Mythbuntu CD
10-15 14:52 DEBUG  Distro:     does not contain C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylACB3.tmp\casper\filesystem.squashfs
10-15 14:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-15 14:52 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
10-15 14:52 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
10-15 14:52 INFO   Distro: Found a valid CD for Ubuntu: D:\
10-15 14:52 INFO   root: Running the CD menu...
10-15 14:52 DEBUG  WindowsFrontend: __init__...
10-15 14:52 DEBUG  WindowsFrontend: on_init...
10-15 14:52 INFO   WindowsFrontend: Operation cancelled
10-15 14:52 DEBUG  WindowsFrontend: frontend.quit
10-15 14:52 DEBUG  WindowsFrontend: frontend.on_quit
10-15 14:52 DEBUG  root: application.on_quit
10-15 14:52 INFO   root: sys.exit
10-15 15:05 INFO   root: === wubi 9.04 rev128 ===
10-15 15:05 DEBUG  root: Logfile is c:\users\snow~1.env\appdata\local\temp\wubi-9.04-rev128.log
10-15 15:05 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
10-15 15:05 DEBUG  CommonBackend: data_dir=C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylCACE.tmp\data
10-15 15:05 DEBUG  WindowsBackend: 7z=C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylCACE.tmp\bin\7z.exe
10-15 15:05 DEBUG  CommonBackend: Fetching basic info...
10-15 15:05 DEBUG  CommonBackend: original_exe=D:\wubi.exe
10-15 15:05 DEBUG  CommonBackend: platform=win32
10-15 15:05 DEBUG  CommonBackend: osname=nt
10-15 15:05 DEBUG  CommonBackend: language=en_US
10-15 15:05 DEBUG  CommonBackend: encoding=cp1252
10-15 15:05 DEBUG  WindowsBackend: arch=amd64
10-15 15:05 DEBUG  CommonBackend: Parsing isolist=C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylCACE.tmp\data\isolist.ini
10-15 15:05 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-15 15:05 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-15 15:05 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-15 15:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-15 15:05 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-15 15:05 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-15 15:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-15 15:05 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-15 15:05 DEBUG  WindowsBackend: Fetching host info...
10-15 15:05 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-15 15:05 DEBUG  WindowsBackend: windows version=vista
10-15 15:05 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Ultimate
10-15 15:05 DEBUG  WindowsBackend: windows_sp=None
10-15 15:05 DEBUG  WindowsBackend: windows_build=6000
10-15 15:05 DEBUG  WindowsBackend: gmt=-5
10-15 15:05 DEBUG  WindowsBackend: country=US
10-15 15:05 DEBUG  WindowsBackend: timezone=America/New_York
10-15 15:05 DEBUG  WindowsBackend: windows_username=Snow.Envi
10-15 15:05 DEBUG  WindowsBackend: user_full_name=Snow.Envi
10-15 15:05 DEBUG  WindowsBackend: user_directory=Snow.Envi
10-15 15:05 DEBUG  WindowsBackend: windows_language_code=1033
10-15 15:05 DEBUG  WindowsBackend: windows_language=English
10-15 15:05 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     E7200  @ 2.53GHz
10-15 15:05 DEBUG  WindowsBackend: bootloader=vista
10-15 15:05 DEBUG  WindowsBackend: system_drive=Drive(C: hd 175834.710938 mb free )
10-15 15:05 DEBUG  WindowsBackend: drive=Drive(C: hd 175834.707031 mb free )
10-15 15:05 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
10-15 15:05 DEBUG  WindowsBackend: drive=Drive(E: removable 0.0 mb free )
10-15 15:05 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
10-15 15:05 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
10-15 15:05 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
10-15 15:05 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
10-15 15:05 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
10-15 15:05 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
10-15 15:05 DEBUG  WindowsBackend: keyboard_id=67699721
10-15 15:05 DEBUG  WindowsBackend: keyboard_layout=us
10-15 15:05 DEBUG  WindowsBackend: keyboard_variant=
10-15 15:05 DEBUG  CommonBackend: locale=en_US.UTF-8
10-15 15:05 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
10-15 15:05 DEBUG  CommonBackend: Searching ISOs on USB devices
10-15 15:05 DEBUG  CommonBackend: Searching for local CDs
10-15 15:05 DEBUG  Distro:   checking whether C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylCACE.tmp is a valid Ubuntu CD
10-15 15:05 DEBUG  Distro:     does not contain C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylCACE.tmp\casper\filesystem.squashfs
10-15 15:05 DEBUG  Distro:   checking whether C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylCACE.tmp is a valid Ubuntu CD
10-15 15:05 DEBUG  Distro:     does not contain C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylCACE.tmp\casper\filesystem.squashfs
10-15 15:05 DEBUG  Distro:   checking whether C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylCACE.tmp is a valid Kubuntu CD
10-15 15:05 DEBUG  Distro:     does not contain C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylCACE.tmp\casper\filesystem.squashfs
10-15 15:05 DEBUG  Distro:   checking whether C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylCACE.tmp is a valid Kubuntu CD
10-15 15:05 DEBUG  Distro:     does not contain C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylCACE.tmp\casper\filesystem.squashfs
10-15 15:05 DEBUG  Distro:   checking whether C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylCACE.tmp is a valid Xubuntu CD
10-15 15:05 DEBUG  Distro:     does not contain C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylCACE.tmp\casper\filesystem.squashfs
10-15 15:05 DEBUG  Distro:   checking whether C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylCACE.tmp is a valid Xubuntu CD
10-15 15:05 DEBUG  Distro:     does not contain C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylCACE.tmp\casper\filesystem.squashfs
10-15 15:05 DEBUG  Distro:   checking whether C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylCACE.tmp is a valid Mythbuntu CD
10-15 15:05 DEBUG  Distro:     does not contain C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylCACE.tmp\casper\filesystem.squashfs
10-15 15:05 DEBUG  Distro:   checking whether C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylCACE.tmp is a valid Mythbuntu CD
10-15 15:05 DEBUG  Distro:     does not contain C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylCACE.tmp\casper\filesystem.squashfs
10-15 15:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-15 15:05 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
10-15 15:05 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
10-15 15:05 INFO   Distro: Found a valid CD for Ubuntu: D:\
10-15 15:05 INFO   root: Running the CD menu...
10-15 15:05 DEBUG  WindowsFrontend: __init__...
10-15 15:05 DEBUG  WindowsFrontend: on_init...
10-15 15:06 INFO   root: CD menu finished
10-15 15:06 INFO   root: Already installed, running the uninstaller...
10-15 15:06 INFO   root: Running the uninstaller...
10-15 15:06 INFO   CommonBackend: This is the uninstaller running
10-15 15:06 INFO   root: Received settings
10-15 15:06 DEBUG  TaskList: # Running tasklist...
10-15 15:06 DEBUG  TaskList: ## Running Backup ISO...
10-15 15:06 DEBUG  TaskList: ## Finished Backup ISO
10-15 15:06 DEBUG  TaskList: ## Running Remove bootloader entry...
10-15 15:06 DEBUG  WindowsBackend: Could not find bcd id
10-15 15:06 DEBUG  WindowsBackend: undo_bootini C:
10-15 15:06 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 175834.707031 mb free )
10-15 15:06 DEBUG  WindowsBackend: undo_bootini E:
10-15 15:06 DEBUG  WindowsBackend: undo_configsys Drive(E: removable 0.0 mb free )
10-15 15:06 DEBUG  WindowsBackend: undo_bootini F:
10-15 15:06 DEBUG  WindowsBackend: undo_configsys Drive(F: removable 0.0 mb free )
10-15 15:06 DEBUG  WindowsBackend: undo_bootini G:
10-15 15:06 DEBUG  WindowsBackend: undo_configsys Drive(G: removable 0.0 mb free )
10-15 15:06 DEBUG  WindowsBackend: undo_bootini H:
10-15 15:06 DEBUG  WindowsBackend: undo_configsys Drive(H: removable 0.0 mb free )
10-15 15:06 DEBUG  TaskList: ## Finished Remove bootloader entry
10-15 15:06 DEBUG  TaskList: ## Running Remove target dir...
10-15 15:06 DEBUG  CommonBackend: Deleting C:\ubuntu
10-15 15:06 DEBUG  TaskList: ## Finished Remove target dir
10-15 15:06 DEBUG  TaskList: ## Running Remove registry key...
10-15 15:06 DEBUG  TaskList: ## Finished Remove registry key
10-15 15:06 DEBUG  TaskList: # Finished tasklist
10-15 15:06 INFO   root: Almost finished uninstalling
10-15 15:06 INFO   root: Finished uninstallation
10-15 15:06 DEBUG  CommonBackend: Fetching basic info...
10-15 15:06 DEBUG  CommonBackend: original_exe=D:\wubi.exe
10-15 15:06 DEBUG  CommonBackend: platform=win32
10-15 15:06 DEBUG  CommonBackend: osname=nt
10-15 15:06 DEBUG  CommonBackend: language=en_US
10-15 15:06 DEBUG  CommonBackend: encoding=cp1252
10-15 15:06 DEBUG  WindowsBackend: arch=amd64
10-15 15:06 DEBUG  CommonBackend: Parsing isolist=C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylCACE.tmp\data\isolist.ini
10-15 15:06 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-15 15:06 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-15 15:06 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-15 15:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-15 15:06 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-15 15:06 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-15 15:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-15 15:06 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-15 15:06 DEBUG  WindowsBackend: Fetching host info...
10-15 15:06 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-15 15:06 DEBUG  WindowsBackend: windows version=vista
10-15 15:06 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Ultimate
10-15 15:06 DEBUG  WindowsBackend: windows_sp=None
10-15 15:06 DEBUG  WindowsBackend: windows_build=6000
10-15 15:06 DEBUG  WindowsBackend: gmt=-5
10-15 15:06 DEBUG  WindowsBackend: country=US
10-15 15:06 DEBUG  WindowsBackend: timezone=America/New_York
10-15 15:06 DEBUG  WindowsBackend: windows_username=Snow.Envi
10-15 15:06 DEBUG  WindowsBackend: user_full_name=Snow.Envi
10-15 15:06 DEBUG  WindowsBackend: user_directory=Snow.Envi
10-15 15:06 DEBUG  WindowsBackend: windows_language_code=1033
10-15 15:06 DEBUG  WindowsBackend: windows_language=English
10-15 15:06 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     E7200  @ 2.53GHz
10-15 15:06 DEBUG  WindowsBackend: bootloader=vista
10-15 15:06 DEBUG  WindowsBackend: system_drive=Drive(C: hd 176534.582031 mb free )
10-15 15:06 DEBUG  WindowsBackend: drive=Drive(C: hd 176534.582031 mb free )
10-15 15:06 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
10-15 15:06 DEBUG  WindowsBackend: drive=Drive(E: removable 0.0 mb free )
10-15 15:06 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
10-15 15:06 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
10-15 15:06 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
10-15 15:06 DEBUG  WindowsBackend: uninstaller_path=None
10-15 15:06 DEBUG  WindowsBackend: previous_target_dir=None
10-15 15:06 DEBUG  WindowsBackend: previous_distro_name=None
10-15 15:06 DEBUG  WindowsBackend: keyboard_id=67699721
10-15 15:06 DEBUG  WindowsBackend: keyboard_layout=us
10-15 15:06 DEBUG  WindowsBackend: keyboard_variant=
10-15 15:06 DEBUG  CommonBackend: locale=en_US.UTF-8
10-15 15:06 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
10-15 15:06 DEBUG  CommonBackend: Searching ISOs on USB devices
10-15 15:06 DEBUG  CommonBackend: Searching for local CDs
10-15 15:06 DEBUG  Distro:   checking whether C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylCACE.tmp is a valid Ubuntu CD
10-15 15:06 DEBUG  Distro:     does not contain C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylCACE.tmp\casper\filesystem.squashfs
10-15 15:06 DEBUG  Distro:   checking whether C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylCACE.tmp is a valid Ubuntu CD
10-15 15:06 DEBUG  Distro:     does not contain C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylCACE.tmp\casper\filesystem.squashfs
10-15 15:06 DEBUG  Distro:   checking whether C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylCACE.tmp is a valid Kubuntu CD
10-15 15:06 DEBUG  Distro:     does not contain C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylCACE.tmp\casper\filesystem.squashfs
10-15 15:06 DEBUG  Distro:   checking whether C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylCACE.tmp is a valid Kubuntu CD
10-15 15:06 DEBUG  Distro:     does not contain C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylCACE.tmp\casper\filesystem.squashfs
10-15 15:06 DEBUG  Distro:   checking whether C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylCACE.tmp is a valid Xubuntu CD
10-15 15:06 DEBUG  Distro:     does not contain C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylCACE.tmp\casper\filesystem.squashfs
10-15 15:06 DEBUG  Distro:   checking whether C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylCACE.tmp is a valid Xubuntu CD
10-15 15:06 DEBUG  Distro:     does not contain C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylCACE.tmp\casper\filesystem.squashfs
10-15 15:06 DEBUG  Distro:   checking whether C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylCACE.tmp is a valid Mythbuntu CD
10-15 15:06 DEBUG  Distro:     does not contain C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylCACE.tmp\casper\filesystem.squashfs
10-15 15:06 DEBUG  Distro:   checking whether C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylCACE.tmp is a valid Mythbuntu CD
10-15 15:06 DEBUG  Distro:     does not contain C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylCACE.tmp\casper\filesystem.squashfs
10-15 15:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-15 15:06 INFO   Distro: Found a valid CD for Ubuntu: D:\
10-15 15:06 INFO   root: Running the installer...
10-15 15:06 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=English, username=snowenvi
10-15 15:06 INFO   root: Received settings
10-15 15:06 DEBUG  TaskList: # Running tasklist...
10-15 15:06 DEBUG  TaskList: ## Running select_target_dir...
10-15 15:06 INFO   WindowsBackend: Installing into C:\ubuntu
10-15 15:06 DEBUG  TaskList: ## Finished select_target_dir
10-15 15:06 DEBUG  TaskList: ## Running create_dir_structure...
10-15 15:06 DEBUG  CommonBackend: Creating dir C:\ubuntu
10-15 15:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
10-15 15:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
10-15 15:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
10-15 15:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
10-15 15:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
10-15 15:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
10-15 15:06 DEBUG  TaskList: ## Finished create_dir_structure
10-15 15:06 DEBUG  TaskList: ## Running uncompress_target_dir...
10-15 15:06 DEBUG  TaskList: ## Finished uncompress_target_dir
10-15 15:06 DEBUG  TaskList: ## Running create_uninstaller...
10-15 15:06 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
10-15 15:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
10-15 15:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
10-15 15:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-15 15:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
10-15 15:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
10-15 15:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-15 15:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
10-15 15:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
10-15 15:06 DEBUG  TaskList: ## Finished create_uninstaller
10-15 15:06 DEBUG  TaskList: ## Running copy_installation_files...
10-15 15:06 DEBUG  WindowsBackend: Copying C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylCACE.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
10-15 15:06 DEBUG  WindowsBackend: Copying C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylCACE.tmp\winboot -> C:\ubuntu\winboot
10-15 15:06 DEBUG  WindowsBackend: Copying C:\Users\SNOW~1.ENV\AppData\Local\Temp\pylCACE.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
10-15 15:06 DEBUG  TaskList: ## Finished copy_installation_files
10-15 15:06 DEBUG  TaskList: ## Running get_iso...
10-15 15:06 DEBUG  TaskList: New task copy_file
10-15 15:06 DEBUG  TaskList: ### Running copy_file...
10-15 15:09 DEBUG  TaskList: ### Finished copy_file
10-15 15:09 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 13] Permission denied
10-15 15:09 DEBUG  TaskList: # Cancelling tasklist
10-15 15:09 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 13] Permission denied
10-15 15:09 DEBUG  TaskList: New task check_iso
10-15 15:09 DEBUG  CommonBackend: Searching for local ISO
10-15 15:09 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
10-15 15:09 DEBUG  TaskList: New task get_metalink
10-15 15:09 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
10-15 15:09 DEBUG  TaskList: # Cancelling tasklist
10-15 15:09 DEBUG  TaskList: # Finished tasklist

---

### Post by phillw on 2009-10-15
Did you follow the instructions here ....

[http://wubi-installer.org/](http://wubi-installer.org/)

If so, the only thing I can think of is that you may have user account control turned on...

If so, try this link.

[http://www.lockergnome.com/windows/2006/12/18/disable-user-account-control-in-vista/](http://www.lockergnome.com/windows/2006/12/18/disable-user-account-control-in-vista/)

to turn it off.

Hope that helps,

Phill.

---

