---
title: "wubi permission denied"
date: 2009-07-01
forum: Installation &amp; Upgrades
---

### Post by thingy87654321 on 2009-07-01
i tried to install ubuntu 9.04 using wubi, i previously had ubuntu installed but i had to reinstall it, i am running windows 7 rc1, the permission denied message that popped up told me to go to a text doc located in my user folder, here is the text of that file



06-30 19:20 INFO   root: === wubi 9.04 rev128 ===
06-30 19:20 DEBUG  root: Logfile is c:\users\christ~1\appdata\local\temp\wubi-9.04-rev128.log
06-30 19:20 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
06-30 19:20 DEBUG  CommonBackend: data_dir=C:\Users\CHRIST~1\AppData\Local\Temp\pylECA8.tmp\data
06-30 19:20 DEBUG  WindowsBackend: 7z=C:\Users\CHRIST~1\AppData\Local\Temp\pylECA8.tmp\bin\7z.exe
06-30 19:20 DEBUG  CommonBackend: Fetching basic info...
06-30 19:20 DEBUG  CommonBackend: original_exe=D:\wubi.exe
06-30 19:20 DEBUG  CommonBackend: platform=win32
06-30 19:20 DEBUG  CommonBackend: osname=nt
06-30 19:20 DEBUG  CommonBackend: language=en_US
06-30 19:20 DEBUG  CommonBackend: encoding=cp1252
06-30 19:20 DEBUG  WindowsBackend: arch=i386
06-30 19:20 DEBUG  CommonBackend: Parsing isolist=C:\Users\CHRIST~1\AppData\Local\Temp\pylECA8.tmp\data\isolist.ini
06-30 19:20 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-30 19:20 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-30 19:20 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-30 19:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-30 19:20 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-30 19:20 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-30 19:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-30 19:20 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-30 19:20 DEBUG  WindowsBackend: Fetching host info...
06-30 19:20 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-30 19:20 DEBUG  WindowsBackend: windows version=vista
06-30 19:20 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
06-30 19:20 DEBUG  WindowsBackend: windows_sp=None
06-30 19:20 DEBUG  WindowsBackend: windows_build=7100
06-30 19:20 DEBUG  WindowsBackend: gmt=-8
06-30 19:20 DEBUG  WindowsBackend: country=US
06-30 19:20 DEBUG  WindowsBackend: timezone=America/Los_Angeles
06-30 19:20 DEBUG  WindowsBackend: windows_username=Christopher Aouate
06-30 19:20 DEBUG  WindowsBackend: user_full_name=Christopher Aouate
06-30 19:20 DEBUG  WindowsBackend: user_directory=Christopher Aouate
06-30 19:20 DEBUG  WindowsBackend: windows_language_code=1033
06-30 19:20 DEBUG  WindowsBackend: windows_language=English
06-30 19:20 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) M processor 1.80GHz
06-30 19:20 DEBUG  WindowsBackend: bootloader=vista
06-30 19:20 DEBUG  WindowsBackend: system_drive=Drive(C: hd 42271.328125 mb free )
06-30 19:20 DEBUG  WindowsBackend: drive=Drive(C: hd 42271.328125 mb free )
06-30 19:20 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
06-30 19:20 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
06-30 19:20 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
06-30 19:20 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
06-30 19:20 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
06-30 19:20 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
06-30 19:20 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
06-30 19:20 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
06-30 19:20 DEBUG  WindowsBackend: keyboard_id=67699721
06-30 19:20 DEBUG  WindowsBackend: keyboard_layout=us
06-30 19:20 DEBUG  WindowsBackend: keyboard_variant=
06-30 19:20 DEBUG  CommonBackend: locale=en_US.UTF-8
06-30 19:20 DEBUG  WindowsBackend: total_memory_mb=1022.9296875
06-30 19:20 DEBUG  CommonBackend: Searching ISOs on USB devices
06-30 19:20 DEBUG  Distro:   checking Ubuntu ISO C:\VL6.0-STD-Gold.iso
06-30 19:20 DEBUG  Distro:     does not contain casper\filesystem.squashfs
06-30 19:20 DEBUG  Distro:   checking Ubuntu ISO C:\VL6.0-STD-Gold.iso
06-30 19:20 DEBUG  Distro:     does not contain casper\filesystem.squashfs
06-30 19:20 DEBUG  Distro:   checking Kubuntu ISO C:\VL6.0-STD-Gold.iso
06-30 19:20 DEBUG  Distro:     does not contain casper\filesystem.squashfs
06-30 19:20 DEBUG  Distro:   checking Kubuntu ISO C:\VL6.0-STD-Gold.iso
06-30 19:20 DEBUG  Distro:     does not contain casper\filesystem.squashfs
06-30 19:20 DEBUG  Distro:   checking Xubuntu ISO C:\VL6.0-STD-Gold.iso
06-30 19:20 DEBUG  Distro:     does not contain casper\filesystem.squashfs
06-30 19:20 DEBUG  Distro:   checking Xubuntu ISO C:\VL6.0-STD-Gold.iso
06-30 19:20 DEBUG  Distro:     does not contain casper\filesystem.squashfs
06-30 19:20 DEBUG  Distro:   checking Mythbuntu ISO C:\VL6.0-STD-Gold.iso
06-30 19:20 DEBUG  Distro:     does not contain casper\filesystem.squashfs
06-30 19:20 DEBUG  Distro:   checking Mythbuntu ISO C:\VL6.0-STD-Gold.iso
06-30 19:20 DEBUG  Distro:     does not contain casper\filesystem.squashfs
06-30 19:20 DEBUG  CommonBackend: Searching for local CDs
06-30 19:20 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pylECA8.tmp is a valid Ubuntu CD
06-30 19:20 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pylECA8.tmp\casper\filesystem.squashfs
06-30 19:20 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pylECA8.tmp is a valid Ubuntu CD
06-30 19:20 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pylECA8.tmp\casper\filesystem.squashfs
06-30 19:20 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pylECA8.tmp is a valid Kubuntu CD
06-30 19:20 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pylECA8.tmp\casper\filesystem.squashfs
06-30 19:20 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pylECA8.tmp is a valid Kubuntu CD
06-30 19:20 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pylECA8.tmp\casper\filesystem.squashfs
06-30 19:20 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pylECA8.tmp is a valid Xubuntu CD
06-30 19:20 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pylECA8.tmp\casper\filesystem.squashfs
06-30 19:20 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pylECA8.tmp is a valid Xubuntu CD
06-30 19:20 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pylECA8.tmp\casper\filesystem.squashfs
06-30 19:20 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pylECA8.tmp is a valid Mythbuntu CD
06-30 19:20 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pylECA8.tmp\casper\filesystem.squashfs
06-30 19:20 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pylECA8.tmp is a valid Mythbuntu CD
06-30 19:20 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pylECA8.tmp\casper\filesystem.squashfs
06-30 19:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-30 19:20 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
06-30 19:20 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
06-30 19:20 DEBUG  Distro: wrong arch: i386 != amd64
06-30 19:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-30 19:20 INFO   Distro: Found a valid CD for Ubuntu: D:\
06-30 19:20 INFO   root: Running the CD menu...
06-30 19:20 DEBUG  WindowsFrontend: __init__...
06-30 19:20 DEBUG  WindowsFrontend: on_init...
06-30 19:20 INFO   root: CD menu finished
06-30 19:20 INFO   root: Running the installer...
06-30 19:21 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=English, username=chris
06-30 19:21 INFO   root: Received settings
06-30 19:21 DEBUG  TaskList: # Running tasklist...
06-30 19:21 DEBUG  TaskList: ## Running select_target_dir...
06-30 19:21 INFO   WindowsBackend: Installing into C:\ubuntu
06-30 19:21 DEBUG  TaskList: ## Finished select_target_dir
06-30 19:21 DEBUG  TaskList: ## Running create_dir_structure...
06-30 19:21 DEBUG  CommonBackend: Creating dir C:\ubuntu
06-30 19:21 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
06-30 19:21 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
06-30 19:21 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
06-30 19:21 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
06-30 19:21 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
06-30 19:21 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
06-30 19:21 DEBUG  TaskList: ## Finished create_dir_structure
06-30 19:21 DEBUG  TaskList: ## Running uncompress_target_dir...
06-30 19:21 DEBUG  TaskList: ## Finished uncompress_target_dir
06-30 19:21 DEBUG  TaskList: ## Running create_uninstaller...
06-30 19:21 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
06-30 19:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
06-30 19:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
06-30 19:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
06-30 19:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
06-30 19:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
06-30 19:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
06-30 19:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
06-30 19:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
06-30 19:21 DEBUG  TaskList: ## Finished create_uninstaller
06-30 19:21 DEBUG  TaskList: ## Running copy_installation_files...
06-30 19:21 DEBUG  WindowsBackend: Copying C:\Users\CHRIST~1\AppData\Local\Temp\pylECA8.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
06-30 19:21 DEBUG  WindowsBackend: Copying C:\Users\CHRIST~1\AppData\Local\Temp\pylECA8.tmp\winboot -> C:\ubuntu\winboot
06-30 19:21 DEBUG  WindowsBackend: Copying C:\Users\CHRIST~1\AppData\Local\Temp\pylECA8.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
06-30 19:21 DEBUG  TaskList: ## Finished copy_installation_files
06-30 19:21 DEBUG  TaskList: ## Running get_iso...
06-30 19:21 DEBUG  TaskList: New task copy_file
06-30 19:21 DEBUG  TaskList: ### Running copy_file...
06-30 19:25 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 13] Permission denied
06-30 19:25 DEBUG  TaskList: # Cancelling tasklist
06-30 19:25 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 13] Permission denied
06-30 19:25 DEBUG  TaskList: New task check_iso
06-30 19:25 DEBUG  CommonBackend: Searching for local ISO
06-30 19:25 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
06-30 19:25 DEBUG  TaskList: New task get_metalink
06-30 19:25 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
06-30 19:25 DEBUG  TaskList: # Cancelling tasklist
06-30 19:25 DEBUG  TaskList: # Finished tasklist
06-30 19:25 INFO   root: === wubi 9.04 rev128 ===
06-30 19:25 DEBUG  root: Logfile is c:\users\christ~1\appdata\local\temp\wubi-9.04-rev128.log
06-30 19:25 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
06-30 19:25 DEBUG  CommonBackend: data_dir=C:\Users\CHRIST~1\AppData\Local\Temp\pyl46C2.tmp\data
06-30 19:25 DEBUG  WindowsBackend: 7z=C:\Users\CHRIST~1\AppData\Local\Temp\pyl46C2.tmp\bin\7z.exe
06-30 19:25 DEBUG  CommonBackend: Fetching basic info...
06-30 19:25 DEBUG  CommonBackend: original_exe=D:\wubi.exe
06-30 19:25 DEBUG  CommonBackend: platform=win32
06-30 19:25 DEBUG  CommonBackend: osname=nt
06-30 19:25 DEBUG  CommonBackend: language=en_US
06-30 19:25 DEBUG  CommonBackend: encoding=cp1252
06-30 19:25 DEBUG  WindowsBackend: arch=i386
06-30 19:25 DEBUG  CommonBackend: Parsing isolist=C:\Users\CHRIST~1\AppData\Local\Temp\pyl46C2.tmp\data\isolist.ini
06-30 19:25 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-30 19:25 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-30 19:25 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-30 19:25 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-30 19:25 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-30 19:25 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-30 19:25 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-30 19:25 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-30 19:25 DEBUG  WindowsBackend: Fetching host info...
06-30 19:25 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-30 19:25 DEBUG  WindowsBackend: windows version=vista
06-30 19:25 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
06-30 19:25 DEBUG  WindowsBackend: windows_sp=None
06-30 19:25 DEBUG  WindowsBackend: windows_build=7100
06-30 19:25 DEBUG  WindowsBackend: gmt=-8
06-30 19:25 DEBUG  WindowsBackend: country=US
06-30 19:25 DEBUG  WindowsBackend: timezone=America/Los_Angeles
06-30 19:25 DEBUG  WindowsBackend: windows_username=Christopher Aouate
06-30 19:25 DEBUG  WindowsBackend: user_full_name=Christopher Aouate
06-30 19:25 DEBUG  WindowsBackend: user_directory=Christopher Aouate
06-30 19:25 DEBUG  WindowsBackend: windows_language_code=1033
06-30 19:25 DEBUG  WindowsBackend: windows_language=English
06-30 19:25 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) M processor 1.80GHz
06-30 19:25 DEBUG  WindowsBackend: bootloader=vista
06-30 19:25 DEBUG  WindowsBackend: system_drive=Drive(C: hd 41471.296875 mb free )
06-30 19:25 DEBUG  WindowsBackend: drive=Drive(C: hd 41471.296875 mb free )
06-30 19:25 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
06-30 19:25 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
06-30 19:25 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
06-30 19:25 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
06-30 19:25 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
06-30 19:25 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
06-30 19:25 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
06-30 19:25 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
06-30 19:25 DEBUG  WindowsBackend: keyboard_id=67699721
06-30 19:25 DEBUG  WindowsBackend: keyboard_layout=us
06-30 19:25 DEBUG  WindowsBackend: keyboard_variant=
06-30 19:25 DEBUG  CommonBackend: locale=en_US.UTF-8
06-30 19:25 DEBUG  WindowsBackend: total_memory_mb=1022.9296875
06-30 19:25 DEBUG  CommonBackend: Searching ISOs on USB devices
06-30 19:25 DEBUG  Distro:   checking Ubuntu ISO C:\VL6.0-STD-Gold.iso
06-30 19:25 DEBUG  Distro:     does not contain casper\filesystem.squashfs
06-30 19:25 DEBUG  Distro:   checking Ubuntu ISO C:\VL6.0-STD-Gold.iso
06-30 19:25 DEBUG  Distro:     does not contain casper\filesystem.squashfs
06-30 19:25 DEBUG  Distro:   checking Kubuntu ISO C:\VL6.0-STD-Gold.iso
06-30 19:25 DEBUG  Distro:     does not contain casper\filesystem.squashfs
06-30 19:25 DEBUG  Distro:   checking Kubuntu ISO C:\VL6.0-STD-Gold.iso
06-30 19:25 DEBUG  Distro:     does not contain casper\filesystem.squashfs
06-30 19:25 DEBUG  Distro:   checking Xubuntu ISO C:\VL6.0-STD-Gold.iso
06-30 19:25 DEBUG  Distro:     does not contain casper\filesystem.squashfs
06-30 19:25 DEBUG  Distro:   checking Xubuntu ISO C:\VL6.0-STD-Gold.iso
06-30 19:25 DEBUG  Distro:     does not contain casper\filesystem.squashfs
06-30 19:25 DEBUG  Distro:   checking Mythbuntu ISO C:\VL6.0-STD-Gold.iso
06-30 19:25 DEBUG  Distro:     does not contain casper\filesystem.squashfs
06-30 19:25 DEBUG  Distro:   checking Mythbuntu ISO C:\VL6.0-STD-Gold.iso
06-30 19:25 DEBUG  Distro:     does not contain casper\filesystem.squashfs
06-30 19:25 DEBUG  CommonBackend: Searching for local CDs
06-30 19:25 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pyl46C2.tmp is a valid Ubuntu CD
06-30 19:25 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pyl46C2.tmp\casper\filesystem.squashfs
06-30 19:25 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pyl46C2.tmp is a valid Ubuntu CD
06-30 19:25 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pyl46C2.tmp\casper\filesystem.squashfs
06-30 19:25 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pyl46C2.tmp is a valid Kubuntu CD
06-30 19:25 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pyl46C2.tmp\casper\filesystem.squashfs
06-30 19:25 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pyl46C2.tmp is a valid Kubuntu CD
06-30 19:25 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pyl46C2.tmp\casper\filesystem.squashfs
06-30 19:25 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pyl46C2.tmp is a valid Xubuntu CD
06-30 19:25 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pyl46C2.tmp\casper\filesystem.squashfs
06-30 19:25 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pyl46C2.tmp is a valid Xubuntu CD
06-30 19:25 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pyl46C2.tmp\casper\filesystem.squashfs
06-30 19:25 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pyl46C2.tmp is a valid Mythbuntu CD
06-30 19:25 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pyl46C2.tmp\casper\filesystem.squashfs
06-30 19:25 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pyl46C2.tmp is a valid Mythbuntu CD
06-30 19:25 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pyl46C2.tmp\casper\filesystem.squashfs
06-30 19:25 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-30 19:25 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
06-30 19:25 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
06-30 19:25 DEBUG  Distro: wrong arch: i386 != amd64
06-30 19:25 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-30 19:25 INFO   Distro: Found a valid CD for Ubuntu: D:\
06-30 19:25 INFO   root: Running the CD menu...
06-30 19:25 DEBUG  WindowsFrontend: __init__...
06-30 19:25 DEBUG  WindowsFrontend: on_init...
06-30 19:25 INFO   root: === wubi 9.04 rev128 ===
06-30 19:25 DEBUG  root: Logfile is c:\users\christ~1\appdata\local\temp\wubi-9.04-rev128.log
06-30 19:25 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
06-30 19:25 DEBUG  CommonBackend: data_dir=C:\Users\CHRIST~1\AppData\Local\Temp\pyl8183.tmp\data
06-30 19:25 DEBUG  WindowsBackend: 7z=C:\Users\CHRIST~1\AppData\Local\Temp\pyl8183.tmp\bin\7z.exe
06-30 19:25 DEBUG  CommonBackend: Fetching basic info...
06-30 19:25 DEBUG  CommonBackend: original_exe=D:\wubi.exe
06-30 19:25 DEBUG  CommonBackend: platform=win32
06-30 19:25 DEBUG  CommonBackend: osname=nt
06-30 19:25 DEBUG  CommonBackend: language=en_US
06-30 19:25 DEBUG  CommonBackend: encoding=cp1252
06-30 19:25 DEBUG  WindowsBackend: arch=i386
06-30 19:25 DEBUG  CommonBackend: Parsing isolist=C:\Users\CHRIST~1\AppData\Local\Temp\pyl8183.tmp\data\isolist.ini
06-30 19:25 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-30 19:25 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-30 19:25 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-30 19:25 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-30 19:25 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-30 19:25 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-30 19:25 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-30 19:25 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-30 19:25 DEBUG  WindowsBackend: Fetching host info...
06-30 19:25 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-30 19:25 DEBUG  WindowsBackend: windows version=vista
06-30 19:25 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
06-30 19:25 DEBUG  WindowsBackend: windows_sp=None
06-30 19:25 DEBUG  WindowsBackend: windows_build=7100
06-30 19:25 DEBUG  WindowsBackend: gmt=-8
06-30 19:25 DEBUG  WindowsBackend: country=US
06-30 19:25 DEBUG  WindowsBackend: timezone=America/Los_Angeles
06-30 19:25 DEBUG  WindowsBackend: windows_username=Christopher Aouate
06-30 19:25 DEBUG  WindowsBackend: user_full_name=Christopher Aouate
06-30 19:25 DEBUG  WindowsBackend: user_directory=Christopher Aouate
06-30 19:25 DEBUG  WindowsBackend: windows_language_code=1033
06-30 19:25 DEBUG  WindowsBackend: windows_language=English
06-30 19:25 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) M processor 1.80GHz
06-30 19:25 DEBUG  WindowsBackend: bootloader=vista
06-30 19:25 DEBUG  WindowsBackend: system_drive=Drive(C: hd 41463.6445313 mb free )
06-30 19:25 DEBUG  WindowsBackend: drive=Drive(C: hd 41463.6445313 mb free )
06-30 19:25 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
06-30 19:25 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
06-30 19:25 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
06-30 19:25 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
06-30 19:25 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
06-30 19:25 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
06-30 19:25 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
06-30 19:25 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
06-30 19:25 DEBUG  WindowsBackend: keyboard_id=67699721
06-30 19:25 DEBUG  WindowsBackend: keyboard_layout=us
06-30 19:25 DEBUG  WindowsBackend: keyboard_variant=
06-30 19:25 DEBUG  CommonBackend: locale=en_US.UTF-8
06-30 19:25 DEBUG  WindowsBackend: total_memory_mb=1022.9296875
06-30 19:25 DEBUG  CommonBackend: Searching ISOs on USB devices
06-30 19:25 DEBUG  Distro:   checking Ubuntu ISO C:\VL6.0-STD-Gold.iso
06-30 19:25 DEBUG  Distro:     does not contain casper\filesystem.squashfs
06-30 19:25 DEBUG  Distro:   checking Ubuntu ISO C:\VL6.0-STD-Gold.iso
06-30 19:25 DEBUG  Distro:     does not contain casper\filesystem.squashfs
06-30 19:25 DEBUG  Distro:   checking Kubuntu ISO C:\VL6.0-STD-Gold.iso
06-30 19:25 DEBUG  Distro:     does not contain casper\filesystem.squashfs
06-30 19:25 DEBUG  Distro:   checking Kubuntu ISO C:\VL6.0-STD-Gold.iso
06-30 19:25 DEBUG  Distro:     does not contain casper\filesystem.squashfs
06-30 19:25 DEBUG  Distro:   checking Xubuntu ISO C:\VL6.0-STD-Gold.iso
06-30 19:25 DEBUG  Distro:     does not contain casper\filesystem.squashfs
06-30 19:25 DEBUG  Distro:   checking Xubuntu ISO C:\VL6.0-STD-Gold.iso
06-30 19:25 DEBUG  Distro:     does not contain casper\filesystem.squashfs
06-30 19:25 DEBUG  Distro:   checking Mythbuntu ISO C:\VL6.0-STD-Gold.iso
06-30 19:25 DEBUG  Distro:     does not contain casper\filesystem.squashfs
06-30 19:25 DEBUG  Distro:   checking Mythbuntu ISO C:\VL6.0-STD-Gold.iso
06-30 19:25 DEBUG  Distro:     does not contain casper\filesystem.squashfs
06-30 19:25 DEBUG  CommonBackend: Searching for local CDs
06-30 19:25 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pyl8183.tmp is a valid Ubuntu CD
06-30 19:25 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pyl8183.tmp\casper\filesystem.squashfs
06-30 19:25 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pyl8183.tmp is a valid Ubuntu CD
06-30 19:25 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pyl8183.tmp\casper\filesystem.squashfs
06-30 19:25 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pyl8183.tmp is a valid Kubuntu CD
06-30 19:25 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pyl8183.tmp\casper\filesystem.squashfs
06-30 19:25 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pyl8183.tmp is a valid Kubuntu CD
06-30 19:25 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pyl8183.tmp\casper\filesystem.squashfs
06-30 19:25 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pyl8183.tmp is a valid Xubuntu CD
06-30 19:25 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pyl8183.tmp\casper\filesystem.squashfs
06-30 19:25 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pyl8183.tmp is a valid Xubuntu CD
06-30 19:25 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pyl8183.tmp\casper\filesystem.squashfs
06-30 19:25 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pyl8183.tmp is a valid Mythbuntu CD
06-30 19:25 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pyl8183.tmp\casper\filesystem.squashfs
06-30 19:25 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pyl8183.tmp is a valid Mythbuntu CD
06-30 19:25 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pyl8183.tmp\casper\filesystem.squashfs
06-30 19:25 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-30 19:25 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
06-30 19:25 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
06-30 19:25 DEBUG  Distro: wrong arch: i386 != amd64
06-30 19:25 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-30 19:25 INFO   Distro: Found a valid CD for Ubuntu: D:\
06-30 19:25 INFO   root: Running the CD menu...
06-30 19:25 DEBUG  WindowsFrontend: __init__...
06-30 19:25 DEBUG  WindowsFrontend: on_init...
06-30 19:25 INFO   WindowsFrontend: Operation cancelled
06-30 19:25 DEBUG  WindowsFrontend: frontend.quit
06-30 19:25 DEBUG  WindowsFrontend: frontend.on_quit
06-30 19:25 DEBUG  root: application.on_quit
06-30 19:25 INFO   root: sys.exit
06-30 19:25 INFO   root: CD menu finished
06-30 19:25 INFO   root: Already installed, running the uninstaller...
06-30 19:25 INFO   root: Running the uninstaller...
06-30 19:25 INFO   CommonBackend: This is the uninstaller running
06-30 19:25 INFO   root: Received settings
06-30 19:25 DEBUG  TaskList: # Running tasklist...
06-30 19:25 DEBUG  TaskList: ## Running Backup ISO...
06-30 19:25 DEBUG  TaskList: ## Finished Backup ISO
06-30 19:25 DEBUG  TaskList: ## Running Remove bootloader entry...
06-30 19:25 DEBUG  WindowsBackend: Could not find bcd id
06-30 19:25 DEBUG  WindowsBackend: undo_bootini C:
06-30 19:25 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 41463.6445313 mb free )
06-30 19:25 DEBUG  TaskList: ## Finished Remove bootloader entry
06-30 19:25 DEBUG  TaskList: ## Running Remove target dir...
06-30 19:25 DEBUG  CommonBackend: Deleting C:\ubuntu
06-30 19:25 DEBUG  TaskList: ## Finished Remove target dir
06-30 19:25 DEBUG  TaskList: ## Running Remove registry key...
06-30 19:25 DEBUG  TaskList: ## Finished Remove registry key
06-30 19:25 DEBUG  TaskList: # Finished tasklist
06-30 19:25 INFO   root: Almost finished uninstalling
06-30 19:25 INFO   root: Finished uninstallation
06-30 19:25 DEBUG  CommonBackend: Fetching basic info...
06-30 19:25 DEBUG  CommonBackend: original_exe=D:\wubi.exe
06-30 19:25 DEBUG  CommonBackend: platform=win32
06-30 19:25 DEBUG  CommonBackend: osname=nt
06-30 19:25 DEBUG  CommonBackend: language=en_US
06-30 19:25 DEBUG  CommonBackend: encoding=cp1252
06-30 19:25 DEBUG  WindowsBackend: arch=i386
06-30 19:25 DEBUG  CommonBackend: Parsing isolist=C:\Users\CHRIST~1\AppData\Local\Temp\pyl8183.tmp\data\isolist.ini
06-30 19:25 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-30 19:25 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-30 19:25 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-30 19:25 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-30 19:25 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-30 19:25 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-30 19:25 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-30 19:25 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-30 19:25 DEBUG  WindowsBackend: Fetching host info...
06-30 19:25 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-30 19:25 DEBUG  WindowsBackend: windows version=vista
06-30 19:25 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
06-30 19:25 DEBUG  WindowsBackend: windows_sp=None
06-30 19:25 DEBUG  WindowsBackend: windows_build=7100
06-30 19:25 DEBUG  WindowsBackend: gmt=-8
06-30 19:25 DEBUG  WindowsBackend: country=US
06-30 19:25 DEBUG  WindowsBackend: timezone=America/Los_Angeles
06-30 19:25 DEBUG  WindowsBackend: windows_username=Christopher Aouate
06-30 19:25 DEBUG  WindowsBackend: user_full_name=Christopher Aouate
06-30 19:25 DEBUG  WindowsBackend: user_directory=Christopher Aouate
06-30 19:25 DEBUG  WindowsBackend: windows_language_code=1033
06-30 19:25 DEBUG  WindowsBackend: windows_language=English
06-30 19:25 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) M processor 1.80GHz
06-30 19:25 DEBUG  WindowsBackend: bootloader=vista
06-30 19:25 DEBUG  WindowsBackend: system_drive=Drive(C: hd 42045.6679688 mb free )
06-30 19:25 DEBUG  WindowsBackend: drive=Drive(C: hd 42045.6679688 mb free )
06-30 19:25 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
06-30 19:25 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
06-30 19:25 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
06-30 19:25 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
06-30 19:25 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
06-30 19:25 DEBUG  WindowsBackend: uninstaller_path=None
06-30 19:25 DEBUG  WindowsBackend: previous_target_dir=None
06-30 19:25 DEBUG  WindowsBackend: previous_distro_name=None
06-30 19:25 DEBUG  WindowsBackend: keyboard_id=67699721
06-30 19:25 DEBUG  WindowsBackend: keyboard_layout=us
06-30 19:25 DEBUG  WindowsBackend: keyboard_variant=
06-30 19:25 DEBUG  CommonBackend: locale=en_US.UTF-8
06-30 19:25 DEBUG  WindowsBackend: total_memory_mb=1022.9296875
06-30 19:25 DEBUG  CommonBackend: Searching ISOs on USB devices
06-30 19:25 DEBUG  Distro:   checking Ubuntu ISO C:\VL6.0-STD-Gold.iso
06-30 19:25 DEBUG  Distro:     does not contain casper\filesystem.squashfs
06-30 19:25 DEBUG  Distro:   checking Ubuntu ISO C:\VL6.0-STD-Gold.iso
06-30 19:25 DEBUG  Distro:     does not contain casper\filesystem.squashfs
06-30 19:25 DEBUG  Distro:   checking Kubuntu ISO C:\VL6.0-STD-Gold.iso
06-30 19:25 DEBUG  Distro:     does not contain casper\filesystem.squashfs
06-30 19:25 DEBUG  Distro:   checking Kubuntu ISO C:\VL6.0-STD-Gold.iso
06-30 19:25 DEBUG  Distro:     does not contain casper\filesystem.squashfs
06-30 19:25 DEBUG  Distro:   checking Xubuntu ISO C:\VL6.0-STD-Gold.iso
06-30 19:25 DEBUG  Distro:     does not contain casper\filesystem.squashfs
06-30 19:25 DEBUG  Distro:   checking Xubuntu ISO C:\VL6.0-STD-Gold.iso
06-30 19:25 DEBUG  Distro:     does not contain casper\filesystem.squashfs
06-30 19:25 DEBUG  Distro:   checking Mythbuntu ISO C:\VL6.0-STD-Gold.iso
06-30 19:25 DEBUG  Distro:     does not contain casper\filesystem.squashfs
06-30 19:25 DEBUG  Distro:   checking Mythbuntu ISO C:\VL6.0-STD-Gold.iso
06-30 19:25 DEBUG  Distro:     does not contain casper\filesystem.squashfs
06-30 19:25 DEBUG  CommonBackend: Searching for local CDs
06-30 19:25 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pyl8183.tmp is a valid Ubuntu CD
06-30 19:25 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pyl8183.tmp\casper\filesystem.squashfs
06-30 19:25 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pyl8183.tmp is a valid Ubuntu CD
06-30 19:25 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pyl8183.tmp\casper\filesystem.squashfs
06-30 19:25 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pyl8183.tmp is a valid Kubuntu CD
06-30 19:25 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pyl8183.tmp\casper\filesystem.squashfs
06-30 19:25 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pyl8183.tmp is a valid Kubuntu CD
06-30 19:25 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pyl8183.tmp\casper\filesystem.squashfs
06-30 19:25 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pyl8183.tmp is a valid Xubuntu CD
06-30 19:25 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pyl8183.tmp\casper\filesystem.squashfs
06-30 19:25 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pyl8183.tmp is a valid Xubuntu CD
06-30 19:25 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pyl8183.tmp\casper\filesystem.squashfs
06-30 19:25 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pyl8183.tmp is a valid Mythbuntu CD
06-30 19:25 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pyl8183.tmp\casper\filesystem.squashfs
06-30 19:25 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pyl8183.tmp is a valid Mythbuntu CD
06-30 19:25 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pyl8183.tmp\casper\filesystem.squashfs
06-30 19:25 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-30 19:25 DEBUG  Distro: wrong arch: i386 != amd64
06-30 19:25 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-30 19:25 INFO   Distro: Found a valid CD for Ubuntu: D:\
06-30 19:25 INFO   root: Running the installer...
06-30 19:26 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=English, username=chris
06-30 19:26 INFO   root: Received settings
06-30 19:26 DEBUG  TaskList: # Running tasklist...
06-30 19:26 DEBUG  TaskList: ## Running select_target_dir...
06-30 19:26 INFO   WindowsBackend: Installing into C:\ubuntu
06-30 19:26 DEBUG  TaskList: ## Finished select_target_dir
06-30 19:26 DEBUG  TaskList: ## Running create_dir_structure...
06-30 19:26 DEBUG  CommonBackend: Creating dir C:\ubuntu
06-30 19:26 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
06-30 19:26 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
06-30 19:26 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
06-30 19:26 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
06-30 19:26 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
06-30 19:26 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
06-30 19:26 DEBUG  TaskList: ## Finished create_dir_structure
06-30 19:26 DEBUG  TaskList: ## Running uncompress_target_dir...
06-30 19:26 DEBUG  TaskList: ## Finished uncompress_target_dir
06-30 19:26 DEBUG  TaskList: ## Running create_uninstaller...
06-30 19:26 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
06-30 19:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
06-30 19:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
06-30 19:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
06-30 19:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
06-30 19:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
06-30 19:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
06-30 19:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
06-30 19:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
06-30 19:26 DEBUG  TaskList: ## Finished create_uninstaller
06-30 19:26 DEBUG  TaskList: ## Running copy_installation_files...
06-30 19:26 DEBUG  WindowsBackend: Copying C:\Users\CHRIST~1\AppData\Local\Temp\pyl8183.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
06-30 19:26 DEBUG  WindowsBackend: Copying C:\Users\CHRIST~1\AppData\Local\Temp\pyl8183.tmp\winboot -> C:\ubuntu\winboot
06-30 19:26 DEBUG  WindowsBackend: Copying C:\Users\CHRIST~1\AppData\Local\Temp\pyl8183.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
06-30 19:26 DEBUG  TaskList: ## Finished copy_installation_files
06-30 19:26 DEBUG  TaskList: ## Running get_iso...
06-30 19:26 DEBUG  TaskList: New task copy_file
06-30 19:26 DEBUG  TaskList: ### Running copy_file...
06-30 19:36 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 13] Permission denied
06-30 19:36 DEBUG  TaskList: # Cancelling tasklist
06-30 19:36 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 13] Permission denied
06-30 19:36 DEBUG  TaskList: New task check_iso
06-30 19:36 DEBUG  CommonBackend: Searching for local ISO
06-30 19:36 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
06-30 19:36 DEBUG  TaskList: New task get_metalink
06-30 19:36 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
06-30 19:36 DEBUG  TaskList: # Cancelling tasklist
06-30 19:36 DEBUG  TaskList: # Finished tasklist
06-30 21:17 INFO   root: === wubi 9.04 rev128 ===
06-30 21:17 DEBUG  root: Logfile is c:\users\christ~1\appdata\local\temp\wubi-9.04-rev128.log
06-30 21:17 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
06-30 21:17 DEBUG  CommonBackend: data_dir=C:\Users\CHRIST~1\AppData\Local\Temp\pyl14F2.tmp\data
06-30 21:17 DEBUG  WindowsBackend: 7z=C:\Users\CHRIST~1\AppData\Local\Temp\pyl14F2.tmp\bin\7z.exe
06-30 21:17 DEBUG  CommonBackend: Fetching basic info...
06-30 21:17 DEBUG  CommonBackend: original_exe=D:\wubi.exe
06-30 21:17 DEBUG  CommonBackend: platform=win32
06-30 21:17 DEBUG  CommonBackend: osname=nt
06-30 21:17 DEBUG  CommonBackend: language=en_US
06-30 21:17 DEBUG  CommonBackend: encoding=cp1252
06-30 21:17 DEBUG  WindowsBackend: arch=i386
06-30 21:17 DEBUG  CommonBackend: Parsing isolist=C:\Users\CHRIST~1\AppData\Local\Temp\pyl14F2.tmp\data\isolist.ini
06-30 21:17 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-30 21:17 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-30 21:17 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-30 21:17 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-30 21:17 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-30 21:17 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-30 21:17 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-30 21:17 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-30 21:17 DEBUG  WindowsBackend: Fetching host info...
06-30 21:17 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-30 21:17 DEBUG  WindowsBackend: windows version=vista
06-30 21:17 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
06-30 21:17 DEBUG  WindowsBackend: windows_sp=None
06-30 21:17 DEBUG  WindowsBackend: windows_build=7100
06-30 21:17 DEBUG  WindowsBackend: gmt=-8
06-30 21:17 DEBUG  WindowsBackend: country=US
06-30 21:17 DEBUG  WindowsBackend: timezone=America/Los_Angeles
06-30 21:17 DEBUG  WindowsBackend: windows_username=Christopher Aouate
06-30 21:17 DEBUG  WindowsBackend: user_full_name=Christopher Aouate
06-30 21:17 DEBUG  WindowsBackend: user_directory=Christopher Aouate
06-30 21:17 DEBUG  WindowsBackend: windows_language_code=1033
06-30 21:17 DEBUG  WindowsBackend: windows_language=English
06-30 21:17 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) M processor 1.80GHz
06-30 21:17 DEBUG  WindowsBackend: bootloader=vista
06-30 21:17 DEBUG  WindowsBackend: system_drive=Drive(C: hd 41217.8125 mb free )
06-30 21:17 DEBUG  WindowsBackend: drive=Drive(C: hd 41217.8125 mb free )
06-30 21:17 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
06-30 21:17 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
06-30 21:17 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
06-30 21:17 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
06-30 21:17 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
06-30 21:17 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
06-30 21:17 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
06-30 21:17 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
06-30 21:17 DEBUG  WindowsBackend: keyboard_id=67699721
06-30 21:17 DEBUG  WindowsBackend: keyboard_layout=us
06-30 21:17 DEBUG  WindowsBackend: keyboard_variant=
06-30 21:17 DEBUG  CommonBackend: locale=en_US.UTF-8
06-30 21:17 DEBUG  WindowsBackend: total_memory_mb=1022.9296875
06-30 21:17 DEBUG  CommonBackend: Searching ISOs on USB devices
06-30 21:17 DEBUG  Distro:   checking Ubuntu ISO C:\VL6.0-STD-Gold.iso
06-30 21:17 DEBUG  Distro:     does not contain casper\filesystem.squashfs
06-30 21:17 DEBUG  Distro:   checking Ubuntu ISO C:\VL6.0-STD-Gold.iso
06-30 21:17 DEBUG  Distro:     does not contain casper\filesystem.squashfs
06-30 21:17 DEBUG  Distro:   checking Kubuntu ISO C:\VL6.0-STD-Gold.iso
06-30 21:17 DEBUG  Distro:     does not contain casper\filesystem.squashfs
06-30 21:17 DEBUG  Distro:   checking Kubuntu ISO C:\VL6.0-STD-Gold.iso
06-30 21:17 DEBUG  Distro:     does not contain casper\filesystem.squashfs
06-30 21:17 DEBUG  Distro:   checking Xubuntu ISO C:\VL6.0-STD-Gold.iso
06-30 21:17 DEBUG  Distro:     does not contain casper\filesystem.squashfs
06-30 21:17 DEBUG  Distro:   checking Xubuntu ISO C:\VL6.0-STD-Gold.iso
06-30 21:17 DEBUG  Distro:     does not contain casper\filesystem.squashfs
06-30 21:17 DEBUG  Distro:   checking Mythbuntu ISO C:\VL6.0-STD-Gold.iso
06-30 21:17 DEBUG  Distro:     does not contain casper\filesystem.squashfs
06-30 21:17 DEBUG  Distro:   checking Mythbuntu ISO C:\VL6.0-STD-Gold.iso
06-30 21:17 DEBUG  Distro:     does not contain casper\filesystem.squashfs
06-30 21:17 DEBUG  CommonBackend: Searching for local CDs
06-30 21:17 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pyl14F2.tmp is a valid Ubuntu CD
06-30 21:17 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pyl14F2.tmp\casper\filesystem.squashfs
06-30 21:17 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pyl14F2.tmp is a valid Ubuntu CD
06-30 21:17 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pyl14F2.tmp\casper\filesystem.squashfs
06-30 21:17 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pyl14F2.tmp is a valid Kubuntu CD
06-30 21:17 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pyl14F2.tmp\casper\filesystem.squashfs
06-30 21:17 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pyl14F2.tmp is a valid Kubuntu CD
06-30 21:17 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pyl14F2.tmp\casper\filesystem.squashfs
06-30 21:17 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pyl14F2.tmp is a valid Xubuntu CD
06-30 21:17 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pyl14F2.tmp\casper\filesystem.squashfs
06-30 21:17 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pyl14F2.tmp is a valid Xubuntu CD
06-30 21:17 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pyl14F2.tmp\casper\filesystem.squashfs
06-30 21:17 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pyl14F2.tmp is a valid Mythbuntu CD
06-30 21:17 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pyl14F2.tmp\casper\filesystem.squashfs
06-30 21:17 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pyl14F2.tmp is a valid Mythbuntu CD
06-30 21:17 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pyl14F2.tmp\casper\filesystem.squashfs
06-30 21:17 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-30 21:17 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 54, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 161, in fetch_basic_info
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 665, in find_any_cd
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\distro.py", line 84, in is_valid_cd
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\distro.py", line 138, in get_info
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 235, in read_file
IOError: [Errno 13] Permission denied
06-30 21:19 INFO   root: === wubi 9.04 rev128 ===
06-30 21:19 DEBUG  root: Logfile is c:\users\christ~1\appdata\local\temp\wubi-9.04-rev128.log
06-30 21:19 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
06-30 21:19 DEBUG  CommonBackend: data_dir=C:\Users\CHRIST~1\AppData\Local\Temp\pyl4BC.tmp\data
06-30 21:19 DEBUG  WindowsBackend: 7z=C:\Users\CHRIST~1\AppData\Local\Temp\pyl4BC.tmp\bin\7z.exe
06-30 21:19 DEBUG  CommonBackend: Fetching basic info...
06-30 21:19 DEBUG  CommonBackend: original_exe=D:\wubi.exe
06-30 21:19 DEBUG  CommonBackend: platform=win32
06-30 21:19 DEBUG  CommonBackend: osname=nt
06-30 21:19 DEBUG  CommonBackend: language=en_US
06-30 21:19 DEBUG  CommonBackend: encoding=cp1252
06-30 21:19 DEBUG  WindowsBackend: arch=i386
06-30 21:19 DEBUG  CommonBackend: Parsing isolist=C:\Users\CHRIST~1\AppData\Local\Temp\pyl4BC.tmp\data\isolist.ini
06-30 21:19 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-30 21:19 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-30 21:19 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-30 21:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-30 21:19 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-30 21:19 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-30 21:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-30 21:19 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-30 21:19 DEBUG  WindowsBackend: Fetching host info...
06-30 21:19 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-30 21:19 DEBUG  WindowsBackend: windows version=vista
06-30 21:19 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
06-30 21:19 DEBUG  WindowsBackend: windows_sp=None
06-30 21:19 DEBUG  WindowsBackend: windows_build=7100
06-30 21:19 DEBUG  WindowsBackend: gmt=-8
06-30 21:19 DEBUG  WindowsBackend: country=US
06-30 21:19 DEBUG  WindowsBackend: timezone=America/Los_Angeles
06-30 21:19 DEBUG  WindowsBackend: windows_username=Christopher Aouate
06-30 21:19 DEBUG  WindowsBackend: user_full_name=Christopher Aouate
06-30 21:19 DEBUG  WindowsBackend: user_directory=Christopher Aouate
06-30 21:19 DEBUG  WindowsBackend: windows_language_code=1033
06-30 21:19 DEBUG  WindowsBackend: windows_language=English
06-30 21:19 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) M processor 1.80GHz
06-30 21:19 DEBUG  WindowsBackend: bootloader=vista
06-30 21:19 DEBUG  WindowsBackend: system_drive=Drive(C: hd 41226.3515625 mb free )
06-30 21:19 DEBUG  WindowsBackend: drive=Drive(C: hd 41226.3515625 mb free )
06-30 21:19 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
06-30 21:19 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
06-30 21:19 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
06-30 21:19 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
06-30 21:19 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
06-30 21:19 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
06-30 21:19 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
06-30 21:19 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
06-30 21:19 DEBUG  WindowsBackend: keyboard_id=67699721
06-30 21:19 DEBUG  WindowsBackend: keyboard_layout=us
06-30 21:19 DEBUG  WindowsBackend: keyboard_variant=
06-30 21:19 DEBUG  CommonBackend: locale=en_US.UTF-8
06-30 21:19 DEBUG  WindowsBackend: total_memory_mb=1022.9296875
06-30 21:19 DEBUG  CommonBackend: Searching ISOs on USB devices
06-30 21:19 DEBUG  Distro:   checking Ubuntu ISO C:\VL6.0-STD-Gold.iso
06-30 21:19 DEBUG  Distro:     does not contain casper\filesystem.squashfs
06-30 21:19 DEBUG  Distro:   checking Ubuntu ISO C:\VL6.0-STD-Gold.iso
06-30 21:19 DEBUG  Distro:     does not contain casper\filesystem.squashfs
06-30 21:19 DEBUG  Distro:   checking Kubuntu ISO C:\VL6.0-STD-Gold.iso
06-30 21:19 DEBUG  Distro:     does not contain casper\filesystem.squashfs
06-30 21:19 DEBUG  Distro:   checking Kubuntu ISO C:\VL6.0-STD-Gold.iso
06-30 21:19 DEBUG  Distro:     does not contain casper\filesystem.squashfs
06-30 21:19 DEBUG  Distro:   checking Xubuntu ISO C:\VL6.0-STD-Gold.iso
06-30 21:19 DEBUG  Distro:     does not contain casper\filesystem.squashfs
06-30 21:19 DEBUG  Distro:   checking Xubuntu ISO C:\VL6.0-STD-Gold.iso
06-30 21:19 DEBUG  Distro:     does not contain casper\filesystem.squashfs
06-30 21:19 DEBUG  Distro:   checking Mythbuntu ISO C:\VL6.0-STD-Gold.iso
06-30 21:19 DEBUG  Distro:     does not contain casper\filesystem.squashfs
06-30 21:19 DEBUG  Distro:   checking Mythbuntu ISO C:\VL6.0-STD-Gold.iso
06-30 21:19 DEBUG  Distro:     does not contain casper\filesystem.squashfs
06-30 21:19 DEBUG  CommonBackend: Searching for local CDs
06-30 21:19 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pyl4BC.tmp is a valid Ubuntu CD
06-30 21:19 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pyl4BC.tmp\casper\filesystem.squashfs
06-30 21:19 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pyl4BC.tmp is a valid Ubuntu CD
06-30 21:19 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pyl4BC.tmp\casper\filesystem.squashfs
06-30 21:19 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pyl4BC.tmp is a valid Kubuntu CD
06-30 21:19 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pyl4BC.tmp\casper\filesystem.squashfs
06-30 21:19 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pyl4BC.tmp is a valid Kubuntu CD
06-30 21:19 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pyl4BC.tmp\casper\filesystem.squashfs
06-30 21:19 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pyl4BC.tmp is a valid Xubuntu CD
06-30 21:19 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pyl4BC.tmp\casper\filesystem.squashfs
06-30 21:19 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pyl4BC.tmp is a valid Xubuntu CD
06-30 21:19 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pyl4BC.tmp\casper\filesystem.squashfs
06-30 21:19 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pyl4BC.tmp is a valid Mythbuntu CD
06-30 21:19 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pyl4BC.tmp\casper\filesystem.squashfs
06-30 21:19 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pyl4BC.tmp is a valid Mythbuntu CD
06-30 21:19 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pyl4BC.tmp\casper\filesystem.squashfs
06-30 21:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-30 21:19 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 54, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 161, in fetch_basic_info
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 665, in find_any_cd
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\distro.py", line 84, in is_valid_cd
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\distro.py", line 138, in get_info
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 235, in read_file
IOError: [Errno 13] Permission denied
07-01 12:28 INFO   root: === wubi 9.04 rev128 ===
07-01 12:28 DEBUG  root: Logfile is c:\users\christ~1\appdata\local\temp\wubi-9.04-rev128.log
07-01 12:28 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
07-01 12:28 DEBUG  CommonBackend: data_dir=C:\Users\CHRIST~1\AppData\Local\Temp\pylBDDD.tmp\data
07-01 12:28 DEBUG  WindowsBackend: 7z=C:\Users\CHRIST~1\AppData\Local\Temp\pylBDDD.tmp\bin\7z.exe
07-01 12:28 DEBUG  CommonBackend: Fetching basic info...
07-01 12:28 DEBUG  CommonBackend: original_exe=D:\wubi.exe
07-01 12:28 DEBUG  CommonBackend: platform=win32
07-01 12:28 DEBUG  CommonBackend: osname=nt
07-01 12:28 DEBUG  CommonBackend: language=en_US
07-01 12:28 DEBUG  CommonBackend: encoding=cp1252
07-01 12:28 DEBUG  WindowsBackend: arch=i386
07-01 12:28 DEBUG  CommonBackend: Parsing isolist=C:\Users\CHRIST~1\AppData\Local\Temp\pylBDDD.tmp\data\isolist.ini
07-01 12:28 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-01 12:28 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-01 12:28 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-01 12:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-01 12:28 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-01 12:28 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-01 12:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-01 12:28 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-01 12:28 DEBUG  WindowsBackend: Fetching host info...
07-01 12:28 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-01 12:28 DEBUG  WindowsBackend: windows version=vista
07-01 12:28 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
07-01 12:28 DEBUG  WindowsBackend: windows_sp=None
07-01 12:28 DEBUG  WindowsBackend: windows_build=7100
07-01 12:28 DEBUG  WindowsBackend: gmt=-8
07-01 12:28 DEBUG  WindowsBackend: country=US
07-01 12:28 DEBUG  WindowsBackend: timezone=America/Los_Angeles
07-01 12:28 DEBUG  WindowsBackend: windows_username=Christopher Aouate
07-01 12:28 DEBUG  WindowsBackend: user_full_name=Christopher Aouate
07-01 12:28 DEBUG  WindowsBackend: user_directory=Christopher Aouate
07-01 12:28 DEBUG  WindowsBackend: windows_language_code=1033
07-01 12:28 DEBUG  WindowsBackend: windows_language=English
07-01 12:28 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) M processor 1.80GHz
07-01 12:28 DEBUG  WindowsBackend: bootloader=vista
07-01 12:28 DEBUG  WindowsBackend: system_drive=Drive(C: hd 42712.921875 mb free )
07-01 12:28 DEBUG  WindowsBackend: drive=Drive(C: hd 42712.921875 mb free )
07-01 12:28 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
07-01 12:28 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
07-01 12:28 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
07-01 12:28 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
07-01 12:28 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
07-01 12:28 DEBUG  WindowsBackend: drive=Drive(I: removable 857.30859375 mb free fat32)
07-01 12:28 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
07-01 12:28 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
07-01 12:28 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
07-01 12:28 DEBUG  WindowsBackend: keyboard_id=67699721
07-01 12:28 DEBUG  WindowsBackend: keyboard_layout=us
07-01 12:28 DEBUG  WindowsBackend: keyboard_variant=
07-01 12:28 DEBUG  CommonBackend: locale=en_US.UTF-8
07-01 12:28 DEBUG  WindowsBackend: total_memory_mb=1022.9296875
07-01 12:28 DEBUG  CommonBackend: Searching ISOs on USB devices
07-01 12:28 DEBUG  Distro:   checking Ubuntu ISO C:\VL6.0-STD-Gold.iso
07-01 12:28 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-01 12:28 DEBUG  Distro:   checking Ubuntu ISO C:\VL6.0-STD-Gold.iso
07-01 12:28 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-01 12:28 DEBUG  Distro:   checking Kubuntu ISO C:\VL6.0-STD-Gold.iso
07-01 12:28 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-01 12:28 DEBUG  Distro:   checking Kubuntu ISO C:\VL6.0-STD-Gold.iso
07-01 12:28 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-01 12:28 DEBUG  Distro:   checking Xubuntu ISO C:\VL6.0-STD-Gold.iso
07-01 12:28 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-01 12:28 DEBUG  Distro:   checking Xubuntu ISO C:\VL6.0-STD-Gold.iso
07-01 12:28 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-01 12:28 DEBUG  Distro:   checking Mythbuntu ISO C:\VL6.0-STD-Gold.iso
07-01 12:28 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-01 12:28 DEBUG  Distro:   checking Mythbuntu ISO C:\VL6.0-STD-Gold.iso
07-01 12:28 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-01 12:28 DEBUG  Distro:   checking Ubuntu ISO I:\TEENpup2009Legacy.iso
07-01 12:28 DEBUG  Distro:     wrong size: 47657310 < 600000000
07-01 12:28 DEBUG  Distro:   checking Ubuntu ISO I:\TEENpup2009Legacy.iso
07-01 12:28 DEBUG  Distro:     wrong size: 47657310 < 600000000
07-01 12:28 DEBUG  Distro:   checking Kubuntu ISO I:\TEENpup2009Legacy.iso
07-01 12:28 DEBUG  Distro:     wrong size: 47657310 < 600000000
07-01 12:28 DEBUG  Distro:   checking Kubuntu ISO I:\TEENpup2009Legacy.iso
07-01 12:28 DEBUG  Distro:     wrong size: 47657310 < 600000000
07-01 12:28 DEBUG  Distro:   checking Xubuntu ISO I:\TEENpup2009Legacy.iso
07-01 12:28 DEBUG  Distro:     wrong size: 47657310 < 600000000
07-01 12:28 DEBUG  Distro:   checking Xubuntu ISO I:\TEENpup2009Legacy.iso
07-01 12:28 DEBUG  Distro:     wrong size: 47657310 < 600000000
07-01 12:28 DEBUG  Distro:   checking Mythbuntu ISO I:\TEENpup2009Legacy.iso
07-01 12:28 DEBUG  Distro:     wrong size: 47657310 < 600000000
07-01 12:28 DEBUG  Distro:   checking Mythbuntu ISO I:\TEENpup2009Legacy.iso
07-01 12:28 DEBUG  Distro:     wrong size: 47657310 < 600000000
07-01 12:28 DEBUG  CommonBackend: Searching for local CDs
07-01 12:28 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pylBDDD.tmp is a valid Ubuntu CD
07-01 12:28 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pylBDDD.tmp\casper\filesystem.squashfs
07-01 12:28 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pylBDDD.tmp is a valid Ubuntu CD
07-01 12:28 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pylBDDD.tmp\casper\filesystem.squashfs
07-01 12:28 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pylBDDD.tmp is a valid Kubuntu CD
07-01 12:28 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pylBDDD.tmp\casper\filesystem.squashfs
07-01 12:28 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pylBDDD.tmp is a valid Kubuntu CD
07-01 12:28 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pylBDDD.tmp\casper\filesystem.squashfs
07-01 12:28 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pylBDDD.tmp is a valid Xubuntu CD
07-01 12:28 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pylBDDD.tmp\casper\filesystem.squashfs
07-01 12:28 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pylBDDD.tmp is a valid Xubuntu CD
07-01 12:28 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pylBDDD.tmp\casper\filesystem.squashfs
07-01 12:28 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pylBDDD.tmp is a valid Mythbuntu CD
07-01 12:28 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pylBDDD.tmp\casper\filesystem.squashfs
07-01 12:28 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pylBDDD.tmp is a valid Mythbuntu CD
07-01 12:28 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pylBDDD.tmp\casper\filesystem.squashfs
07-01 12:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-01 12:28 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
07-01 12:28 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
07-01 12:28 DEBUG  Distro: wrong arch: i386 != amd64
07-01 12:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-01 12:28 INFO   Distro: Found a valid CD for Ubuntu: D:\
07-01 12:28 INFO   root: Running the CD menu...
07-01 12:28 DEBUG  WindowsFrontend: __init__...
07-01 12:28 DEBUG  WindowsFrontend: on_init...
07-01 12:29 INFO   root: CD menu finished
07-01 12:29 INFO   root: Already installed, running the uninstaller...
07-01 12:29 INFO   root: Running the uninstaller...
07-01 12:29 INFO   CommonBackend: This is the uninstaller running
07-01 12:29 INFO   root: Received settings
07-01 12:29 DEBUG  TaskList: # Running tasklist...
07-01 12:29 DEBUG  TaskList: ## Running Backup ISO...
07-01 12:29 DEBUG  TaskList: ## Finished Backup ISO
07-01 12:29 DEBUG  TaskList: ## Running Remove bootloader entry...
07-01 12:29 DEBUG  WindowsBackend: Could not find bcd id
07-01 12:29 DEBUG  WindowsBackend: undo_bootini C:
07-01 12:29 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 42712.921875 mb free )
07-01 12:29 DEBUG  WindowsBackend: undo_bootini I:
07-01 12:29 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 857.30859375 mb free fat32)
07-01 12:29 DEBUG  TaskList: ## Finished Remove bootloader entry
07-01 12:29 DEBUG  TaskList: ## Running Remove target dir...
07-01 12:29 DEBUG  CommonBackend: Deleting C:\ubuntu
07-01 12:29 DEBUG  TaskList: ## Finished Remove target dir
07-01 12:29 DEBUG  TaskList: ## Running Remove registry key...
07-01 12:29 DEBUG  TaskList: ## Finished Remove registry key
07-01 12:29 DEBUG  TaskList: # Finished tasklist
07-01 12:29 INFO   root: Almost finished uninstalling
07-01 12:29 INFO   root: Finished uninstallation
07-01 12:29 DEBUG  CommonBackend: Fetching basic info...
07-01 12:29 DEBUG  CommonBackend: original_exe=D:\wubi.exe
07-01 12:29 DEBUG  CommonBackend: platform=win32
07-01 12:29 DEBUG  CommonBackend: osname=nt
07-01 12:29 DEBUG  CommonBackend: language=en_US
07-01 12:29 DEBUG  CommonBackend: encoding=cp1252
07-01 12:29 DEBUG  WindowsBackend: arch=i386
07-01 12:29 DEBUG  CommonBackend: Parsing isolist=C:\Users\CHRIST~1\AppData\Local\Temp\pylBDDD.tmp\data\isolist.ini
07-01 12:29 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-01 12:29 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-01 12:29 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-01 12:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-01 12:29 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-01 12:29 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-01 12:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-01 12:29 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-01 12:29 DEBUG  WindowsBackend: Fetching host info...
07-01 12:29 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-01 12:29 DEBUG  WindowsBackend: windows version=vista
07-01 12:29 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
07-01 12:29 DEBUG  WindowsBackend: windows_sp=None
07-01 12:29 DEBUG  WindowsBackend: windows_build=7100
07-01 12:29 DEBUG  WindowsBackend: gmt=-8
07-01 12:29 DEBUG  WindowsBackend: country=US
07-01 12:29 DEBUG  WindowsBackend: timezone=America/Los_Angeles
07-01 12:29 DEBUG  WindowsBackend: windows_username=Christopher Aouate
07-01 12:29 DEBUG  WindowsBackend: user_full_name=Christopher Aouate
07-01 12:29 DEBUG  WindowsBackend: user_directory=Christopher Aouate
07-01 12:29 DEBUG  WindowsBackend: windows_language_code=1033
07-01 12:29 DEBUG  WindowsBackend: windows_language=English
07-01 12:29 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) M processor 1.80GHz
07-01 12:29 DEBUG  WindowsBackend: bootloader=vista
07-01 12:29 DEBUG  WindowsBackend: system_drive=Drive(C: hd 43287.3242188 mb free )
07-01 12:29 DEBUG  WindowsBackend: drive=Drive(C: hd 43287.3242188 mb free )
07-01 12:29 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
07-01 12:29 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
07-01 12:29 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
07-01 12:29 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
07-01 12:29 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
07-01 12:29 DEBUG  WindowsBackend: drive=Drive(I: removable 857.30859375 mb free fat32)
07-01 12:29 DEBUG  WindowsBackend: uninstaller_path=None
07-01 12:29 DEBUG  WindowsBackend: previous_target_dir=None
07-01 12:29 DEBUG  WindowsBackend: previous_distro_name=None
07-01 12:29 DEBUG  WindowsBackend: keyboard_id=67699721
07-01 12:29 DEBUG  WindowsBackend: keyboard_layout=us
07-01 12:29 DEBUG  WindowsBackend: keyboard_variant=
07-01 12:29 DEBUG  CommonBackend: locale=en_US.UTF-8
07-01 12:29 DEBUG  WindowsBackend: total_memory_mb=1022.9296875
07-01 12:29 DEBUG  CommonBackend: Searching ISOs on USB devices
07-01 12:29 DEBUG  Distro:   checking Ubuntu ISO C:\VL6.0-STD-Gold.iso
07-01 12:29 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-01 12:29 DEBUG  Distro:   checking Ubuntu ISO C:\VL6.0-STD-Gold.iso
07-01 12:29 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-01 12:29 DEBUG  Distro:   checking Kubuntu ISO C:\VL6.0-STD-Gold.iso
07-01 12:29 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-01 12:29 DEBUG  Distro:   checking Kubuntu ISO C:\VL6.0-STD-Gold.iso
07-01 12:29 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-01 12:29 DEBUG  Distro:   checking Xubuntu ISO C:\VL6.0-STD-Gold.iso
07-01 12:29 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-01 12:29 DEBUG  Distro:   checking Xubuntu ISO C:\VL6.0-STD-Gold.iso
07-01 12:29 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-01 12:29 DEBUG  Distro:   checking Mythbuntu ISO C:\VL6.0-STD-Gold.iso
07-01 12:29 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-01 12:29 DEBUG  Distro:   checking Mythbuntu ISO C:\VL6.0-STD-Gold.iso
07-01 12:29 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-01 12:29 DEBUG  Distro:   checking Ubuntu ISO I:\TEENpup2009Legacy.iso
07-01 12:29 DEBUG  Distro:     wrong size: 47657310 < 600000000
07-01 12:29 DEBUG  Distro:   checking Ubuntu ISO I:\TEENpup2009Legacy.iso
07-01 12:29 DEBUG  Distro:     wrong size: 47657310 < 600000000
07-01 12:29 DEBUG  Distro:   checking Kubuntu ISO I:\TEENpup2009Legacy.iso
07-01 12:29 DEBUG  Distro:     wrong size: 47657310 < 600000000
07-01 12:29 DEBUG  Distro:   checking Kubuntu ISO I:\TEENpup2009Legacy.iso
07-01 12:29 DEBUG  Distro:     wrong size: 47657310 < 600000000
07-01 12:29 DEBUG  Distro:   checking Xubuntu ISO I:\TEENpup2009Legacy.iso
07-01 12:29 DEBUG  Distro:     wrong size: 47657310 < 600000000
07-01 12:29 DEBUG  Distro:   checking Xubuntu ISO I:\TEENpup2009Legacy.iso
07-01 12:29 DEBUG  Distro:     wrong size: 47657310 < 600000000
07-01 12:29 DEBUG  Distro:   checking Mythbuntu ISO I:\TEENpup2009Legacy.iso
07-01 12:29 DEBUG  Distro:     wrong size: 47657310 < 600000000
07-01 12:29 DEBUG  Distro:   checking Mythbuntu ISO I:\TEENpup2009Legacy.iso
07-01 12:29 DEBUG  Distro:     wrong size: 47657310 < 600000000
07-01 12:29 DEBUG  CommonBackend: Searching for local CDs
07-01 12:29 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pylBDDD.tmp is a valid Ubuntu CD
07-01 12:29 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pylBDDD.tmp\casper\filesystem.squashfs
07-01 12:29 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pylBDDD.tmp is a valid Ubuntu CD
07-01 12:29 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pylBDDD.tmp\casper\filesystem.squashfs
07-01 12:29 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pylBDDD.tmp is a valid Kubuntu CD
07-01 12:29 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pylBDDD.tmp\casper\filesystem.squashfs
07-01 12:29 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pylBDDD.tmp is a valid Kubuntu CD
07-01 12:29 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pylBDDD.tmp\casper\filesystem.squashfs
07-01 12:29 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pylBDDD.tmp is a valid Xubuntu CD
07-01 12:29 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pylBDDD.tmp\casper\filesystem.squashfs
07-01 12:29 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pylBDDD.tmp is a valid Xubuntu CD
07-01 12:29 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pylBDDD.tmp\casper\filesystem.squashfs
07-01 12:29 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pylBDDD.tmp is a valid Mythbuntu CD
07-01 12:29 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pylBDDD.tmp\casper\filesystem.squashfs
07-01 12:29 DEBUG  Distro:   checking whether C:\Users\CHRIST~1\AppData\Local\Temp\pylBDDD.tmp is a valid Mythbuntu CD
07-01 12:29 DEBUG  Distro:     does not contain C:\Users\CHRIST~1\AppData\Local\Temp\pylBDDD.tmp\casper\filesystem.squashfs
07-01 12:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-01 12:29 DEBUG  Distro: wrong arch: i386 != amd64
07-01 12:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-01 12:29 INFO   Distro: Found a valid CD for Ubuntu: D:\
07-01 12:29 INFO   root: Running the installer...
07-01 12:29 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=English, username=chris
07-01 12:29 INFO   root: Received settings
07-01 12:29 DEBUG  TaskList: # Running tasklist...
07-01 12:29 DEBUG  TaskList: ## Running select_target_dir...
07-01 12:29 INFO   WindowsBackend: Installing into C:\ubuntu
07-01 12:29 DEBUG  TaskList: ## Finished select_target_dir
07-01 12:29 DEBUG  TaskList: ## Running create_dir_structure...
07-01 12:29 DEBUG  CommonBackend: Creating dir C:\ubuntu
07-01 12:29 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
07-01 12:29 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
07-01 12:29 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
07-01 12:29 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
07-01 12:29 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
07-01 12:29 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
07-01 12:29 DEBUG  TaskList: ## Finished create_dir_structure
07-01 12:29 DEBUG  TaskList: ## Running uncompress_target_dir...
07-01 12:29 DEBUG  TaskList: ## Finished uncompress_target_dir
07-01 12:29 DEBUG  TaskList: ## Running create_uninstaller...
07-01 12:29 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
07-01 12:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
07-01 12:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
07-01 12:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-01 12:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
07-01 12:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
07-01 12:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-01 12:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
07-01 12:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
07-01 12:29 DEBUG  TaskList: ## Finished create_uninstaller
07-01 12:29 DEBUG  TaskList: ## Running copy_installation_files...
07-01 12:29 DEBUG  WindowsBackend: Copying C:\Users\CHRIST~1\AppData\Local\Temp\pylBDDD.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
07-01 12:29 DEBUG  WindowsBackend: Copying C:\Users\CHRIST~1\AppData\Local\Temp\pylBDDD.tmp\winboot -> C:\ubuntu\winboot
07-01 12:29 DEBUG  WindowsBackend: Copying C:\Users\CHRIST~1\AppData\Local\Temp\pylBDDD.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
07-01 12:29 DEBUG  TaskList: ## Finished copy_installation_files
07-01 12:29 DEBUG  TaskList: ## Running get_iso...
07-01 12:29 DEBUG  TaskList: New task copy_file
07-01 12:29 DEBUG  TaskList: ### Running copy_file...
07-01 12:32 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 13] Permission denied
07-01 12:32 DEBUG  TaskList: # Cancelling tasklist
07-01 12:32 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 13] Permission denied
07-01 12:32 DEBUG  TaskList: New task check_iso
07-01 12:32 DEBUG  CommonBackend: Searching for local ISO
07-01 12:32 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
07-01 12:32 DEBUG  TaskList: New task get_metalink
07-01 12:32 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
07-01 12:32 DEBUG  TaskList: # Cancelling tasklist
07-01 12:32 DEBUG  TaskList: # Finished tasklist


whats wrong, why wont it let me install

---

### Post by artemka373 on 2009-07-02
I have this problem, too. But I am installing Kubuntu 9.04. Windows XP SP3 x86 Rus.
UPDATE:
I tried to begin install Kubuntu a 6 hours. I hate this bug!!
If your Windows is not in English and you want English Ubuntu then change Region, etc. to English or USA.
Remember the letter of partition of DVD-ROM (eg. D: or E:
Remove FULLY DVD-ROM from PC.
Download DAEMON Tools Lite. Install. Reboot PC.
Create a virtual DVD-ROM with partition of the removed DVD-ROM.
Mount the Ubuntu .iso image
Click second button.
Complete instruction.
UNMOUNT the Ubuntu .iso image.
REMOVE the VIRTUAL DVD-ROM.
Choose Reboot now but when Windows will be shutdowned POWER OFF DISABLE COMPUTER.
When PC is shutdowned, move DVD-ROM to the PC.
POWER ON / ENABLE PC.
Choose Kubuntu.
Wait some minutes.
Configure network settings and update Kubuntu.

---

