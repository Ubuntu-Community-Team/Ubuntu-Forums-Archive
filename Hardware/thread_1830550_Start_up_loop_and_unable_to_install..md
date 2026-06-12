---
title: "Start up loop and unable to install."
date: 2011-08-21
forum: Hardware
---

### Post by facexscar93 on 2011-08-21
Hello everyone,
 I am a new user to Ubuntu but I am mainly capable with computers. I restart my computer with Ubuntu on a USB flash drive and it will go into the start up loop. After this i tried to install it onto my computer in a dual OS set-up, but this would not work and i would get the message...


08-19 17:48 INFO   root: === wubi 11.04 rev211 ===
08-19 17:48 DEBUG  root: Logfile is c:\users\jerren\appdata\local\temp\wubi-11.04-rev211.log
08-19 17:48 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\wubi.exe"']
08-19 17:48 DEBUG  CommonBackend: data_dir=C:\Users\jerren\AppData\Local\Temp\pyl979F.tmp\data
08-19 17:48 DEBUG  WindowsBackend: 7z=C:\Users\jerren\AppData\Local\Temp\pyl979F.tmp\bin\7z.exe
08-19 17:48 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
08-19 17:48 DEBUG  CommonBackend: Fetching basic info...
08-19 17:48 DEBUG  CommonBackend: original_exe=G:\wubi.exe
08-19 17:48 DEBUG  CommonBackend: platform=win32
08-19 17:48 DEBUG  CommonBackend: osname=nt
08-19 17:48 DEBUG  CommonBackend: language=en_US
08-19 17:48 DEBUG  CommonBackend: encoding=cp1252
08-19 17:48 DEBUG  WindowsBackend: arch=amd64
08-19 17:48 DEBUG  CommonBackend: Parsing isolist=C:\Users\jerren\AppData\Local\Temp\pyl979F.tmp\data\isolist.ini
08-19 17:48 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-19 17:48 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-19 17:48 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-19 17:48 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-19 17:48 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-19 17:48 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-19 17:48 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-19 17:48 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-19 17:48 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
08-19 17:48 DEBUG  WindowsBackend: Fetching host info...
08-19 17:48 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-19 17:48 DEBUG  WindowsBackend: windows version=vista
08-19 17:48 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Premium
08-19 17:48 DEBUG  WindowsBackend: windows_sp=None
08-19 17:48 DEBUG  WindowsBackend: windows_build=6000
08-19 17:48 DEBUG  WindowsBackend: gmt=-5
08-19 17:48 DEBUG  WindowsBackend: country=US
08-19 17:48 DEBUG  WindowsBackend: timezone=America/New_York
08-19 17:48 DEBUG  WindowsBackend: windows_username=jerren
08-19 17:48 DEBUG  WindowsBackend: user_full_name=jerren
08-19 17:48 DEBUG  WindowsBackend: user_directory=C:\Users\jerren
08-19 17:48 DEBUG  WindowsBackend: windows_language_code=1033
08-19 17:48 DEBUG  WindowsBackend: windows_language=English
08-19 17:48 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor TK-53
08-19 17:48 DEBUG  WindowsBackend: bootloader=vista
08-19 17:48 DEBUG  WindowsBackend: system_drive=Drive(C: hd 64368.1132813 mb free ntfs)
08-19 17:48 DEBUG  WindowsBackend: drive=Drive(C: hd 64368.1132813 mb free ntfs)
08-19 17:48 DEBUG  WindowsBackend: drive=Drive(D: hd 1770.39453125 mb free ntfs)
08-19 17:48 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
08-19 17:48 DEBUG  WindowsBackend: drive=Drive(F: removable 824.296875 mb free fat32)
08-19 17:48 DEBUG  WindowsBackend: drive=Drive(G: removable 7023.24804688 mb free fat32)
08-19 17:48 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
08-19 17:48 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
08-19 17:48 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
08-19 17:48 DEBUG  WindowsBackend: keyboard_id=67699721
08-19 17:48 DEBUG  WindowsBackend: keyboard_layout=us
08-19 17:48 DEBUG  WindowsBackend: keyboard_variant=
08-19 17:48 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
08-19 17:48 DEBUG  CommonBackend: locale=en_US.UTF-8
08-19 17:48 DEBUG  WindowsBackend: total_memory_mb=1982.0
08-19 17:48 DEBUG  CommonBackend: Searching ISOs on USB devices
08-19 17:48 DEBUG  CommonBackend: Searching for local CDs
08-19 17:48 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pyl979F.tmp is a valid Ubuntu CD
08-19 17:48 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pyl979F.tmp\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pyl979F.tmp is a valid Ubuntu CD
08-19 17:48 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pyl979F.tmp\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pyl979F.tmp is a valid Ubuntu Netbook CD
08-19 17:48 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pyl979F.tmp\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pyl979F.tmp is a valid Kubuntu CD
08-19 17:48 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pyl979F.tmp\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pyl979F.tmp is a valid Kubuntu CD
08-19 17:48 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pyl979F.tmp\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pyl979F.tmp is a valid Xubuntu CD
08-19 17:48 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pyl979F.tmp\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pyl979F.tmp is a valid Xubuntu CD
08-19 17:48 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pyl979F.tmp\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pyl979F.tmp is a valid Mythbuntu CD
08-19 17:48 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pyl979F.tmp\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pyl979F.tmp is a valid Mythbuntu CD
08-19 17:48 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pyl979F.tmp\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-19 17:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-19 17:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
08-19 17:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-19 17:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-19 17:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-19 17:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-19 17:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-19 17:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-19 17:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-19 17:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-19 17:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
08-19 17:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-19 17:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-19 17:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-19 17:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-19 17:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-19 17:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-19 17:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-19 17:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-19 17:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
08-19 17:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-19 17:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-19 17:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-19 17:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-19 17:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-19 17:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-19 17:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-19 17:48 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
08-19 17:48 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
08-19 17:48 INFO   Distro: Found a valid CD for Ubuntu: G:\
08-19 17:48 INFO   root: Running the CD menu...
08-19 17:48 DEBUG  WindowsFrontend: __init__...
08-19 17:48 DEBUG  WindowsFrontend: on_init...
08-19 17:48 INFO   WinuiPage: appname=wubi, localedir=C:\Users\jerren\AppData\Local\Temp\pyl979F.tmp\translations, languages=['en_US', 'en']
08-19 17:48 INFO   WinuiPage: appname=wubi, localedir=C:\Users\jerren\AppData\Local\Temp\pyl979F.tmp\translations, languages=['en_US', 'en']
08-19 17:48 INFO   root: === wubi 11.04 rev211 ===
08-19 17:48 DEBUG  root: Logfile is c:\users\jerren\appdata\local\temp\wubi-11.04-rev211.log
08-19 17:48 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\wubi.exe"']
08-19 17:48 DEBUG  CommonBackend: data_dir=C:\Users\jerren\AppData\Local\Temp\pyl979E.tmp\data
08-19 17:48 DEBUG  WindowsBackend: 7z=C:\Users\jerren\AppData\Local\Temp\pyl979E.tmp\bin\7z.exe
08-19 17:48 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
08-19 17:48 DEBUG  CommonBackend: Fetching basic info...
08-19 17:48 DEBUG  CommonBackend: original_exe=G:\wubi.exe
08-19 17:48 DEBUG  CommonBackend: platform=win32
08-19 17:48 DEBUG  CommonBackend: osname=nt
08-19 17:48 DEBUG  CommonBackend: language=en_US
08-19 17:48 DEBUG  CommonBackend: encoding=cp1252
08-19 17:48 DEBUG  WindowsBackend: arch=amd64
08-19 17:48 DEBUG  CommonBackend: Parsing isolist=C:\Users\jerren\AppData\Local\Temp\pyl979E.tmp\data\isolist.ini
08-19 17:48 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-19 17:48 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-19 17:48 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-19 17:48 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-19 17:48 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-19 17:48 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-19 17:48 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-19 17:48 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-19 17:48 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
08-19 17:48 DEBUG  WindowsBackend: Fetching host info...
08-19 17:48 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-19 17:48 DEBUG  WindowsBackend: windows version=vista
08-19 17:48 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Premium
08-19 17:48 DEBUG  WindowsBackend: windows_sp=None
08-19 17:48 DEBUG  WindowsBackend: windows_build=6000
08-19 17:48 DEBUG  WindowsBackend: gmt=-5
08-19 17:48 DEBUG  WindowsBackend: country=US
08-19 17:48 DEBUG  WindowsBackend: timezone=America/New_York
08-19 17:48 DEBUG  WindowsBackend: windows_username=jerren
08-19 17:48 DEBUG  WindowsBackend: user_full_name=jerren
08-19 17:48 DEBUG  WindowsBackend: user_directory=C:\Users\jerren
08-19 17:48 DEBUG  WindowsBackend: windows_language_code=1033
08-19 17:48 DEBUG  WindowsBackend: windows_language=English
08-19 17:48 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor TK-53
08-19 17:48 DEBUG  WindowsBackend: bootloader=vista
08-19 17:48 DEBUG  WindowsBackend: system_drive=Drive(C: hd 64367.8515625 mb free ntfs)
08-19 17:48 DEBUG  WindowsBackend: drive=Drive(C: hd 64367.8515625 mb free ntfs)
08-19 17:48 DEBUG  WindowsBackend: drive=Drive(D: hd 1770.39453125 mb free ntfs)
08-19 17:48 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
08-19 17:48 DEBUG  WindowsBackend: drive=Drive(F: removable 824.296875 mb free fat32)
08-19 17:48 DEBUG  WindowsBackend: drive=Drive(G: removable 7023.24804688 mb free fat32)
08-19 17:48 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
08-19 17:48 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
08-19 17:48 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
08-19 17:48 DEBUG  WindowsBackend: keyboard_id=67699721
08-19 17:48 DEBUG  WindowsBackend: keyboard_layout=us
08-19 17:48 DEBUG  WindowsBackend: keyboard_variant=
08-19 17:48 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
08-19 17:48 DEBUG  CommonBackend: locale=en_US.UTF-8
08-19 17:48 DEBUG  WindowsBackend: total_memory_mb=1982.0
08-19 17:48 DEBUG  CommonBackend: Searching ISOs on USB devices
08-19 17:48 DEBUG  CommonBackend: Searching for local CDs
08-19 17:48 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pyl979E.tmp is a valid Ubuntu CD
08-19 17:48 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pyl979E.tmp\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pyl979E.tmp is a valid Ubuntu CD
08-19 17:48 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pyl979E.tmp\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pyl979E.tmp is a valid Ubuntu Netbook CD
08-19 17:48 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pyl979E.tmp\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pyl979E.tmp is a valid Kubuntu CD
08-19 17:48 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pyl979E.tmp\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pyl979E.tmp is a valid Kubuntu CD
08-19 17:48 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pyl979E.tmp\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pyl979E.tmp is a valid Xubuntu CD
08-19 17:48 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pyl979E.tmp\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pyl979E.tmp is a valid Xubuntu CD
08-19 17:48 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pyl979E.tmp\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pyl979E.tmp is a valid Mythbuntu CD
08-19 17:48 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pyl979E.tmp\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pyl979E.tmp is a valid Mythbuntu CD
08-19 17:48 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pyl979E.tmp\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-19 17:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-19 17:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
08-19 17:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-19 17:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-19 17:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-19 17:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-19 17:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-19 17:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-19 17:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-19 17:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-19 17:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
08-19 17:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-19 17:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-19 17:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-19 17:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-19 17:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-19 17:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-19 17:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-19 17:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-19 17:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
08-19 17:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-19 17:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-19 17:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-19 17:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-19 17:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-19 17:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-19 17:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-19 17:48 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-19 17:48 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
08-19 17:48 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
08-19 17:48 INFO   Distro: Found a valid CD for Ubuntu: G:\
08-19 17:48 INFO   root: Running the CD menu...
08-19 17:48 DEBUG  WindowsFrontend: __init__...
08-19 17:48 DEBUG  WindowsFrontend: on_init...
08-19 17:48 INFO   WinuiPage: appname=wubi, localedir=C:\Users\jerren\AppData\Local\Temp\pyl979E.tmp\translations, languages=['en_US', 'en']
08-19 17:48 INFO   WinuiPage: appname=wubi, localedir=C:\Users\jerren\AppData\Local\Temp\pyl979E.tmp\translations, languages=['en_US', 'en']
08-19 17:48 INFO   root: CD menu finished
08-19 17:48 INFO   root: Already installed, running the uninstaller...
08-19 17:48 INFO   root: Running the uninstaller...
08-19 17:48 INFO   CommonBackend: Launching previous uninestaller C:\ubuntu\uninstall-wubi.exe
08-19 17:48 DEBUG  root: application.quit
08-19 17:48 DEBUG  WindowsFrontend: frontend.quit
08-19 17:48 DEBUG  WindowsFrontend: frontend.on_quit
08-19 17:48 DEBUG  root: application.on_quit
08-19 17:48 INFO   root: sys.exit
08-19 17:50 INFO   root: CD menu finished
08-19 17:50 INFO   root: Already installed, running the uninstaller...
08-19 17:50 INFO   root: Running the uninstaller...
08-19 17:50 INFO   CommonBackend: Launching previous uninestaller C:\ubuntu\uninstall-wubi.exe
08-19 17:50 DEBUG  root: application.quit
08-19 17:50 DEBUG  WindowsFrontend: frontend.quit
08-19 17:50 DEBUG  WindowsFrontend: frontend.on_quit
08-19 17:50 DEBUG  root: application.on_quit
08-19 17:50 INFO   root: sys.exit
08-20 22:21 INFO   root: === wubi 11.04 rev211 ===
08-20 22:21 DEBUG  root: Logfile is c:\users\jerren\appdata\local\temp\wubi-11.04-rev211.log
08-20 22:21 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\wubi.exe"']
08-20 22:21 DEBUG  CommonBackend: data_dir=C:\Users\jerren\AppData\Local\Temp\pylFA93.tmp\data
08-20 22:21 DEBUG  WindowsBackend: 7z=C:\Users\jerren\AppData\Local\Temp\pylFA93.tmp\bin\7z.exe
08-20 22:21 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
08-20 22:21 DEBUG  CommonBackend: Fetching basic info...
08-20 22:21 DEBUG  CommonBackend: original_exe=G:\wubi.exe
08-20 22:21 DEBUG  CommonBackend: platform=win32
08-20 22:21 DEBUG  CommonBackend: osname=nt
08-20 22:21 DEBUG  CommonBackend: language=en_US
08-20 22:21 DEBUG  CommonBackend: encoding=cp1252
08-20 22:21 DEBUG  WindowsBackend: arch=amd64
08-20 22:21 DEBUG  CommonBackend: Parsing isolist=C:\Users\jerren\AppData\Local\Temp\pylFA93.tmp\data\isolist.ini
08-20 22:21 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-20 22:21 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-20 22:21 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-20 22:21 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-20 22:21 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-20 22:21 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-20 22:21 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-20 22:21 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-20 22:21 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
08-20 22:21 DEBUG  WindowsBackend: Fetching host info...
08-20 22:21 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-20 22:21 DEBUG  WindowsBackend: windows version=vista
08-20 22:21 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Premium
08-20 22:21 DEBUG  WindowsBackend: windows_sp=None
08-20 22:21 DEBUG  WindowsBackend: windows_build=6000
08-20 22:21 DEBUG  WindowsBackend: gmt=-5
08-20 22:21 DEBUG  WindowsBackend: country=US
08-20 22:21 DEBUG  WindowsBackend: timezone=America/New_York
08-20 22:21 DEBUG  WindowsBackend: windows_username=jerren
08-20 22:21 DEBUG  WindowsBackend: user_full_name=jerren
08-20 22:21 DEBUG  WindowsBackend: user_directory=C:\Users\jerren
08-20 22:21 DEBUG  WindowsBackend: windows_language_code=1033
08-20 22:21 DEBUG  WindowsBackend: windows_language=English
08-20 22:21 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor TK-53
08-20 22:21 DEBUG  WindowsBackend: bootloader=vista
08-20 22:21 DEBUG  WindowsBackend: system_drive=Drive(C: hd 72247.0742188 mb free ntfs)
08-20 22:21 DEBUG  WindowsBackend: drive=Drive(C: hd 72247.0742188 mb free ntfs)
08-20 22:21 DEBUG  WindowsBackend: drive=Drive(D: hd 1770.39453125 mb free ntfs)
08-20 22:21 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
08-20 22:21 DEBUG  WindowsBackend: drive=Drive(F: removable 824.296875 mb free fat32)
08-20 22:21 DEBUG  WindowsBackend: drive=Drive(G: removable 6335.52734375 mb free fat32)
08-20 22:21 DEBUG  WindowsBackend: uninstaller_path=None
08-20 22:21 DEBUG  WindowsBackend: previous_target_dir=None
08-20 22:21 DEBUG  WindowsBackend: previous_distro_name=None
08-20 22:21 DEBUG  WindowsBackend: keyboard_id=67699721
08-20 22:21 DEBUG  WindowsBackend: keyboard_layout=us
08-20 22:21 DEBUG  WindowsBackend: keyboard_variant=
08-20 22:21 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
08-20 22:21 DEBUG  CommonBackend: locale=en_US.UTF-8
08-20 22:21 DEBUG  WindowsBackend: total_memory_mb=1982.0
08-20 22:21 DEBUG  CommonBackend: Searching ISOs on USB devices
08-20 22:21 DEBUG  Distro:   checking Ubuntu ISO G:\ubuntu-10.04.3-desktop-i386.iso
08-20 22:21 DEBUG  WindowsBackend:   extracting .disk\info from G:\ubuntu-10.04.3-desktop-i386.iso
08-20 22:21 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.3 LTS "Lucid Lynx" - Release i386 (20110720.1)
08-20 22:21 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.3', 'build': '20110720.1', 'codename': 'Lucid Lynx', 'arch': 'i386'}
08-20 22:21 DEBUG  Distro: wrong version: 10.04.3 != 11.04
08-20 22:21 DEBUG  Distro:   checking Ubuntu ISO G:\ubuntu-10.04.3-desktop-i386.iso
08-20 22:21 DEBUG  Distro: wrong version: 10.04.3 != 11.04
08-20 22:21 DEBUG  Distro:   checking Ubuntu Netbook ISO G:\ubuntu-10.04.3-desktop-i386.iso
08-20 22:21 DEBUG  Distro: wrong name: Ubuntu != Ubuntu Netbook
08-20 22:21 DEBUG  Distro:   checking Kubuntu ISO G:\ubuntu-10.04.3-desktop-i386.iso
08-20 22:21 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
08-20 22:21 DEBUG  Distro:   checking Kubuntu ISO G:\ubuntu-10.04.3-desktop-i386.iso
08-20 22:21 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
08-20 22:21 DEBUG  Distro:   checking Xubuntu ISO G:\ubuntu-10.04.3-desktop-i386.iso
08-20 22:21 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
08-20 22:21 DEBUG  Distro:   checking Xubuntu ISO G:\ubuntu-10.04.3-desktop-i386.iso
08-20 22:21 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
08-20 22:21 DEBUG  Distro:   checking Mythbuntu ISO G:\ubuntu-10.04.3-desktop-i386.iso
08-20 22:21 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
08-20 22:21 DEBUG  Distro:   checking Mythbuntu ISO G:\ubuntu-10.04.3-desktop-i386.iso
08-20 22:21 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
08-20 22:21 DEBUG  CommonBackend: Searching for local CDs
08-20 22:21 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pylFA93.tmp is a valid Ubuntu CD
08-20 22:21 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pylFA93.tmp\casper\filesystem.squashfs
08-20 22:21 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pylFA93.tmp is a valid Ubuntu CD
08-20 22:21 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pylFA93.tmp\casper\filesystem.squashfs
08-20 22:21 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pylFA93.tmp is a valid Ubuntu Netbook CD
08-20 22:21 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pylFA93.tmp\casper\filesystem.squashfs
08-20 22:21 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pylFA93.tmp is a valid Kubuntu CD
08-20 22:21 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pylFA93.tmp\casper\filesystem.squashfs
08-20 22:21 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pylFA93.tmp is a valid Kubuntu CD
08-20 22:21 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pylFA93.tmp\casper\filesystem.squashfs
08-20 22:21 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pylFA93.tmp is a valid Xubuntu CD
08-20 22:21 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pylFA93.tmp\casper\filesystem.squashfs
08-20 22:21 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pylFA93.tmp is a valid Xubuntu CD
08-20 22:21 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pylFA93.tmp\casper\filesystem.squashfs
08-20 22:21 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pylFA93.tmp is a valid Mythbuntu CD
08-20 22:21 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pylFA93.tmp\casper\filesystem.squashfs
08-20 22:21 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pylFA93.tmp is a valid Mythbuntu CD
08-20 22:21 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pylFA93.tmp\casper\filesystem.squashfs
08-20 22:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-20 22:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 22:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-20 22:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 22:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
08-20 22:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 22:21 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-20 22:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 22:21 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-20 22:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 22:21 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-20 22:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 22:21 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-20 22:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 22:21 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-20 22:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 22:21 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-20 22:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 22:21 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-20 22:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 22:21 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-20 22:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 22:21 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
08-20 22:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 22:21 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-20 22:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 22:21 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-20 22:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 22:21 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-20 22:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 22:21 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-20 22:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 22:21 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-20 22:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 22:21 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-20 22:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 22:21 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-20 22:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 22:21 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-20 22:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 22:21 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
08-20 22:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 22:21 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-20 22:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 22:21 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-20 22:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 22:21 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-20 22:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 22:21 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-20 22:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 22:21 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-20 22:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 22:21 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-20 22:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 22:21 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-20 22:21 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
08-20 22:21 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
08-20 22:21 INFO   Distro: Found a valid CD for Ubuntu: G:\
08-20 22:21 INFO   root: Running the CD menu...
08-20 22:21 DEBUG  WindowsFrontend: __init__...
08-20 22:21 DEBUG  WindowsFrontend: on_init...
08-20 22:21 INFO   WinuiPage: appname=wubi, localedir=C:\Users\jerren\AppData\Local\Temp\pylFA93.tmp\translations, languages=['en_US', 'en']
08-20 22:21 INFO   WinuiPage: appname=wubi, localedir=C:\Users\jerren\AppData\Local\Temp\pylFA93.tmp\translations, languages=['en_US', 'en']
08-20 22:21 INFO   root: CD menu finished
08-20 22:21 INFO   root: Running the CD boot helper...
08-20 22:21 INFO   WinuiPage: appname=wubi, localedir=C:\Users\jerren\AppData\Local\Temp\pylFA93.tmp\translations, languages=['en_US', 'en']
08-20 22:21 INFO   WinuiPage: appname=wubi, localedir=C:\Users\jerren\AppData\Local\Temp\pylFA93.tmp\translations, languages=['en_US', 'en']
08-20 22:21 INFO   root: CD boot helper confirmed
08-20 22:21 INFO   WinuiPage: appname=wubi, localedir=C:\Users\jerren\AppData\Local\Temp\pylFA93.tmp\translations, languages=['en_US', 'en']
08-20 22:21 DEBUG  TaskList: # Running tasklist...
08-20 22:21 DEBUG  TaskList: ## Running select_target_dir...
08-20 22:21 INFO   WindowsBackend: Installing into C:\ubuntu
08-20 22:21 DEBUG  TaskList: ## Finished select_target_dir
08-20 22:21 DEBUG  TaskList: ## Running create_dir_structure...
08-20 22:21 DEBUG  CommonBackend: Creating dir C:\ubuntu
08-20 22:21 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
08-20 22:21 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
08-20 22:21 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
08-20 22:21 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
08-20 22:21 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
08-20 22:21 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
08-20 22:21 DEBUG  TaskList: ## Finished create_dir_structure
08-20 22:21 DEBUG  TaskList: ## Running uncompress_target_dir...
08-20 22:21 DEBUG  TaskList: ## Finished uncompress_target_dir
08-20 22:21 DEBUG  TaskList: ## Running create_uninstaller...
08-20 22:21 DEBUG  WindowsBackend: Copying uninstaller G:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
08-20 22:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
08-20 22:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
08-20 22:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
08-20 22:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
08-20 22:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
08-20 22:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
08-20 22:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
08-20 22:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
08-20 22:21 DEBUG  TaskList: ## Finished create_uninstaller
08-20 22:21 DEBUG  TaskList: ## Running copy_installation_files...
08-20 22:21 DEBUG  WindowsBackend: Copying C:\Users\jerren\AppData\Local\Temp\pylFA93.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
08-20 22:21 DEBUG  WindowsBackend: Copying C:\Users\jerren\AppData\Local\Temp\pylFA93.tmp\winboot -> C:\ubuntu\winboot
08-20 22:21 DEBUG  WindowsBackend: Copying C:\Users\jerren\AppData\Local\Temp\pylFA93.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
08-20 22:21 DEBUG  TaskList: ## Finished copy_installation_files
08-20 22:21 DEBUG  TaskList: ## Running use_cd...
08-20 22:21 DEBUG  TaskList: New task copy_file
08-20 22:21 DEBUG  TaskList: ### Running copy_file...
08-20 22:31 DEBUG  TaskList: ### Finished copy_file
08-20 22:31 DEBUG  TaskList: New task check_iso
08-20 22:31 DEBUG  TaskList: ### Running check_iso...
08-20 22:31 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
08-20 22:31 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
08-20 22:31 DEBUG  Distro:     wrong size: 8169676800 > 900000000
08-20 22:31 DEBUG  TaskList: ### Finished check_iso
08-20 22:31 DEBUG  TaskList: ## Finished use_cd
08-20 22:31 DEBUG  TaskList: ## Running extract_kernel...
08-20 22:31 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 515, in extract_kernel
Exception: Could not retrieve the required installation files
08-20 22:31 DEBUG  TaskList: # Cancelling tasklist
08-20 22:31 DEBUG  TaskList: # Finished tasklist
08-20 22:31 ERROR  root: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 129, in select_task
  File "\lib\wubi\application.py", line 195, in run_cd_menu
  File "\lib\wubi\application.py", line 121, in select_task
  File "\lib\wubi\application.py", line 218, in run_cd_boot
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 515, in extract_kernel
Exception: Could not retrieve the required installation files
08-20 22:46 INFO   root: === wubi 11.04 rev211 ===
08-20 22:46 DEBUG  root: Logfile is c:\users\jerren\appdata\local\temp\wubi-11.04-rev211.log
08-20 22:46 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\wubi.exe"']
08-20 22:46 DEBUG  CommonBackend: data_dir=C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp\data
08-20 22:46 DEBUG  WindowsBackend: 7z=C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp\bin\7z.exe
08-20 22:46 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
08-20 22:46 DEBUG  CommonBackend: Fetching basic info...
08-20 22:46 DEBUG  CommonBackend: original_exe=G:\wubi.exe
08-20 22:46 DEBUG  CommonBackend: platform=win32
08-20 22:46 DEBUG  CommonBackend: osname=nt
08-20 22:46 DEBUG  CommonBackend: language=en_US
08-20 22:46 DEBUG  CommonBackend: encoding=cp1252
08-20 22:46 DEBUG  WindowsBackend: arch=amd64
08-20 22:46 DEBUG  CommonBackend: Parsing isolist=C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp\data\isolist.ini
08-20 22:46 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-20 22:46 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-20 22:46 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-20 22:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-20 22:46 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-20 22:46 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-20 22:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-20 22:46 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-20 22:46 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
08-20 22:46 DEBUG  WindowsBackend: Fetching host info...
08-20 22:46 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-20 22:46 DEBUG  WindowsBackend: windows version=vista
08-20 22:46 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Premium
08-20 22:46 DEBUG  WindowsBackend: windows_sp=None
08-20 22:46 DEBUG  WindowsBackend: windows_build=6000
08-20 22:46 DEBUG  WindowsBackend: gmt=-5
08-20 22:46 DEBUG  WindowsBackend: country=US
08-20 22:46 DEBUG  WindowsBackend: timezone=America/New_York
08-20 22:46 DEBUG  WindowsBackend: windows_username=jerren
08-20 22:46 DEBUG  WindowsBackend: user_full_name=jerren
08-20 22:46 DEBUG  WindowsBackend: user_directory=C:\Users\jerren
08-20 22:46 DEBUG  WindowsBackend: windows_language_code=1033
08-20 22:46 DEBUG  WindowsBackend: windows_language=English
08-20 22:46 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor TK-53
08-20 22:46 DEBUG  WindowsBackend: bootloader=vista
08-20 22:46 DEBUG  WindowsBackend: system_drive=Drive(C: hd 64452.7890625 mb free ntfs)
08-20 22:46 DEBUG  WindowsBackend: drive=Drive(C: hd 64452.7890625 mb free ntfs)
08-20 22:46 DEBUG  WindowsBackend: drive=Drive(D: hd 1770.39453125 mb free ntfs)
08-20 22:46 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
08-20 22:46 DEBUG  WindowsBackend: drive=Drive(F: removable 824.296875 mb free fat32)
08-20 22:46 DEBUG  WindowsBackend: drive=Drive(G: removable 6335.52734375 mb free fat32)
08-20 22:46 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
08-20 22:46 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
08-20 22:46 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
08-20 22:46 DEBUG  WindowsBackend: keyboard_id=67699721
08-20 22:46 DEBUG  WindowsBackend: keyboard_layout=us
08-20 22:46 DEBUG  WindowsBackend: keyboard_variant=
08-20 22:46 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
08-20 22:46 DEBUG  CommonBackend: locale=en_US.UTF-8
08-20 22:46 DEBUG  WindowsBackend: total_memory_mb=1982.0
08-20 22:46 DEBUG  CommonBackend: Searching ISOs on USB devices
08-20 22:46 DEBUG  Distro:   checking Ubuntu ISO G:\ubuntu-10.04.3-desktop-i386.iso
08-20 22:46 DEBUG  WindowsBackend:   extracting .disk\info from G:\ubuntu-10.04.3-desktop-i386.iso
08-20 22:46 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.3 LTS "Lucid Lynx" - Release i386 (20110720.1)
08-20 22:46 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.3', 'build': '20110720.1', 'codename': 'Lucid Lynx', 'arch': 'i386'}
08-20 22:46 DEBUG  Distro: wrong version: 10.04.3 != 11.04
08-20 22:46 DEBUG  Distro:   checking Ubuntu ISO G:\ubuntu-10.04.3-desktop-i386.iso
08-20 22:46 DEBUG  Distro: wrong version: 10.04.3 != 11.04
08-20 22:46 DEBUG  Distro:   checking Ubuntu Netbook ISO G:\ubuntu-10.04.3-desktop-i386.iso
08-20 22:46 DEBUG  Distro: wrong name: Ubuntu != Ubuntu Netbook
08-20 22:46 DEBUG  Distro:   checking Kubuntu ISO G:\ubuntu-10.04.3-desktop-i386.iso
08-20 22:46 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
08-20 22:46 DEBUG  Distro:   checking Kubuntu ISO G:\ubuntu-10.04.3-desktop-i386.iso
08-20 22:46 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
08-20 22:46 DEBUG  Distro:   checking Xubuntu ISO G:\ubuntu-10.04.3-desktop-i386.iso
08-20 22:46 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
08-20 22:46 DEBUG  Distro:   checking Xubuntu ISO G:\ubuntu-10.04.3-desktop-i386.iso
08-20 22:46 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
08-20 22:46 DEBUG  Distro:   checking Mythbuntu ISO G:\ubuntu-10.04.3-desktop-i386.iso
08-20 22:46 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
08-20 22:46 DEBUG  Distro:   checking Mythbuntu ISO G:\ubuntu-10.04.3-desktop-i386.iso
08-20 22:46 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
08-20 22:46 DEBUG  CommonBackend: Searching for local CDs
08-20 22:46 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp is a valid Ubuntu CD
08-20 22:46 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp is a valid Ubuntu CD
08-20 22:46 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp is a valid Ubuntu Netbook CD
08-20 22:46 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp is a valid Kubuntu CD
08-20 22:46 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp is a valid Kubuntu CD
08-20 22:46 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp is a valid Xubuntu CD
08-20 22:46 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp is a valid Xubuntu CD
08-20 22:46 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp is a valid Mythbuntu CD
08-20 22:46 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp is a valid Mythbuntu CD
08-20 22:46 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-20 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-20 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
08-20 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-20 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-20 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-20 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-20 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-20 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-20 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-20 22:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-20 22:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
08-20 22:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-20 22:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-20 22:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-20 22:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-20 22:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-20 22:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-20 22:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-20 22:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-20 22:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
08-20 22:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-20 22:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-20 22:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-20 22:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-20 22:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-20 22:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-20 22:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-20 22:46 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
08-20 22:46 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
08-20 22:46 INFO   Distro: Found a valid CD for Ubuntu: G:\
08-20 22:46 INFO   root: Running the CD menu...
08-20 22:46 DEBUG  WindowsFrontend: __init__...
08-20 22:46 DEBUG  WindowsFrontend: on_init...
08-20 22:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp\translations, languages=['en_US', 'en']
08-20 22:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp\translations, languages=['en_US', 'en']
08-20 22:46 INFO   root: CD menu finished
08-20 22:46 INFO   root: Already installed, running the uninstaller...
08-20 22:46 INFO   root: Running the uninstaller...
08-20 22:46 INFO   CommonBackend: This is the uninstaller running
08-20 22:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp\translations, languages=['en_US', 'en']
08-20 22:46 INFO   root: Received settings
08-20 22:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp\translations, languages=['en_US', 'en']
08-20 22:46 DEBUG  TaskList: # Running tasklist...
08-20 22:46 DEBUG  TaskList: ## Running Backup ISO...
08-20 22:46 DEBUG  TaskList: ## Finished Backup ISO
08-20 22:46 DEBUG  TaskList: ## Running Remove bootloader entry...
08-20 22:46 DEBUG  WindowsBackend: Could not find bcd id
08-20 22:46 DEBUG  WindowsBackend: undo_bootini C:
08-20 22:46 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 64452.7890625 mb free ntfs)
08-20 22:46 DEBUG  WindowsBackend: undo_bootini D:
08-20 22:46 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 1770.39453125 mb free ntfs)
08-20 22:46 DEBUG  WindowsBackend: undo_bootini F:
08-20 22:46 DEBUG  WindowsBackend: undo_configsys Drive(F: removable 824.296875 mb free fat32)
08-20 22:46 DEBUG  WindowsBackend: undo_bootini G:
08-20 22:46 DEBUG  WindowsBackend: undo_configsys Drive(G: removable 6335.52734375 mb free fat32)
08-20 22:46 DEBUG  TaskList: ## Finished Remove bootloader entry
08-20 22:46 DEBUG  TaskList: ## Running Remove target dir...
08-20 22:46 DEBUG  CommonBackend: Deleting C:\ubuntu
08-20 22:46 DEBUG  TaskList: ## Finished Remove target dir
08-20 22:46 DEBUG  TaskList: ## Running Remove registry key...
08-20 22:46 DEBUG  TaskList: ## Finished Remove registry key
08-20 22:46 DEBUG  TaskList: # Finished tasklist
08-20 22:46 INFO   root: Almost finished uninstalling
08-20 22:46 INFO   root: Finished uninstallation
08-20 22:46 DEBUG  CommonBackend: Fetching basic info...
08-20 22:46 DEBUG  CommonBackend: original_exe=G:\wubi.exe
08-20 22:46 DEBUG  CommonBackend: platform=win32
08-20 22:46 DEBUG  CommonBackend: osname=nt
08-20 22:46 DEBUG  WindowsBackend: arch=amd64
08-20 22:46 DEBUG  CommonBackend: Parsing isolist=C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp\data\isolist.ini
08-20 22:46 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-20 22:46 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-20 22:46 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-20 22:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-20 22:46 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-20 22:46 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-20 22:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-20 22:46 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-20 22:46 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
08-20 22:46 DEBUG  WindowsBackend: Fetching host info...
08-20 22:46 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-20 22:46 DEBUG  WindowsBackend: windows version=vista
08-20 22:46 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Premium
08-20 22:46 DEBUG  WindowsBackend: windows_sp=None
08-20 22:46 DEBUG  WindowsBackend: windows_build=6000
08-20 22:46 DEBUG  WindowsBackend: gmt=-5
08-20 22:46 DEBUG  WindowsBackend: country=US
08-20 22:46 DEBUG  WindowsBackend: timezone=America/New_York
08-20 22:46 DEBUG  WindowsBackend: windows_username=jerren
08-20 22:46 DEBUG  WindowsBackend: user_full_name=jerren
08-20 22:46 DEBUG  WindowsBackend: user_directory=C:\Users\jerren
08-20 22:46 DEBUG  WindowsBackend: windows_language_code=1033
08-20 22:46 DEBUG  WindowsBackend: windows_language=English
08-20 22:46 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor TK-53
08-20 22:46 DEBUG  WindowsBackend: bootloader=vista
08-20 22:46 DEBUG  WindowsBackend: system_drive=Drive(C: hd 72245.6289063 mb free ntfs)
08-20 22:46 DEBUG  WindowsBackend: drive=Drive(C: hd 72245.6054688 mb free ntfs)
08-20 22:46 DEBUG  WindowsBackend: drive=Drive(D: hd 1770.39453125 mb free ntfs)
08-20 22:46 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
08-20 22:46 DEBUG  WindowsBackend: drive=Drive(F: removable 824.296875 mb free fat32)
08-20 22:46 DEBUG  WindowsBackend: drive=Drive(G: removable 6335.52734375 mb free fat32)
08-20 22:46 DEBUG  WindowsBackend: uninstaller_path=None
08-20 22:46 DEBUG  WindowsBackend: previous_target_dir=None
08-20 22:46 DEBUG  WindowsBackend: previous_distro_name=None
08-20 22:46 DEBUG  WindowsBackend: keyboard_id=67699721
08-20 22:46 DEBUG  WindowsBackend: keyboard_layout=us
08-20 22:46 DEBUG  WindowsBackend: keyboard_variant=
08-20 22:46 DEBUG  WindowsBackend: total_memory_mb=1982.0
08-20 22:46 DEBUG  CommonBackend: Searching ISOs on USB devices
08-20 22:46 DEBUG  Distro:   checking Ubuntu ISO G:\ubuntu-10.04.3-desktop-i386.iso
08-20 22:46 DEBUG  Distro: wrong version: 10.04.3 != 11.04
08-20 22:46 DEBUG  Distro:   checking Ubuntu ISO G:\ubuntu-10.04.3-desktop-i386.iso
08-20 22:46 DEBUG  Distro: wrong version: 10.04.3 != 11.04
08-20 22:46 DEBUG  Distro:   checking Ubuntu Netbook ISO G:\ubuntu-10.04.3-desktop-i386.iso
08-20 22:46 DEBUG  Distro: wrong name: Ubuntu != Ubuntu Netbook
08-20 22:46 DEBUG  Distro:   checking Kubuntu ISO G:\ubuntu-10.04.3-desktop-i386.iso
08-20 22:46 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
08-20 22:46 DEBUG  Distro:   checking Kubuntu ISO G:\ubuntu-10.04.3-desktop-i386.iso
08-20 22:46 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
08-20 22:46 DEBUG  Distro:   checking Xubuntu ISO G:\ubuntu-10.04.3-desktop-i386.iso
08-20 22:46 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
08-20 22:46 DEBUG  Distro:   checking Xubuntu ISO G:\ubuntu-10.04.3-desktop-i386.iso
08-20 22:46 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
08-20 22:46 DEBUG  Distro:   checking Mythbuntu ISO G:\ubuntu-10.04.3-desktop-i386.iso
08-20 22:46 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
08-20 22:46 DEBUG  Distro:   checking Mythbuntu ISO G:\ubuntu-10.04.3-desktop-i386.iso
08-20 22:46 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
08-20 22:46 DEBUG  CommonBackend: Searching for local CDs
08-20 22:46 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp is a valid Ubuntu CD
08-20 22:46 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp is a valid Ubuntu CD
08-20 22:46 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp is a valid Ubuntu Netbook CD
08-20 22:46 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp is a valid Kubuntu CD
08-20 22:46 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp is a valid Kubuntu CD
08-20 22:46 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp is a valid Xubuntu CD
08-20 22:46 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp is a valid Xubuntu CD
08-20 22:46 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp is a valid Mythbuntu CD
08-20 22:46 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp is a valid Mythbuntu CD
08-20 22:46 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-20 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-20 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
08-20 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-20 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-20 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-20 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-20 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-20 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-20 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-20 22:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-20 22:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
08-20 22:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-20 22:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-20 22:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-20 22:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-20 22:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-20 22:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-20 22:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-20 22:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-20 22:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
08-20 22:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-20 22:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-20 22:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-20 22:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-20 22:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-20 22:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-20 22:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-20 22:46 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-20 22:46 INFO   Distro: Found a valid CD for Ubuntu: G:\
08-20 22:46 INFO   root: Running the CD boot helper...
08-20 22:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp\translations, languages=['en_US', 'en']
08-20 22:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp\translations, languages=['en_US', 'en']
08-20 22:46 INFO   root: CD boot helper confirmed
08-20 22:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp\translations, languages=['en_US', 'en']
08-20 22:46 DEBUG  TaskList: # Running tasklist...
08-20 22:46 DEBUG  TaskList: ## Running select_target_dir...
08-20 22:46 INFO   WindowsBackend: Installing into C:\ubuntu
08-20 22:46 DEBUG  TaskList: ## Finished select_target_dir
08-20 22:46 DEBUG  TaskList: ## Running create_dir_structure...
08-20 22:46 DEBUG  CommonBackend: Creating dir C:\ubuntu
08-20 22:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
08-20 22:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
08-20 22:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
08-20 22:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
08-20 22:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
08-20 22:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
08-20 22:46 DEBUG  TaskList: ## Finished create_dir_structure
08-20 22:46 DEBUG  TaskList: ## Running uncompress_target_dir...
08-20 22:46 DEBUG  TaskList: ## Finished uncompress_target_dir
08-20 22:46 DEBUG  TaskList: ## Running create_uninstaller...
08-20 22:46 DEBUG  WindowsBackend: Copying uninstaller G:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
08-20 22:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
08-20 22:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
08-20 22:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
08-20 22:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
08-20 22:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
08-20 22:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
08-20 22:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
08-20 22:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
08-20 22:46 DEBUG  TaskList: ## Finished create_uninstaller
08-20 22:46 DEBUG  TaskList: ## Running copy_installation_files...
08-20 22:46 DEBUG  WindowsBackend: Copying C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
08-20 22:46 DEBUG  WindowsBackend: Copying C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp\winboot -> C:\ubuntu\winboot
08-20 22:46 DEBUG  WindowsBackend: Copying C:\Users\jerren\AppData\Local\Temp\pyl844C.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
08-20 22:46 DEBUG  TaskList: ## Finished copy_installation_files
08-20 22:46 DEBUG  TaskList: ## Running use_cd...
08-20 22:46 DEBUG  TaskList: New task copy_file
08-20 22:46 DEBUG  TaskList: ### Running copy_file...
08-20 22:54 DEBUG  TaskList: ### Finished copy_file
08-20 22:54 DEBUG  TaskList: New task check_iso
08-20 22:54 DEBUG  TaskList: ### Running check_iso...
08-20 22:54 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
08-20 22:54 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
08-20 22:54 DEBUG  Distro:     wrong size: 8169676800 > 900000000
08-20 22:54 DEBUG  TaskList: ### Finished check_iso
08-20 22:54 DEBUG  TaskList: ## Finished use_cd
08-20 22:54 DEBUG  TaskList: ## Running extract_kernel...
08-20 22:54 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 515, in extract_kernel
Exception: Could not retrieve the required installation files
08-20 22:54 DEBUG  TaskList: # Cancelling tasklist
08-20 22:54 DEBUG  TaskList: # Finished tasklist
08-20 22:54 ERROR  root: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 129, in select_task
  File "\lib\wubi\application.py", line 195, in run_cd_menu
  File "\lib\wubi\application.py", line 121, in select_task
  File "\lib\wubi\application.py", line 218, in run_cd_boot
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 515, in extract_kernel
Exception: Could not retrieve the required installation files
08-21 21:27 INFO   root: === wubi 11.04 rev211 ===
08-21 21:27 DEBUG  root: Logfile is c:\users\jerren\appdata\local\temp\wubi-11.04-rev211.log
08-21 21:27 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\wubi.exe"', '--cdmenu']
08-21 21:27 DEBUG  CommonBackend: data_dir=C:\Users\jerren\AppData\Local\Temp\pylD114.tmp\data
08-21 21:27 DEBUG  WindowsBackend: 7z=C:\Users\jerren\AppData\Local\Temp\pylD114.tmp\bin\7z.exe
08-21 21:27 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
08-21 21:27 DEBUG  CommonBackend: Fetching basic info...
08-21 21:27 DEBUG  CommonBackend: original_exe=G:\wubi.exe
08-21 21:27 DEBUG  CommonBackend: platform=win32
08-21 21:27 DEBUG  CommonBackend: osname=nt
08-21 21:27 DEBUG  CommonBackend: language=en_US
08-21 21:27 DEBUG  CommonBackend: encoding=cp1252
08-21 21:27 DEBUG  WindowsBackend: arch=amd64
08-21 21:27 DEBUG  CommonBackend: Parsing isolist=C:\Users\jerren\AppData\Local\Temp\pylD114.tmp\data\isolist.ini
08-21 21:27 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-21 21:27 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-21 21:27 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-21 21:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-21 21:27 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-21 21:27 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-21 21:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-21 21:27 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-21 21:27 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
08-21 21:27 DEBUG  WindowsBackend: Fetching host info...
08-21 21:27 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-21 21:27 DEBUG  WindowsBackend: windows version=vista
08-21 21:27 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Premium
08-21 21:27 DEBUG  WindowsBackend: windows_sp=None
08-21 21:27 DEBUG  WindowsBackend: windows_build=6000
08-21 21:27 DEBUG  WindowsBackend: gmt=-5
08-21 21:27 DEBUG  WindowsBackend: country=US
08-21 21:27 DEBUG  WindowsBackend: timezone=America/New_York
08-21 21:27 DEBUG  WindowsBackend: windows_username=jerren
08-21 21:27 DEBUG  WindowsBackend: user_full_name=jerren
08-21 21:27 DEBUG  WindowsBackend: user_directory=C:\Users\jerren
08-21 21:27 DEBUG  WindowsBackend: windows_language_code=1033
08-21 21:27 DEBUG  WindowsBackend: windows_language=English
08-21 21:27 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor TK-53
08-21 21:27 DEBUG  WindowsBackend: bootloader=vista
08-21 21:27 DEBUG  WindowsBackend: system_drive=Drive(C: hd 64355.3046875 mb free ntfs)
08-21 21:27 DEBUG  WindowsBackend: drive=Drive(C: hd 64355.3046875 mb free ntfs)
08-21 21:27 DEBUG  WindowsBackend: drive=Drive(D: hd 1770.39453125 mb free ntfs)
08-21 21:27 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
08-21 21:27 DEBUG  WindowsBackend: drive=Drive(G: removable 6335.52734375 mb free fat32)
08-21 21:27 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
08-21 21:27 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
08-21 21:27 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
08-21 21:27 DEBUG  WindowsBackend: keyboard_id=67699721
08-21 21:27 DEBUG  WindowsBackend: keyboard_layout=us
08-21 21:27 DEBUG  WindowsBackend: keyboard_variant=
08-21 21:27 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
08-21 21:27 DEBUG  CommonBackend: locale=en_US.UTF-8
08-21 21:27 DEBUG  WindowsBackend: total_memory_mb=1982.0
08-21 21:27 DEBUG  CommonBackend: Searching ISOs on USB devices
08-21 21:27 DEBUG  Distro:   checking Ubuntu ISO G:\ubuntu-10.04.3-desktop-i386.iso
08-21 21:27 DEBUG  WindowsBackend:   extracting .disk\info from G:\ubuntu-10.04.3-desktop-i386.iso
08-21 21:27 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.3 LTS "Lucid Lynx" - Release i386 (20110720.1)
08-21 21:27 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.3', 'build': '20110720.1', 'codename': 'Lucid Lynx', 'arch': 'i386'}
08-21 21:27 DEBUG  Distro: wrong version: 10.04.3 != 11.04
08-21 21:27 DEBUG  Distro:   checking Ubuntu ISO G:\ubuntu-10.04.3-desktop-i386.iso
08-21 21:27 DEBUG  Distro: wrong version: 10.04.3 != 11.04
08-21 21:27 DEBUG  Distro:   checking Ubuntu Netbook ISO G:\ubuntu-10.04.3-desktop-i386.iso
08-21 21:27 DEBUG  Distro: wrong name: Ubuntu != Ubuntu Netbook
08-21 21:27 DEBUG  Distro:   checking Kubuntu ISO G:\ubuntu-10.04.3-desktop-i386.iso
08-21 21:27 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
08-21 21:27 DEBUG  Distro:   checking Kubuntu ISO G:\ubuntu-10.04.3-desktop-i386.iso
08-21 21:27 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
08-21 21:27 DEBUG  Distro:   checking Xubuntu ISO G:\ubuntu-10.04.3-desktop-i386.iso
08-21 21:27 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
08-21 21:27 DEBUG  Distro:   checking Xubuntu ISO G:\ubuntu-10.04.3-desktop-i386.iso
08-21 21:27 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
08-21 21:27 DEBUG  Distro:   checking Mythbuntu ISO G:\ubuntu-10.04.3-desktop-i386.iso
08-21 21:27 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
08-21 21:27 DEBUG  Distro:   checking Mythbuntu ISO G:\ubuntu-10.04.3-desktop-i386.iso
08-21 21:27 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
08-21 21:27 DEBUG  CommonBackend: Searching for local CDs
08-21 21:27 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pylD114.tmp is a valid Ubuntu CD
08-21 21:27 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pylD114.tmp\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pylD114.tmp is a valid Ubuntu CD
08-21 21:27 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pylD114.tmp\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pylD114.tmp is a valid Ubuntu Netbook CD
08-21 21:27 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pylD114.tmp\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pylD114.tmp is a valid Kubuntu CD
08-21 21:27 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pylD114.tmp\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pylD114.tmp is a valid Kubuntu CD
08-21 21:27 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pylD114.tmp\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pylD114.tmp is a valid Xubuntu CD
08-21 21:27 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pylD114.tmp\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pylD114.tmp is a valid Xubuntu CD
08-21 21:27 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pylD114.tmp\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pylD114.tmp is a valid Mythbuntu CD
08-21 21:27 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pylD114.tmp\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pylD114.tmp is a valid Mythbuntu CD
08-21 21:27 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pylD114.tmp\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-21 21:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-21 21:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
08-21 21:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-21 21:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-21 21:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-21 21:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-21 21:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-21 21:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-21 21:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-21 21:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-21 21:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
08-21 21:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-21 21:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-21 21:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-21 21:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-21 21:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-21 21:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-21 21:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-21 21:27 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
08-21 21:27 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
08-21 21:27 INFO   Distro: Found a valid CD for Ubuntu: G:\
08-21 21:27 INFO   root: Running the CD menu...
08-21 21:27 DEBUG  WindowsFrontend: __init__...
08-21 21:27 DEBUG  WindowsFrontend: on_init...
08-21 21:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\jerren\AppData\Local\Temp\pylD114.tmp\translations, languages=['en_US', 'en']
08-21 21:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\jerren\AppData\Local\Temp\pylD114.tmp\translations, languages=['en_US', 'en']
08-21 21:27 INFO   root: CD menu finished
08-21 21:27 INFO   root: Already installed, running the uninstaller...
08-21 21:27 INFO   root: Running the uninstaller...
08-21 21:27 INFO   CommonBackend: This is the uninstaller running
08-21 21:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\jerren\AppData\Local\Temp\pylD114.tmp\translations, languages=['en_US', 'en']
08-21 21:27 INFO   root: Received settings
08-21 21:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\jerren\AppData\Local\Temp\pylD114.tmp\translations, languages=['en_US', 'en']
08-21 21:27 DEBUG  TaskList: # Running tasklist...
08-21 21:27 DEBUG  TaskList: ## Running Backup ISO...
08-21 21:27 DEBUG  TaskList: ## Finished Backup ISO
08-21 21:27 DEBUG  TaskList: ## Running Remove bootloader entry...
08-21 21:27 DEBUG  WindowsBackend: Could not find bcd id
08-21 21:27 DEBUG  WindowsBackend: undo_bootini C:
08-21 21:27 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 64355.3046875 mb free ntfs)
08-21 21:27 DEBUG  WindowsBackend: undo_bootini D:
08-21 21:27 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 1770.39453125 mb free ntfs)
08-21 21:27 DEBUG  WindowsBackend: undo_bootini G:
08-21 21:27 DEBUG  WindowsBackend: undo_configsys Drive(G: removable 6335.52734375 mb free fat32)
08-21 21:27 DEBUG  TaskList: ## Finished Remove bootloader entry
08-21 21:27 DEBUG  TaskList: ## Running Remove target dir...
08-21 21:27 DEBUG  CommonBackend: Deleting C:\ubuntu
08-21 21:27 DEBUG  TaskList: ## Finished Remove target dir
08-21 21:27 DEBUG  TaskList: ## Running Remove registry key...
08-21 21:27 DEBUG  TaskList: ## Finished Remove registry key
08-21 21:27 DEBUG  TaskList: # Finished tasklist
08-21 21:27 INFO   root: Almost finished uninstalling
08-21 21:27 INFO   root: Finished uninstallation
08-21 21:27 DEBUG  CommonBackend: Fetching basic info...
08-21 21:27 DEBUG  CommonBackend: original_exe=G:\wubi.exe
08-21 21:27 DEBUG  CommonBackend: platform=win32
08-21 21:27 DEBUG  CommonBackend: osname=nt
08-21 21:27 DEBUG  WindowsBackend: arch=amd64
08-21 21:27 DEBUG  CommonBackend: Parsing isolist=C:\Users\jerren\AppData\Local\Temp\pylD114.tmp\data\isolist.ini
08-21 21:27 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-21 21:27 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-21 21:27 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-21 21:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-21 21:27 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-21 21:27 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-21 21:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-21 21:27 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-21 21:27 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
08-21 21:27 DEBUG  WindowsBackend: Fetching host info...
08-21 21:27 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-21 21:27 DEBUG  WindowsBackend: windows version=vista
08-21 21:27 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Premium
08-21 21:27 DEBUG  WindowsBackend: windows_sp=None
08-21 21:27 DEBUG  WindowsBackend: windows_build=6000
08-21 21:27 DEBUG  WindowsBackend: gmt=-5
08-21 21:27 DEBUG  WindowsBackend: country=US
08-21 21:27 DEBUG  WindowsBackend: timezone=America/New_York
08-21 21:27 DEBUG  WindowsBackend: windows_username=jerren
08-21 21:27 DEBUG  WindowsBackend: user_full_name=jerren
08-21 21:27 DEBUG  WindowsBackend: user_directory=C:\Users\jerren
08-21 21:27 DEBUG  WindowsBackend: windows_language_code=1033
08-21 21:27 DEBUG  WindowsBackend: windows_language=English
08-21 21:27 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor TK-53
08-21 21:27 DEBUG  WindowsBackend: bootloader=vista
08-21 21:27 DEBUG  WindowsBackend: system_drive=Drive(C: hd 72147.8945313 mb free ntfs)
08-21 21:27 DEBUG  WindowsBackend: drive=Drive(C: hd 72147.8945313 mb free ntfs)
08-21 21:27 DEBUG  WindowsBackend: drive=Drive(D: hd 1770.39453125 mb free ntfs)
08-21 21:27 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
08-21 21:27 DEBUG  WindowsBackend: drive=Drive(G: removable 6335.52734375 mb free fat32)
08-21 21:27 DEBUG  WindowsBackend: uninstaller_path=None
08-21 21:27 DEBUG  WindowsBackend: previous_target_dir=None
08-21 21:27 DEBUG  WindowsBackend: previous_distro_name=None
08-21 21:27 DEBUG  WindowsBackend: keyboard_id=67699721
08-21 21:27 DEBUG  WindowsBackend: keyboard_layout=us
08-21 21:27 DEBUG  WindowsBackend: keyboard_variant=
08-21 21:27 DEBUG  WindowsBackend: total_memory_mb=1982.0
08-21 21:27 DEBUG  CommonBackend: Searching ISOs on USB devices
08-21 21:27 DEBUG  Distro:   checking Ubuntu ISO G:\ubuntu-10.04.3-desktop-i386.iso
08-21 21:27 DEBUG  Distro: wrong version: 10.04.3 != 11.04
08-21 21:27 DEBUG  Distro:   checking Ubuntu ISO G:\ubuntu-10.04.3-desktop-i386.iso
08-21 21:27 DEBUG  Distro: wrong version: 10.04.3 != 11.04
08-21 21:27 DEBUG  Distro:   checking Ubuntu Netbook ISO G:\ubuntu-10.04.3-desktop-i386.iso
08-21 21:27 DEBUG  Distro: wrong name: Ubuntu != Ubuntu Netbook
08-21 21:27 DEBUG  Distro:   checking Kubuntu ISO G:\ubuntu-10.04.3-desktop-i386.iso
08-21 21:27 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
08-21 21:27 DEBUG  Distro:   checking Kubuntu ISO G:\ubuntu-10.04.3-desktop-i386.iso
08-21 21:27 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
08-21 21:27 DEBUG  Distro:   checking Xubuntu ISO G:\ubuntu-10.04.3-desktop-i386.iso
08-21 21:27 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
08-21 21:27 DEBUG  Distro:   checking Xubuntu ISO G:\ubuntu-10.04.3-desktop-i386.iso
08-21 21:27 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
08-21 21:27 DEBUG  Distro:   checking Mythbuntu ISO G:\ubuntu-10.04.3-desktop-i386.iso
08-21 21:27 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
08-21 21:27 DEBUG  Distro:   checking Mythbuntu ISO G:\ubuntu-10.04.3-desktop-i386.iso
08-21 21:27 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
08-21 21:27 DEBUG  CommonBackend: Searching for local CDs
08-21 21:27 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pylD114.tmp is a valid Ubuntu CD
08-21 21:27 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pylD114.tmp\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pylD114.tmp is a valid Ubuntu CD
08-21 21:27 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pylD114.tmp\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pylD114.tmp is a valid Ubuntu Netbook CD
08-21 21:27 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pylD114.tmp\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pylD114.tmp is a valid Kubuntu CD
08-21 21:27 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pylD114.tmp\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pylD114.tmp is a valid Kubuntu CD
08-21 21:27 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pylD114.tmp\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pylD114.tmp is a valid Xubuntu CD
08-21 21:27 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pylD114.tmp\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pylD114.tmp is a valid Xubuntu CD
08-21 21:27 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pylD114.tmp\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pylD114.tmp is a valid Mythbuntu CD
08-21 21:27 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pylD114.tmp\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether C:\Users\jerren\AppData\Local\Temp\pylD114.tmp is a valid Mythbuntu CD
08-21 21:27 DEBUG  Distro:     does not contain C:\Users\jerren\AppData\Local\Temp\pylD114.tmp\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-21 21:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-21 21:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
08-21 21:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-21 21:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-21 21:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-21 21:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-21 21:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-21 21:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-21 21:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-21 21:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-21 21:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
08-21 21:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-21 21:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-21 21:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-21 21:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-21 21:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-21 21:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-21 21:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-21 21:27 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-21 21:27 INFO   Distro: Found a valid CD for Ubuntu: G:\
08-21 21:27 INFO   root: Running the CD boot helper...
08-21 21:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\jerren\AppData\Local\Temp\pylD114.tmp\translations, languages=['en_US', 'en']
08-21 21:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\jerren\AppData\Local\Temp\pylD114.tmp\translations, languages=['en_US', 'en']
08-21 21:28 INFO   root: CD boot helper confirmed
08-21 21:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\jerren\AppData\Local\Temp\pylD114.tmp\translations, languages=['en_US', 'en']
08-21 21:28 DEBUG  TaskList: # Running tasklist...
08-21 21:28 DEBUG  TaskList: ## Running select_target_dir...
08-21 21:28 INFO   WindowsBackend: Installing into C:\ubuntu
08-21 21:28 DEBUG  TaskList: ## Finished select_target_dir
08-21 21:28 DEBUG  TaskList: ## Running create_dir_structure...
08-21 21:28 DEBUG  CommonBackend: Creating dir C:\ubuntu
08-21 21:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
08-21 21:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
08-21 21:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
08-21 21:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
08-21 21:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
08-21 21:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
08-21 21:28 DEBUG  TaskList: ## Finished create_dir_structure
08-21 21:28 DEBUG  TaskList: ## Running uncompress_target_dir...
08-21 21:28 DEBUG  TaskList: ## Finished uncompress_target_dir
08-21 21:28 DEBUG  TaskList: ## Running create_uninstaller...
08-21 21:28 DEBUG  WindowsBackend: Copying uninstaller G:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
08-21 21:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
08-21 21:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
08-21 21:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
08-21 21:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
08-21 21:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
08-21 21:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
08-21 21:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
08-21 21:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
08-21 21:28 DEBUG  TaskList: ## Finished create_uninstaller
08-21 21:28 DEBUG  TaskList: ## Running copy_installation_files...
08-21 21:28 DEBUG  WindowsBackend: Copying C:\Users\jerren\AppData\Local\Temp\pylD114.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
08-21 21:28 DEBUG  WindowsBackend: Copying C:\Users\jerren\AppData\Local\Temp\pylD114.tmp\winboot -> C:\ubuntu\winboot
08-21 21:28 DEBUG  WindowsBackend: Copying C:\Users\jerren\AppData\Local\Temp\pylD114.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
08-21 21:28 DEBUG  TaskList: ## Finished copy_installation_files
08-21 21:28 DEBUG  TaskList: ## Running use_cd...
08-21 21:28 DEBUG  TaskList: New task copy_file
08-21 21:28 DEBUG  TaskList: ### Running copy_file...
08-21 21:38 DEBUG  TaskList: ### Finished copy_file
08-21 21:38 DEBUG  TaskList: New task check_iso
08-21 21:38 DEBUG  TaskList: ### Running check_iso...
08-21 21:38 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
08-21 21:38 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
08-21 21:38 DEBUG  Distro:     wrong size: 8169676800 > 900000000
08-21 21:38 DEBUG  TaskList: ### Finished check_iso
08-21 21:38 DEBUG  TaskList: ## Finished use_cd
08-21 21:38 DEBUG  TaskList: ## Running extract_kernel...
08-21 21:38 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 515, in extract_kernel
Exception: Could not retrieve the required installation files
08-21 21:38 DEBUG  TaskList: # Cancelling tasklist
08-21 21:38 DEBUG  TaskList: # Finished tasklist
08-21 21:38 ERROR  root: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 129, in select_task
  File "\lib\wubi\application.py", line 195, in run_cd_menu
  File "\lib\wubi\application.py", line 121, in select_task
  File "\lib\wubi\application.py", line 218, in run_cd_boot
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 515, in extract_kernel
Exception: Could not retrieve the required installation files


