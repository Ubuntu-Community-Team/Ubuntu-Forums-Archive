---
title: "Problem Installing U 9.04 in windows"
date: 2009-08-21
forum: Installation &amp; Upgrades
---

### Post by abyu on 2009-08-21
Hello
Iam having problem installing ubuntu 9.04 in windows vista, it says permission denied.and  generated following log file

08-20 17:38 INFO   root: === wubi 9.04 rev128 ===
08-20 17:38 DEBUG  root: Logfile is c:\users\jegan\appdata\local\temp\wubi-9.04-rev128.log
08-20 17:38 DEBUG  root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"']
08-20 17:38 DEBUG  CommonBackend: data_dir=C:\Users\Jegan\AppData\Local\Temp\pylD0D5.tmp\data
08-20 17:38 DEBUG  WindowsBackend: 7z=C:\Users\Jegan\AppData\Local\Temp\pylD0D5.tmp\bin\7z.exe
08-20 17:38 DEBUG  CommonBackend: Fetching basic info...
08-20 17:38 DEBUG  CommonBackend: original_exe=I:\wubi.exe
08-20 17:38 DEBUG  CommonBackend: platform=win32
08-20 17:38 DEBUG  CommonBackend: osname=nt
08-20 17:38 DEBUG  CommonBackend: language=en_IN
08-20 17:38 DEBUG  CommonBackend: encoding=cp1252
08-20 17:38 DEBUG  WindowsBackend: arch=amd64
08-20 17:38 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jegan\AppData\Local\Temp\pylD0D5.tmp\data\isolist.ini
08-20 17:38 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-20 17:38 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-20 17:38 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-20 17:38 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-20 17:38 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-20 17:38 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-20 17:38 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-20 17:38 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-20 17:38 DEBUG  WindowsBackend: Fetching host info...
08-20 17:38 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-20 17:38 DEBUG  WindowsBackend: windows version=vista
08-20 17:38 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Premium
08-20 17:38 DEBUG  WindowsBackend: windows_sp=Service Pack 1
08-20 17:38 DEBUG  WindowsBackend: windows_build=6001
08-20 17:38 DEBUG  WindowsBackend: gmt=5
08-20 17:38 DEBUG  WindowsBackend: country=IN
08-20 17:38 DEBUG  WindowsBackend: timezone=Asia/Calcutta
08-20 17:38 DEBUG  WindowsBackend: windows_username=Jegan
08-20 17:38 DEBUG  WindowsBackend: user_full_name=Jegan
08-20 17:38 DEBUG  WindowsBackend: user_directory=Jegan
08-20 17:38 DEBUG  WindowsBackend: windows_language_code=1033
08-20 17:38 DEBUG  WindowsBackend: windows_language=English
08-20 17:38 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T6400  @ 2.00GHz
08-20 17:38 DEBUG  WindowsBackend: bootloader=vista
08-20 17:38 DEBUG  WindowsBackend: system_drive=Drive(C: hd 79296.8867188 mb free )
08-20 17:38 DEBUG  WindowsBackend: drive=Drive(C: hd 79296.8867188 mb free )
08-20 17:38 DEBUG  WindowsBackend: drive=Drive(D: hd 18293.2460938 mb free ntfs)
08-20 17:38 DEBUG  WindowsBackend: drive=Drive(E: hd 8822.47265625 mb free ntfs)
08-20 17:38 DEBUG  WindowsBackend: drive=Drive(F: hd 18513.2460938 mb free ntfs)
08-20 17:38 DEBUG  WindowsBackend: drive=Drive(G: hd 19547.296875 mb free ntfs)
08-20 17:38 DEBUG  WindowsBackend: drive=Drive(H: hd 20389.7265625 mb free ntfs)
08-20 17:38 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
08-20 17:38 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
08-20 17:38 DEBUG  WindowsBackend: drive=Drive(K: cd 0.0 mb free )
08-20 17:38 DEBUG  WindowsBackend: uninstaller_path=None
08-20 17:38 DEBUG  WindowsBackend: previous_target_dir=None
08-20 17:38 DEBUG  WindowsBackend: previous_distro_name=None
08-20 17:38 DEBUG  WindowsBackend: keyboard_id=67699721
08-20 17:38 DEBUG  WindowsBackend: keyboard_layout=in
08-20 17:38 DEBUG  WindowsBackend: keyboard_variant=
08-20 17:38 DEBUG  CommonBackend: locale=en_IN
08-20 17:38 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
08-20 17:38 DEBUG  CommonBackend: Searching ISOs on USB devices
08-20 17:38 DEBUG  CommonBackend: Searching for local CDs
08-20 17:38 DEBUG  Distro:   checking whether C:\Users\Jegan\AppData\Local\Temp\pylD0D5.tmp is a valid Ubuntu CD
08-20 17:38 DEBUG  Distro:     does not contain C:\Users\Jegan\AppData\Local\Temp\pylD0D5.tmp\casper\filesystem.squashfs
08-20 17:38 DEBUG  Distro:   checking whether C:\Users\Jegan\AppData\Local\Temp\pylD0D5.tmp is a valid Ubuntu CD
08-20 17:38 DEBUG  Distro:     does not contain C:\Users\Jegan\AppData\Local\Temp\pylD0D5.tmp\casper\filesystem.squashfs
08-20 17:38 DEBUG  Distro:   checking whether C:\Users\Jegan\AppData\Local\Temp\pylD0D5.tmp is a valid Kubuntu CD
08-20 17:38 DEBUG  Distro:     does not contain C:\Users\Jegan\AppData\Local\Temp\pylD0D5.tmp\casper\filesystem.squashfs
08-20 17:38 DEBUG  Distro:   checking whether C:\Users\Jegan\AppData\Local\Temp\pylD0D5.tmp is a valid Kubuntu CD
08-20 17:38 DEBUG  Distro:     does not contain C:\Users\Jegan\AppData\Local\Temp\pylD0D5.tmp\casper\filesystem.squashfs
08-20 17:38 DEBUG  Distro:   checking whether C:\Users\Jegan\AppData\Local\Temp\pylD0D5.tmp is a valid Xubuntu CD
08-20 17:38 DEBUG  Distro:     does not contain C:\Users\Jegan\AppData\Local\Temp\pylD0D5.tmp\casper\filesystem.squashfs
08-20 17:38 DEBUG  Distro:   checking whether C:\Users\Jegan\AppData\Local\Temp\pylD0D5.tmp is a valid Xubuntu CD
08-20 17:38 DEBUG  Distro:     does not contain C:\Users\Jegan\AppData\Local\Temp\pylD0D5.tmp\casper\filesystem.squashfs
08-20 17:38 DEBUG  Distro:   checking whether C:\Users\Jegan\AppData\Local\Temp\pylD0D5.tmp is a valid Mythbuntu CD
08-20 17:38 DEBUG  Distro:     does not contain C:\Users\Jegan\AppData\Local\Temp\pylD0D5.tmp\casper\filesystem.squashfs
08-20 17:38 DEBUG  Distro:   checking whether C:\Users\Jegan\AppData\Local\Temp\pylD0D5.tmp is a valid Mythbuntu CD
08-20 17:38 DEBUG  Distro:     does not contain C:\Users\Jegan\AppData\Local\Temp\pylD0D5.tmp\casper\filesystem.squashfs
08-20 17:38 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-20 17:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 17:38 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-20 17:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 17:38 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-20 17:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 17:38 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-20 17:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 17:38 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-20 17:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 17:38 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-20 17:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 17:38 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-20 17:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 17:38 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-20 17:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 17:38 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-20 17:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 17:38 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-20 17:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 17:38 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-20 17:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 17:38 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-20 17:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 17:38 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-20 17:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 17:38 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-20 17:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 17:38 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-20 17:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 17:38 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-20 17:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 17:38 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-20 17:38 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 17:38 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-20 17:38 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 17:38 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-20 17:38 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 17:38 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-20 17:38 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 17:38 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-20 17:38 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 17:38 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-20 17:38 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 17:38 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-20 17:38 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 17:38 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-20 17:38 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 17:38 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-20 17:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-20 17:38 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-20 17:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-20 17:38 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-20 17:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-20 17:38 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-20 17:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-20 17:38 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-20 17:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-20 17:38 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-20 17:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-20 17:38 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-20 17:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-20 17:38 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-20 17:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-20 17:38 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-20 17:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-20 17:38 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-20 17:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-20 17:38 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-20 17:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-20 17:38 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-20 17:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-20 17:38 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-20 17:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-20 17:38 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-20 17:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-20 17:38 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-20 17:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-20 17:38 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-20 17:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-20 17:38 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-20 17:38 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
08-20 17:38 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
08-20 17:38 INFO   Distro: Found a valid CD for Ubuntu: I:\
08-20 17:38 INFO   root: Running the CD menu...
08-20 17:38 DEBUG  WindowsFrontend: __init__...
08-20 17:38 DEBUG  WindowsFrontend: on_init...
08-20 17:38 INFO   root: CD menu finished
08-20 17:38 INFO   root: Running the installer...
08-20 17:39 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=8000MB, distro_name=Ubuntu, language=English, username=jegan
08-20 17:39 INFO   root: Received settings
08-20 17:39 DEBUG  TaskList: # Running tasklist...
08-20 17:39 DEBUG  TaskList: ## Running select_target_dir...
08-20 17:39 INFO   WindowsBackend: Installing into C:\ubuntu
08-20 17:39 DEBUG  TaskList: ## Finished select_target_dir
08-20 17:39 DEBUG  TaskList: ## Running create_dir_structure...
08-20 17:39 DEBUG  CommonBackend: Creating dir C:\ubuntu
08-20 17:39 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
08-20 17:39 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
08-20 17:39 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
08-20 17:39 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
08-20 17:39 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
08-20 17:39 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
08-20 17:39 DEBUG  TaskList: ## Finished create_dir_structure
08-20 17:39 DEBUG  TaskList: ## Running uncompress_target_dir...
08-20 17:39 DEBUG  TaskList: ## Finished uncompress_target_dir
08-20 17:39 DEBUG  TaskList: ## Running create_uninstaller...
08-20 17:39 DEBUG  WindowsBackend: Copying uninstaller I:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
08-20 17:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
08-20 17:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
08-20 17:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
08-20 17:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
08-20 17:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
08-20 17:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
08-20 17:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
08-20 17:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
08-20 17:39 DEBUG  TaskList: ## Finished create_uninstaller
08-20 17:39 DEBUG  TaskList: ## Running copy_installation_files...
08-20 17:39 DEBUG  WindowsBackend: Copying C:\Users\Jegan\AppData\Local\Temp\pylD0D5.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
08-20 17:39 DEBUG  WindowsBackend: Copying C:\Users\Jegan\AppData\Local\Temp\pylD0D5.tmp\winboot -> C:\ubuntu\winboot
08-20 17:39 DEBUG  WindowsBackend: Copying C:\Users\Jegan\AppData\Local\Temp\pylD0D5.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
08-20 17:39 DEBUG  TaskList: ## Finished copy_installation_files
08-20 17:39 DEBUG  TaskList: ## Running get_iso...
08-20 17:39 DEBUG  TaskList: New task copy_file
08-20 17:39 DEBUG  TaskList: ### Running copy_file...
08-20 17:42 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 13] Permission denied
08-20 17:42 DEBUG  TaskList: # Cancelling tasklist
08-20 17:42 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 13] Permission denied
08-20 17:42 DEBUG  TaskList: New task check_iso
08-20 17:42 DEBUG  CommonBackend: Searching for local ISO
08-20 17:42 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
08-20 17:42 DEBUG  TaskList: New task get_metalink
08-20 17:42 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
08-20 17:42 DEBUG  TaskList: # Cancelling tasklist
08-20 17:42 DEBUG  TaskList: # Finished tasklist
08-20 17:45 INFO   root: === wubi 9.04 rev128 ===
08-20 17:45 DEBUG  root: Logfile is c:\users\jegan\appdata\local\temp\wubi-9.04-rev128.log
08-20 17:45 DEBUG  root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"']
08-20 17:45 DEBUG  CommonBackend: data_dir=C:\Users\Jegan\AppData\Local\Temp\pylD1DE.tmp\data
08-20 17:45 DEBUG  WindowsBackend: 7z=C:\Users\Jegan\AppData\Local\Temp\pylD1DE.tmp\bin\7z.exe
08-20 17:45 DEBUG  CommonBackend: Fetching basic info...
08-20 17:45 DEBUG  CommonBackend: original_exe=I:\wubi.exe
08-20 17:45 DEBUG  CommonBackend: platform=win32
08-20 17:45 DEBUG  CommonBackend: osname=nt
08-20 17:45 DEBUG  CommonBackend: language=en_IN
08-20 17:45 DEBUG  CommonBackend: encoding=cp1252
08-20 17:45 DEBUG  WindowsBackend: arch=amd64
08-20 17:45 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jegan\AppData\Local\Temp\pylD1DE.tmp\data\isolist.ini
08-20 17:45 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-20 17:45 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-20 17:45 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-20 17:45 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-20 17:45 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-20 17:45 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-20 17:45 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-20 17:45 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-20 17:45 DEBUG  WindowsBackend: Fetching host info...
08-20 17:45 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-20 17:45 DEBUG  WindowsBackend: windows version=vista
08-20 17:45 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Premium
08-20 17:45 DEBUG  WindowsBackend: windows_sp=Service Pack 1
08-20 17:45 DEBUG  WindowsBackend: windows_build=6001
08-20 17:45 DEBUG  WindowsBackend: gmt=5
08-20 17:45 DEBUG  WindowsBackend: country=IN
08-20 17:45 DEBUG  WindowsBackend: timezone=Asia/Calcutta
08-20 17:45 DEBUG  WindowsBackend: windows_username=Jegan
08-20 17:45 DEBUG  WindowsBackend: user_full_name=Jegan
08-20 17:45 DEBUG  WindowsBackend: user_directory=Jegan
08-20 17:45 DEBUG  WindowsBackend: windows_language_code=1033
08-20 17:45 DEBUG  WindowsBackend: windows_language=English
08-20 17:45 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T6400  @ 2.00GHz
08-20 17:45 DEBUG  WindowsBackend: bootloader=vista
08-20 17:45 DEBUG  WindowsBackend: system_drive=Drive(C: hd 78883.4375 mb free )
08-20 17:45 DEBUG  WindowsBackend: drive=Drive(C: hd 78883.4375 mb free )
08-20 17:45 DEBUG  WindowsBackend: drive=Drive(D: hd 18293.2460938 mb free ntfs)
08-20 17:45 DEBUG  WindowsBackend: drive=Drive(E: hd 8822.47265625 mb free ntfs)
08-20 17:45 DEBUG  WindowsBackend: drive=Drive(F: hd 18513.2460938 mb free ntfs)
08-20 17:45 DEBUG  WindowsBackend: drive=Drive(G: hd 19547.296875 mb free ntfs)
08-20 17:45 DEBUG  WindowsBackend: drive=Drive(H: hd 20389.7265625 mb free ntfs)
08-20 17:45 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
08-20 17:45 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
08-20 17:45 DEBUG  WindowsBackend: drive=Drive(K: cd 0.0 mb free )
08-20 17:45 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
08-20 17:45 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
08-20 17:45 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
08-20 17:45 DEBUG  WindowsBackend: keyboard_id=67699721
08-20 17:45 DEBUG  WindowsBackend: keyboard_layout=in
08-20 17:45 DEBUG  WindowsBackend: keyboard_variant=
08-20 17:45 DEBUG  CommonBackend: locale=en_IN
08-20 17:45 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
08-20 17:45 DEBUG  CommonBackend: Searching ISOs on USB devices
08-20 17:45 DEBUG  CommonBackend: Searching for local CDs
08-20 17:45 DEBUG  Distro:   checking whether C:\Users\Jegan\AppData\Local\Temp\pylD1DE.tmp is a valid Ubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain C:\Users\Jegan\AppData\Local\Temp\pylD1DE.tmp\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether C:\Users\Jegan\AppData\Local\Temp\pylD1DE.tmp is a valid Ubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain C:\Users\Jegan\AppData\Local\Temp\pylD1DE.tmp\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether C:\Users\Jegan\AppData\Local\Temp\pylD1DE.tmp is a valid Kubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain C:\Users\Jegan\AppData\Local\Temp\pylD1DE.tmp\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether C:\Users\Jegan\AppData\Local\Temp\pylD1DE.tmp is a valid Kubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain C:\Users\Jegan\AppData\Local\Temp\pylD1DE.tmp\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether C:\Users\Jegan\AppData\Local\Temp\pylD1DE.tmp is a valid Xubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain C:\Users\Jegan\AppData\Local\Temp\pylD1DE.tmp\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether C:\Users\Jegan\AppData\Local\Temp\pylD1DE.tmp is a valid Xubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain C:\Users\Jegan\AppData\Local\Temp\pylD1DE.tmp\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether C:\Users\Jegan\AppData\Local\Temp\pylD1DE.tmp is a valid Mythbuntu CD
08-20 17:45 DEBUG  Distro:     does not contain C:\Users\Jegan\AppData\Local\Temp\pylD1DE.tmp\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether C:\Users\Jegan\AppData\Local\Temp\pylD1DE.tmp is a valid Mythbuntu CD
08-20 17:45 DEBUG  Distro:     does not contain C:\Users\Jegan\AppData\Local\Temp\pylD1DE.tmp\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-20 17:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-20 17:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-20 17:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-20 17:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-20 17:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-20 17:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-20 17:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-20 17:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-20 17:45 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-20 17:45 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-20 17:45 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
08-20 17:45 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
08-20 17:45 INFO   Distro: Found a valid CD for Ubuntu: I:\
08-20 17:45 INFO   root: Running the CD menu...
08-20 17:45 DEBUG  WindowsFrontend: __init__...
08-20 17:45 DEBUG  WindowsFrontend: on_init...
08-20 17:45 INFO   root: CD menu finished
08-20 17:45 INFO   root: Already installed, running the uninstaller...
08-20 17:45 INFO   root: Running the uninstaller...
08-20 17:45 INFO   CommonBackend: This is the uninstaller running
08-20 17:45 INFO   root: Received settings
08-20 17:45 DEBUG  TaskList: # Running tasklist...
08-20 17:45 DEBUG  TaskList: ## Running Backup ISO...
08-20 17:45 DEBUG  TaskList: ## Finished Backup ISO
08-20 17:45 DEBUG  TaskList: ## Running Remove bootloader entry...
08-20 17:45 DEBUG  WindowsBackend: Could not find bcd id
08-20 17:45 DEBUG  WindowsBackend: undo_bootini C:
08-20 17:45 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 78883.4375 mb free )
08-20 17:45 DEBUG  WindowsBackend: undo_bootini D:
08-20 17:45 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 18293.2460938 mb free ntfs)
08-20 17:45 DEBUG  WindowsBackend: undo_bootini E:
08-20 17:45 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 8822.47265625 mb free ntfs)
08-20 17:45 DEBUG  WindowsBackend: undo_bootini F:
08-20 17:45 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 18513.2460938 mb free ntfs)
08-20 17:45 DEBUG  WindowsBackend: undo_bootini G:
08-20 17:45 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 19547.296875 mb free ntfs)
08-20 17:45 DEBUG  WindowsBackend: undo_bootini H:
08-20 17:45 DEBUG  WindowsBackend: undo_configsys Drive(H: hd 20389.7265625 mb free ntfs)
08-20 17:45 DEBUG  TaskList: ## Finished Remove bootloader entry
08-20 17:45 DEBUG  TaskList: ## Running Remove target dir...
08-20 17:45 DEBUG  CommonBackend: Deleting C:\ubuntu
08-20 17:45 DEBUG  TaskList: ## Finished Remove target dir
08-20 17:45 DEBUG  TaskList: ## Running Remove registry key...
08-20 17:45 DEBUG  TaskList: ## Finished Remove registry key
08-20 17:45 DEBUG  TaskList: # Finished tasklist
08-20 17:45 INFO   root: Almost finished uninstalling
08-20 17:45 INFO   root: Finished uninstallation
08-20 17:45 DEBUG  CommonBackend: Fetching basic info...
08-20 17:45 DEBUG  CommonBackend: original_exe=I:\wubi.exe
08-20 17:45 DEBUG  CommonBackend: platform=win32
08-20 17:45 DEBUG  CommonBackend: osname=nt
08-20 17:45 DEBUG  CommonBackend: language=en_IN
08-20 17:45 DEBUG  CommonBackend: encoding=cp1252
08-20 17:45 DEBUG  WindowsBackend: arch=amd64
08-20 17:45 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jegan\AppData\Local\Temp\pylD1DE.tmp\data\isolist.ini
08-20 17:45 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-20 17:45 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-20 17:45 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-20 17:45 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-20 17:45 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-20 17:45 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-20 17:45 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-20 17:45 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-20 17:45 DEBUG  WindowsBackend: Fetching host info...
08-20 17:45 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-20 17:45 DEBUG  WindowsBackend: windows version=vista
08-20 17:45 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Premium
08-20 17:45 DEBUG  WindowsBackend: windows_sp=Service Pack 1
08-20 17:45 DEBUG  WindowsBackend: windows_build=6001
08-20 17:45 DEBUG  WindowsBackend: gmt=5
08-20 17:45 DEBUG  WindowsBackend: country=IN
08-20 17:45 DEBUG  WindowsBackend: timezone=Asia/Calcutta
08-20 17:45 DEBUG  WindowsBackend: windows_username=Jegan
08-20 17:45 DEBUG  WindowsBackend: user_full_name=Jegan
08-20 17:45 DEBUG  WindowsBackend: user_directory=Jegan
08-20 17:45 DEBUG  WindowsBackend: windows_language_code=1033
08-20 17:45 DEBUG  WindowsBackend: windows_language=English
08-20 17:45 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T6400  @ 2.00GHz
08-20 17:45 DEBUG  WindowsBackend: bootloader=vista
08-20 17:45 DEBUG  WindowsBackend: system_drive=Drive(C: hd 79295.3242188 mb free )
08-20 17:45 DEBUG  WindowsBackend: drive=Drive(C: hd 79295.3242188 mb free )
08-20 17:45 DEBUG  WindowsBackend: drive=Drive(D: hd 18293.2460938 mb free ntfs)
08-20 17:45 DEBUG  WindowsBackend: drive=Drive(E: hd 8822.47265625 mb free ntfs)
08-20 17:45 DEBUG  WindowsBackend: drive=Drive(F: hd 18513.2460938 mb free ntfs)
08-20 17:45 DEBUG  WindowsBackend: drive=Drive(G: hd 19547.296875 mb free ntfs)
08-20 17:45 DEBUG  WindowsBackend: drive=Drive(H: hd 20389.7265625 mb free ntfs)
08-20 17:45 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
08-20 17:45 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
08-20 17:45 DEBUG  WindowsBackend: drive=Drive(K: cd 0.0 mb free )
08-20 17:45 DEBUG  WindowsBackend: uninstaller_path=None
08-20 17:45 DEBUG  WindowsBackend: previous_target_dir=None
08-20 17:45 DEBUG  WindowsBackend: previous_distro_name=None
08-20 17:45 DEBUG  WindowsBackend: keyboard_id=67699721
08-20 17:45 DEBUG  WindowsBackend: keyboard_layout=in
08-20 17:45 DEBUG  WindowsBackend: keyboard_variant=
08-20 17:45 DEBUG  CommonBackend: locale=en_IN
08-20 17:45 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
08-20 17:45 DEBUG  CommonBackend: Searching ISOs on USB devices
08-20 17:45 DEBUG  CommonBackend: Searching for local CDs
08-20 17:45 DEBUG  Distro:   checking whether C:\Users\Jegan\AppData\Local\Temp\pylD1DE.tmp is a valid Ubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain C:\Users\Jegan\AppData\Local\Temp\pylD1DE.tmp\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether C:\Users\Jegan\AppData\Local\Temp\pylD1DE.tmp is a valid Ubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain C:\Users\Jegan\AppData\Local\Temp\pylD1DE.tmp\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether C:\Users\Jegan\AppData\Local\Temp\pylD1DE.tmp is a valid Kubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain C:\Users\Jegan\AppData\Local\Temp\pylD1DE.tmp\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether C:\Users\Jegan\AppData\Local\Temp\pylD1DE.tmp is a valid Kubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain C:\Users\Jegan\AppData\Local\Temp\pylD1DE.tmp\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether C:\Users\Jegan\AppData\Local\Temp\pylD1DE.tmp is a valid Xubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain C:\Users\Jegan\AppData\Local\Temp\pylD1DE.tmp\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether C:\Users\Jegan\AppData\Local\Temp\pylD1DE.tmp is a valid Xubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain C:\Users\Jegan\AppData\Local\Temp\pylD1DE.tmp\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether C:\Users\Jegan\AppData\Local\Temp\pylD1DE.tmp is a valid Mythbuntu CD
08-20 17:45 DEBUG  Distro:     does not contain C:\Users\Jegan\AppData\Local\Temp\pylD1DE.tmp\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether C:\Users\Jegan\AppData\Local\Temp\pylD1DE.tmp is a valid Mythbuntu CD
08-20 17:45 DEBUG  Distro:     does not contain C:\Users\Jegan\AppData\Local\Temp\pylD1DE.tmp\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-20 17:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-20 17:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-20 17:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-20 17:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-20 17:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-20 17:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-20 17:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-20 17:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-20 17:45 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-20 17:45 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-20 17:45 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-20 17:45 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-20 17:45 INFO   Distro: Found a valid CD for Ubuntu: I:\
08-20 17:45 INFO   root: Running the installer...
08-20 17:45 DEBUG  WinuiInstallationPage: target_drive=H:, installation_size=8000MB, distro_name=Ubuntu, language=English, username=jegan
08-20 17:45 INFO   root: Received settings
08-20 17:45 DEBUG  TaskList: # Running tasklist...
08-20 17:45 DEBUG  TaskList: ## Running select_target_dir...
08-20 17:45 INFO   WindowsBackend: Installing into H:\ubuntu
08-20 17:45 DEBUG  TaskList: ## Finished select_target_dir
08-20 17:45 DEBUG  TaskList: ## Running create_dir_structure...
08-20 17:45 DEBUG  CommonBackend: Creating dir H:\ubuntu
08-20 17:45 DEBUG  CommonBackend: Creating dir H:\ubuntu\disks
08-20 17:45 DEBUG  CommonBackend: Creating dir H:\ubuntu\install
08-20 17:45 DEBUG  CommonBackend: Creating dir H:\ubuntu\install\boot
08-20 17:45 DEBUG  CommonBackend: Creating dir H:\ubuntu\disks\boot
08-20 17:45 DEBUG  CommonBackend: Creating dir H:\ubuntu\disks\boot\grub
08-20 17:45 DEBUG  CommonBackend: Creating dir H:\ubuntu\install\boot\grub
08-20 17:45 DEBUG  TaskList: ## Finished create_dir_structure
08-20 17:45 DEBUG  TaskList: ## Running uncompress_target_dir...
08-20 17:45 DEBUG  TaskList: ## Finished uncompress_target_dir
08-20 17:45 DEBUG  TaskList: ## Running create_uninstaller...
08-20 17:45 DEBUG  WindowsBackend: Copying uninstaller I:\wubi.exe -> H:\ubuntu\uninstall-wubi.exe
08-20 17:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString H:\ubuntu\uninstall-wubi.exe
08-20 17:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir H:\ubuntu
08-20 17:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
08-20 17:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon H:\ubuntu\Ubuntu.ico
08-20 17:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
08-20 17:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
08-20 17:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
08-20 17:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
08-20 17:45 DEBUG  TaskList: ## Finished create_uninstaller
08-20 17:45 DEBUG  TaskList: ## Running copy_installation_files...
08-20 17:45 DEBUG  WindowsBackend: Copying C:\Users\Jegan\AppData\Local\Temp\pylD1DE.tmp\data\custom-installation -> H:\ubuntu\install\custom-installation
08-20 17:45 DEBUG  WindowsBackend: Copying C:\Users\Jegan\AppData\Local\Temp\pylD1DE.tmp\winboot -> H:\ubuntu\winboot
08-20 17:45 DEBUG  WindowsBackend: Copying C:\Users\Jegan\AppData\Local\Temp\pylD1DE.tmp\data\images\Ubuntu.ico -> H:\ubuntu\Ubuntu.ico
08-20 17:45 DEBUG  TaskList: ## Finished copy_installation_files
08-20 17:45 DEBUG  TaskList: ## Running get_iso...
08-20 17:45 DEBUG  TaskList: New task copy_file
08-20 17:45 DEBUG  TaskList: ### Running copy_file...
08-20 17:50 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 13] Permission denied
08-20 17:50 DEBUG  TaskList: # Cancelling tasklist
08-20 17:50 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 13] Permission denied
08-20 17:50 DEBUG  TaskList: New task check_iso
08-20 17:50 DEBUG  CommonBackend: Searching for local ISO
08-20 17:50 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
08-20 17:50 DEBUG  TaskList: New task get_metalink
08-20 17:50 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
08-20 17:50 DEBUG  TaskList: # Cancelling tasklist
08-20 17:50 DEBUG  TaskList: # Finished tasklist

can anybody help me with regard.
Thank you

---

### Post by earthpigg on 2009-08-21
you are trying a wubi install, i take it?

are you the administrator of that vista machine?

---

### Post by abyu on 2009-08-22
yes i'm using the wubi install..
and i'm the administrator of the system.
i'm using windows vista home premium..

---

### Post by earthpigg on 2009-08-22
have you tried turning off UAC temporarily?

---

### Post by Mark Phelps on 2009-08-23
This is a known problem when read errors are encountered with the CD.  Try downloading a fresh copy or reburning the CD with very turned on to check the burn.

---

