---
title: "Newb here, having installation problems"
date: 2009-08-17
forum: Installation &amp; Upgrades
---

### Post by gonedioital on 2009-08-17
Hello, 

I'm new to Linux, and trying to install Desktop version 9.04, 32 bit Linux Ubuntu.

I've burned the ISO to a disc using Roxio 2009 Platinum, and verified the disc, which was successful.  

I'm attempting to install inside Windows, so I can have the dual boot option.

Every time I install I get the following error.

"Permission Denied" Please see the log file in G:\Users\Andrew\Local\Appdata\temp\wubi-9.04-rev128.log

I've tried to run the installation as an Administrator, and that didn't work, and I've set the compatibility mode to Windows XP SP2, and that didn't work either.

Any ideas? I'm fresh out, but would really like to get this working.

_**System Specs**_
Dell Dimension 8400
Intel 4 3.0 GHZ Processor
3 GB Memory
ATI Radeon HD 2600 PRO 512 MB Video Card
SB Live Audigy 2 Sound Card
Philips DVD Burner
LG Blu-Ray Reader/DVD Burner
3.5" Floppy Drive
Windows Vista Home Edition
100GB HD (29 GB Free Space)
75 GB HD (30 GB Free Space)
Wireless Ethernet Card


Here's the contents of the log file.


