---
title: "Error installing Kubuntu through Wubi on Windows 7"
date: 2009-07-26
forum: Installation &amp; Upgrades
---

### Post by racie on 2009-07-26
Hello, I've installed an Ubuntu OS on my computer before and decided to take a break from it.  Now I want to install it again, but Wubi gives me an error message when I try to install Kubuntu.  The error message pops up almost right after I click install.  I'm running Windows 7, in case that has anything to do with it.


It says, "An error occurred:

Cannot download the metalink and therefore the ISO

For more information, please see the log file:
c:\users\rachael\appdata\local\temp\wubi-9.04-rev129.log"

Here is what it says in the log file:
```
07-26 17:31 INFO   root: === wubi 9.04 rev129 ===
07-26 17:31 DEBUG  root: Logfile is c:\users\rachael\appdata\local\temp\wubi-9.04-rev129.log
07-26 17:31 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Rachael\\Downloads\\wubi.exe"']
07-26 17:31 DEBUG  CommonBackend: data_dir=C:\Users\Rachael\AppData\Local\Temp\pyl70BC.tmp\data
07-26 17:31 DEBUG  WindowsBackend: 7z=C:\Users\Rachael\AppData\Local\Temp\pyl70BC.tmp\bin\7z.exe
07-26 17:31 DEBUG  CommonBackend: Fetching basic info...
07-26 17:31 DEBUG  CommonBackend: original_exe=C:\Users\Rachael\Downloads\wubi.exe
07-26 17:31 DEBUG  CommonBackend: platform=win32
07-26 17:31 DEBUG  CommonBackend: osname=nt
07-26 17:31 DEBUG  CommonBackend: language=en_US
07-26 17:31 DEBUG  CommonBackend: encoding=cp1252
07-26 17:31 DEBUG  WindowsBackend: arch=amd64
07-26 17:31 DEBUG  CommonBackend: Parsing isolist=C:\Users\Rachael\AppData\Local\Temp\pyl70BC.tmp\data\isolist.ini
07-26 17:31 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-26 17:31 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-26 17:31 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-26 17:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-26 17:31 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-26 17:31 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-26 17:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-26 17:31 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-26 17:31 DEBUG  WindowsBackend: Fetching host info...
07-26 17:31 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-26 17:31 DEBUG  WindowsBackend: windows version=vista
07-26 17:31 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
07-26 17:31 DEBUG  WindowsBackend: windows_sp=None
07-26 17:31 DEBUG  WindowsBackend: windows_build=7100
07-26 17:31 DEBUG  WindowsBackend: gmt=-5
07-26 17:31 DEBUG  WindowsBackend: country=US
07-26 17:31 DEBUG  WindowsBackend: timezone=America/New_York
07-26 17:31 DEBUG  WindowsBackend: windows_username=Rachael
07-26 17:31 DEBUG  WindowsBackend: user_full_name=Rachael
07-26 17:31 DEBUG  WindowsBackend: user_directory=Rachael
07-26 17:31 DEBUG  WindowsBackend: windows_language_code=1033
07-26 17:31 DEBUG  WindowsBackend: windows_language=English
07-26 17:31 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) 64 X2 Mobile Technology TL-58
07-26 17:31 DEBUG  WindowsBackend: bootloader=vista
07-26 17:31 DEBUG  WindowsBackend: system_drive=Drive(C: hd 59560.2890625 mb free )
07-26 17:31 DEBUG  WindowsBackend: drive=Drive(C: hd 59560.2890625 mb free )
07-26 17:31 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
07-26 17:31 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
07-26 17:31 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
07-26 17:31 DEBUG  WindowsBackend: uninstaller_path=None
07-26 17:31 DEBUG  WindowsBackend: previous_target_dir=None
07-26 17:31 DEBUG  WindowsBackend: previous_distro_name=None
07-26 17:31 DEBUG  WindowsBackend: keyboard_id=67699721
07-26 17:31 DEBUG  WindowsBackend: keyboard_layout=us
07-26 17:31 DEBUG  WindowsBackend: keyboard_variant=
07-26 17:31 DEBUG  CommonBackend: locale=en_US.UTF-8
07-26 17:31 DEBUG  WindowsBackend: total_memory_mb=1982.92578125
07-26 17:31 DEBUG  CommonBackend: Searching ISOs on USB devices
07-26 17:31 DEBUG  CommonBackend: Searching for local CDs
07-26 17:31 DEBUG  Distro:   checking whether C:\Users\Rachael\AppData\Local\Temp\pyl70BC.tmp is a valid Ubuntu CD
07-26 17:31 DEBUG  Distro:     does not contain C:\Users\Rachael\AppData\Local\Temp\pyl70BC.tmp\casper\filesystem.squashfs
07-26 17:31 DEBUG  Distro:   checking whether C:\Users\Rachael\AppData\Local\Temp\pyl70BC.tmp is a valid Ubuntu CD
07-26 17:31 DEBUG  Distro:     does not contain C:\Users\Rachael\AppData\Local\Temp\pyl70BC.tmp\casper\filesystem.squashfs
07-26 17:31 DEBUG  Distro:   checking whether C:\Users\Rachael\AppData\Local\Temp\pyl70BC.tmp is a valid Kubuntu CD
07-26 17:31 DEBUG  Distro:     does not contain C:\Users\Rachael\AppData\Local\Temp\pyl70BC.tmp\casper\filesystem.squashfs
07-26 17:31 DEBUG  Distro:   checking whether C:\Users\Rachael\AppData\Local\Temp\pyl70BC.tmp is a valid Kubuntu CD
07-26 17:31 DEBUG  Distro:     does not contain C:\Users\Rachael\AppData\Local\Temp\pyl70BC.tmp\casper\filesystem.squashfs
07-26 17:31 DEBUG  Distro:   checking whether C:\Users\Rachael\AppData\Local\Temp\pyl70BC.tmp is a valid Xubuntu CD
07-26 17:31 DEBUG  Distro:     does not contain C:\Users\Rachael\AppData\Local\Temp\pyl70BC.tmp\casper\filesystem.squashfs
07-26 17:31 DEBUG  Distro:   checking whether C:\Users\Rachael\AppData\Local\Temp\pyl70BC.tmp is a valid Xubuntu CD
07-26 17:31 DEBUG  Distro:     does not contain C:\Users\Rachael\AppData\Local\Temp\pyl70BC.tmp\casper\filesystem.squashfs
07-26 17:31 DEBUG  Distro:   checking whether C:\Users\Rachael\AppData\Local\Temp\pyl70BC.tmp is a valid Mythbuntu CD
07-26 17:31 DEBUG  Distro:     does not contain C:\Users\Rachael\AppData\Local\Temp\pyl70BC.tmp\casper\filesystem.squashfs
07-26 17:31 DEBUG  Distro:   checking whether C:\Users\Rachael\AppData\Local\Temp\pyl70BC.tmp is a valid Mythbuntu CD
07-26 17:31 DEBUG  Distro:     does not contain C:\Users\Rachael\AppData\Local\Temp\pyl70BC.tmp\casper\filesystem.squashfs
07-26 17:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-26 17:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 17:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-26 17:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 17:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-26 17:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 17:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-26 17:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 17:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-26 17:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 17:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-26 17:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 17:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-26 17:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 17:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-26 17:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 17:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-26 17:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 17:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-26 17:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 17:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-26 17:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 17:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-26 17:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 17:31 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-26 17:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 17:31 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-26 17:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 17:31 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-26 17:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 17:31 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-26 17:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 17:31 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-26 17:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 17:31 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-26 17:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 17:31 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-26 17:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 17:31 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-26 17:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 17:31 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-26 17:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 17:31 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-26 17:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 17:31 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-26 17:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 17:31 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-26 17:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 17:31 INFO   root: Running the installer...
07-26 17:31 DEBUG  WindowsFrontend: __init__...
07-26 17:31 DEBUG  WindowsFrontend: on_init...
07-26 17:34 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=8000MB, distro_name=Kubuntu, language=English, username=rachael
07-26 17:34 INFO   root: Received settings
07-26 17:34 DEBUG  TaskList: # Running tasklist...
07-26 17:34 DEBUG  TaskList: ## Running select_target_dir...
07-26 17:34 INFO   WindowsBackend: Installing into C:\ubuntu
07-26 17:34 DEBUG  TaskList: ## Finished select_target_dir
07-26 17:34 DEBUG  TaskList: ## Running create_dir_structure...
07-26 17:34 DEBUG  CommonBackend: Creating dir C:\ubuntu
07-26 17:34 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
07-26 17:34 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
07-26 17:34 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
07-26 17:34 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
07-26 17:34 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
07-26 17:34 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
07-26 17:34 DEBUG  TaskList: ## Finished create_dir_structure
07-26 17:34 DEBUG  TaskList: ## Running uncompress_target_dir...
07-26 17:34 DEBUG  TaskList: ## Finished uncompress_target_dir
07-26 17:34 DEBUG  TaskList: ## Running create_uninstaller...
07-26 17:34 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Rachael\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
07-26 17:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
07-26 17:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
07-26 17:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Kubuntu
07-26 17:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Kubuntu.ico
07-26 17:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev129
07-26 17:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Kubuntu
07-26 17:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.kubuntu.org
07-26 17:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
07-26 17:34 DEBUG  TaskList: ## Finished create_uninstaller
07-26 17:34 DEBUG  TaskList: ## Running copy_installation_files...
07-26 17:34 DEBUG  WindowsBackend: Copying C:\Users\Rachael\AppData\Local\Temp\pyl70BC.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
07-26 17:34 DEBUG  WindowsBackend: Copying C:\Users\Rachael\AppData\Local\Temp\pyl70BC.tmp\winboot -> C:\ubuntu\winboot
07-26 17:34 DEBUG  WindowsBackend: Copying C:\Users\Rachael\AppData\Local\Temp\pyl70BC.tmp\data\images\Kubuntu.ico -> C:\ubuntu\Kubuntu.ico
07-26 17:34 DEBUG  TaskList: ## Finished copy_installation_files
07-26 17:34 DEBUG  TaskList: ## Running get_iso...
07-26 17:34 DEBUG  CommonBackend: Searching for local CD
07-26 17:34 DEBUG  Distro:   checking whether C:\Users\Rachael\AppData\Local\Temp\pyl70BC.tmp is a valid Kubuntu CD
07-26 17:34 DEBUG  Distro:     does not contain C:\Users\Rachael\AppData\Local\Temp\pyl70BC.tmp\casper\filesystem.squashfs
07-26 17:34 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-26 17:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 17:34 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-26 17:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 17:34 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-26 17:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 17:34 DEBUG  CommonBackend: Searching for local ISO
07-26 17:34 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
07-26 17:34 DEBUG  TaskList: New task get_metalink
07-26 17:34 DEBUG  TaskList: ### Running get_metalink...
07-26 17:34 DEBUG  downloader: downloading releases.ubuntu.com/kubuntu/9.04/kubuntu-9.04-desktop-i386.metalink > C:\ubuntu\install
07-26 17:34 ERROR  CommonBackend: Cannot download metalink file releases.ubuntu.com/kubuntu/9.04/kubuntu-9.04-desktop-i386.metalink err=[Errno 2] Local file does not exist: C:\Users\Rachael\AppData\Local\Temp\pyl70BC.tmp\releases.ubuntu.com\kubuntu\9.04\kubuntu-9.04-desktop-i386.metalink
07-26 17:34 DEBUG  downloader: downloading http://cdimage.ubuntu.com/kubuntu/daily-live/current/jaunty-desktop-amd64.metalink > C:\ubuntu\install
07-26 17:34 ERROR  CommonBackend: Cannot download metalink file2 http://cdimage.ubuntu.com/kubuntu/daily-live/current/jaunty-desktop-amd64.metalink err=[Errno 14] HTTP Error 404: Not Found
07-26 17:34 DEBUG  TaskList: ### Finished get_metalink
07-26 17:34 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
07-26 17:34 DEBUG  TaskList: # Cancelling tasklist
07-26 17:34 ERROR  root: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 129, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
Exception: Cannot download the metalink and therefore the ISO
07-26 17:34 DEBUG  TaskList: # Finished tasklist
07-26 17:35 INFO   root: === wubi 9.04 rev129 ===
07-26 17:35 DEBUG  root: Logfile is c:\users\rachael\appdata\local\temp\wubi-9.04-rev129.log
07-26 17:35 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Rachael\\Downloads\\wubi.exe"']
07-26 17:35 DEBUG  CommonBackend: data_dir=C:\Users\Rachael\AppData\Local\Temp\pyl41E0.tmp\data
07-26 17:35 DEBUG  WindowsBackend: 7z=C:\Users\Rachael\AppData\Local\Temp\pyl41E0.tmp\bin\7z.exe
07-26 17:35 DEBUG  CommonBackend: Fetching basic info...
07-26 17:35 DEBUG  CommonBackend: original_exe=C:\Users\Rachael\Downloads\wubi.exe
07-26 17:35 DEBUG  CommonBackend: platform=win32
07-26 17:35 DEBUG  CommonBackend: osname=nt
07-26 17:35 DEBUG  CommonBackend: language=en_US
07-26 17:35 DEBUG  CommonBackend: encoding=cp1252
07-26 17:35 DEBUG  WindowsBackend: arch=amd64
07-26 17:35 DEBUG  CommonBackend: Parsing isolist=C:\Users\Rachael\AppData\Local\Temp\pyl41E0.tmp\data\isolist.ini
07-26 17:35 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-26 17:35 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-26 17:35 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-26 17:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-26 17:35 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-26 17:35 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-26 17:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-26 17:35 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-26 17:35 DEBUG  WindowsBackend: Fetching host info...
07-26 17:35 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-26 17:35 DEBUG  WindowsBackend: windows version=vista
07-26 17:35 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
07-26 17:35 DEBUG  WindowsBackend: windows_sp=None
07-26 17:35 DEBUG  WindowsBackend: windows_build=7100
07-26 17:35 DEBUG  WindowsBackend: gmt=-5
07-26 17:35 DEBUG  WindowsBackend: country=US
07-26 17:35 DEBUG  WindowsBackend: timezone=America/New_York
07-26 17:35 DEBUG  WindowsBackend: windows_username=Rachael
07-26 17:35 DEBUG  WindowsBackend: user_full_name=Rachael
07-26 17:35 DEBUG  WindowsBackend: user_directory=Rachael
07-26 17:35 DEBUG  WindowsBackend: windows_language_code=1033
07-26 17:35 DEBUG  WindowsBackend: windows_language=English
07-26 17:35 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) 64 X2 Mobile Technology TL-58
07-26 17:35 DEBUG  WindowsBackend: bootloader=vista
07-26 17:35 DEBUG  WindowsBackend: system_drive=Drive(C: hd 59558.1796875 mb free )
07-26 17:35 DEBUG  WindowsBackend: drive=Drive(C: hd 59558.1796875 mb free )
07-26 17:35 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
07-26 17:35 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
07-26 17:35 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
07-26 17:35 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
07-26 17:35 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
07-26 17:35 DEBUG  WindowsBackend: previous_distro_name=Kubuntu
07-26 17:35 DEBUG  WindowsBackend: keyboard_id=67699721
07-26 17:35 DEBUG  WindowsBackend: keyboard_layout=us
07-26 17:35 DEBUG  WindowsBackend: keyboard_variant=
07-26 17:35 DEBUG  CommonBackend: locale=en_US.UTF-8
07-26 17:35 DEBUG  WindowsBackend: total_memory_mb=1982.92578125
07-26 17:35 DEBUG  CommonBackend: Searching ISOs on USB devices
07-26 17:35 DEBUG  CommonBackend: Searching for local CDs
07-26 17:35 DEBUG  Distro:   checking whether C:\Users\Rachael\AppData\Local\Temp\pyl41E0.tmp is a valid Ubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain C:\Users\Rachael\AppData\Local\Temp\pyl41E0.tmp\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether C:\Users\Rachael\AppData\Local\Temp\pyl41E0.tmp is a valid Ubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain C:\Users\Rachael\AppData\Local\Temp\pyl41E0.tmp\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether C:\Users\Rachael\AppData\Local\Temp\pyl41E0.tmp is a valid Kubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain C:\Users\Rachael\AppData\Local\Temp\pyl41E0.tmp\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether C:\Users\Rachael\AppData\Local\Temp\pyl41E0.tmp is a valid Kubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain C:\Users\Rachael\AppData\Local\Temp\pyl41E0.tmp\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether C:\Users\Rachael\AppData\Local\Temp\pyl41E0.tmp is a valid Xubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain C:\Users\Rachael\AppData\Local\Temp\pyl41E0.tmp\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether C:\Users\Rachael\AppData\Local\Temp\pyl41E0.tmp is a valid Xubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain C:\Users\Rachael\AppData\Local\Temp\pyl41E0.tmp\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether C:\Users\Rachael\AppData\Local\Temp\pyl41E0.tmp is a valid Mythbuntu CD
07-26 17:35 DEBUG  Distro:     does not contain C:\Users\Rachael\AppData\Local\Temp\pyl41E0.tmp\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether C:\Users\Rachael\AppData\Local\Temp\pyl41E0.tmp is a valid Mythbuntu CD
07-26 17:35 DEBUG  Distro:     does not contain C:\Users\Rachael\AppData\Local\Temp\pyl41E0.tmp\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-26 17:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-26 17:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-26 17:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-26 17:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-26 17:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-26 17:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 17:35 INFO   root: Already installed, running the uninstaller...
07-26 17:35 INFO   root: Running the uninstaller...
07-26 17:35 INFO   CommonBackend: This is the uninstaller running
07-26 17:35 DEBUG  WindowsFrontend: __init__...
07-26 17:35 DEBUG  WindowsFrontend: on_init...
07-26 17:35 INFO   root: Received settings
07-26 17:35 DEBUG  TaskList: # Running tasklist...
07-26 17:35 DEBUG  TaskList: ## Running Backup ISO...
07-26 17:35 DEBUG  TaskList: ## Finished Backup ISO
07-26 17:35 DEBUG  TaskList: ## Running Remove bootloader entry...
07-26 17:35 DEBUG  WindowsBackend: Could not find bcd id
07-26 17:35 DEBUG  WindowsBackend: undo_bootini C:
07-26 17:35 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 59558.1796875 mb free )
07-26 17:35 DEBUG  TaskList: ## Finished Remove bootloader entry
07-26 17:35 DEBUG  TaskList: ## Running Remove target dir...
07-26 17:35 DEBUG  CommonBackend: Deleting C:\ubuntu
07-26 17:35 DEBUG  TaskList: ## Finished Remove target dir
07-26 17:35 DEBUG  TaskList: ## Running Remove registry key...
07-26 17:35 DEBUG  TaskList: ## Finished Remove registry key
07-26 17:35 DEBUG  TaskList: # Finished tasklist
07-26 17:35 INFO   root: Almost finished uninstalling
07-26 17:35 INFO   root: Finished uninstallation
07-26 17:35 DEBUG  CommonBackend: Fetching basic info...
07-26 17:35 DEBUG  CommonBackend: original_exe=C:\Users\Rachael\Downloads\wubi.exe
07-26 17:35 DEBUG  CommonBackend: platform=win32
07-26 17:35 DEBUG  CommonBackend: osname=nt
07-26 17:35 DEBUG  CommonBackend: language=en_US
07-26 17:35 DEBUG  CommonBackend: encoding=cp1252
07-26 17:35 DEBUG  WindowsBackend: arch=amd64
07-26 17:35 DEBUG  CommonBackend: Parsing isolist=C:\Users\Rachael\AppData\Local\Temp\pyl41E0.tmp\data\isolist.ini
07-26 17:35 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-26 17:35 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-26 17:35 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-26 17:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-26 17:35 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-26 17:35 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-26 17:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-26 17:35 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-26 17:35 DEBUG  WindowsBackend: Fetching host info...
07-26 17:35 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-26 17:35 DEBUG  WindowsBackend: windows version=vista
07-26 17:35 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
07-26 17:35 DEBUG  WindowsBackend: windows_sp=None
07-26 17:35 DEBUG  WindowsBackend: windows_build=7100
07-26 17:35 DEBUG  WindowsBackend: gmt=-5
07-26 17:35 DEBUG  WindowsBackend: country=US
07-26 17:35 DEBUG  WindowsBackend: timezone=America/New_York
07-26 17:35 DEBUG  WindowsBackend: windows_username=Rachael
07-26 17:35 DEBUG  WindowsBackend: user_full_name=Rachael
07-26 17:35 DEBUG  WindowsBackend: user_directory=Rachael
07-26 17:35 DEBUG  WindowsBackend: windows_language_code=1033
07-26 17:35 DEBUG  WindowsBackend: windows_language=English
07-26 17:35 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) 64 X2 Mobile Technology TL-58
07-26 17:35 DEBUG  WindowsBackend: bootloader=vista
07-26 17:35 DEBUG  WindowsBackend: system_drive=Drive(C: hd 59560.0703125 mb free )
07-26 17:35 DEBUG  WindowsBackend: drive=Drive(C: hd 59560.0703125 mb free )
07-26 17:35 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
07-26 17:35 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
07-26 17:35 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
07-26 17:35 DEBUG  WindowsBackend: uninstaller_path=None
07-26 17:35 DEBUG  WindowsBackend: previous_target_dir=None
07-26 17:35 DEBUG  WindowsBackend: previous_distro_name=None
07-26 17:35 DEBUG  WindowsBackend: keyboard_id=67699721
07-26 17:35 DEBUG  WindowsBackend: keyboard_layout=us
07-26 17:35 DEBUG  WindowsBackend: keyboard_variant=
07-26 17:35 DEBUG  CommonBackend: locale=en_US.UTF-8
07-26 17:35 DEBUG  WindowsBackend: total_memory_mb=1982.92578125
07-26 17:35 DEBUG  CommonBackend: Searching ISOs on USB devices
07-26 17:35 DEBUG  CommonBackend: Searching for local CDs
07-26 17:35 DEBUG  Distro:   checking whether C:\Users\Rachael\AppData\Local\Temp\pyl41E0.tmp is a valid Ubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain C:\Users\Rachael\AppData\Local\Temp\pyl41E0.tmp\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether C:\Users\Rachael\AppData\Local\Temp\pyl41E0.tmp is a valid Ubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain C:\Users\Rachael\AppData\Local\Temp\pyl41E0.tmp\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether C:\Users\Rachael\AppData\Local\Temp\pyl41E0.tmp is a valid Kubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain C:\Users\Rachael\AppData\Local\Temp\pyl41E0.tmp\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether C:\Users\Rachael\AppData\Local\Temp\pyl41E0.tmp is a valid Kubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain C:\Users\Rachael\AppData\Local\Temp\pyl41E0.tmp\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether C:\Users\Rachael\AppData\Local\Temp\pyl41E0.tmp is a valid Xubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain C:\Users\Rachael\AppData\Local\Temp\pyl41E0.tmp\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether C:\Users\Rachael\AppData\Local\Temp\pyl41E0.tmp is a valid Xubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain C:\Users\Rachael\AppData\Local\Temp\pyl41E0.tmp\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether C:\Users\Rachael\AppData\Local\Temp\pyl41E0.tmp is a valid Mythbuntu CD
07-26 17:35 DEBUG  Distro:     does not contain C:\Users\Rachael\AppData\Local\Temp\pyl41E0.tmp\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether C:\Users\Rachael\AppData\Local\Temp\pyl41E0.tmp is a valid Mythbuntu CD
07-26 17:35 DEBUG  Distro:     does not contain C:\Users\Rachael\AppData\Local\Temp\pyl41E0.tmp\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-26 17:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-26 17:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-26 17:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-26 17:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-26 17:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-26 17:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 17:35 INFO   root: Running the installer...
07-26 17:35 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=10000MB, distro_name=Kubuntu, language=English, username=rachael
07-26 17:35 INFO   root: Received settings
07-26 17:35 DEBUG  TaskList: # Running tasklist...
07-26 17:35 DEBUG  TaskList: ## Running select_target_dir...
07-26 17:35 INFO   WindowsBackend: Installing into C:\ubuntu
07-26 17:35 DEBUG  TaskList: ## Finished select_target_dir
07-26 17:35 DEBUG  TaskList: ## Running create_dir_structure...
07-26 17:35 DEBUG  CommonBackend: Creating dir C:\ubuntu
07-26 17:35 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
07-26 17:35 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
07-26 17:35 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
07-26 17:35 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
07-26 17:35 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
07-26 17:35 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
07-26 17:35 DEBUG  TaskList: ## Finished create_dir_structure
07-26 17:35 DEBUG  TaskList: ## Running uncompress_target_dir...
07-26 17:35 DEBUG  TaskList: ## Finished uncompress_target_dir
07-26 17:35 DEBUG  TaskList: ## Running create_uninstaller...
07-26 17:35 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Rachael\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
07-26 17:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
07-26 17:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
07-26 17:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Kubuntu
07-26 17:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Kubuntu.ico
07-26 17:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev129
07-26 17:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Kubuntu
07-26 17:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.kubuntu.org
07-26 17:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
07-26 17:35 DEBUG  TaskList: ## Finished create_uninstaller
07-26 17:35 DEBUG  TaskList: ## Running copy_installation_files...
07-26 17:35 DEBUG  WindowsBackend: Copying C:\Users\Rachael\AppData\Local\Temp\pyl41E0.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
07-26 17:35 DEBUG  WindowsBackend: Copying C:\Users\Rachael\AppData\Local\Temp\pyl41E0.tmp\winboot -> C:\ubuntu\winboot
07-26 17:35 DEBUG  WindowsBackend: Copying C:\Users\Rachael\AppData\Local\Temp\pyl41E0.tmp\data\images\Kubuntu.ico -> C:\ubuntu\Kubuntu.ico
07-26 17:35 DEBUG  TaskList: ## Finished copy_installation_files
07-26 17:35 DEBUG  TaskList: ## Running get_iso...
07-26 17:35 DEBUG  CommonBackend: Searching for local CD
07-26 17:35 DEBUG  Distro:   checking whether C:\Users\Rachael\AppData\Local\Temp\pyl41E0.tmp is a valid Kubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain C:\Users\Rachael\AppData\Local\Temp\pyl41E0.tmp\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 17:35 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-26 17:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 17:35 DEBUG  CommonBackend: Searching for local ISO
07-26 17:35 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
07-26 17:35 DEBUG  TaskList: New task get_metalink
07-26 17:35 DEBUG  TaskList: ### Running get_metalink...
07-26 17:35 DEBUG  downloader: downloading releases.ubuntu.com/kubuntu/9.04/kubuntu-9.04-desktop-i386.metalink > C:\ubuntu\install
07-26 17:35 ERROR  CommonBackend: Cannot download metalink file releases.ubuntu.com/kubuntu/9.04/kubuntu-9.04-desktop-i386.metalink err=[Errno 2] Local file does not exist: C:\Users\Rachael\AppData\Local\Temp\pyl41E0.tmp\releases.ubuntu.com\kubuntu\9.04\kubuntu-9.04-desktop-i386.metalink
07-26 17:35 DEBUG  downloader: downloading http://cdimage.ubuntu.com/kubuntu/daily-live/current/jaunty-desktop-amd64.metalink > C:\ubuntu\install
07-26 17:35 ERROR  CommonBackend: Cannot download metalink file2 http://cdimage.ubuntu.com/kubuntu/daily-live/current/jaunty-desktop-amd64.metalink err=[Errno 14] HTTP Error 404: Not Found
07-26 17:35 DEBUG  TaskList: ### Finished get_metalink
07-26 17:35 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
07-26 17:35 DEBUG  TaskList: # Cancelling tasklist
07-26 17:35 DEBUG  TaskList: # Finished tasklist
07-26 17:35 ERROR  root: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 129, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
Exception: Cannot download the metalink and therefore the ISO
07-26 17:41 INFO   root: === wubi 9.04 rev129 ===
07-26 17:41 DEBUG  root: Logfile is c:\users\rachael\appdata\local\temp\wubi-9.04-rev129.log
07-26 17:41 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Rachael\\Downloads\\wubi.exe"']
07-26 17:41 DEBUG  CommonBackend: data_dir=C:\Users\Rachael\AppData\Local\Temp\pyl7520.tmp\data
07-26 17:41 DEBUG  WindowsBackend: 7z=C:\Users\Rachael\AppData\Local\Temp\pyl7520.tmp\bin\7z.exe
07-26 17:41 DEBUG  CommonBackend: Fetching basic info...
07-26 17:41 DEBUG  CommonBackend: original_exe=C:\Users\Rachael\Downloads\wubi.exe
07-26 17:41 DEBUG  CommonBackend: platform=win32
07-26 17:41 DEBUG  CommonBackend: osname=nt
07-26 17:41 DEBUG  CommonBackend: language=en_US
07-26 17:41 DEBUG  CommonBackend: encoding=cp1252
07-26 17:41 DEBUG  WindowsBackend: arch=amd64
07-26 17:41 DEBUG  CommonBackend: Parsing isolist=C:\Users\Rachael\AppData\Local\Temp\pyl7520.tmp\data\isolist.ini
07-26 17:41 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-26 17:41 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-26 17:41 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-26 17:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-26 17:41 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-26 17:41 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-26 17:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-26 17:41 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-26 17:41 DEBUG  WindowsBackend: Fetching host info...
07-26 17:41 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-26 17:41 DEBUG  WindowsBackend: windows version=vista
07-26 17:41 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
07-26 17:41 DEBUG  WindowsBackend: windows_sp=None
07-26 17:41 DEBUG  WindowsBackend: windows_build=7100
07-26 17:41 DEBUG  WindowsBackend: gmt=-5
07-26 17:41 DEBUG  WindowsBackend: country=US
07-26 17:41 DEBUG  WindowsBackend: timezone=America/New_York
07-26 17:41 DEBUG  WindowsBackend: windows_username=Rachael
07-26 17:41 DEBUG  WindowsBackend: user_full_name=Rachael
07-26 17:41 DEBUG  WindowsBackend: user_directory=Rachael
07-26 17:41 DEBUG  WindowsBackend: windows_language_code=1033
07-26 17:41 DEBUG  WindowsBackend: windows_language=English
07-26 17:41 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) 64 X2 Mobile Technology TL-58
07-26 17:41 DEBUG  WindowsBackend: bootloader=vista
07-26 17:41 DEBUG  WindowsBackend: system_drive=Drive(C: hd 59557.5820313 mb free )
07-26 17:41 DEBUG  WindowsBackend: drive=Drive(C: hd 59557.5820313 mb free )
07-26 17:41 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
07-26 17:41 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
07-26 17:41 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
07-26 17:41 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
07-26 17:41 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
07-26 17:41 DEBUG  WindowsBackend: previous_distro_name=Kubuntu
07-26 17:41 DEBUG  WindowsBackend: keyboard_id=67699721
07-26 17:41 DEBUG  WindowsBackend: keyboard_layout=us
07-26 17:41 DEBUG  WindowsBackend: keyboard_variant=
07-26 17:41 DEBUG  CommonBackend: locale=en_US.UTF-8
07-26 17:41 DEBUG  WindowsBackend: total_memory_mb=1982.92578125
07-26 17:41 DEBUG  CommonBackend: Searching ISOs on USB devices
07-26 17:41 DEBUG  CommonBackend: Searching for local CDs
07-26 17:41 DEBUG  Distro:   checking whether C:\Users\Rachael\AppData\Local\Temp\pyl7520.tmp is a valid Ubuntu CD
07-26 17:41 DEBUG  Distro:     does not contain C:\Users\Rachael\AppData\Local\Temp\pyl7520.tmp\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether C:\Users\Rachael\AppData\Local\Temp\pyl7520.tmp is a valid Ubuntu CD
07-26 17:41 DEBUG  Distro:     does not contain C:\Users\Rachael\AppData\Local\Temp\pyl7520.tmp\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether C:\Users\Rachael\AppData\Local\Temp\pyl7520.tmp is a valid Kubuntu CD
07-26 17:41 DEBUG  Distro:     does not contain C:\Users\Rachael\AppData\Local\Temp\pyl7520.tmp\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether C:\Users\Rachael\AppData\Local\Temp\pyl7520.tmp is a valid Kubuntu CD
07-26 17:41 DEBUG  Distro:     does not contain C:\Users\Rachael\AppData\Local\Temp\pyl7520.tmp\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether C:\Users\Rachael\AppData\Local\Temp\pyl7520.tmp is a valid Xubuntu CD
07-26 17:41 DEBUG  Distro:     does not contain C:\Users\Rachael\AppData\Local\Temp\pyl7520.tmp\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether C:\Users\Rachael\AppData\Local\Temp\pyl7520.tmp is a valid Xubuntu CD
07-26 17:41 DEBUG  Distro:     does not contain C:\Users\Rachael\AppData\Local\Temp\pyl7520.tmp\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether C:\Users\Rachael\AppData\Local\Temp\pyl7520.tmp is a valid Mythbuntu CD
07-26 17:41 DEBUG  Distro:     does not contain C:\Users\Rachael\AppData\Local\Temp\pyl7520.tmp\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether C:\Users\Rachael\AppData\Local\Temp\pyl7520.tmp is a valid Mythbuntu CD
07-26 17:41 DEBUG  Distro:     does not contain C:\Users\Rachael\AppData\Local\Temp\pyl7520.tmp\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-26 17:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-26 17:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-26 17:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-26 17:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-26 17:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-26 17:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-26 17:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-26 17:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-26 17:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-26 17:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-26 17:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-26 17:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-26 17:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-26 17:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-26 17:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-26 17:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-26 17:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-26 17:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-26 17:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-26 17:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-26 17:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-26 17:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-26 17:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-26 17:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 17:41 INFO   root: Already installed, running the uninstaller...
07-26 17:41 INFO   root: Running the uninstaller...
07-26 17:41 INFO   CommonBackend: This is the uninstaller running
07-26 17:41 DEBUG  WindowsFrontend: __init__...
07-26 17:41 DEBUG  WindowsFrontend: on_init...
07-26 17:41 INFO   root: Received settings
07-26 17:41 DEBUG  TaskList: # Running tasklist...
07-26 17:41 DEBUG  TaskList: ## Running Backup ISO...
07-26 17:41 DEBUG  TaskList: ## Finished Backup ISO
07-26 17:41 DEBUG  TaskList: ## Running Remove bootloader entry...
07-26 17:41 DEBUG  WindowsBackend: Could not find bcd id
07-26 17:41 DEBUG  WindowsBackend: undo_bootini C:
07-26 17:41 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 59557.5820313 mb free )
07-26 17:41 DEBUG  TaskList: ## Finished Remove bootloader entry
07-26 17:41 DEBUG  TaskList: ## Running Remove target dir...
07-26 17:41 DEBUG  CommonBackend: Deleting C:\ubuntu
07-26 17:41 DEBUG  TaskList: ## Finished Remove target dir
07-26 17:41 DEBUG  TaskList: ## Running Remove registry key...
07-26 17:41 DEBUG  TaskList: ## Finished Remove registry key
07-26 17:41 DEBUG  TaskList: # Finished tasklist
07-26 17:41 INFO   root: Almost finished uninstalling
07-26 17:41 INFO   root: Finished uninstallation
07-26 17:41 DEBUG  CommonBackend: Fetching basic info...
07-26 17:41 DEBUG  CommonBackend: original_exe=C:\Users\Rachael\Downloads\wubi.exe
07-26 17:41 DEBUG  CommonBackend: platform=win32
07-26 17:41 DEBUG  CommonBackend: osname=nt
07-26 17:41 DEBUG  CommonBackend: language=en_US
07-26 17:41 DEBUG  CommonBackend: encoding=cp1252
07-26 17:41 DEBUG  WindowsBackend: arch=amd64
07-26 17:41 DEBUG  CommonBackend: Parsing isolist=C:\Users\Rachael\AppData\Local\Temp\pyl7520.tmp\data\isolist.ini
07-26 17:41 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-26 17:41 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-26 17:41 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-26 17:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-26 17:41 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-26 17:41 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-26 17:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-26 17:41 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-26 17:41 DEBUG  WindowsBackend: Fetching host info...
07-26 17:41 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-26 17:41 DEBUG  WindowsBackend: windows version=vista
07-26 17:41 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
07-26 17:41 DEBUG  WindowsBackend: windows_sp=None
07-26 17:41 DEBUG  WindowsBackend: windows_build=7100
07-26 17:41 DEBUG  WindowsBackend: gmt=-5
07-26 17:41 DEBUG  WindowsBackend: country=US
07-26 17:41 DEBUG  WindowsBackend: timezone=America/New_York
07-26 17:41 DEBUG  WindowsBackend: windows_username=Rachael
07-26 17:41 DEBUG  WindowsBackend: user_full_name=Rachael
07-26 17:41 DEBUG  WindowsBackend: user_directory=Rachael
07-26 17:41 DEBUG  WindowsBackend: windows_language_code=1033
07-26 17:41 DEBUG  WindowsBackend: windows_language=English
07-26 17:41 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) 64 X2 Mobile Technology TL-58
07-26 17:41 DEBUG  WindowsBackend: bootloader=vista
07-26 17:41 DEBUG  WindowsBackend: system_drive=Drive(C: hd 59559.484375 mb free )
07-26 17:41 DEBUG  WindowsBackend: drive=Drive(C: hd 59559.484375 mb free )
07-26 17:41 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
07-26 17:41 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
07-26 17:41 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
07-26 17:41 DEBUG  WindowsBackend: uninstaller_path=None
07-26 17:41 DEBUG  WindowsBackend: previous_target_dir=None
07-26 17:41 DEBUG  WindowsBackend: previous_distro_name=None
07-26 17:41 DEBUG  WindowsBackend: keyboard_id=67699721
07-26 17:41 DEBUG  WindowsBackend: keyboard_layout=us
07-26 17:41 DEBUG  WindowsBackend: keyboard_variant=
07-26 17:41 DEBUG  CommonBackend: locale=en_US.UTF-8
07-26 17:41 DEBUG  WindowsBackend: total_memory_mb=1982.92578125
07-26 17:41 DEBUG  CommonBackend: Searching ISOs on USB devices
07-26 17:41 DEBUG  CommonBackend: Searching for local CDs
07-26 17:41 DEBUG  Distro:   checking whether C:\Users\Rachael\AppData\Local\Temp\pyl7520.tmp is a valid Ubuntu CD
07-26 17:41 DEBUG  Distro:     does not contain C:\Users\Rachael\AppData\Local\Temp\pyl7520.tmp\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether C:\Users\Rachael\AppData\Local\Temp\pyl7520.tmp is a valid Ubuntu CD
07-26 17:41 DEBUG  Distro:     does not contain C:\Users\Rachael\AppData\Local\Temp\pyl7520.tmp\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether C:\Users\Rachael\AppData\Local\Temp\pyl7520.tmp is a valid Kubuntu CD
07-26 17:41 DEBUG  Distro:     does not contain C:\Users\Rachael\AppData\Local\Temp\pyl7520.tmp\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether C:\Users\Rachael\AppData\Local\Temp\pyl7520.tmp is a valid Kubuntu CD
07-26 17:41 DEBUG  Distro:     does not contain C:\Users\Rachael\AppData\Local\Temp\pyl7520.tmp\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether C:\Users\Rachael\AppData\Local\Temp\pyl7520.tmp is a valid Xubuntu CD
07-26 17:41 DEBUG  Distro:     does not contain C:\Users\Rachael\AppData\Local\Temp\pyl7520.tmp\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether C:\Users\Rachael\AppData\Local\Temp\pyl7520.tmp is a valid Xubuntu CD
07-26 17:41 DEBUG  Distro:     does not contain C:\Users\Rachael\AppData\Local\Temp\pyl7520.tmp\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether C:\Users\Rachael\AppData\Local\Temp\pyl7520.tmp is a valid Mythbuntu CD
07-26 17:41 DEBUG  Distro:     does not contain C:\Users\Rachael\AppData\Local\Temp\pyl7520.tmp\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether C:\Users\Rachael\AppData\Local\Temp\pyl7520.tmp is a valid Mythbuntu CD
07-26 17:41 DEBUG  Distro:     does not contain C:\Users\Rachael\AppData\Local\Temp\pyl7520.tmp\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-26 17:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-26 17:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-26 17:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-26 17:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-26 17:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-26 17:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-26 17:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-26 17:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-26 17:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-26 17:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-26 17:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-26 17:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-26 17:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-26 17:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-26 17:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-26 17:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-26 17:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-26 17:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-26 17:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-26 17:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-26 17:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-26 17:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-26 17:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 17:41 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-26 17:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 17:41 INFO   root: Running the installer...
07-26 17:41 INFO   WindowsFrontend: Operation cancelled
07-26 17:41 DEBUG  WindowsFrontend: frontend.quit
07-26 17:41 DEBUG  WindowsFrontend: frontend.on_quit
07-26 17:41 DEBUG  root: application.on_quit
07-26 17:41 INFO   root: sys.exit
```

Thanks!

---