I have a dv9000 hp pavilion it is currently running off of vista and I was hoping to switch to ubuntu.

---

### Post by hansdown on 2011-08-21
Welcome to the forum, facexscar93.

Is your computer 32bit, or 64bit?

Sorry, but your logs cover a three day period, with almost every ubuntu distribution, in both architectures.

You may wish to look at burning the ISO to, either a cd, or usb.

[https://help.ubuntu.com/8.04/switching/installing.html](https://help.ubuntu.com/8.04/switching/installing.html)

---

### Post by bcbc on 2011-08-21
You can't install wubi with an 8GB USB drive. It's a little buggy... what it does is copy the ISO which is actually the 8GB partition, and then it checks the image to see if it's a CD ISO in a unsophisticated check that fails anything over 900,000 bytes. Since 8GB is > 900000 it fails. (The check is designed to distinguish between a CD ISO and a DVD ISO)

Anyway... if you want Wubi, you need to remove the G: USB and install Wubi in some other method: e.g. copy wubi.exe onto your harddrive in the same directory as the ISO you used to create the USB, then run wubi from there.

Just make sure you remove the USB or wubi.exe will find it and fail again.

PS Wubi installs Ubuntu in a virtual disk within your Windows partition. It's a good way to try out Ubuntu and is easily uninstallable from Control Panel. If you actually intend to create a long-term dual boot installation, it's better to boot your computer from the USB and partition and install.

---

### Post by facexscar93 on 2011-08-23
My computer is a 32 bit version of vista..... yay -_-

---

### Post by facexscar93 on 2011-08-23
I might not have mentioned before but when having the .iso on my 8gb flash drive and try to boot from usb it goes into a continuous start up loop. Then if i try to go to any of the options menus in the beginning it just freezes up.

---