> 08-16 23:39 INFO   root: === wubi 9.04 rev128 ===
08-16 23:39 DEBUG  root: Logfile is g:\users\andrew\appdata\local\temp\wubi-9.04-rev128.log
08-16 23:39 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\ubuntu\\uninstall-wubi.exe"']
08-16 23:39 DEBUG  CommonBackend: data_dir=G:\Users\Andrew\AppData\Local\Temp\pylBC4D.tmp\data
08-16 23:39 DEBUG  WindowsBackend: 7z=G:\Users\Andrew\AppData\Local\Temp\pylBC4D.tmp\bin\7z.exe
08-16 23:39 DEBUG  CommonBackend: Fetching basic info...
08-16 23:39 DEBUG  CommonBackend: original_exe=G:\ubuntu\uninstall-wubi.exe
08-16 23:39 DEBUG  CommonBackend: platform=win32
08-16 23:39 DEBUG  CommonBackend: osname=nt
08-16 23:39 DEBUG  CommonBackend: language=en_US
08-16 23:39 DEBUG  CommonBackend: encoding=cp1252
08-16 23:39 DEBUG  WindowsBackend: arch=amd64
08-16 23:39 DEBUG  CommonBackend: Parsing isolist=G:\Users\Andrew\AppData\Local\Temp\pylBC4D.tmp\data\isolist.ini
08-16 23:39 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-16 23:39 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-16 23:39 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-16 23:39 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-16 23:39 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-16 23:39 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-16 23:39 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-16 23:39 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-16 23:39 DEBUG  WindowsBackend: Fetching host info...
08-16 23:39 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-16 23:39 DEBUG  WindowsBackend: windows version=vista
08-16 23:39 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Basic
08-16 23:39 DEBUG  WindowsBackend: windows_sp=Service Pack 1
08-16 23:39 DEBUG  WindowsBackend: windows_build=6001
08-16 23:39 DEBUG  WindowsBackend: gmt=-6
08-16 23:39 DEBUG  WindowsBackend: country=US
08-16 23:39 DEBUG  WindowsBackend: timezone=America/Chicago
08-16 23:39 DEBUG  WindowsBackend: windows_username=Andrew
08-16 23:39 DEBUG  WindowsBackend: user_full_name=Andrew
08-16 23:39 DEBUG  WindowsBackend: user_directory=Andrew
08-16 23:39 DEBUG  WindowsBackend: windows_language_code=1033
08-16 23:39 DEBUG  WindowsBackend: windows_language=English
08-16 23:39 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) 4 CPU 3.00GHz
08-16 23:39 DEBUG  WindowsBackend: bootloader=vista
08-16 23:39 DEBUG  WindowsBackend: system_drive=Drive(G: hd 31349.4414063 mb free )
08-16 23:39 DEBUG  WindowsBackend: drive=Drive(C: hd 30225.578125 mb free ntfs)
08-16 23:39 DEBUG  WindowsBackend: drive=Drive(D: hd 0.0 mb free )
08-16 23:39 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
08-16 23:39 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
08-16 23:39 DEBUG  WindowsBackend: drive=Drive(G: hd 31349.4414063 mb free )
08-16 23:39 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
08-16 23:39 DEBUG  WindowsBackend: uninstaller_path=G:\ubuntu\uninstall-wubi.exe
08-16 23:39 DEBUG  WindowsBackend: previous_target_dir=G:\ubuntu
08-16 23:39 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
08-16 23:39 DEBUG  WindowsBackend: keyboard_id=67699721
08-16 23:39 DEBUG  WindowsBackend: keyboard_layout=us
08-16 23:39 DEBUG  WindowsBackend: keyboard_variant=
08-16 23:39 DEBUG  CommonBackend: locale=en_US.UTF-8
08-16 23:39 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
08-16 23:39 DEBUG  CommonBackend: Searching ISOs on USB devices
08-16 23:39 DEBUG  CommonBackend: Searching for local CDs
08-16 23:39 DEBUG  Distro:   checking whether C:\ is a valid Ubuntu CD
08-16 23:39 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
08-16 23:39 DEBUG  Distro:   checking whether C:\ is a valid Ubuntu CD
08-16 23:39 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
08-16 23:39 DEBUG  Distro:   checking whether C:\ is a valid Kubuntu CD
08-16 23:39 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
08-16 23:39 DEBUG  Distro:   checking whether C:\ is a valid Kubuntu CD
08-16 23:39 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
08-16 23:39 DEBUG  Distro:   checking whether C:\ is a valid Xubuntu CD
08-16 23:39 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
08-16 23:39 DEBUG  Distro:   checking whether C:\ is a valid Xubuntu CD
08-16 23:39 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
08-16 23:39 DEBUG  Distro:   checking whether C:\ is a valid Mythbuntu CD
08-16 23:39 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
08-16 23:39 DEBUG  Distro:   checking whether C:\ is a valid Mythbuntu CD
08-16 23:39 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
08-16 23:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-16 23:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-16 23:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-16 23:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-16 23:39 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-16 23:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-16 23:39 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-16 23:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-16 23:39 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-16 23:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-16 23:39 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-16 23:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-16 23:39 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-16 23:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-16 23:39 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-16 23:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-16 23:39 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-16 23:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-16 23:39 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-16 23:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-16 23:39 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-16 23:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-16 23:39 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-16 23:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-16 23:39 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-16 23:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-16 23:39 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-16 23:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-16 23:39 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-16 23:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-16 23:39 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-16 23:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-16 23:39 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-16 23:39 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
08-16 23:39 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
08-16 23:39 INFO   Distro: Found a valid CD for Ubuntu: F:\
08-16 23:39 INFO   root: Running the uninstaller...
08-16 23:39 INFO   CommonBackend: This is the uninstaller running
08-16 23:39 DEBUG  WindowsFrontend: __init__...
08-16 23:39 DEBUG  WindowsFrontend: on_init...
08-16 23:40 INFO   root: Received settings
08-16 23:40 DEBUG  TaskList: # Running tasklist...
08-16 23:40 DEBUG  TaskList: ## Running Backup ISO...
08-16 23:40 DEBUG  TaskList: ## Finished Backup ISO
08-16 23:40 DEBUG  TaskList: ## Running Remove bootloader entry...
08-16 23:40 DEBUG  WindowsBackend: Could not find bcd id
08-16 23:40 DEBUG  WindowsBackend: undo_bootini C:
08-16 23:40 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 30225.578125 mb free ntfs)
08-16 23:40 DEBUG  WindowsBackend: undo_bootini D:
08-16 23:40 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 0.0 mb free )
08-16 23:40 DEBUG  WindowsBackend: undo_bootini G:
08-16 23:40 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 31349.4414063 mb free )
08-16 23:40 DEBUG  WindowsBackend: undo_bootini H:
08-16 23:40 DEBUG  WindowsBackend: undo_configsys Drive(H: removable 0.0 mb free )
08-16 23:40 DEBUG  TaskList: ## Finished Remove bootloader entry
08-16 23:40 DEBUG  TaskList: ## Running Remove target dir...
08-16 23:40 DEBUG  CommonBackend: Deleting G:\ubuntu
08-16 23:40 DEBUG  TaskList: ## Finished Remove target dir
08-16 23:40 DEBUG  TaskList: ## Running Remove registry key...
08-16 23:40 DEBUG  TaskList: ## Finished Remove registry key
08-16 23:40 DEBUG  TaskList: # Finished tasklist
08-16 23:40 INFO   root: Almost finished uninstalling
08-16 23:40 INFO   root: Finished uninstallation
08-16 23:40 DEBUG  root: application.quit
08-16 23:40 DEBUG  WindowsFrontend: frontend.quit
08-16 23:40 DEBUG  WindowsFrontend: frontend.on_quit
08-16 23:40 DEBUG  root: application.on_quit
08-16 23:40 INFO   root: sys.exit
08-16 23:40 INFO   root: === wubi 9.04 rev128 ===
08-16 23:40 DEBUG  root: Logfile is g:\users\andrew\appdata\local\temp\wubi-9.04-rev128.log
08-16 23:40 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
08-16 23:40 DEBUG  CommonBackend: data_dir=G:\Users\Andrew\AppData\Local\Temp\pyl195A.tmp\data
08-16 23:40 DEBUG  WindowsBackend: 7z=G:\Users\Andrew\AppData\Local\Temp\pyl195A.tmp\bin\7z.exe
08-16 23:40 DEBUG  CommonBackend: Fetching basic info...
08-16 23:40 DEBUG  CommonBackend: original_exe=F:\wubi.exe
08-16 23:40 DEBUG  CommonBackend: platform=win32
08-16 23:40 DEBUG  CommonBackend: osname=nt
08-16 23:40 DEBUG  CommonBackend: language=en_US
08-16 23:40 DEBUG  CommonBackend: encoding=cp1252
08-16 23:40 DEBUG  WindowsBackend: arch=amd64
08-16 23:40 DEBUG  CommonBackend: Parsing isolist=G:\Users\Andrew\AppData\Local\Temp\pyl195A.tmp\data\isolist.ini
08-16 23:40 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-16 23:40 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-16 23:40 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-16 23:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-16 23:40 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-16 23:40 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-16 23:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-16 23:40 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-16 23:40 DEBUG  WindowsBackend: Fetching host info...
08-16 23:40 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-16 23:40 DEBUG  WindowsBackend: windows version=xp
08-16 23:40 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
08-16 23:40 DEBUG  WindowsBackend: windows_sp=Service Pack 2
08-16 23:40 DEBUG  WindowsBackend: windows_build=2600
08-16 23:40 DEBUG  WindowsBackend: gmt=-6
08-16 23:40 DEBUG  WindowsBackend: country=US
08-16 23:40 DEBUG  WindowsBackend: timezone=America/Chicago
08-16 23:40 DEBUG  WindowsBackend: windows_username=Andrew
08-16 23:40 DEBUG  WindowsBackend: user_full_name=Andrew
08-16 23:40 DEBUG  WindowsBackend: user_directory=Andrew
08-16 23:40 DEBUG  WindowsBackend: windows_language_code=1033
08-16 23:40 DEBUG  WindowsBackend: windows_language=English
08-16 23:40 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) 4 CPU 3.00GHz
08-16 23:40 DEBUG  WindowsBackend: bootloader=xp
08-16 23:40 DEBUG  WindowsBackend: system_drive=Drive(G: hd 32047.59375 mb free )
08-16 23:40 DEBUG  WindowsBackend: drive=Drive(C: hd 30225.578125 mb free ntfs)
08-16 23:40 DEBUG  WindowsBackend: drive=Drive(D: hd 0.0 mb free )
08-16 23:40 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
08-16 23:40 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
08-16 23:40 DEBUG  WindowsBackend: drive=Drive(G: hd 32048.09375 mb free )
08-16 23:40 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
08-16 23:40 DEBUG  WindowsBackend: uninstaller_path=None
08-16 23:40 DEBUG  WindowsBackend: previous_target_dir=None
08-16 23:40 DEBUG  WindowsBackend: previous_distro_name=None
08-16 23:40 DEBUG  WindowsBackend: keyboard_id=67699721
08-16 23:40 DEBUG  WindowsBackend: keyboard_layout=us
08-16 23:40 DEBUG  WindowsBackend: keyboard_variant=
08-16 23:40 DEBUG  CommonBackend: locale=en_US.UTF-8
08-16 23:40 DEBUG  WindowsBackend: total_memory_mb=1023.99999905
08-16 23:40 DEBUG  CommonBackend: Searching ISOs on USB devices
08-16 23:40 DEBUG  CommonBackend: Searching for local CDs
08-16 23:40 DEBUG  Distro:   checking whether C:\ is a valid Ubuntu CD
08-16 23:40 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
08-16 23:40 DEBUG  Distro:   checking whether C:\ is a valid Ubuntu CD
08-16 23:40 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
08-16 23:40 DEBUG  Distro:   checking whether C:\ is a valid Kubuntu CD
08-16 23:40 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
08-16 23:40 DEBUG  Distro:   checking whether C:\ is a valid Kubuntu CD
08-16 23:40 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
08-16 23:40 DEBUG  Distro:   checking whether C:\ is a valid Xubuntu CD
08-16 23:40 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
08-16 23:40 DEBUG  Distro:   checking whether C:\ is a valid Xubuntu CD
08-16 23:40 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
08-16 23:40 DEBUG  Distro:   checking whether C:\ is a valid Mythbuntu CD
08-16 23:40 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
08-16 23:40 DEBUG  Distro:   checking whether C:\ is a valid Mythbuntu CD
08-16 23:40 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
08-16 23:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-16 23:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-16 23:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-16 23:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-16 23:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-16 23:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-16 23:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-16 23:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-16 23:40 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-16 23:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-16 23:40 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-16 23:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-16 23:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-16 23:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-16 23:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-16 23:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-16 23:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-16 23:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-16 23:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-16 23:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-16 23:40 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-16 23:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-16 23:40 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-16 23:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-16 23:40 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-16 23:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-16 23:40 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-16 23:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-16 23:40 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-16 23:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-16 23:40 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-16 23:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-16 23:40 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-16 23:40 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
08-16 23:40 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
08-16 23:40 INFO   Distro: Found a valid CD for Ubuntu: F:\
08-16 23:40 INFO   root: Running the CD menu...
08-16 23:40 DEBUG  WindowsFrontend: __init__...
08-16 23:40 DEBUG  WindowsFrontend: on_init...
08-16 23:40 INFO   WindowsFrontend: Operation cancelled
08-16 23:40 DEBUG  WindowsFrontend: frontend.quit
08-16 23:40 DEBUG  WindowsFrontend: frontend.on_quit
08-16 23:40 DEBUG  root: application.on_quit
08-16 23:40 INFO   root: sys.exit
08-16 23:40 INFO   root: === wubi 9.04 rev128 ===
08-16 23:40 DEBUG  root: Logfile is g:\users\andrew\appdata\local\temp\wubi-9.04-rev128.log
08-16 23:40 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
08-16 23:40 DEBUG  CommonBackend: data_dir=G:\Users\Andrew\AppData\Local\Temp\pylA479.tmp\data
08-16 23:40 DEBUG  WindowsBackend: 7z=G:\Users\Andrew\AppData\Local\Temp\pylA479.tmp\bin\7z.exe
08-16 23:40 DEBUG  CommonBackend: Fetching basic info...
08-16 23:40 DEBUG  CommonBackend: original_exe=F:\wubi.exe
08-16 23:40 DEBUG  CommonBackend: platform=win32
08-16 23:40 DEBUG  CommonBackend: osname=nt
08-16 23:40 DEBUG  CommonBackend: language=en_US
08-16 23:40 DEBUG  CommonBackend: encoding=cp1252
08-16 23:40 DEBUG  WindowsBackend: arch=amd64
08-16 23:40 DEBUG  CommonBackend: Parsing isolist=G:\Users\Andrew\AppData\Local\Temp\pylA479.tmp\data\isolist.ini
08-16 23:40 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-16 23:40 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-16 23:40 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-16 23:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-16 23:40 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-16 23:40 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-16 23:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-16 23:40 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-16 23:40 DEBUG  WindowsBackend: Fetching host info...
08-16 23:40 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-16 23:40 DEBUG  WindowsBackend: windows version=xp
08-16 23:40 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
08-16 23:40 DEBUG  WindowsBackend: windows_sp=Service Pack 2
08-16 23:40 DEBUG  WindowsBackend: windows_build=2600
08-16 23:40 DEBUG  WindowsBackend: gmt=-6
08-16 23:40 DEBUG  WindowsBackend: country=US
08-16 23:40 DEBUG  WindowsBackend: timezone=America/Chicago
08-16 23:40 DEBUG  WindowsBackend: windows_username=Andrew
08-16 23:40 DEBUG  WindowsBackend: user_full_name=Andrew
08-16 23:40 DEBUG  WindowsBackend: user_directory=Andrew
08-16 23:40 DEBUG  WindowsBackend: windows_language_code=1033
08-16 23:40 DEBUG  WindowsBackend: windows_language=English
08-16 23:40 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) 4 CPU 3.00GHz
08-16 23:40 DEBUG  WindowsBackend: bootloader=xp
08-16 23:40 DEBUG  WindowsBackend: system_drive=Drive(G: hd 32046.7460938 mb free )
08-16 23:40 DEBUG  WindowsBackend: drive=Drive(C: hd 30225.578125 mb free ntfs)
08-16 23:40 DEBUG  WindowsBackend: drive=Drive(D: hd 0.0 mb free )
08-16 23:40 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
08-16 23:40 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
08-16 23:40 DEBUG  WindowsBackend: drive=Drive(G: hd 32046.6835938 mb free )
08-16 23:40 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
08-16 23:40 DEBUG  WindowsBackend: uninstaller_path=None
08-16 23:40 DEBUG  WindowsBackend: previous_target_dir=None
08-16 23:40 DEBUG  WindowsBackend: previous_distro_name=None
08-16 23:40 DEBUG  WindowsBackend: keyboard_id=67699721
08-16 23:40 DEBUG  WindowsBackend: keyboard_layout=us
08-16 23:40 DEBUG  WindowsBackend: keyboard_variant=
08-16 23:40 DEBUG  CommonBackend: locale=en_US.UTF-8
08-16 23:40 DEBUG  WindowsBackend: total_memory_mb=1023.99999905
08-16 23:40 DEBUG  CommonBackend: Searching ISOs on USB devices
08-16 23:40 DEBUG  CommonBackend: Searching for local CDs
08-16 23:40 DEBUG  Distro:   checking whether C:\ is a valid Ubuntu CD
08-16 23:40 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
08-16 23:40 DEBUG  Distro:   checking whether C:\ is a valid Ubuntu CD
08-16 23:40 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
08-16 23:40 DEBUG  Distro:   checking whether C:\ is a valid Kubuntu CD
08-16 23:40 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
08-16 23:40 DEBUG  Distro:   checking whether C:\ is a valid Kubuntu CD
08-16 23:40 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
08-16 23:40 DEBUG  Distro:   checking whether C:\ is a valid Xubuntu CD
08-16 23:40 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
08-16 23:40 DEBUG  Distro:   checking whether C:\ is a valid Xubuntu CD
08-16 23:40 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
08-16 23:40 DEBUG  Distro:   checking whether C:\ is a valid Mythbuntu CD
08-16 23:40 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
08-16 23:40 DEBUG  Distro:   checking whether C:\ is a valid Mythbuntu CD
08-16 23:40 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
08-16 23:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-16 23:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-16 23:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-16 23:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-16 23:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-16 23:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-16 23:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-16 23:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-16 23:40 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-16 23:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-16 23:40 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-16 23:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-16 23:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-16 23:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-16 23:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-16 23:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-16 23:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-16 23:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-16 23:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-16 23:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-16 23:40 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-16 23:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-16 23:40 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-16 23:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-16 23:40 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-16 23:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-16 23:40 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-16 23:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-16 23:40 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-16 23:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-16 23:40 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-16 23:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-16 23:40 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-16 23:40 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
08-16 23:40 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
08-16 23:40 INFO   Distro: Found a valid CD for Ubuntu: F:\
08-16 23:40 INFO   root: Running the CD menu...
08-16 23:40 DEBUG  WindowsFrontend: __init__...
08-16 23:40 DEBUG  WindowsFrontend: on_init...
08-16 23:41 INFO   root: CD menu finished
08-16 23:41 INFO   root: Running the installer...
08-16 23:41 DEBUG  WinuiInstallationPage: target_drive=G:, installation_size=20000MB, distro_name=Ubuntu, language=English, username=andrew
08-16 23:41 INFO   root: Received settings
08-16 23:41 DEBUG  TaskList: # Running tasklist...
08-16 23:41 DEBUG  TaskList: ## Running select_target_dir...
08-16 23:41 INFO   WindowsBackend: Installing into G:\ubuntu
08-16 23:41 DEBUG  TaskList: ## Finished select_target_dir
08-16 23:41 DEBUG  TaskList: ## Running create_dir_structure...
08-16 23:41 DEBUG  CommonBackend: Creating dir G:\ubuntu
08-16 23:41 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks
08-16 23:41 DEBUG  CommonBackend: Creating dir G:\ubuntu\install
08-16 23:41 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot
08-16 23:41 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot
08-16 23:41 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot\grub
08-16 23:41 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot\grub
08-16 23:41 DEBUG  TaskList: ## Finished create_dir_structure
08-16 23:41 DEBUG  TaskList: ## Running uncompress_target_dir...
08-16 23:41 DEBUG  TaskList: ## Finished uncompress_target_dir
08-16 23:41 DEBUG  TaskList: ## Running create_uninstaller...
08-16 23:41 DEBUG  WindowsBackend: Copying uninstaller F:\wubi.exe -> G:\ubuntu\uninstall-wubi.exe
08-16 23:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString G:\ubuntu\uninstall-wubi.exe
08-16 23:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir G:\ubuntu
08-16 23:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
08-16 23:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon G:\ubuntu\Ubuntu.ico
08-16 23:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
08-16 23:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
08-16 23:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
08-16 23:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
08-16 23:41 DEBUG  TaskList: ## Finished create_uninstaller
08-16 23:41 DEBUG  TaskList: ## Running copy_installation_files...
08-16 23:41 DEBUG  WindowsBackend: Copying G:\Users\Andrew\AppData\Local\Temp\pylA479.tmp\data\custom-installation -> G:\ubuntu\install\custom-installation
08-16 23:41 DEBUG  WindowsBackend: Copying G:\Users\Andrew\AppData\Local\Temp\pylA479.tmp\winboot -> G:\ubuntu\winboot
08-16 23:41 DEBUG  WindowsBackend: Copying G:\Users\Andrew\AppData\Local\Temp\pylA479.tmp\data\images\Ubuntu.ico -> G:\ubuntu\Ubuntu.ico
08-16 23:41 DEBUG  TaskList: ## Finished copy_installation_files
08-16 23:41 DEBUG  TaskList: ## Running get_iso...
08-16 23:41 DEBUG  TaskList: New task copy_file
08-16 23:41 DEBUG  TaskList: ### Running copy_file...
08-16 23:45 DEBUG  TaskList: ### Finished copy_file
08-16 23:45 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 13] Permission denied
08-16 23:45 DEBUG  TaskList: # Cancelling tasklist
08-16 23:45 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 13] Permission denied
08-16 23:45 DEBUG  TaskList: New task check_iso
08-16 23:45 DEBUG  CommonBackend: Searching for local ISO
08-16 23:45 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
08-16 23:45 DEBUG  TaskList: New task get_metalink
08-16 23:45 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
08-16 23:45 DEBUG  TaskList: # Cancelling tasklist
08-16 23:45 DEBUG  TaskList: # Finished tasklist


---

### Post by pandanuma on 2009-08-17
from first line of your quote, looks like you are using wubi to install ubuntu...
not familiar with that but hopefully you are...

check out
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) 
second paragraph has wubi link...

I dual boot ubuntu and windows vista and used the above link to determine how I would set up my partitions [not the wubi link]
although you dont seem to have a lot of free space on any one of your harddrives you could squeeze it in and give it a test drive...

you will have to shrink a partition in windows to free up some space for ubuntu
you should be able to do that within windows vista [25 gig??]
please check ubuntu's minimum install requirements...
pop in the ubuntu instalation disk and reboot
when the install page loads, click the install button and follow the instructions
it will ask you to partition the drive, read carefully and select dual boot button
make a new partition about 5 gigs for / (root) and select 'mount as root'?
make a new partition for /swap 3gigs
make a new partition for /home using whats left of your unused partition
carry on with the install

***this is just a quick idea of what you have to do, hope its helpful ***

---

