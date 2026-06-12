---
title: "Problem with wubi; access denied."
date: 2009-07-21
forum: Installation &amp; Upgrades
---

### Post by Lisheo on 2009-07-21
Gets to about 30 seconds left, then access denied. I'm logged in as Admin, so what's happening? Log attached.

07-21 15:55 INFO   root: === wubi 9.04 rev128 ===
07-21 15:55 DEBUG  root: Logfile is c:\users\lisheo\appdata\local\temp\wubi-9.04-rev128.log
07-21 15:55 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu']
07-21 15:55 DEBUG  CommonBackend: data_dir=C:\Users\Lisheo\AppData\Local\Temp\pylEAEA.tmp\data
07-21 15:55 DEBUG  WindowsBackend: 7z=C:\Users\Lisheo\AppData\Local\Temp\pylEAEA.tmp\bin\7z.exe
07-21 15:55 DEBUG  CommonBackend: Fetching basic info...
07-21 15:55 DEBUG  CommonBackend: original_exe=E:\wubi.exe
07-21 15:55 DEBUG  CommonBackend: platform=win32
07-21 15:55 DEBUG  CommonBackend: osname=nt
07-21 15:55 DEBUG  CommonBackend: language=en_IE
07-21 15:55 DEBUG  CommonBackend: encoding=cp1252
07-21 15:55 DEBUG  WindowsBackend: arch=amd64
07-21 15:55 DEBUG  CommonBackend: Parsing isolist=C:\Users\Lisheo\AppData\Local\Temp\pylEAEA.tmp\data\isolist.ini
07-21 15:55 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-21 15:55 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-21 15:55 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-21 15:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-21 15:55 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-21 15:55 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-21 15:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-21 15:55 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-21 15:55 DEBUG  WindowsBackend: Fetching host info...
07-21 15:55 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-21 15:55 DEBUG  WindowsBackend: windows version=vista
07-21 15:55 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Basic
07-21 15:55 DEBUG  WindowsBackend: windows_sp=Service Pack 1
07-21 15:55 DEBUG  WindowsBackend: windows_build=6001
07-21 15:55 DEBUG  WindowsBackend: gmt=0
07-21 15:55 DEBUG  WindowsBackend: country=IE
07-21 15:55 DEBUG  WindowsBackend: timezone=Europe/Dublin
07-21 15:55 DEBUG  WindowsBackend: windows_username=Lisheo
07-21 15:55 DEBUG  WindowsBackend: user_full_name=Lisheo
07-21 15:55 DEBUG  WindowsBackend: user_directory=Lisheo
07-21 15:55 DEBUG  WindowsBackend: windows_language_code=1033
07-21 15:55 DEBUG  WindowsBackend: windows_language=English
07-21 15:55 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T5800  @ 2.00GHz
07-21 15:55 DEBUG  WindowsBackend: bootloader=vista
07-21 15:55 DEBUG  WindowsBackend: system_drive=Drive(C: hd 14131.6132813 mb free )
07-21 15:55 DEBUG  WindowsBackend: drive=Drive(C: hd 14131.6132813 mb free )
07-21 15:55 DEBUG  WindowsBackend: drive=Drive(D: hd 50033.8320313 mb free ntfs)
07-21 15:55 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
07-21 15:55 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
07-21 15:55 DEBUG  WindowsBackend: uninstaller_path=None
07-21 15:55 DEBUG  WindowsBackend: previous_target_dir=None
07-21 15:55 DEBUG  WindowsBackend: previous_distro_name=None
07-21 15:55 DEBUG  WindowsBackend: keyboard_id=403249161
07-21 15:55 DEBUG  WindowsBackend: keyboard_layout=ie
07-21 15:55 DEBUG  WindowsBackend: keyboard_variant=
07-21 15:55 DEBUG  CommonBackend: locale=en_IE.UTF-8
07-21 15:55 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
07-21 15:55 DEBUG  CommonBackend: Searching ISOs on USB devices
07-21 15:55 DEBUG  CommonBackend: Searching for local CDs
07-21 15:55 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pylEAEA.tmp is a valid Ubuntu CD
07-21 15:55 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pylEAEA.tmp\casper\filesystem.squashfs
07-21 15:55 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pylEAEA.tmp is a valid Ubuntu CD
07-21 15:55 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pylEAEA.tmp\casper\filesystem.squashfs
07-21 15:55 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pylEAEA.tmp is a valid Kubuntu CD
07-21 15:55 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pylEAEA.tmp\casper\filesystem.squashfs
07-21 15:55 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pylEAEA.tmp is a valid Kubuntu CD
07-21 15:55 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pylEAEA.tmp\casper\filesystem.squashfs
07-21 15:55 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pylEAEA.tmp is a valid Xubuntu CD
07-21 15:55 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pylEAEA.tmp\casper\filesystem.squashfs
07-21 15:55 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pylEAEA.tmp is a valid Xubuntu CD
07-21 15:55 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pylEAEA.tmp\casper\filesystem.squashfs
07-21 15:55 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pylEAEA.tmp is a valid Mythbuntu CD
07-21 15:55 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pylEAEA.tmp\casper\filesystem.squashfs
07-21 15:55 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pylEAEA.tmp is a valid Mythbuntu CD
07-21 15:55 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pylEAEA.tmp\casper\filesystem.squashfs
07-21 15:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-21 15:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 15:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-21 15:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 15:55 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-21 15:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 15:55 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-21 15:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 15:55 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-21 15:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 15:55 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-21 15:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 15:55 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-21 15:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 15:55 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-21 15:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 15:55 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-21 15:55 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
07-21 15:55 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
07-21 15:55 INFO   Distro: Found a valid CD for Ubuntu: E:\
07-21 15:55 INFO   root: Running the CD menu...
07-21 15:55 DEBUG  WindowsFrontend: __init__...
07-21 15:55 DEBUG  WindowsFrontend: on_init...
07-21 15:55 INFO   root: CD menu finished
07-21 15:55 INFO   root: Running the installer...
07-21 15:56 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=8000MB, distro_name=Ubuntu, language=English, username=lisheo
07-21 15:56 INFO   root: Received settings
07-21 15:56 DEBUG  TaskList: # Running tasklist...
07-21 15:56 DEBUG  TaskList: ## Running select_target_dir...
07-21 15:56 INFO   WindowsBackend: Installing into D:\ubuntu
07-21 15:56 DEBUG  TaskList: ## Finished select_target_dir
07-21 15:56 DEBUG  TaskList: ## Running create_dir_structure...
07-21 15:56 DEBUG  CommonBackend: Creating dir D:\ubuntu
07-21 15:56 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
07-21 15:56 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
07-21 15:56 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
07-21 15:56 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
07-21 15:56 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
07-21 15:56 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
07-21 15:56 DEBUG  TaskList: ## Finished create_dir_structure
07-21 15:56 DEBUG  TaskList: ## Running uncompress_target_dir...
07-21 15:56 DEBUG  TaskList: ## Finished uncompress_target_dir
07-21 15:56 DEBUG  TaskList: ## Running create_uninstaller...
07-21 15:56 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
07-21 15:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
07-21 15:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
07-21 15:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-21 15:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
07-21 15:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
07-21 15:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-21 15:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
07-21 15:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
07-21 15:56 DEBUG  TaskList: ## Finished create_uninstaller
07-21 15:56 DEBUG  TaskList: ## Running copy_installation_files...
07-21 15:56 DEBUG  WindowsBackend: Copying C:\Users\Lisheo\AppData\Local\Temp\pylEAEA.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
07-21 15:56 DEBUG  WindowsBackend: Copying C:\Users\Lisheo\AppData\Local\Temp\pylEAEA.tmp\winboot -> D:\ubuntu\winboot
07-21 15:56 DEBUG  WindowsBackend: Copying C:\Users\Lisheo\AppData\Local\Temp\pylEAEA.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
07-21 15:56 DEBUG  TaskList: ## Finished copy_installation_files
07-21 15:56 DEBUG  TaskList: ## Running get_iso...
07-21 15:56 DEBUG  TaskList: New task copy_file
07-21 15:56 DEBUG  TaskList: ### Running copy_file...
07-21 16:00 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 13] Permission denied
07-21 16:00 DEBUG  TaskList: # Cancelling tasklist
07-21 16:00 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 13] Permission denied
07-21 16:00 DEBUG  TaskList: New task check_iso
07-21 16:00 DEBUG  CommonBackend: Searching for local ISO
07-21 16:00 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
07-21 16:00 DEBUG  TaskList: New task get_metalink
07-21 16:00 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
07-21 16:00 DEBUG  TaskList: # Cancelling tasklist
07-21 16:00 DEBUG  TaskList: # Finished tasklist
07-21 16:04 INFO   root: === wubi 9.04 rev128 ===
07-21 16:04 DEBUG  root: Logfile is c:\users\lisheo\appdata\local\temp\wubi-9.04-rev128.log
07-21 16:04 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\ubuntu\\uninstall-wubi.exe"']
07-21 16:04 DEBUG  CommonBackend: data_dir=C:\Users\Lisheo\AppData\Local\Temp\pylEB96.tmp\data
07-21 16:04 DEBUG  WindowsBackend: 7z=C:\Users\Lisheo\AppData\Local\Temp\pylEB96.tmp\bin\7z.exe
07-21 16:04 DEBUG  CommonBackend: Fetching basic info...
07-21 16:04 DEBUG  CommonBackend: original_exe=D:\ubuntu\uninstall-wubi.exe
07-21 16:04 DEBUG  CommonBackend: platform=win32
07-21 16:04 DEBUG  CommonBackend: osname=nt
07-21 16:04 DEBUG  CommonBackend: language=en_IE
07-21 16:04 DEBUG  CommonBackend: encoding=cp1252
07-21 16:04 DEBUG  WindowsBackend: arch=amd64
07-21 16:04 DEBUG  CommonBackend: Parsing isolist=C:\Users\Lisheo\AppData\Local\Temp\pylEB96.tmp\data\isolist.ini
07-21 16:04 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-21 16:04 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-21 16:04 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-21 16:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-21 16:04 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-21 16:04 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-21 16:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-21 16:04 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-21 16:04 DEBUG  WindowsBackend: Fetching host info...
07-21 16:04 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-21 16:04 DEBUG  WindowsBackend: windows version=vista
07-21 16:04 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Basic
07-21 16:04 DEBUG  WindowsBackend: windows_sp=Service Pack 1
07-21 16:04 DEBUG  WindowsBackend: windows_build=6001
07-21 16:04 DEBUG  WindowsBackend: gmt=0
07-21 16:04 DEBUG  WindowsBackend: country=IE
07-21 16:04 DEBUG  WindowsBackend: timezone=Europe/Dublin
07-21 16:04 DEBUG  WindowsBackend: windows_username=Lisheo
07-21 16:04 DEBUG  WindowsBackend: user_full_name=Lisheo
07-21 16:04 DEBUG  WindowsBackend: user_directory=Lisheo
07-21 16:04 DEBUG  WindowsBackend: windows_language_code=1033
07-21 16:04 DEBUG  WindowsBackend: windows_language=English
07-21 16:04 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T5800  @ 2.00GHz
07-21 16:04 DEBUG  WindowsBackend: bootloader=vista
07-21 16:04 DEBUG  WindowsBackend: system_drive=Drive(C: hd 15455.1171875 mb free )
07-21 16:04 DEBUG  WindowsBackend: drive=Drive(C: hd 15455.1171875 mb free )
07-21 16:04 DEBUG  WindowsBackend: drive=Drive(D: hd 49455.9179688 mb free ntfs)
07-21 16:04 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
07-21 16:04 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
07-21 16:04 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
07-21 16:04 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
07-21 16:04 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
07-21 16:04 DEBUG  WindowsBackend: keyboard_id=403249161
07-21 16:04 DEBUG  WindowsBackend: keyboard_layout=ie
07-21 16:04 DEBUG  WindowsBackend: keyboard_variant=
07-21 16:04 DEBUG  CommonBackend: locale=en_IE.UTF-8
07-21 16:04 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
07-21 16:04 DEBUG  CommonBackend: Searching ISOs on USB devices
07-21 16:04 DEBUG  CommonBackend: Searching for local CDs
07-21 16:04 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pylEB96.tmp is a valid Ubuntu CD
07-21 16:04 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pylEB96.tmp\casper\filesystem.squashfs
07-21 16:04 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pylEB96.tmp is a valid Ubuntu CD
07-21 16:04 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pylEB96.tmp\casper\filesystem.squashfs
07-21 16:04 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pylEB96.tmp is a valid Kubuntu CD
07-21 16:04 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pylEB96.tmp\casper\filesystem.squashfs
07-21 16:04 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pylEB96.tmp is a valid Kubuntu CD
07-21 16:04 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pylEB96.tmp\casper\filesystem.squashfs
07-21 16:04 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pylEB96.tmp is a valid Xubuntu CD
07-21 16:04 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pylEB96.tmp\casper\filesystem.squashfs
07-21 16:04 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pylEB96.tmp is a valid Xubuntu CD
07-21 16:04 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pylEB96.tmp\casper\filesystem.squashfs
07-21 16:04 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pylEB96.tmp is a valid Mythbuntu CD
07-21 16:04 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pylEB96.tmp\casper\filesystem.squashfs
07-21 16:04 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pylEB96.tmp is a valid Mythbuntu CD
07-21 16:04 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pylEB96.tmp\casper\filesystem.squashfs
07-21 16:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-21 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 16:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-21 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 16:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-21 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 16:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-21 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 16:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-21 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 16:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-21 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 16:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-21 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 16:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-21 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 16:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-21 16:04 INFO   root: === wubi 9.04 rev128 ===
07-21 16:04 DEBUG  root: Logfile is c:\users\lisheo\appdata\local\temp\wubi-9.04-rev128.log
07-21 16:04 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\ubuntu\\uninstall-wubi.exe"']
07-21 16:04 DEBUG  CommonBackend: data_dir=C:\Users\Lisheo\AppData\Local\Temp\pyl43D3.tmp\data
07-21 16:04 DEBUG  WindowsBackend: 7z=C:\Users\Lisheo\AppData\Local\Temp\pyl43D3.tmp\bin\7z.exe
07-21 16:04 DEBUG  CommonBackend: Fetching basic info...
07-21 16:04 DEBUG  CommonBackend: original_exe=D:\ubuntu\uninstall-wubi.exe
07-21 16:04 DEBUG  CommonBackend: platform=win32
07-21 16:04 DEBUG  CommonBackend: osname=nt
07-21 16:04 DEBUG  CommonBackend: language=en_IE
07-21 16:04 DEBUG  CommonBackend: encoding=cp1252
07-21 16:04 DEBUG  WindowsBackend: arch=amd64
07-21 16:04 DEBUG  CommonBackend: Parsing isolist=C:\Users\Lisheo\AppData\Local\Temp\pyl43D3.tmp\data\isolist.ini
07-21 16:04 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-21 16:04 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-21 16:04 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-21 16:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-21 16:04 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-21 16:04 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-21 16:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-21 16:04 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-21 16:04 DEBUG  WindowsBackend: Fetching host info...
07-21 16:04 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-21 16:04 DEBUG  WindowsBackend: windows version=vista
07-21 16:04 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Basic
07-21 16:04 DEBUG  WindowsBackend: windows_sp=Service Pack 1
07-21 16:04 DEBUG  WindowsBackend: windows_build=6001
07-21 16:04 DEBUG  WindowsBackend: gmt=0
07-21 16:04 DEBUG  WindowsBackend: country=IE
07-21 16:04 DEBUG  WindowsBackend: timezone=Europe/Dublin
07-21 16:04 DEBUG  WindowsBackend: windows_username=Lisheo
07-21 16:04 DEBUG  WindowsBackend: user_full_name=Lisheo
07-21 16:04 DEBUG  WindowsBackend: user_directory=Lisheo
07-21 16:04 DEBUG  WindowsBackend: windows_language_code=1033
07-21 16:04 DEBUG  WindowsBackend: windows_language=English
07-21 16:04 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T5800  @ 2.00GHz
07-21 16:04 DEBUG  WindowsBackend: bootloader=vista
07-21 16:04 DEBUG  WindowsBackend: system_drive=Drive(C: hd 15448.2734375 mb free )
07-21 16:04 DEBUG  WindowsBackend: drive=Drive(C: hd 15448.2734375 mb free )
07-21 16:04 DEBUG  WindowsBackend: drive=Drive(D: hd 49455.9179688 mb free ntfs)
07-21 16:05 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
07-21 16:05 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
07-21 16:05 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
07-21 16:05 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
07-21 16:05 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
07-21 16:05 DEBUG  WindowsBackend: keyboard_id=403249161
07-21 16:05 DEBUG  WindowsBackend: keyboard_layout=ie
07-21 16:05 DEBUG  WindowsBackend: keyboard_variant=
07-21 16:05 DEBUG  CommonBackend: locale=en_IE.UTF-8
07-21 16:05 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
07-21 16:05 DEBUG  CommonBackend: Searching ISOs on USB devices
07-21 16:05 DEBUG  CommonBackend: Searching for local CDs
07-21 16:05 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pyl43D3.tmp is a valid Ubuntu CD
07-21 16:05 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pyl43D3.tmp\casper\filesystem.squashfs
07-21 16:05 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pyl43D3.tmp is a valid Ubuntu CD
07-21 16:05 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pyl43D3.tmp\casper\filesystem.squashfs
07-21 16:05 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pyl43D3.tmp is a valid Kubuntu CD
07-21 16:05 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pyl43D3.tmp\casper\filesystem.squashfs
07-21 16:05 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pyl43D3.tmp is a valid Kubuntu CD
07-21 16:05 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pyl43D3.tmp\casper\filesystem.squashfs
07-21 16:05 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pyl43D3.tmp is a valid Xubuntu CD
07-21 16:05 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pyl43D3.tmp\casper\filesystem.squashfs
07-21 16:05 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pyl43D3.tmp is a valid Xubuntu CD
07-21 16:05 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pyl43D3.tmp\casper\filesystem.squashfs
07-21 16:05 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pyl43D3.tmp is a valid Mythbuntu CD
07-21 16:05 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pyl43D3.tmp\casper\filesystem.squashfs
07-21 16:05 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pyl43D3.tmp is a valid Mythbuntu CD
07-21 16:05 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pyl43D3.tmp\casper\filesystem.squashfs
07-21 16:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-21 16:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 16:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-21 16:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 16:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-21 16:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 16:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-21 16:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 16:05 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-21 16:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 16:05 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-21 16:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 16:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-21 16:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 16:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-21 16:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 16:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-21 16:05 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
07-21 16:05 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
07-21 16:05 INFO   Distro: Found a valid CD for Ubuntu: E:\
07-21 16:05 INFO   root: Running the uninstaller...
07-21 16:05 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
07-21 16:05 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
07-21 16:05 INFO   Distro: Found a valid CD for Ubuntu: E:\
07-21 16:05 INFO   root: Running the uninstaller...
07-21 16:05 INFO   CommonBackend: This is the uninstaller running
07-21 16:05 DEBUG  WindowsFrontend: __init__...
07-21 16:05 INFO   CommonBackend: This is the uninstaller running
07-21 16:05 DEBUG  WindowsFrontend: __init__...
07-21 16:05 DEBUG  WindowsFrontend: on_init...
07-21 16:05 DEBUG  WindowsFrontend: on_init...
07-21 16:05 INFO   root: Received settings
07-21 16:05 DEBUG  TaskList: # Running tasklist...
07-21 16:05 DEBUG  TaskList: ## Running Backup ISO...
07-21 16:05 DEBUG  TaskList: ## Finished Backup ISO
07-21 16:05 DEBUG  TaskList: ## Running Remove bootloader entry...
07-21 16:05 DEBUG  WindowsBackend: Could not find bcd id
07-21 16:05 DEBUG  WindowsBackend: undo_bootini C:
07-21 16:05 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 15448.2734375 mb free )
07-21 16:05 DEBUG  WindowsBackend: undo_bootini D:
07-21 16:05 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 49455.9179688 mb free ntfs)
07-21 16:05 DEBUG  TaskList: ## Finished Remove bootloader entry
07-21 16:05 DEBUG  TaskList: ## Running Remove target dir...
07-21 16:05 DEBUG  CommonBackend: Deleting D:\ubuntu
07-21 16:05 DEBUG  TaskList: ## Finished Remove target dir
07-21 16:05 DEBUG  TaskList: ## Running Remove registry key...
07-21 16:05 DEBUG  TaskList: ## Finished Remove registry key
07-21 16:05 DEBUG  TaskList: # Finished tasklist
07-21 16:05 INFO   root: Almost finished uninstalling
07-21 16:05 INFO   root: Finished uninstallation
07-21 16:05 DEBUG  root: application.quit
07-21 16:05 DEBUG  WindowsFrontend: frontend.quit
07-21 16:05 DEBUG  WindowsFrontend: frontend.on_quit
07-21 16:05 DEBUG  root: application.on_quit
07-21 16:05 INFO   root: sys.exit
07-21 16:05 INFO   WindowsFrontend: Operation cancelled
07-21 16:05 DEBUG  WindowsFrontend: frontend.quit
07-21 16:05 DEBUG  WindowsFrontend: frontend.on_quit
07-21 16:05 DEBUG  root: application.on_quit
07-21 16:05 INFO   root: sys.exit
07-21 16:07 INFO   root: === wubi 9.04 rev128 ===
07-21 16:07 DEBUG  root: Logfile is c:\users\lisheo\appdata\local\temp\wubi-9.04-rev128.log
07-21 16:07 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu']
07-21 16:07 DEBUG  CommonBackend: data_dir=C:\Users\Lisheo\AppData\Local\Temp\pylF67F.tmp\data
07-21 16:07 DEBUG  WindowsBackend: 7z=C:\Users\Lisheo\AppData\Local\Temp\pylF67F.tmp\bin\7z.exe
07-21 16:07 DEBUG  CommonBackend: Fetching basic info...
07-21 16:07 DEBUG  CommonBackend: original_exe=E:\wubi.exe
07-21 16:07 DEBUG  CommonBackend: platform=win32
07-21 16:07 DEBUG  CommonBackend: osname=nt
07-21 16:07 DEBUG  CommonBackend: language=en_IE
07-21 16:07 DEBUG  CommonBackend: encoding=cp1252
07-21 16:07 DEBUG  WindowsBackend: arch=amd64
07-21 16:07 DEBUG  CommonBackend: Parsing isolist=C:\Users\Lisheo\AppData\Local\Temp\pylF67F.tmp\data\isolist.ini
07-21 16:07 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-21 16:07 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-21 16:07 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-21 16:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-21 16:07 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-21 16:07 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-21 16:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-21 16:07 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-21 16:07 DEBUG  WindowsBackend: Fetching host info...
07-21 16:07 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-21 16:07 DEBUG  WindowsBackend: windows version=vista
07-21 16:07 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Basic
07-21 16:07 DEBUG  WindowsBackend: windows_sp=Service Pack 1
07-21 16:07 DEBUG  WindowsBackend: windows_build=6001
07-21 16:07 DEBUG  WindowsBackend: gmt=0
07-21 16:07 DEBUG  WindowsBackend: country=IE
07-21 16:07 DEBUG  WindowsBackend: timezone=Europe/Dublin
07-21 16:07 DEBUG  WindowsBackend: windows_username=Lisheo
07-21 16:07 DEBUG  WindowsBackend: user_full_name=Lisheo
07-21 16:07 DEBUG  WindowsBackend: user_directory=Lisheo
07-21 16:07 DEBUG  WindowsBackend: windows_language_code=1033
07-21 16:07 DEBUG  WindowsBackend: windows_language=English
07-21 16:07 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T5800  @ 2.00GHz
07-21 16:07 DEBUG  WindowsBackend: bootloader=vista
07-21 16:07 DEBUG  WindowsBackend: system_drive=Drive(C: hd 15454.8476563 mb free )
07-21 16:07 DEBUG  WindowsBackend: drive=Drive(C: hd 15454.8476563 mb free )
07-21 16:07 DEBUG  WindowsBackend: drive=Drive(D: hd 50033.8320313 mb free ntfs)
07-21 16:07 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
07-21 16:07 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
07-21 16:07 DEBUG  WindowsBackend: uninstaller_path=None
07-21 16:07 DEBUG  WindowsBackend: previous_target_dir=None
07-21 16:07 DEBUG  WindowsBackend: previous_distro_name=None
07-21 16:07 DEBUG  WindowsBackend: keyboard_id=403249161
07-21 16:07 DEBUG  WindowsBackend: keyboard_layout=ie
07-21 16:07 DEBUG  WindowsBackend: keyboard_variant=
07-21 16:07 DEBUG  CommonBackend: locale=en_IE.UTF-8
07-21 16:07 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
07-21 16:07 DEBUG  CommonBackend: Searching ISOs on USB devices
07-21 16:07 DEBUG  CommonBackend: Searching for local CDs
07-21 16:07 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pylF67F.tmp is a valid Ubuntu CD
07-21 16:07 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pylF67F.tmp\casper\filesystem.squashfs
07-21 16:07 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pylF67F.tmp is a valid Ubuntu CD
07-21 16:07 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pylF67F.tmp\casper\filesystem.squashfs
07-21 16:07 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pylF67F.tmp is a valid Kubuntu CD
07-21 16:07 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pylF67F.tmp\casper\filesystem.squashfs
07-21 16:07 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pylF67F.tmp is a valid Kubuntu CD
07-21 16:07 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pylF67F.tmp\casper\filesystem.squashfs
07-21 16:07 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pylF67F.tmp is a valid Xubuntu CD
07-21 16:07 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pylF67F.tmp\casper\filesystem.squashfs
07-21 16:07 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pylF67F.tmp is a valid Xubuntu CD
07-21 16:07 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pylF67F.tmp\casper\filesystem.squashfs
07-21 16:07 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pylF67F.tmp is a valid Mythbuntu CD
07-21 16:07 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pylF67F.tmp\casper\filesystem.squashfs
07-21 16:07 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pylF67F.tmp is a valid Mythbuntu CD
07-21 16:07 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pylF67F.tmp\casper\filesystem.squashfs
07-21 16:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-21 16:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 16:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-21 16:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 16:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-21 16:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 16:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-21 16:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 16:07 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-21 16:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 16:07 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-21 16:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 16:07 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-21 16:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 16:07 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-21 16:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 16:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-21 16:07 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
07-21 16:07 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
07-21 16:07 INFO   Distro: Found a valid CD for Ubuntu: E:\
07-21 16:07 INFO   root: Running the CD menu...
07-21 16:07 DEBUG  WindowsFrontend: __init__...
07-21 16:07 DEBUG  WindowsFrontend: on_init...
07-21 16:07 INFO   root: CD menu finished
07-21 16:07 INFO   root: Running the installer...
07-21 16:08 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=9000MB, distro_name=Ubuntu, language=English, username=lisheo
07-21 16:08 INFO   root: Received settings
07-21 16:08 DEBUG  TaskList: # Running tasklist...
07-21 16:08 DEBUG  TaskList: ## Running select_target_dir...
07-21 16:08 INFO   WindowsBackend: Installing into C:\ubuntu
07-21 16:08 DEBUG  TaskList: ## Finished select_target_dir
07-21 16:08 DEBUG  TaskList: ## Running create_dir_structure...
07-21 16:08 DEBUG  CommonBackend: Creating dir C:\ubuntu
07-21 16:08 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
07-21 16:08 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
07-21 16:08 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
07-21 16:08 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
07-21 16:08 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
07-21 16:08 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
07-21 16:08 DEBUG  TaskList: ## Finished create_dir_structure
07-21 16:08 DEBUG  TaskList: ## Running uncompress_target_dir...
07-21 16:08 DEBUG  TaskList: ## Finished uncompress_target_dir
07-21 16:08 DEBUG  TaskList: ## Running create_uninstaller...
07-21 16:08 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
07-21 16:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
07-21 16:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
07-21 16:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-21 16:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
07-21 16:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
07-21 16:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-21 16:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
07-21 16:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
07-21 16:08 DEBUG  TaskList: ## Finished create_uninstaller
07-21 16:08 DEBUG  TaskList: ## Running copy_installation_files...
07-21 16:08 DEBUG  WindowsBackend: Copying C:\Users\Lisheo\AppData\Local\Temp\pylF67F.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
07-21 16:08 DEBUG  WindowsBackend: Copying C:\Users\Lisheo\AppData\Local\Temp\pylF67F.tmp\winboot -> C:\ubuntu\winboot
07-21 16:08 DEBUG  WindowsBackend: Copying C:\Users\Lisheo\AppData\Local\Temp\pylF67F.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
07-21 16:08 DEBUG  TaskList: ## Finished copy_installation_files
07-21 16:08 DEBUG  TaskList: ## Running get_iso...
07-21 16:08 DEBUG  TaskList: New task copy_file
07-21 16:08 DEBUG  TaskList: ### Running copy_file...
07-21 16:10 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 13] Permission denied
07-21 16:10 DEBUG  TaskList: # Cancelling tasklist
07-21 16:10 DEBUG  TaskList: New task check_iso
07-21 16:10 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 13] Permission denied
07-21 16:10 DEBUG  CommonBackend: Searching for local ISO
07-21 16:10 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
07-21 16:10 DEBUG  TaskList: New task get_metalink
07-21 16:10 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
07-21 16:10 DEBUG  TaskList: # Cancelling tasklist
07-21 16:10 DEBUG  TaskList: # Finished tasklist
07-21 16:13 INFO   root: === wubi 9.04 rev128 ===
07-21 16:13 DEBUG  root: Logfile is c:\users\lisheo\appdata\local\temp\wubi-9.04-rev128.log
07-21 16:13 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
07-21 16:13 DEBUG  CommonBackend: data_dir=C:\Users\Lisheo\AppData\Local\Temp\pyl2211.tmp\data
07-21 16:13 DEBUG  WindowsBackend: 7z=C:\Users\Lisheo\AppData\Local\Temp\pyl2211.tmp\bin\7z.exe
07-21 16:13 DEBUG  CommonBackend: Fetching basic info...
07-21 16:13 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
07-21 16:13 DEBUG  CommonBackend: platform=win32
07-21 16:13 DEBUG  CommonBackend: osname=nt
07-21 16:13 DEBUG  CommonBackend: language=en_IE
07-21 16:13 DEBUG  CommonBackend: encoding=cp1252
07-21 16:13 DEBUG  WindowsBackend: arch=amd64
07-21 16:13 DEBUG  CommonBackend: Parsing isolist=C:\Users\Lisheo\AppData\Local\Temp\pyl2211.tmp\data\isolist.ini
07-21 16:13 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-21 16:13 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-21 16:13 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-21 16:13 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-21 16:13 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-21 16:13 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-21 16:13 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-21 16:13 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-21 16:13 DEBUG  WindowsBackend: Fetching host info...
07-21 16:13 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-21 16:13 DEBUG  WindowsBackend: windows version=vista
07-21 16:13 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Basic
07-21 16:13 DEBUG  WindowsBackend: windows_sp=Service Pack 1
07-21 16:13 DEBUG  WindowsBackend: windows_build=6001
07-21 16:13 DEBUG  WindowsBackend: gmt=0
07-21 16:13 DEBUG  WindowsBackend: country=IE
07-21 16:13 DEBUG  WindowsBackend: timezone=Europe/Dublin
07-21 16:13 DEBUG  WindowsBackend: windows_username=Lisheo
07-21 16:13 DEBUG  WindowsBackend: user_full_name=Lisheo
07-21 16:13 DEBUG  WindowsBackend: user_directory=Lisheo
07-21 16:13 DEBUG  WindowsBackend: windows_language_code=1033
07-21 16:13 DEBUG  WindowsBackend: windows_language=English
07-21 16:13 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T5800  @ 2.00GHz
07-21 16:13 DEBUG  WindowsBackend: bootloader=vista
07-21 16:13 DEBUG  WindowsBackend: system_drive=Drive(C: hd 14875.6132813 mb free )
07-21 16:13 DEBUG  WindowsBackend: drive=Drive(C: hd 14875.6132813 mb free )
07-21 16:13 DEBUG  WindowsBackend: drive=Drive(D: hd 50033.8320313 mb free ntfs)
07-21 16:13 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
07-21 16:13 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
07-21 16:13 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
07-21 16:13 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
07-21 16:13 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
07-21 16:13 DEBUG  WindowsBackend: keyboard_id=403249161
07-21 16:13 DEBUG  WindowsBackend: keyboard_layout=ie
07-21 16:13 DEBUG  WindowsBackend: keyboard_variant=
07-21 16:13 DEBUG  CommonBackend: locale=en_IE.UTF-8
07-21 16:13 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
07-21 16:13 DEBUG  CommonBackend: Searching ISOs on USB devices
07-21 16:13 DEBUG  CommonBackend: Searching for local CDs
07-21 16:13 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pyl2211.tmp is a valid Ubuntu CD
07-21 16:13 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pyl2211.tmp\casper\filesystem.squashfs
07-21 16:13 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pyl2211.tmp is a valid Ubuntu CD
07-21 16:13 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pyl2211.tmp\casper\filesystem.squashfs
07-21 16:13 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pyl2211.tmp is a valid Kubuntu CD
07-21 16:13 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pyl2211.tmp\casper\filesystem.squashfs
07-21 16:13 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pyl2211.tmp is a valid Kubuntu CD
07-21 16:13 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pyl2211.tmp\casper\filesystem.squashfs
07-21 16:13 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pyl2211.tmp is a valid Xubuntu CD
07-21 16:13 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pyl2211.tmp\casper\filesystem.squashfs
07-21 16:13 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pyl2211.tmp is a valid Xubuntu CD
07-21 16:13 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pyl2211.tmp\casper\filesystem.squashfs
07-21 16:13 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pyl2211.tmp is a valid Mythbuntu CD
07-21 16:13 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pyl2211.tmp\casper\filesystem.squashfs
07-21 16:13 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pyl2211.tmp is a valid Mythbuntu CD
07-21 16:13 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pyl2211.tmp\casper\filesystem.squashfs
07-21 16:13 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-21 16:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 16:13 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-21 16:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 16:13 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-21 16:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 16:13 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-21 16:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 16:13 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-21 16:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 16:13 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-21 16:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 16:13 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-21 16:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 16:13 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-21 16:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 16:13 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-21 16:13 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
07-21 16:13 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
07-21 16:13 INFO   Distro: Found a valid CD for Ubuntu: E:\
07-21 16:13 INFO   root: Running the uninstaller...
07-21 16:13 INFO   CommonBackend: This is the uninstaller running
07-21 16:13 DEBUG  WindowsFrontend: __init__...
07-21 16:13 DEBUG  WindowsFrontend: on_init...
07-21 16:13 INFO   root: Received settings
07-21 16:13 DEBUG  TaskList: # Running tasklist...
07-21 16:13 DEBUG  TaskList: ## Running Backup ISO...
07-21 16:13 DEBUG  TaskList: ## Finished Backup ISO
07-21 16:13 DEBUG  TaskList: ## Running Remove bootloader entry...
07-21 16:13 DEBUG  WindowsBackend: Could not find bcd id
07-21 16:13 DEBUG  WindowsBackend: undo_bootini C:
07-21 16:13 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 14875.6132813 mb free )
07-21 16:13 DEBUG  WindowsBackend: undo_bootini D:
07-21 16:13 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 50033.8320313 mb free ntfs)
07-21 16:13 DEBUG  TaskList: ## Finished Remove bootloader entry
07-21 16:13 DEBUG  TaskList: ## Running Remove target dir...
07-21 16:13 DEBUG  CommonBackend: Deleting C:\ubuntu
07-21 16:13 DEBUG  TaskList: ## Finished Remove target dir
07-21 16:13 DEBUG  TaskList: ## Running Remove registry key...
07-21 16:13 DEBUG  TaskList: ## Finished Remove registry key
07-21 16:13 DEBUG  TaskList: # Finished tasklist
07-21 16:13 INFO   root: Almost finished uninstalling
07-21 16:13 INFO   root: Finished uninstallation
07-21 16:13 DEBUG  root: application.quit
07-21 16:13 DEBUG  WindowsFrontend: frontend.quit
07-21 16:13 DEBUG  WindowsFrontend: frontend.on_quit
07-21 16:13 DEBUG  root: application.on_quit
07-21 16:13 INFO   root: sys.exit
07-21 16:14 INFO   root: === wubi 9.04 rev128 ===
07-21 16:14 DEBUG  root: Logfile is c:\users\lisheo\appdata\local\temp\wubi-9.04-rev128.log
07-21 16:14 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu']
07-21 16:14 DEBUG  CommonBackend: data_dir=C:\Users\Lisheo\AppData\Local\Temp\pyl66BE.tmp\data
07-21 16:14 DEBUG  WindowsBackend: 7z=C:\Users\Lisheo\AppData\Local\Temp\pyl66BE.tmp\bin\7z.exe
07-21 16:14 DEBUG  CommonBackend: Fetching basic info...
07-21 16:14 DEBUG  CommonBackend: original_exe=E:\wubi.exe
07-21 16:14 DEBUG  CommonBackend: platform=win32
07-21 16:14 DEBUG  CommonBackend: osname=nt
07-21 16:14 DEBUG  CommonBackend: language=en_IE
07-21 16:14 DEBUG  CommonBackend: encoding=cp1252
07-21 16:14 DEBUG  WindowsBackend: arch=amd64
07-21 16:14 DEBUG  CommonBackend: Parsing isolist=C:\Users\Lisheo\AppData\Local\Temp\pyl66BE.tmp\data\isolist.ini
07-21 16:14 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-21 16:14 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-21 16:14 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-21 16:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-21 16:14 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-21 16:14 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-21 16:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-21 16:14 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-21 16:14 DEBUG  WindowsBackend: Fetching host info...
07-21 16:14 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-21 16:14 DEBUG  WindowsBackend: windows version=vista
07-21 16:14 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Basic
07-21 16:14 DEBUG  WindowsBackend: windows_sp=Service Pack 1
07-21 16:14 DEBUG  WindowsBackend: windows_build=6001
07-21 16:14 DEBUG  WindowsBackend: gmt=0
07-21 16:14 DEBUG  WindowsBackend: country=IE
07-21 16:14 DEBUG  WindowsBackend: timezone=Europe/Dublin
07-21 16:14 DEBUG  WindowsBackend: windows_username=Lisheo
07-21 16:14 DEBUG  WindowsBackend: user_full_name=Lisheo
07-21 16:14 DEBUG  WindowsBackend: user_directory=Lisheo
07-21 16:14 DEBUG  WindowsBackend: windows_language_code=1033
07-21 16:14 DEBUG  WindowsBackend: windows_language=English
07-21 16:14 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T5800  @ 2.00GHz
07-21 16:14 DEBUG  WindowsBackend: bootloader=vista
07-21 16:14 DEBUG  WindowsBackend: system_drive=Drive(C: hd 15452.828125 mb free )
07-21 16:14 DEBUG  WindowsBackend: drive=Drive(C: hd 15452.828125 mb free )
07-21 16:14 DEBUG  WindowsBackend: drive=Drive(D: hd 50033.8320313 mb free ntfs)
07-21 16:14 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
07-21 16:14 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
07-21 16:14 DEBUG  WindowsBackend: uninstaller_path=None
07-21 16:14 DEBUG  WindowsBackend: previous_target_dir=None
07-21 16:14 DEBUG  WindowsBackend: previous_distro_name=None
07-21 16:14 DEBUG  WindowsBackend: keyboard_id=403249161
07-21 16:14 DEBUG  WindowsBackend: keyboard_layout=ie
07-21 16:14 DEBUG  WindowsBackend: keyboard_variant=
07-21 16:14 DEBUG  CommonBackend: locale=en_IE.UTF-8
07-21 16:14 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
07-21 16:14 DEBUG  CommonBackend: Searching ISOs on USB devices
07-21 16:14 DEBUG  CommonBackend: Searching for local CDs
07-21 16:14 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pyl66BE.tmp is a valid Ubuntu CD
07-21 16:14 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pyl66BE.tmp\casper\filesystem.squashfs
07-21 16:14 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pyl66BE.tmp is a valid Ubuntu CD
07-21 16:14 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pyl66BE.tmp\casper\filesystem.squashfs
07-21 16:14 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pyl66BE.tmp is a valid Kubuntu CD
07-21 16:14 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pyl66BE.tmp\casper\filesystem.squashfs
07-21 16:14 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pyl66BE.tmp is a valid Kubuntu CD
07-21 16:14 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pyl66BE.tmp\casper\filesystem.squashfs
07-21 16:14 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pyl66BE.tmp is a valid Xubuntu CD
07-21 16:14 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pyl66BE.tmp\casper\filesystem.squashfs
07-21 16:14 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pyl66BE.tmp is a valid Xubuntu CD
07-21 16:14 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pyl66BE.tmp\casper\filesystem.squashfs
07-21 16:14 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pyl66BE.tmp is a valid Mythbuntu CD
07-21 16:14 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pyl66BE.tmp\casper\filesystem.squashfs
07-21 16:14 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pyl66BE.tmp is a valid Mythbuntu CD
07-21 16:14 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pyl66BE.tmp\casper\filesystem.squashfs
07-21 16:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-21 16:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 16:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-21 16:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 16:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-21 16:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 16:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-21 16:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 16:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-21 16:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 16:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-21 16:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 16:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-21 16:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 16:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-21 16:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 16:14 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-21 16:14 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
07-21 16:14 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
07-21 16:14 INFO   Distro: Found a valid CD for Ubuntu: E:\
07-21 16:14 INFO   root: Running the CD menu...
07-21 16:14 DEBUG  WindowsFrontend: __init__...
07-21 16:14 DEBUG  WindowsFrontend: on_init...
07-21 16:14 INFO   root: CD menu finished
07-21 16:14 INFO   root: Running the installer...
07-21 16:15 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=10000MB, distro_name=Ubuntu, language=English, username=lisheo
07-21 16:15 INFO   root: Received settings
07-21 16:15 DEBUG  TaskList: # Running tasklist...
07-21 16:15 DEBUG  TaskList: ## Running select_target_dir...
07-21 16:15 INFO   WindowsBackend: Installing into D:\ubuntu
07-21 16:15 DEBUG  TaskList: ## Finished select_target_dir
07-21 16:15 DEBUG  TaskList: ## Running create_dir_structure...
07-21 16:15 DEBUG  CommonBackend: Creating dir D:\ubuntu
07-21 16:15 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
07-21 16:15 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
07-21 16:15 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
07-21 16:15 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
07-21 16:15 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
07-21 16:15 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
07-21 16:15 DEBUG  TaskList: ## Finished create_dir_structure
07-21 16:15 DEBUG  TaskList: ## Running uncompress_target_dir...
07-21 16:15 DEBUG  TaskList: ## Finished uncompress_target_dir
07-21 16:15 DEBUG  TaskList: ## Running create_uninstaller...
07-21 16:15 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
07-21 16:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
07-21 16:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
07-21 16:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-21 16:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
07-21 16:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
07-21 16:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-21 16:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
07-21 16:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
07-21 16:15 DEBUG  TaskList: ## Finished create_uninstaller
07-21 16:15 DEBUG  TaskList: ## Running copy_installation_files...
07-21 16:15 DEBUG  WindowsBackend: Copying C:\Users\Lisheo\AppData\Local\Temp\pyl66BE.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
07-21 16:15 DEBUG  WindowsBackend: Copying C:\Users\Lisheo\AppData\Local\Temp\pyl66BE.tmp\winboot -> D:\ubuntu\winboot
07-21 16:15 DEBUG  WindowsBackend: Copying C:\Users\Lisheo\AppData\Local\Temp\pyl66BE.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
07-21 16:15 DEBUG  TaskList: ## Finished copy_installation_files
07-21 16:15 DEBUG  TaskList: ## Running get_iso...
07-21 16:15 DEBUG  TaskList: New task copy_file
07-21 16:15 DEBUG  TaskList: ### Running copy_file...
07-21 16:17 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 13] Permission denied
07-21 16:17 DEBUG  TaskList: # Cancelling tasklist
07-21 16:17 DEBUG  TaskList: New task check_iso
07-21 16:17 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 13] Permission denied
07-21 16:17 DEBUG  CommonBackend: Searching for local ISO
07-21 16:17 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
07-21 16:17 DEBUG  TaskList: New task get_metalink
07-21 16:17 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
07-21 16:17 DEBUG  TaskList: # Cancelling tasklist
07-21 16:17 DEBUG  TaskList: # Finished tasklist
07-21 16:17 INFO   root: === wubi 9.04 rev128 ===
07-21 16:17 DEBUG  root: Logfile is c:\users\lisheo\appdata\local\temp\wubi-9.04-rev128.log
07-21 16:17 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\ubuntu\\uninstall-wubi.exe"']
07-21 16:17 DEBUG  CommonBackend: data_dir=C:\Users\Lisheo\AppData\Local\Temp\pylF576.tmp\data
07-21 16:17 DEBUG  WindowsBackend: 7z=C:\Users\Lisheo\AppData\Local\Temp\pylF576.tmp\bin\7z.exe
07-21 16:17 DEBUG  CommonBackend: Fetching basic info...
07-21 16:17 DEBUG  CommonBackend: original_exe=D:\ubuntu\uninstall-wubi.exe
07-21 16:17 DEBUG  CommonBackend: platform=win32
07-21 16:17 DEBUG  CommonBackend: osname=nt
07-21 16:17 DEBUG  CommonBackend: language=en_IE
07-21 16:17 DEBUG  CommonBackend: encoding=cp1252
07-21 16:17 DEBUG  WindowsBackend: arch=amd64
07-21 16:17 DEBUG  CommonBackend: Parsing isolist=C:\Users\Lisheo\AppData\Local\Temp\pylF576.tmp\data\isolist.ini
07-21 16:17 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-21 16:17 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-21 16:17 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-21 16:17 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-21 16:17 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-21 16:17 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-21 16:17 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-21 16:17 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-21 16:17 DEBUG  WindowsBackend: Fetching host info...
07-21 16:17 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-21 16:17 DEBUG  WindowsBackend: windows version=vista
07-21 16:17 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Basic
07-21 16:17 DEBUG  WindowsBackend: windows_sp=Service Pack 1
07-21 16:17 DEBUG  WindowsBackend: windows_build=6001
07-21 16:17 DEBUG  WindowsBackend: gmt=0
07-21 16:17 DEBUG  WindowsBackend: country=IE
07-21 16:17 DEBUG  WindowsBackend: timezone=Europe/Dublin
07-21 16:17 DEBUG  WindowsBackend: windows_username=Lisheo
07-21 16:17 DEBUG  WindowsBackend: user_full_name=Lisheo
07-21 16:17 DEBUG  WindowsBackend: user_directory=Lisheo
07-21 16:17 DEBUG  WindowsBackend: windows_language_code=1033
07-21 16:17 DEBUG  WindowsBackend: windows_language=English
07-21 16:17 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T5800  @ 2.00GHz
07-21 16:17 DEBUG  WindowsBackend: bootloader=vista
07-21 16:17 DEBUG  WindowsBackend: system_drive=Drive(C: hd 15451.671875 mb free )
07-21 16:17 DEBUG  WindowsBackend: drive=Drive(C: hd 15451.671875 mb free )
07-21 16:17 DEBUG  WindowsBackend: drive=Drive(D: hd 49455.9179688 mb free ntfs)
07-21 16:17 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
07-21 16:17 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
07-21 16:17 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
07-21 16:17 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
07-21 16:17 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
07-21 16:17 DEBUG  WindowsBackend: keyboard_id=403249161
07-21 16:17 DEBUG  WindowsBackend: keyboard_layout=ie
07-21 16:17 DEBUG  WindowsBackend: keyboard_variant=
07-21 16:17 DEBUG  CommonBackend: locale=en_IE.UTF-8
07-21 16:17 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
07-21 16:17 DEBUG  CommonBackend: Searching ISOs on USB devices
07-21 16:17 DEBUG  CommonBackend: Searching for local CDs
07-21 16:17 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pylF576.tmp is a valid Ubuntu CD
07-21 16:17 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pylF576.tmp\casper\filesystem.squashfs
07-21 16:17 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pylF576.tmp is a valid Ubuntu CD
07-21 16:17 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pylF576.tmp\casper\filesystem.squashfs
07-21 16:17 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pylF576.tmp is a valid Kubuntu CD
07-21 16:17 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pylF576.tmp\casper\filesystem.squashfs
07-21 16:17 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pylF576.tmp is a valid Kubuntu CD
07-21 16:17 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pylF576.tmp\casper\filesystem.squashfs
07-21 16:17 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pylF576.tmp is a valid Xubuntu CD
07-21 16:17 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pylF576.tmp\casper\filesystem.squashfs
07-21 16:17 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pylF576.tmp is a valid Xubuntu CD
07-21 16:17 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pylF576.tmp\casper\filesystem.squashfs
07-21 16:17 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pylF576.tmp is a valid Mythbuntu CD
07-21 16:17 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pylF576.tmp\casper\filesystem.squashfs
07-21 16:17 DEBUG  Distro:   checking whether C:\Users\Lisheo\AppData\Local\Temp\pylF576.tmp is a valid Mythbuntu CD
07-21 16:17 DEBUG  Distro:     does not contain C:\Users\Lisheo\AppData\Local\Temp\pylF576.tmp\casper\filesystem.squashfs
07-21 16:17 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-21 16:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 16:17 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-21 16:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 16:17 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-21 16:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 16:17 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-21 16:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 16:17 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-21 16:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 16:17 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-21 16:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 16:17 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-21 16:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 16:17 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-21 16:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-21 16:17 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-21 16:17 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
07-21 16:17 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
07-21 16:17 INFO   Distro: Found a valid CD for Ubuntu: E:\
07-21 16:17 INFO   root: Running the uninstaller...
07-21 16:17 INFO   CommonBackend: This is the uninstaller running
07-21 16:17 DEBUG  WindowsFrontend: __init__...
07-21 16:17 DEBUG  WindowsFrontend: on_init...
07-21 16:17 INFO   root: Received settings
07-21 16:17 DEBUG  TaskList: # Running tasklist...
07-21 16:17 DEBUG  TaskList: ## Running Backup ISO...
07-21 16:17 DEBUG  TaskList: ## Finished Backup ISO
07-21 16:17 DEBUG  TaskList: ## Running Remove bootloader entry...
07-21 16:17 DEBUG  WindowsBackend: Could not find bcd id
07-21 16:17 DEBUG  WindowsBackend: undo_bootini C:
07-21 16:17 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 15451.671875 mb free )
07-21 16:17 DEBUG  WindowsBackend: undo_bootini D:
07-21 16:17 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 49455.9179688 mb free ntfs)
07-21 16:17 DEBUG  TaskList: ## Finished Remove bootloader entry
07-21 16:17 DEBUG  TaskList: ## Running Remove target dir...
07-21 16:17 DEBUG  CommonBackend: Deleting D:\ubuntu
07-21 16:17 DEBUG  TaskList: ## Finished Remove target dir
07-21 16:17 DEBUG  TaskList: ## Running Remove registry key...
07-21 16:17 DEBUG  TaskList: ## Finished Remove registry key
07-21 16:17 DEBUG  TaskList: # Finished tasklist
07-21 16:17 INFO   root: Almost finished uninstalling
07-21 16:17 INFO   root: Finished uninstallation
07-21 16:17 DEBUG  root: application.quit
07-21 16:17 DEBUG  WindowsFrontend: frontend.quit
07-21 16:17 DEBUG  WindowsFrontend: frontend.on_quit
07-21 16:17 DEBUG  root: application.on_quit
07-21 16:17 INFO   root: sys.exit

---

### Post by bacil on 2009-07-21
I am testing wubi now. for another thread that seems to have exactly the same problem, will let you know. 

thread is ... [http://ubuntuforums.org/showthread.php?p=7652425](http://ubuntuforums.org/showthread.php?p=7652425)

---

