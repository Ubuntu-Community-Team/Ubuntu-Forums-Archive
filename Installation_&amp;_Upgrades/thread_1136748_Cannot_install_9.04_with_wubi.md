---
title: "Cannot install 9.04 with wubi"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by vikrant_me on 2009-04-25
I am an administrator on my system trying to install on a NTFS drive.My installation of ubuntu within windows fails with the errors below: 

```
04-24 14:47 INFO   root: === wubi 9.04 rev128 ===
04-24 14:47 DEBUG  root: Logfile is c:\docume~1\vicky\locals~1\temp\wubi-9.04-rev128.log
04-24 14:47 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
04-24 14:47 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl15B.tmp\data
04-24 14:47 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl15B.tmp\bin\7z.exe
04-24 14:47 DEBUG  CommonBackend: Fetching basic info...
04-24 14:47 DEBUG  CommonBackend: original_exe=D:\wubi.exe
04-24 14:47 DEBUG  CommonBackend: platform=win32
04-24 14:47 DEBUG  CommonBackend: osname=nt
04-24 14:47 DEBUG  CommonBackend: language=en_US
04-24 14:47 DEBUG  CommonBackend: encoding=cp1252
04-24 14:47 DEBUG  WindowsBackend: arch=amd64
04-24 14:47 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl15B.tmp\data\isolist.ini
04-24 14:47 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-24 14:47 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-24 14:47 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-24 14:47 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-24 14:47 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-24 14:47 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-24 14:47 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-24 14:47 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-24 14:47 DEBUG  WindowsBackend: Fetching host info...
04-24 14:47 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-24 14:47 DEBUG  WindowsBackend: windows version=xp
04-24 14:47 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-24 14:47 DEBUG  WindowsBackend: windows_sp=Service Pack 3
04-24 14:47 DEBUG  WindowsBackend: windows_build=2600
04-24 14:47 DEBUG  WindowsBackend: gmt=5
04-24 14:47 DEBUG  WindowsBackend: country=US
04-24 14:47 DEBUG  WindowsBackend: timezone=America/New_York
04-24 14:47 DEBUG  WindowsBackend: windows_username=vicky
04-24 14:47 DEBUG  WindowsBackend: user_full_name=vicky
04-24 14:47 DEBUG  WindowsBackend: user_directory=vicky
04-24 14:47 DEBUG  WindowsBackend: windows_language_code=1033
04-24 14:47 DEBUG  WindowsBackend: windows_language=English
04-24 14:47 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 3600+
04-24 14:47 DEBUG  WindowsBackend: bootloader=xp
04-24 14:47 DEBUG  WindowsBackend: system_drive=Drive(C: hd 24383.0585938 mb free )
04-24 14:47 DEBUG  WindowsBackend: drive=Drive(C: hd 24383.0585938 mb free )
04-24 14:47 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
04-24 14:47 DEBUG  WindowsBackend: drive=Drive(E: hd 370435.746094 mb free ntfs)
04-24 14:47 DEBUG  WindowsBackend: drive=Drive(F: hd 28485.0898438 mb free ntfs)
04-24 14:47 DEBUG  WindowsBackend: drive=Drive(I: hd 211135.753906 mb free ntfs)
04-24 14:47 DEBUG  WindowsBackend: drive=Drive(J: hd 29694.9335938 mb free ntfs)
04-24 14:47 DEBUG  WindowsBackend: uninstaller_path=None
04-24 14:47 DEBUG  WindowsBackend: previous_target_dir=None
04-24 14:47 DEBUG  WindowsBackend: previous_distro_name=None
04-24 14:47 DEBUG  WindowsBackend: keyboard_id=67699721
04-24 14:47 DEBUG  WindowsBackend: keyboard_layout=us
04-24 14:47 DEBUG  WindowsBackend: keyboard_variant=
04-24 14:47 DEBUG  CommonBackend: locale=en_US.UTF-8
04-24 14:47 DEBUG  WindowsBackend: total_memory_mb=1471.35546875
04-24 14:47 DEBUG  CommonBackend: Searching ISOs on USB devices
04-24 14:47 DEBUG  CommonBackend: Searching for local CDs
04-24 14:47 DEBUG  Distro:   checking whether C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl15B.tmp is a valid Ubuntu CD
04-24 14:47 DEBUG  Distro:     does not contain C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl15B.tmp\casper\filesystem.squashfs
04-24 14:47 DEBUG  Distro:   checking whether C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl15B.tmp is a valid Ubuntu CD
04-24 14:47 DEBUG  Distro:     does not contain C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl15B.tmp\casper\filesystem.squashfs
04-24 14:47 DEBUG  Distro:   checking whether C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl15B.tmp is a valid Kubuntu CD
04-24 14:47 DEBUG  Distro:     does not contain C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl15B.tmp\casper\filesystem.squashfs
04-24 14:47 DEBUG  Distro:   checking whether C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl15B.tmp is a valid Kubuntu CD
04-24 14:47 DEBUG  Distro:     does not contain C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl15B.tmp\casper\filesystem.squashfs
04-24 14:47 DEBUG  Distro:   checking whether C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl15B.tmp is a valid Xubuntu CD
04-24 14:47 DEBUG  Distro:     does not contain C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl15B.tmp\casper\filesystem.squashfs
04-24 14:47 DEBUG  Distro:   checking whether C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl15B.tmp is a valid Xubuntu CD
04-24 14:47 DEBUG  Distro:     does not contain C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl15B.tmp\casper\filesystem.squashfs
04-24 14:47 DEBUG  Distro:   checking whether C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl15B.tmp is a valid Mythbuntu CD
04-24 14:47 DEBUG  Distro:     does not contain C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl15B.tmp\casper\filesystem.squashfs
04-24 14:47 DEBUG  Distro:   checking whether C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl15B.tmp is a valid Mythbuntu CD
04-24 14:47 DEBUG  Distro:     does not contain C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl15B.tmp\casper\filesystem.squashfs
04-24 14:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-24 14:47 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
04-24 14:47 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
04-24 14:47 INFO   Distro: Found a valid CD for Ubuntu: D:\
04-24 14:47 INFO   root: Running the CD menu...
04-24 14:47 DEBUG  WindowsFrontend: __init__...
04-24 14:47 DEBUG  WindowsFrontend: on_init...
04-25 01:17 INFO   root: === wubi 9.04 rev128 ===
04-25 01:17 DEBUG  root: Logfile is c:\docume~1\vicky\locals~1\temp\wubi-9.04-rev128.log
04-25 01:17 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
04-25 01:17 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl7.tmp\data
04-25 01:17 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl7.tmp\bin\7z.exe
04-25 01:17 DEBUG  CommonBackend: Fetching basic info...
04-25 01:17 DEBUG  CommonBackend: original_exe=D:\wubi.exe
04-25 01:17 DEBUG  CommonBackend: platform=win32
04-25 01:17 DEBUG  CommonBackend: osname=nt
04-25 01:17 DEBUG  CommonBackend: language=en_US
04-25 01:17 DEBUG  CommonBackend: encoding=cp1252
04-25 01:17 DEBUG  WindowsBackend: arch=amd64
04-25 01:17 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl7.tmp\data\isolist.ini
04-25 01:17 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-25 01:17 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-25 01:17 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-25 01:17 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-25 01:17 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-25 01:17 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-25 01:17 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-25 01:17 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-25 01:17 DEBUG  WindowsBackend: Fetching host info...
04-25 01:17 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-25 01:17 DEBUG  WindowsBackend: windows version=xp
04-25 01:17 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-25 01:17 DEBUG  WindowsBackend: windows_sp=Service Pack 3
04-25 01:17 DEBUG  WindowsBackend: windows_build=2600
04-25 01:17 DEBUG  WindowsBackend: gmt=5
04-25 01:17 DEBUG  WindowsBackend: country=US
04-25 01:17 DEBUG  WindowsBackend: timezone=America/New_York
04-25 01:17 DEBUG  WindowsBackend: windows_username=vicky
04-25 01:17 DEBUG  WindowsBackend: user_full_name=vicky
04-25 01:17 DEBUG  WindowsBackend: user_directory=vicky
04-25 01:17 DEBUG  WindowsBackend: windows_language_code=1033
04-25 01:17 DEBUG  WindowsBackend: windows_language=English
04-25 01:17 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 3600+
04-25 01:17 DEBUG  WindowsBackend: bootloader=xp
04-25 01:17 DEBUG  WindowsBackend: system_drive=Drive(C: hd 24414.7421875 mb free )
04-25 01:17 DEBUG  WindowsBackend: drive=Drive(C: hd 24414.7421875 mb free )
04-25 01:17 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
04-25 01:17 DEBUG  WindowsBackend: drive=Drive(E: hd 369736.796875 mb free ntfs)
04-25 01:17 DEBUG  WindowsBackend: drive=Drive(F: hd 28485.1015625 mb free ntfs)
04-25 01:17 DEBUG  WindowsBackend: drive=Drive(I: hd 211135.765625 mb free ntfs)
04-25 01:17 DEBUG  WindowsBackend: drive=Drive(J: hd 29698.4453125 mb free ntfs)
04-25 01:17 DEBUG  WindowsBackend: uninstaller_path=None
04-25 01:17 DEBUG  WindowsBackend: previous_target_dir=None
04-25 01:17 DEBUG  WindowsBackend: previous_distro_name=None
04-25 01:17 DEBUG  WindowsBackend: keyboard_id=67699721
04-25 01:17 DEBUG  WindowsBackend: keyboard_layout=us
04-25 01:17 DEBUG  WindowsBackend: keyboard_variant=
04-25 01:17 DEBUG  CommonBackend: locale=en_US.UTF-8
04-25 01:17 DEBUG  WindowsBackend: total_memory_mb=1471.35546875
04-25 01:17 DEBUG  CommonBackend: Searching ISOs on USB devices
04-25 01:17 DEBUG  CommonBackend: Searching for local CDs
04-25 01:17 DEBUG  Distro:   checking whether C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl7.tmp is a valid Ubuntu CD
04-25 01:17 DEBUG  Distro:     does not contain C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
04-25 01:17 DEBUG  Distro:   checking whether C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl7.tmp is a valid Ubuntu CD
04-25 01:17 DEBUG  Distro:     does not contain C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
04-25 01:17 DEBUG  Distro:   checking whether C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl7.tmp is a valid Kubuntu CD
04-25 01:17 DEBUG  Distro:     does not contain C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
04-25 01:17 DEBUG  Distro:   checking whether C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl7.tmp is a valid Kubuntu CD
04-25 01:17 DEBUG  Distro:     does not contain C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
04-25 01:17 DEBUG  Distro:   checking whether C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl7.tmp is a valid Xubuntu CD
04-25 01:17 DEBUG  Distro:     does not contain C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
04-25 01:17 DEBUG  Distro:   checking whether C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl7.tmp is a valid Xubuntu CD
04-25 01:17 DEBUG  Distro:     does not contain C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
04-25 01:17 DEBUG  Distro:   checking whether C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl7.tmp is a valid Mythbuntu CD
04-25 01:17 DEBUG  Distro:     does not contain C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
04-25 01:17 DEBUG  Distro:   checking whether C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl7.tmp is a valid Mythbuntu CD
04-25 01:17 DEBUG  Distro:     does not contain C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
04-25 01:17 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-25 01:17 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
04-25 01:17 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
04-25 01:17 INFO   Distro: Found a valid CD for Ubuntu: D:\
04-25 01:17 INFO   root: Running the CD menu...
04-25 01:17 DEBUG  WindowsFrontend: __init__...
04-25 01:17 DEBUG  WindowsFrontend: on_init...
04-25 16:45 INFO   root: === wubi 9.04 rev128 ===
04-25 16:45 DEBUG  root: Logfile is c:\docume~1\vicky\locals~1\temp\wubi-9.04-rev128.log
04-25 16:45 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
04-25 16:45 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl1C.tmp\data
04-25 16:45 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl1C.tmp\bin\7z.exe
04-25 16:45 DEBUG  CommonBackend: Fetching basic info...
04-25 16:45 DEBUG  CommonBackend: original_exe=D:\wubi.exe
04-25 16:45 DEBUG  CommonBackend: platform=win32
04-25 16:45 DEBUG  CommonBackend: osname=nt
04-25 16:45 DEBUG  CommonBackend: language=en_US
04-25 16:45 DEBUG  CommonBackend: encoding=cp1252
04-25 16:45 DEBUG  WindowsBackend: arch=amd64
04-25 16:45 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl1C.tmp\data\isolist.ini
04-25 16:45 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-25 16:45 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-25 16:45 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-25 16:45 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-25 16:45 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-25 16:45 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-25 16:45 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-25 16:45 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-25 16:45 DEBUG  WindowsBackend: Fetching host info...
04-25 16:45 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-25 16:45 DEBUG  WindowsBackend: windows version=xp
04-25 16:45 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-25 16:45 DEBUG  WindowsBackend: windows_sp=Service Pack 3
04-25 16:45 DEBUG  WindowsBackend: windows_build=2600
04-25 16:45 DEBUG  WindowsBackend: gmt=5
04-25 16:45 DEBUG  WindowsBackend: country=US
04-25 16:45 DEBUG  WindowsBackend: timezone=America/New_York
04-25 16:45 DEBUG  WindowsBackend: windows_username=vicky
04-25 16:45 DEBUG  WindowsBackend: user_full_name=vicky
04-25 16:45 DEBUG  WindowsBackend: user_directory=vicky
04-25 16:45 DEBUG  WindowsBackend: windows_language_code=1033
04-25 16:45 DEBUG  WindowsBackend: windows_language=English
04-25 16:45 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 3600+
04-25 16:45 DEBUG  WindowsBackend: bootloader=xp
04-25 16:45 DEBUG  WindowsBackend: system_drive=Drive(C: hd 24429.8476563 mb free )
04-25 16:45 DEBUG  WindowsBackend: drive=Drive(C: hd 24429.8476563 mb free )
04-25 16:45 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
04-25 16:45 DEBUG  WindowsBackend: drive=Drive(E: hd 341300.714844 mb free ntfs)
04-25 16:45 DEBUG  WindowsBackend: drive=Drive(F: hd 28485.1015625 mb free ntfs)
04-25 16:45 DEBUG  WindowsBackend: drive=Drive(I: hd 211141.421875 mb free ntfs)
04-25 16:45 DEBUG  WindowsBackend: drive=Drive(J: hd 29698.4453125 mb free ntfs)
04-25 16:45 DEBUG  WindowsBackend: uninstaller_path=None
04-25 16:45 DEBUG  WindowsBackend: previous_target_dir=None
04-25 16:45 DEBUG  WindowsBackend: previous_distro_name=None
04-25 16:45 DEBUG  WindowsBackend: keyboard_id=67699721
04-25 16:45 DEBUG  WindowsBackend: keyboard_layout=us
04-25 16:45 DEBUG  WindowsBackend: keyboard_variant=
04-25 16:45 DEBUG  CommonBackend: locale=en_US.UTF-8
04-25 16:45 DEBUG  WindowsBackend: total_memory_mb=1471.35546875
04-25 16:45 DEBUG  CommonBackend: Searching ISOs on USB devices
04-25 16:45 DEBUG  CommonBackend: Searching for local CDs
04-25 16:45 DEBUG  Distro:   checking whether C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl1C.tmp is a valid Ubuntu CD
04-25 16:45 DEBUG  Distro:     does not contain C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl1C.tmp\casper\filesystem.squashfs
04-25 16:45 DEBUG  Distro:   checking whether C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl1C.tmp is a valid Ubuntu CD
04-25 16:45 DEBUG  Distro:     does not contain C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl1C.tmp\casper\filesystem.squashfs
04-25 16:45 DEBUG  Distro:   checking whether C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl1C.tmp is a valid Kubuntu CD
04-25 16:45 DEBUG  Distro:     does not contain C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl1C.tmp\casper\filesystem.squashfs
04-25 16:45 DEBUG  Distro:   checking whether C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl1C.tmp is a valid Kubuntu CD
04-25 16:45 DEBUG  Distro:     does not contain C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl1C.tmp\casper\filesystem.squashfs
04-25 16:45 DEBUG  Distro:   checking whether C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl1C.tmp is a valid Xubuntu CD
04-25 16:45 DEBUG  Distro:     does not contain C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl1C.tmp\casper\filesystem.squashfs
04-25 16:45 DEBUG  Distro:   checking whether C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl1C.tmp is a valid Xubuntu CD
04-25 16:45 DEBUG  Distro:     does not contain C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl1C.tmp\casper\filesystem.squashfs
04-25 16:45 DEBUG  Distro:   checking whether C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl1C.tmp is a valid Mythbuntu CD
04-25 16:45 DEBUG  Distro:     does not contain C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl1C.tmp\casper\filesystem.squashfs
04-25 16:45 DEBUG  Distro:   checking whether C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl1C.tmp is a valid Mythbuntu CD
04-25 16:45 DEBUG  Distro:     does not contain C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl1C.tmp\casper\filesystem.squashfs
04-25 16:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-25 16:45 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
04-25 16:45 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
04-25 16:45 INFO   Distro: Found a valid CD for Ubuntu: D:\
04-25 16:45 INFO   root: Running the CD menu...
04-25 16:45 DEBUG  WindowsFrontend: __init__...
04-25 16:45 DEBUG  WindowsFrontend: on_init...
04-25 16:46 INFO   root: CD menu finished
04-25 16:46 INFO   root: Running the installer...
04-25 16:47 DEBUG  WinuiInstallationPage: target_drive=E:, installation_size=13000MB, distro_name=Ubuntu, language=English, username=vicky
04-25 16:47 INFO   root: Received settings
04-25 16:47 DEBUG  TaskList: # Running tasklist...
04-25 16:47 DEBUG  TaskList: ## Running select_target_dir...
04-25 16:47 INFO   WindowsBackend: Installing into E:\ubuntu
04-25 16:47 DEBUG  TaskList: ## Finished select_target_dir
04-25 16:47 DEBUG  TaskList: ## Running create_dir_structure...
04-25 16:47 DEBUG  CommonBackend: Creating dir E:\ubuntu
04-25 16:47 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks
04-25 16:47 DEBUG  CommonBackend: Creating dir E:\ubuntu\install
04-25 16:47 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot
04-25 16:47 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot
04-25 16:47 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot\grub
04-25 16:47 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot\grub
04-25 16:47 DEBUG  TaskList: ## Finished create_dir_structure
04-25 16:47 DEBUG  TaskList: ## Running uncompress_target_dir...
04-25 16:47 DEBUG  TaskList: ## Finished uncompress_target_dir
04-25 16:47 DEBUG  TaskList: ## Running create_uninstaller...
04-25 16:47 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> E:\ubuntu\uninstall-wubi.exe
04-25 16:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString E:\ubuntu\uninstall-wubi.exe
04-25 16:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir E:\ubuntu
04-25 16:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-25 16:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon E:\ubuntu\Ubuntu.ico
04-25 16:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
04-25 16:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-25 16:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
04-25 16:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
04-25 16:47 DEBUG  TaskList: ## Finished create_uninstaller
04-25 16:47 DEBUG  TaskList: ## Running copy_installation_files...
04-25 16:47 DEBUG  WindowsBackend: Copying C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl1C.tmp\data\custom-installation -> E:\ubuntu\install\custom-installation
04-25 16:47 DEBUG  WindowsBackend: Copying C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl1C.tmp\winboot -> E:\ubuntu\winboot
04-25 16:47 DEBUG  WindowsBackend: Copying C:\DOCUME~1\vicky\LOCALS~1\Temp\pyl1C.tmp\data\images\Ubuntu.ico -> E:\ubuntu\Ubuntu.ico
04-25 16:47 DEBUG  TaskList: ## Finished copy_installation_files
04-25 16:47 DEBUG  TaskList: ## Running get_iso...
04-25 16:47 DEBUG  TaskList: New task copy_file
04-25 16:47 DEBUG  TaskList: ### Running copy_file...
04-25 16:50 DEBUG  TaskList: ### Finished copy_file
04-25 16:50 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 13] Permission denied
04-25 16:50 DEBUG  TaskList: # Cancelling tasklist
04-25 16:50 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 13] Permission denied
04-25 16:50 DEBUG  TaskList: New task check_iso
04-25 16:50 DEBUG  CommonBackend: Searching for local ISO
04-25 16:50 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
04-25 16:50 DEBUG  TaskList: New task get_metalink
04-25 16:50 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
04-25 16:50 DEBUG  TaskList: # Cancelling tasklist
04-25 16:50 DEBUG  TaskList: # Finished tasklist

```

---

### Post by lisati on 2009-04-25
I think others have experienced a similar problem. (I kinda got sidetracked looking for the relevant information.....)

EDIT: found the thread I was looking for: [http://ubuntuforums.org/showthread.php?t=1134741](http://ubuntuforums.org/showthread.php?t=1134741) - nothing useful to report yet, I think there might be a bug that needs to be reported.

---

