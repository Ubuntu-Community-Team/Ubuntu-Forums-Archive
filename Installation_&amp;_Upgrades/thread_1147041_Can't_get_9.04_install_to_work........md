---
title: "Can't get 9.04 install to work......."
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by Siggyfreud on 2009-05-03
This is been nothing but frustratng for me. I have tried using CD & USB to install Kubuntu 9.04 to no avail. This is the error message I get at this point. This is the install attempt log. I wanted to install as a dual boot, anyway tried Wubi too and of course no sucess.
 
05-03 01:45 INFO root: === wubi 9.04 rev128 ===
05-03 01:45 DEBUG root: Logfile is c:\users\george\appdata\local\temp\wubi-9.04-rev128.log
05-03 01:45 DEBUG root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"', '--cdmenu']
05-03 01:45 DEBUG CommonBackend: data_dir=C:\Users\George\AppData\Local\Temp\pylEF4D.tmp\data
05-03 01:45 DEBUG WindowsBackend: 7z=C:\Users\George\AppData\Local\Temp\pylEF4D.tmp\bin\7z.exe
05-03 01:45 DEBUG CommonBackend: Fetching basic info...
05-03 01:45 DEBUG CommonBackend: original_exe=I:\wubi.exe
05-03 01:45 DEBUG CommonBackend: platform=win32
05-03 01:45 DEBUG CommonBackend: osname=nt
05-03 01:45 DEBUG CommonBackend: language=en_US
05-03 01:45 DEBUG CommonBackend: encoding=cp1252
05-03 01:45 DEBUG WindowsBackend: arch=amd64
05-03 01:45 DEBUG CommonBackend: Parsing isolist=C:\Users\George\AppData\Local\Temp\pylEF4D.tmp\data\isolist.ini
05-03 01:45 DEBUG CommonBackend: Adding distro Xubuntu-i386
05-03 01:45 DEBUG CommonBackend: Adding distro Xubuntu-amd64
05-03 01:45 DEBUG CommonBackend: Adding distro Kubuntu-amd64
05-03 01:45 DEBUG CommonBackend: Adding distro Mythbuntu-i386
05-03 01:45 DEBUG CommonBackend: Adding distro Ubuntu-amd64
05-03 01:45 DEBUG CommonBackend: Adding distro Ubuntu-i386
05-03 01:45 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
05-03 01:45 DEBUG CommonBackend: Adding distro Kubuntu-i386
05-03 01:45 DEBUG WindowsBackend: Fetching host info...
05-03 01:45 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-03 01:45 DEBUG WindowsBackend: windows version=vista
05-03 01:45 DEBUG WindowsBackend: windows_version2=Windows 7 Ultimate
05-03 01:45 DEBUG WindowsBackend: windows_sp=None
05-03 01:45 DEBUG WindowsBackend: windows_build=7000
05-03 01:45 DEBUG WindowsBackend: gmt=-5
05-03 01:45 DEBUG WindowsBackend: country=US
05-03 01:45 DEBUG WindowsBackend: timezone=America/New_York
05-03 01:45 DEBUG WindowsBackend: windows_username=George
05-03 01:45 DEBUG WindowsBackend: user_full_name=George
05-03 01:45 DEBUG WindowsBackend: user_directory=George
05-03 01:45 DEBUG WindowsBackend: windows_language_code=1033
05-03 01:45 DEBUG WindowsBackend: windows_language=English
05-03 01:45 DEBUG WindowsBackend: processor_name=Intel(R) Core(TM) i7 CPU 920 @ 2.67GHz
05-03 01:45 DEBUG WindowsBackend: bootloader=vista
05-03 01:45 DEBUG WindowsBackend: system_drive=Drive(C: hd 128440.554688 mb free )
05-03 01:45 DEBUG WindowsBackend: drive=Drive(C: hd 128440.554688 mb free )
05-03 01:45 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free )
05-03 01:45 DEBUG WindowsBackend: drive=Drive(E: cd 0.0 mb free )
05-03 01:45 DEBUG WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
05-03 01:45 DEBUG WindowsBackend: uninstaller_path=None
05-03 01:45 DEBUG WindowsBackend: previous_target_dir=None
05-03 01:45 DEBUG WindowsBackend: previous_distro_name=None
05-03 01:45 DEBUG WindowsBackend: keyboard_id=67699721
05-03 01:45 DEBUG WindowsBackend: keyboard_layout=us
05-03 01:45 DEBUG WindowsBackend: keyboard_variant=
05-03 01:45 DEBUG CommonBackend: locale=en_US.UTF-8
05-03 01:45 DEBUG WindowsBackend: total_memory_mb=4095.99999905
05-03 01:45 DEBUG CommonBackend: Searching ISOs on USB devices
05-03 01:45 DEBUG CommonBackend: Searching for local CDs
05-03 01:45 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pylEF4D.tmp is a valid Ubuntu CD
05-03 01:45 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pylEF4D.tmp\casper\filesystem.squashfs
05-03 01:45 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pylEF4D.tmp is a valid Ubuntu CD
05-03 01:45 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pylEF4D.tmp\casper\filesystem.squashfs
05-03 01:45 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pylEF4D.tmp is a valid Kubuntu CD
05-03 01:45 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pylEF4D.tmp\casper\filesystem.squashfs
05-03 01:45 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pylEF4D.tmp is a valid Kubuntu CD
05-03 01:45 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pylEF4D.tmp\casper\filesystem.squashfs
05-03 01:45 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pylEF4D.tmp is a valid Xubuntu CD
05-03 01:45 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pylEF4D.tmp\casper\filesystem.squashfs
05-03 01:45 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pylEF4D.tmp is a valid Xubuntu CD
05-03 01:45 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pylEF4D.tmp\casper\filesystem.squashfs
05-03 01:45 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pylEF4D.tmp is a valid Mythbuntu CD
05-03 01:45 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pylEF4D.tmp\casper\filesystem.squashfs
05-03 01:45 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pylEF4D.tmp is a valid Mythbuntu CD
05-03 01:45 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pylEF4D.tmp\casper\filesystem.squashfs
05-03 01:45 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
05-03 01:45 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
05-03 01:45 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
05-03 01:45 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
05-03 01:45 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
05-03 01:45 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
05-03 01:45 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
05-03 01:45 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
05-03 01:45 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
05-03 01:45 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
05-03 01:45 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
05-03 01:45 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
05-03 01:45 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
05-03 01:45 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
05-03 01:45 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
05-03 01:45 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
05-03 01:45 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
05-03 01:45 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
05-03 01:45 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
05-03 01:45 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
05-03 01:45 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
05-03 01:45 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
05-03 01:45 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
05-03 01:45 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
05-03 01:45 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
05-03 01:45 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
05-03 01:45 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
05-03 01:45 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
05-03 01:45 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
05-03 01:45 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
05-03 01:45 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
05-03 01:45 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
05-03 01:45 DEBUG Distro: checking whether I:\ is a valid Ubuntu CD
05-03 01:45 DEBUG Distro: info=Kubuntu 9.04 "Jaunty Jackalope" - Release amd64 (20090420.1)
05-03 01:45 DEBUG Distro: parsed info={'name': 'Kubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'amd64'}
05-03 01:45 DEBUG Distro: wrong name: Kubuntu != Ubuntu
05-03 01:45 DEBUG Distro: checking whether I:\ is a valid Ubuntu CD
05-03 01:45 DEBUG Distro: wrong name: Kubuntu != Ubuntu
05-03 01:45 DEBUG Distro: checking whether I:\ is a valid Kubuntu CD
05-03 01:45 INFO Distro: Found a valid CD for Kubuntu: I:\
05-03 01:45 INFO root: Running the CD menu...
05-03 01:45 DEBUG WindowsFrontend: __init__...
05-03 01:45 DEBUG WindowsFrontend: on_init...
05-03 01:46 DEBUG root: application.quit
05-03 01:46 DEBUG WindowsFrontend: frontend.quit
05-03 01:46 DEBUG WindowsFrontend: frontend.on_quit
05-03 01:46 DEBUG root: application.on_quit
05-03 01:46 INFO root: sys.exit
05-03 01:47 INFO root: === wubi 9.04 rev128 ===
05-03 01:47 DEBUG root: Logfile is c:\users\george\appdata\local\temp\wubi-9.04-rev128.log
05-03 01:47 DEBUG root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"']
05-03 01:47 DEBUG CommonBackend: data_dir=C:\Users\George\AppData\Local\Temp\pyl6759.tmp\data
05-03 01:47 DEBUG WindowsBackend: 7z=C:\Users\George\AppData\Local\Temp\pyl6759.tmp\bin\7z.exe
05-03 01:47 DEBUG CommonBackend: Fetching basic info...
05-03 01:47 DEBUG CommonBackend: original_exe=I:\wubi.exe
05-03 01:47 DEBUG CommonBackend: platform=win32
05-03 01:47 DEBUG CommonBackend: osname=nt
05-03 01:47 DEBUG CommonBackend: language=en_US
05-03 01:47 DEBUG CommonBackend: encoding=cp1252
05-03 01:47 DEBUG WindowsBackend: arch=amd64
05-03 01:47 DEBUG CommonBackend: Parsing isolist=C:\Users\George\AppData\Local\Temp\pyl6759.tmp\data\isolist.ini
05-03 01:47 DEBUG CommonBackend: Adding distro Xubuntu-i386
05-03 01:47 DEBUG CommonBackend: Adding distro Xubuntu-amd64
05-03 01:47 DEBUG CommonBackend: Adding distro Kubuntu-amd64
05-03 01:47 DEBUG CommonBackend: Adding distro Mythbuntu-i386
05-03 01:47 DEBUG CommonBackend: Adding distro Ubuntu-amd64
05-03 01:47 DEBUG CommonBackend: Adding distro Ubuntu-i386
05-03 01:47 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
05-03 01:47 DEBUG CommonBackend: Adding distro Kubuntu-i386
05-03 01:47 DEBUG WindowsBackend: Fetching host info...
05-03 01:47 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-03 01:47 DEBUG WindowsBackend: windows version=vista
05-03 01:47 DEBUG WindowsBackend: windows_version2=Windows 7 Ultimate
05-03 01:47 DEBUG WindowsBackend: windows_sp=None
05-03 01:47 DEBUG WindowsBackend: windows_build=7000
05-03 01:47 DEBUG WindowsBackend: gmt=-5
05-03 01:47 DEBUG WindowsBackend: country=US
05-03 01:47 DEBUG WindowsBackend: timezone=America/New_York
05-03 01:47 DEBUG WindowsBackend: windows_username=George
05-03 01:47 DEBUG WindowsBackend: user_full_name=George
05-03 01:47 DEBUG WindowsBackend: user_directory=George
05-03 01:47 DEBUG WindowsBackend: windows_language_code=1033
05-03 01:47 DEBUG WindowsBackend: windows_language=English
05-03 01:47 DEBUG WindowsBackend: processor_name=Intel(R) Core(TM) i7 CPU 920 @ 2.67GHz
05-03 01:47 DEBUG WindowsBackend: bootloader=vista
05-03 01:47 DEBUG WindowsBackend: system_drive=Drive(C: hd 128439.882813 mb free )
05-03 01:47 DEBUG WindowsBackend: drive=Drive(C: hd 128439.882813 mb free )
05-03 01:47 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free )
05-03 01:47 DEBUG WindowsBackend: drive=Drive(E: cd 0.0 mb free )
05-03 01:47 DEBUG WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
05-03 01:47 DEBUG WindowsBackend: uninstaller_path=None
05-03 01:47 DEBUG WindowsBackend: previous_target_dir=None
05-03 01:47 DEBUG WindowsBackend: previous_distro_name=None
05-03 01:47 DEBUG WindowsBackend: keyboard_id=67699721
05-03 01:47 DEBUG WindowsBackend: keyboard_layout=us
05-03 01:47 DEBUG WindowsBackend: keyboard_variant=
05-03 01:47 DEBUG CommonBackend: locale=en_US.UTF-8
05-03 01:47 DEBUG WindowsBackend: total_memory_mb=4095.99999905
05-03 01:47 DEBUG CommonBackend: Searching ISOs on USB devices
05-03 01:47 DEBUG CommonBackend: Searching for local CDs
05-03 01:47 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pyl6759.tmp is a valid Ubuntu CD
05-03 01:47 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pyl6759.tmp\casper\filesystem.squashfs
05-03 01:47 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pyl6759.tmp is a valid Ubuntu CD
05-03 01:47 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pyl6759.tmp\casper\filesystem.squashfs
05-03 01:47 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pyl6759.tmp is a valid Kubuntu CD
05-03 01:47 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pyl6759.tmp\casper\filesystem.squashfs
05-03 01:47 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pyl6759.tmp is a valid Kubuntu CD
05-03 01:47 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pyl6759.tmp\casper\filesystem.squashfs
05-03 01:47 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pyl6759.tmp is a valid Xubuntu CD
05-03 01:47 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pyl6759.tmp\casper\filesystem.squashfs
05-03 01:47 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pyl6759.tmp is a valid Xubuntu CD
05-03 01:47 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pyl6759.tmp\casper\filesystem.squashfs
05-03 01:47 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pyl6759.tmp is a valid Mythbuntu CD
05-03 01:47 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pyl6759.tmp\casper\filesystem.squashfs
05-03 01:47 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pyl6759.tmp is a valid Mythbuntu CD
05-03 01:47 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pyl6759.tmp\casper\filesystem.squashfs
05-03 01:47 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
05-03 01:47 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
05-03 01:47 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
05-03 01:47 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
05-03 01:47 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
05-03 01:47 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
05-03 01:47 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
05-03 01:47 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
05-03 01:47 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
05-03 01:47 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
05-03 01:47 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
05-03 01:47 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
05-03 01:47 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
05-03 01:47 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
05-03 01:47 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
05-03 01:47 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
05-03 01:47 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
05-03 01:47 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
05-03 01:47 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
05-03 01:47 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
05-03 01:47 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
05-03 01:47 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
05-03 01:47 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
05-03 01:47 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
05-03 01:47 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
05-03 01:47 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
05-03 01:47 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
05-03 01:47 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
05-03 01:47 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
05-03 01:47 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
05-03 01:47 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
05-03 01:47 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
05-03 01:47 DEBUG Distro: checking whether I:\ is a valid Ubuntu CD
05-03 01:47 DEBUG Distro: info=Kubuntu 9.04 "Jaunty Jackalope" - Release amd64 (20090420.1)
05-03 01:47 DEBUG Distro: parsed info={'name': 'Kubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'amd64'}
05-03 01:47 DEBUG Distro: wrong name: Kubuntu != Ubuntu
05-03 01:47 DEBUG Distro: checking whether I:\ is a valid Ubuntu CD
05-03 01:47 DEBUG Distro: wrong name: Kubuntu != Ubuntu
05-03 01:47 DEBUG Distro: checking whether I:\ is a valid Kubuntu CD
05-03 01:47 INFO Distro: Found a valid CD for Kubuntu: I:\
05-03 01:47 INFO root: Running the CD menu...
05-03 01:47 DEBUG WindowsFrontend: __init__...
05-03 01:47 DEBUG WindowsFrontend: on_init...
05-03 01:47 INFO root: CD menu finished
05-03 01:47 INFO root: Running the CD boot helper...
05-03 01:48 INFO WindowsFrontend: Operation cancelled
05-03 01:48 DEBUG WindowsFrontend: frontend.quit
05-03 01:48 DEBUG WindowsFrontend: frontend.on_quit
05-03 01:48 DEBUG root: application.on_quit
05-03 01:48 INFO root: sys.exit
05-03 01:51 INFO root: === wubi 9.04 rev128 ===
05-03 01:51 DEBUG root: Logfile is c:\users\george\appdata\local\temp\wubi-9.04-rev128.log
05-03 01:51 DEBUG root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"', '--cdmenu']
05-03 01:51 DEBUG CommonBackend: data_dir=C:\Users\George\AppData\Local\Temp\pylB1C1.tmp\data
05-03 01:51 DEBUG WindowsBackend: 7z=C:\Users\George\AppData\Local\Temp\pylB1C1.tmp\bin\7z.exe
05-03 01:51 DEBUG CommonBackend: Fetching basic info...
05-03 01:51 DEBUG CommonBackend: original_exe=I:\wubi.exe
05-03 01:51 DEBUG CommonBackend: platform=win32
05-03 01:51 DEBUG CommonBackend: osname=nt
05-03 01:51 DEBUG CommonBackend: language=en_US
05-03 01:51 DEBUG CommonBackend: encoding=cp1252
05-03 01:51 DEBUG WindowsBackend: arch=amd64
05-03 01:51 DEBUG CommonBackend: Parsing isolist=C:\Users\George\AppData\Local\Temp\pylB1C1.tmp\data\isolist.ini
05-03 01:51 DEBUG CommonBackend: Adding distro Xubuntu-i386
05-03 01:51 DEBUG CommonBackend: Adding distro Xubuntu-amd64
05-03 01:51 DEBUG CommonBackend: Adding distro Kubuntu-amd64
05-03 01:51 DEBUG CommonBackend: Adding distro Mythbuntu-i386
05-03 01:51 DEBUG CommonBackend: Adding distro Ubuntu-amd64
05-03 01:51 DEBUG CommonBackend: Adding distro Ubuntu-i386
05-03 01:51 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
05-03 01:51 DEBUG CommonBackend: Adding distro Kubuntu-i386
05-03 01:51 DEBUG WindowsBackend: Fetching host info...
05-03 01:51 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-03 01:51 DEBUG WindowsBackend: windows version=vista
05-03 01:51 DEBUG WindowsBackend: windows_version2=Windows 7 Ultimate
05-03 01:51 DEBUG WindowsBackend: windows_sp=None
05-03 01:51 DEBUG WindowsBackend: windows_build=7000
05-03 01:51 DEBUG WindowsBackend: gmt=-5
05-03 01:51 DEBUG WindowsBackend: country=US
05-03 01:51 DEBUG WindowsBackend: timezone=America/New_York
05-03 01:51 DEBUG WindowsBackend: windows_username=George
05-03 01:51 DEBUG WindowsBackend: user_full_name=George
05-03 01:51 DEBUG WindowsBackend: user_directory=George
05-03 01:51 DEBUG WindowsBackend: windows_language_code=1033
05-03 01:51 DEBUG WindowsBackend: windows_language=English
05-03 01:51 DEBUG WindowsBackend: processor_name=Intel(R) Core(TM) i7 CPU 920 @ 2.67GHz
05-03 01:51 DEBUG WindowsBackend: bootloader=vista
05-03 01:51 DEBUG WindowsBackend: system_drive=Drive(C: hd 128435.859375 mb free )
05-03 01:51 DEBUG WindowsBackend: drive=Drive(C: hd 128435.859375 mb free )
05-03 01:51 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free udf)
05-03 01:51 DEBUG WindowsBackend: drive=Drive(E: cd 0.0 mb free )
05-03 01:51 DEBUG WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
05-03 01:51 DEBUG WindowsBackend: uninstaller_path=None
05-03 01:51 DEBUG WindowsBackend: previous_target_dir=None
05-03 01:51 DEBUG WindowsBackend: previous_distro_name=None
05-03 01:51 DEBUG WindowsBackend: keyboard_id=67699721
05-03 01:51 DEBUG WindowsBackend: keyboard_layout=us
05-03 01:51 DEBUG WindowsBackend: keyboard_variant=
05-03 01:51 DEBUG CommonBackend: locale=en_US.UTF-8
05-03 01:51 DEBUG WindowsBackend: total_memory_mb=4095.99999905
05-03 01:51 DEBUG CommonBackend: Searching ISOs on USB devices
05-03 01:51 DEBUG Distro: checking Ubuntu ISO D:\kubuntu-9.04-desktop-amd64.iso
05-03 01:51 DEBUG WindowsBackend: extracting .disk\info from D:\kubuntu-9.04-desktop-amd64.iso
05-03 01:51 DEBUG Distro: info=Kubuntu 9.04 "Jaunty Jackalope" - Release amd64 (20090420.1)
05-03 01:51 DEBUG Distro: parsed info={'name': 'Kubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'amd64'}
05-03 01:51 DEBUG Distro: wrong name: Kubuntu != Ubuntu
05-03 01:51 DEBUG Distro: checking Ubuntu ISO D:\kubuntu-9.04-desktop-amd64.iso
05-03 01:51 DEBUG Distro: wrong name: Kubuntu != Ubuntu
05-03 01:51 DEBUG Distro: checking Kubuntu ISO D:\kubuntu-9.04-desktop-amd64.iso
05-03 01:51 INFO Distro: Found a valid iso for Kubuntu: D:\kubuntu-9.04-desktop-amd64.iso
05-03 01:51 DEBUG CommonBackend: Searching for local CDs
05-03 01:51 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pylB1C1.tmp is a valid Ubuntu CD
05-03 01:51 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pylB1C1.tmp\casper\filesystem.squashfs
05-03 01:51 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pylB1C1.tmp is a valid Ubuntu CD
05-03 01:51 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pylB1C1.tmp\casper\filesystem.squashfs
05-03 01:51 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pylB1C1.tmp is a valid Kubuntu CD
05-03 01:51 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pylB1C1.tmp\casper\filesystem.squashfs
05-03 01:51 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pylB1C1.tmp is a valid Kubuntu CD
05-03 01:51 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pylB1C1.tmp\casper\filesystem.squashfs
05-03 01:51 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pylB1C1.tmp is a valid Xubuntu CD
05-03 01:51 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pylB1C1.tmp\casper\filesystem.squashfs
05-03 01:51 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pylB1C1.tmp is a valid Xubuntu CD
05-03 01:51 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pylB1C1.tmp\casper\filesystem.squashfs
05-03 01:51 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pylB1C1.tmp is a valid Mythbuntu CD
05-03 01:51 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pylB1C1.tmp\casper\filesystem.squashfs
05-03 01:51 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pylB1C1.tmp is a valid Mythbuntu CD
05-03 01:51 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pylB1C1.tmp\casper\filesystem.squashfs
05-03 01:51 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
05-03 01:51 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
05-03 01:51 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
05-03 01:51 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
05-03 01:51 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
05-03 01:51 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
05-03 01:51 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
05-03 01:51 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
05-03 01:51 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
05-03 01:51 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
05-03 01:51 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
05-03 01:51 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
05-03 01:51 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
05-03 01:51 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
05-03 01:51 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
05-03 01:51 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
05-03 01:51 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
05-03 01:51 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
05-03 01:51 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
05-03 01:51 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
05-03 01:51 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
05-03 01:51 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
05-03 01:51 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
05-03 01:51 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
05-03 01:51 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
05-03 01:51 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
05-03 01:51 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
05-03 01:51 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
05-03 01:51 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
05-03 01:51 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
05-03 01:51 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
05-03 01:51 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
05-03 01:51 DEBUG Distro: checking whether I:\ is a valid Ubuntu CD
05-03 01:51 DEBUG Distro: info=Kubuntu 9.04 "Jaunty Jackalope" - Release amd64 (20090420.1)
05-03 01:51 DEBUG Distro: parsed info={'name': 'Kubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'amd64'}
05-03 01:51 DEBUG Distro: wrong name: Kubuntu != Ubuntu
05-03 01:51 DEBUG Distro: checking whether I:\ is a valid Ubuntu CD
05-03 01:51 DEBUG Distro: wrong name: Kubuntu != Ubuntu
05-03 01:51 DEBUG Distro: checking whether I:\ is a valid Kubuntu CD
05-03 01:51 INFO Distro: Found a valid CD for Kubuntu: I:\
05-03 01:51 INFO root: Running the CD menu...
05-03 01:51 DEBUG WindowsFrontend: __init__...
05-03 01:51 DEBUG WindowsFrontend: on_init...
05-03 01:51 INFO root: CD menu finished
05-03 01:51 INFO root: Running the CD boot helper...
05-03 01:51 INFO root: CD boot helper confirmed
05-03 01:51 DEBUG TaskList: # Running tasklist...
05-03 01:51 DEBUG TaskList: ## Running select_target_dir...
05-03 01:51 INFO WindowsBackend: Installing into C:\ubuntu
05-03 01:51 DEBUG TaskList: ## Finished select_target_dir
05-03 01:51 DEBUG TaskList: ## Running create_dir_structure...
05-03 01:51 DEBUG CommonBackend: Creating dir C:\ubuntu
05-03 01:51 DEBUG CommonBackend: Creating dir C:\ubuntu\disks
05-03 01:51 DEBUG CommonBackend: Creating dir C:\ubuntu\install
05-03 01:51 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot
05-03 01:51 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot
05-03 01:51 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-03 01:51 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-03 01:51 DEBUG TaskList: ## Finished create_dir_structure
05-03 01:51 DEBUG TaskList: ## Running uncompress_target_dir...
05-03 01:51 DEBUG TaskList: ## Finished uncompress_target_dir
05-03 01:51 DEBUG TaskList: ## Running create_uninstaller...
05-03 01:51 DEBUG WindowsBackend: Copying uninstaller I:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
05-03 01:51 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-03 01:51 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-03 01:51 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Kubuntu
05-03 01:51 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Kubuntu.ico
05-03 01:51 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
05-03 01:51 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Kubuntu
05-03 01:51 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.kubuntu.org](http://www.kubuntu.org)
05-03 01:51 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-03 01:51 DEBUG TaskList: ## Finished create_uninstaller
05-03 01:51 DEBUG TaskList: ## Running copy_installation_files...
05-03 01:51 DEBUG WindowsBackend: Copying C:\Users\George\AppData\Local\Temp\pylB1C1.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-03 01:51 DEBUG WindowsBackend: Copying C:\Users\George\AppData\Local\Temp\pylB1C1.tmp\winboot -> C:\ubuntu\winboot
05-03 01:51 DEBUG WindowsBackend: Copying C:\Users\George\AppData\Local\Temp\pylB1C1.tmp\data\images\Kubuntu.ico -> C:\ubuntu\Kubuntu.ico
05-03 01:51 DEBUG TaskList: ## Finished copy_installation_files
05-03 01:51 DEBUG TaskList: ## Running use_cd...
05-03 01:51 DEBUG TaskList: New task copy_file
05-03 01:51 DEBUG TaskList: ### Running copy_file...
05-03 01:51 DEBUG TaskList: ### Finished copy_file
05-03 01:51 DEBUG TaskList: New task check_iso
05-03 01:51 DEBUG TaskList: ### Running check_iso...
05-03 01:51 DEBUG CommonBackend: Checking C:\ubuntu\install\installation.iso
05-03 01:51 DEBUG WindowsBackend: extracting .disk\info from C:\ubuntu\install\installation.iso
05-03 01:51 DEBUG Distro: info=Kubuntu 9.04 "Jaunty Jackalope" - Release amd64 (20090420.1)
05-03 01:51 DEBUG Distro: parsed info={'name': 'Kubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'amd64'}
05-03 01:51 DEBUG TaskList: New task get_metalink
05-03 01:51 DEBUG TaskList: #### Running get_metalink...
05-03 01:51 DEBUG downloader: downloading releases.ubuntu.com/kubuntu/9.04/kubuntu-9.04-desktop-i386.metalink > C:\ubuntu\install
05-03 01:51 ERROR CommonBackend: Cannot download metalink file releases.ubuntu.com/kubuntu/9.04/kubuntu-9.04-desktop-i386.metalink err=[Errno 2] Local file does not exist: C:\Users\George\AppData\Local\Temp\pylB1C1.tmp\releases.ubuntu.com\kubuntu\9.04\kubuntu-9.04-desktop-i386.metalink
05-03 01:51 DEBUG downloader: downloading [http://cdimage.ubuntu.com/kubuntu/daily-live/current/jaunty-desktop-amd64.metalink](http://cdimage.ubuntu.com/kubuntu/daily-live/current/jaunty-desktop-amd64.metalink) > C:\ubuntu\install
05-03 01:51 DEBUG downloader: Download start filename=C:\ubuntu\install\jaunty-desktop-amd64.metalink, url=http://cdimage.ubuntu.com/kubuntu/daily-live/current/jaunty-desktop-amd64.metalink, basename=jaunty-desktop-amd64.metalink, length=1018, text=None
05-03 01:51 DEBUG downloader: download finished (read 1018 bytes)
05-03 01:51 DEBUG downloader: downloading [http://cdimage.ubuntu.com/kubuntu/daily-live/current/MD5SUMS-metalink](http://cdimage.ubuntu.com/kubuntu/daily-live/current/MD5SUMS-metalink) > C:\ubuntu\install
05-03 01:52 DEBUG downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://cdimage.ubuntu.com/kubuntu/daily-live/current/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=127, text=None
05-03 01:52 DEBUG downloader: download finished (read 127 bytes)
05-03 01:52 DEBUG downloader: downloading [http://cdimage.ubuntu.com/kubuntu/daily-live/current/MD5SUMS-metalink.gpg](http://cdimage.ubuntu.com/kubuntu/daily-live/current/MD5SUMS-metalink.gpg) > C:\ubuntu\install
05-03 01:52 DEBUG downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://cdimage.ubuntu.com/kubuntu/daily-live/current/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
05-03 01:52 DEBUG downloader: download finished (read 189 bytes)
05-03 01:52 INFO saplog: Verified a signature from ID:'46181433FBB75451'.
05-03 01:52 INFO saplog: Checking block bindings..
05-03 01:52 INFO saplog: Key verified successfully.
05-03 01:52 DEBUG CommonBackend: metalink md5sums:
213076dbd7cad431df67f13607a906b3 jaunty-desktop-amd64.metalink
42a2643f19a353ea1adb0c10acdd34e7 jaunty-desktop-i386.metalink
05-03 01:52 DEBUG TaskList: #### Finished get_metalink
05-03 01:52 DEBUG TaskList: New task get_file_md5
05-03 01:52 DEBUG TaskList: #### Running get_file_md5...
05-03 01:52 DEBUG TaskList: #### Finished get_file_md5
05-03 01:52 DEBUG TaskList: ### Finished check_iso
05-03 01:52 DEBUG TaskList: ## Finished use_cd
05-03 01:52 DEBUG TaskList: ## Running extract_kernel...
05-03 01:52 DEBUG CommonBackend: Copying files from CD I:\
05-03 01:52 DEBUG CommonBackend: Checking kernel, initrd and md5sums
05-03 01:52 DEBUG CommonBackend: checking C:\ubuntu\install\boot\vmlinuz
05-03 01:52 DEBUG CommonBackend: C:\ubuntu\install\boot\vmlinuz md5 = d15243d1203d0aecf187ff969d6764ea == d15243d1203d0aecf187ff969d6764ea
05-03 01:52 DEBUG CommonBackend: checking C:\ubuntu\install\boot\initrd.gz
05-03 01:52 DEBUG CommonBackend: C:\ubuntu\install\boot\initrd.gz md5 = f870f36498107f36b716dbba9c41dc39 == f870f36498107f36b716dbba9c41dc39
05-03 01:52 DEBUG TaskList: ## Finished extract_kernel
05-03 01:52 DEBUG TaskList: ## Running create_preseed_cdboot...
05-03 01:52 DEBUG TaskList: ## Finished create_preseed_cdboot
05-03 01:52 DEBUG TaskList: ## Running modify_bootloader...
05-03 01:52 DEBUG TaskList: New task modify_bcd
05-03 01:52 DEBUG TaskList: ### Running modify_bcd...
05-03 01:52 DEBUG WindowsBackend: modify_bcd Drive(C: hd 128435.859375 mb free )
05-03 01:52 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {4e25f714-380e-11de-97b1-98e2532e6882}
05-03 01:52 DEBUG TaskList: ### Finished modify_bcd
05-03 01:52 DEBUG TaskList: ## Finished modify_bootloader
05-03 01:52 DEBUG TaskList: ## Running modify_grub_configuration...
05-03 01:52 DEBUG TaskList: ## Finished modify_grub_configuration
05-03 01:52 DEBUG TaskList: ## Running uncompress_files...
05-03 01:52 DEBUG WindowsBackend: compact C:\ubuntu\install\boot /U /A /F
05-03 01:52 DEBUG WindowsBackend: compact C:\ubuntu\install\boot\*.* /U /A /F
05-03 01:52 DEBUG TaskList: ## Finished uncompress_files
05-03 01:52 DEBUG TaskList: ## Running eject_cd...
05-03 01:52 DEBUG TaskList: ## Finished eject_cd
05-03 01:52 DEBUG TaskList: # Finished tasklist
05-03 01:52 INFO root: Almost finished installing
05-03 01:53 INFO root: Finished installation
05-03 01:53 DEBUG root: application.quit
05-03 01:53 DEBUG WindowsFrontend: frontend.quit
05-03 01:53 DEBUG WindowsFrontend: frontend.on_quit
05-03 01:53 DEBUG root: application.on_quit
05-03 01:53 INFO root: sys.exit
05-03 02:29 INFO root: === wubi 9.04 rev128 ===
05-03 02:29 DEBUG root: Logfile is c:\users\george\appdata\local\temp\wubi-9.04-rev128.log
05-03 02:29 DEBUG root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\George\\AppData\\Local\\Microsoft\\Windows\\Burn\\Burn\\wubi.exe"']
05-03 02:29 DEBUG CommonBackend: data_dir=C:\Users\George\AppData\Local\Temp\pyl9F98.tmp\data
05-03 02:29 DEBUG WindowsBackend: 7z=C:\Users\George\AppData\Local\Temp\pyl9F98.tmp\bin\7z.exe
05-03 02:29 DEBUG CommonBackend: Fetching basic info...
05-03 02:29 DEBUG CommonBackend: original_exe=C:\Users\George\AppData\Local\Microsoft\Windows\Burn\Burn\wubi.exe
05-03 02:29 DEBUG CommonBackend: platform=win32
05-03 02:29 DEBUG CommonBackend: osname=nt
05-03 02:29 DEBUG CommonBackend: language=en_US
05-03 02:29 DEBUG CommonBackend: encoding=cp1252
05-03 02:29 DEBUG WindowsBackend: arch=amd64
05-03 02:29 DEBUG CommonBackend: Parsing isolist=C:\Users\George\AppData\Local\Temp\pyl9F98.tmp\data\isolist.ini
05-03 02:29 DEBUG CommonBackend: Adding distro Xubuntu-i386
05-03 02:29 DEBUG CommonBackend: Adding distro Xubuntu-amd64
05-03 02:29 DEBUG CommonBackend: Adding distro Kubuntu-amd64
05-03 02:29 DEBUG CommonBackend: Adding distro Mythbuntu-i386
05-03 02:29 DEBUG CommonBackend: Adding distro Ubuntu-amd64
05-03 02:29 DEBUG CommonBackend: Adding distro Ubuntu-i386
05-03 02:29 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
05-03 02:29 DEBUG CommonBackend: Adding distro Kubuntu-i386
05-03 02:29 DEBUG WindowsBackend: Fetching host info...
05-03 02:29 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-03 02:29 DEBUG WindowsBackend: windows version=vista
05-03 02:29 DEBUG WindowsBackend: windows_version2=Windows 7 Ultimate
05-03 02:29 DEBUG WindowsBackend: windows_sp=None
05-03 02:29 DEBUG WindowsBackend: windows_build=7000
05-03 02:29 DEBUG WindowsBackend: gmt=-5
05-03 02:29 DEBUG WindowsBackend: country=US
05-03 02:29 DEBUG WindowsBackend: timezone=America/New_York
05-03 02:29 DEBUG WindowsBackend: windows_username=George
05-03 02:29 DEBUG WindowsBackend: user_full_name=George
05-03 02:29 DEBUG WindowsBackend: user_directory=George
05-03 02:29 DEBUG WindowsBackend: windows_language_code=1033
05-03 02:29 DEBUG WindowsBackend: windows_language=English
05-03 02:29 DEBUG WindowsBackend: processor_name=Intel(R) Core(TM) i7 CPU 920 @ 2.67GHz
05-03 02:29 DEBUG WindowsBackend: bootloader=vista
05-03 02:29 DEBUG WindowsBackend: system_drive=Drive(C: hd 126339.714844 mb free )
05-03 02:29 DEBUG WindowsBackend: drive=Drive(C: hd 126339.714844 mb free )
05-03 02:29 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
05-03 02:29 DEBUG WindowsBackend: drive=Drive(E: cd 0.0 mb free )
05-03 02:29 DEBUG WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-03 02:29 DEBUG WindowsBackend: previous_target_dir=C:\ubuntu
05-03 02:29 DEBUG WindowsBackend: previous_distro_name=Kubuntu
05-03 02:29 DEBUG WindowsBackend: keyboard_id=67699721
05-03 02:29 DEBUG WindowsBackend: keyboard_layout=us
05-03 02:29 DEBUG WindowsBackend: keyboard_variant=
05-03 02:29 DEBUG CommonBackend: locale=en_US.UTF-8
05-03 02:29 DEBUG WindowsBackend: total_memory_mb=4095.99999905
05-03 02:29 DEBUG CommonBackend: Searching ISOs on USB devices
05-03 02:29 DEBUG CommonBackend: Searching for local CDs
05-03 02:29 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pyl9F98.tmp is a valid Ubuntu CD
05-03 02:29 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pyl9F98.tmp\casper\filesystem.squashfs
05-03 02:29 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pyl9F98.tmp is a valid Ubuntu CD
05-03 02:29 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pyl9F98.tmp\casper\filesystem.squashfs
05-03 02:29 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pyl9F98.tmp is a valid Kubuntu CD
05-03 02:29 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pyl9F98.tmp\casper\filesystem.squashfs
05-03 02:29 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pyl9F98.tmp is a valid Kubuntu CD
05-03 02:29 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pyl9F98.tmp\casper\filesystem.squashfs
05-03 02:29 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pyl9F98.tmp is a valid Xubuntu CD
05-03 02:29 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pyl9F98.tmp\casper\filesystem.squashfs
05-03 02:29 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pyl9F98.tmp is a valid Xubuntu CD
05-03 02:29 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pyl9F98.tmp\casper\filesystem.squashfs
05-03 02:29 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pyl9F98.tmp is a valid Mythbuntu CD
05-03 02:29 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pyl9F98.tmp\casper\filesystem.squashfs
05-03 02:29 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pyl9F98.tmp is a valid Mythbuntu CD
05-03 02:29 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pyl9F98.tmp\casper\filesystem.squashfs
05-03 02:29 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
05-03 02:29 DEBUG Distro: info=Ubuntu 8.10 "Intrepid Ibex" - Release i386 (20081029.5)
05-03 02:29 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '8.10', 'build': '20081029.5', 'codename': 'Intrepid Ibex', 'arch': 'i386'}
05-03 02:29 DEBUG Distro: wrong version: 8.10 != 9.04
05-03 02:29 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
05-03 02:29 DEBUG Distro: wrong version: 8.10 != 9.04
05-03 02:29 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
05-03 02:29 DEBUG Distro: wrong name: Ubuntu != Kubuntu
05-03 02:29 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
05-03 02:29 DEBUG Distro: wrong name: Ubuntu != Kubuntu
05-03 02:29 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
05-03 02:29 DEBUG Distro: wrong name: Ubuntu != Xubuntu
05-03 02:29 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
05-03 02:29 DEBUG Distro: wrong name: Ubuntu != Xubuntu
05-03 02:29 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
05-03 02:29 DEBUG Distro: wrong name: Ubuntu != Mythbuntu
05-03 02:29 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
05-03 02:29 DEBUG Distro: wrong name: Ubuntu != Mythbuntu
05-03 02:29 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
05-03 02:29 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
05-03 02:29 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
05-03 02:29 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
05-03 02:29 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
05-03 02:29 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
05-03 02:29 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
05-03 02:29 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
05-03 02:29 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
05-03 02:29 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
05-03 02:29 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
05-03 02:29 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
05-03 02:29 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
05-03 02:29 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
05-03 02:29 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
05-03 02:29 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
05-03 02:29 INFO root: Already installed, running the uninstaller...
05-03 02:29 INFO root: Running the uninstaller...
05-03 02:29 INFO CommonBackend: This is the uninstaller running
05-03 02:29 DEBUG WindowsFrontend: __init__...
05-03 02:29 DEBUG WindowsFrontend: on_init...
05-03 02:29 INFO root: Received settings
05-03 02:29 DEBUG TaskList: # Running tasklist...
05-03 02:29 DEBUG TaskList: ## Running Backup ISO...
05-03 02:29 DEBUG TaskList: ## Finished Backup ISO
05-03 02:29 DEBUG TaskList: ## Running Remove bootloader entry...
05-03 02:29 DEBUG WindowsBackend: Removing bcd entry {4e25f714-380e-11de-97b1-98e2532e6882}
05-03 02:29 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
05-03 02:29 DEBUG WindowsBackend: undo_bootini C:
05-03 02:29 DEBUG WindowsBackend: undo_configsys Drive(C: hd 126339.714844 mb free )
05-03 02:29 DEBUG TaskList: ## Finished Remove bootloader entry
05-03 02:29 DEBUG TaskList: ## Running Remove target dir...
05-03 02:29 DEBUG CommonBackend: Deleting C:\ubuntu
05-03 02:29 DEBUG TaskList: ## Finished Remove target dir
05-03 02:29 DEBUG TaskList: ## Running Remove registry key...
05-03 02:29 DEBUG TaskList: ## Finished Remove registry key
05-03 02:29 DEBUG TaskList: # Finished tasklist
05-03 02:29 INFO root: Almost finished uninstalling
05-03 02:29 INFO root: Finished uninstallation
05-03 02:29 DEBUG CommonBackend: Fetching basic info...
05-03 02:29 DEBUG CommonBackend: original_exe=C:\Users\George\AppData\Local\Microsoft\Windows\Burn\Burn\wubi.exe
05-03 02:29 DEBUG CommonBackend: platform=win32
05-03 02:29 DEBUG CommonBackend: osname=nt
05-03 02:29 DEBUG CommonBackend: language=en_US
05-03 02:29 DEBUG CommonBackend: encoding=cp1252
05-03 02:29 DEBUG WindowsBackend: arch=amd64
05-03 02:29 DEBUG CommonBackend: Parsing isolist=C:\Users\George\AppData\Local\Temp\pyl9F98.tmp\data\isolist.ini
05-03 02:29 DEBUG CommonBackend: Adding distro Xubuntu-i386
05-03 02:29 DEBUG CommonBackend: Adding distro Xubuntu-amd64
05-03 02:29 DEBUG CommonBackend: Adding distro Kubuntu-amd64
05-03 02:29 DEBUG CommonBackend: Adding distro Mythbuntu-i386
05-03 02:29 DEBUG CommonBackend: Adding distro Ubuntu-amd64
05-03 02:29 DEBUG CommonBackend: Adding distro Ubuntu-i386
05-03 02:29 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
05-03 02:29 DEBUG CommonBackend: Adding distro Kubuntu-i386
05-03 02:29 DEBUG WindowsBackend: Fetching host info...
05-03 02:29 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-03 02:29 DEBUG WindowsBackend: windows version=vista
05-03 02:29 DEBUG WindowsBackend: windows_version2=Windows 7 Ultimate
05-03 02:29 DEBUG WindowsBackend: windows_sp=None
05-03 02:29 DEBUG WindowsBackend: windows_build=7000
05-03 02:29 DEBUG WindowsBackend: gmt=-5
05-03 02:29 DEBUG WindowsBackend: country=US
05-03 02:29 DEBUG WindowsBackend: timezone=America/New_York
05-03 02:29 DEBUG WindowsBackend: windows_username=George
05-03 02:29 DEBUG WindowsBackend: user_full_name=George
05-03 02:29 DEBUG WindowsBackend: user_directory=George
05-03 02:29 DEBUG WindowsBackend: windows_language_code=1033
05-03 02:29 DEBUG WindowsBackend: windows_language=English
05-03 02:29 DEBUG WindowsBackend: processor_name=Intel(R) Core(TM) i7 CPU 920 @ 2.67GHz
05-03 02:29 DEBUG WindowsBackend: bootloader=vista
05-03 02:29 DEBUG WindowsBackend: system_drive=Drive(C: hd 127047.625 mb free )
05-03 02:29 DEBUG WindowsBackend: drive=Drive(C: hd 127047.625 mb free )
05-03 02:29 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
05-03 02:29 DEBUG WindowsBackend: drive=Drive(E: cd 0.0 mb free )
05-03 02:29 DEBUG WindowsBackend: uninstaller_path=None
05-03 02:29 DEBUG WindowsBackend: previous_target_dir=None
05-03 02:29 DEBUG WindowsBackend: previous_distro_name=None
05-03 02:29 DEBUG WindowsBackend: keyboard_id=67699721
05-03 02:29 DEBUG WindowsBackend: keyboard_layout=us
05-03 02:29 DEBUG WindowsBackend: keyboard_variant=
05-03 02:29 DEBUG CommonBackend: locale=en_US.UTF-8
05-03 02:29 DEBUG WindowsBackend: total_memory_mb=4095.99999905
05-03 02:29 DEBUG CommonBackend: Searching ISOs on USB devices
05-03 02:29 DEBUG CommonBackend: Searching for local CDs
05-03 02:29 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pyl9F98.tmp is a valid Ubuntu CD
05-03 02:29 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pyl9F98.tmp\casper\filesystem.squashfs
05-03 02:29 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pyl9F98.tmp is a valid Ubuntu CD
05-03 02:29 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pyl9F98.tmp\casper\filesystem.squashfs
05-03 02:29 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pyl9F98.tmp is a valid Kubuntu CD
05-03 02:29 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pyl9F98.tmp\casper\filesystem.squashfs
05-03 02:29 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pyl9F98.tmp is a valid Kubuntu CD
05-03 02:29 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pyl9F98.tmp\casper\filesystem.squashfs
05-03 02:29 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pyl9F98.tmp is a valid Xubuntu CD
05-03 02:29 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pyl9F98.tmp\casper\filesystem.squashfs
05-03 02:29 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pyl9F98.tmp is a valid Xubuntu CD
05-03 02:29 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pyl9F98.tmp\casper\filesystem.squashfs
05-03 02:29 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pyl9F98.tmp is a valid Mythbuntu CD
05-03 02:29 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pyl9F98.tmp\casper\filesystem.squashfs
05-03 02:29 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pyl9F98.tmp is a valid Mythbuntu CD
05-03 02:29 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pyl9F98.tmp\casper\filesystem.squashfs
05-03 02:29 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
05-03 02:29 DEBUG Distro: wrong version: 8.10 != 9.04
05-03 02:29 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
05-03 02:29 DEBUG Distro: wrong version: 8.10 != 9.04
05-03 02:29 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
05-03 02:29 DEBUG Distro: wrong name: Ubuntu != Kubuntu
05-03 02:29 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
05-03 02:29 DEBUG Distro: wrong name: Ubuntu != Kubuntu
05-03 02:29 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
05-03 02:29 DEBUG Distro: wrong name: Ubuntu != Xubuntu
05-03 02:29 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
05-03 02:29 DEBUG Distro: wrong name: Ubuntu != Xubuntu
05-03 02:29 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
05-03 02:29 DEBUG Distro: wrong name: Ubuntu != Mythbuntu
05-03 02:29 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
05-03 02:29 DEBUG Distro: wrong name: Ubuntu != Mythbuntu
05-03 02:29 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
05-03 02:29 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
05-03 02:29 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
05-03 02:29 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
05-03 02:29 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
05-03 02:29 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
05-03 02:29 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
05-03 02:29 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
05-03 02:29 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
05-03 02:29 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
05-03 02:29 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
05-03 02:29 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
05-03 02:29 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
05-03 02:29 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
05-03 02:29 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
05-03 02:29 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
05-03 02:29 INFO root: Running the installer...
05-03 02:30 INFO WindowsFrontend: Operation cancelled
05-03 02:30 DEBUG WindowsFrontend: frontend.quit
05-03 02:30 DEBUG WindowsFrontend: frontend.on_quit
05-03 02:30 DEBUG root: application.on_quit
05-03 02:30 INFO root: sys.exit
05-03 03:36 INFO root: === wubi 9.04 rev128 ===
05-03 03:36 DEBUG root: Logfile is c:\users\george\appdata\local\temp\wubi-9.04-rev128.log
05-03 03:36 DEBUG root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
05-03 03:36 DEBUG CommonBackend: data_dir=C:\Users\George\AppData\Local\Temp\pylD068.tmp\data
05-03 03:36 DEBUG WindowsBackend: 7z=C:\Users\George\AppData\Local\Temp\pylD068.tmp\bin\7z.exe
05-03 03:36 DEBUG CommonBackend: Fetching basic info...
05-03 03:36 DEBUG CommonBackend: original_exe=D:\wubi.exe
05-03 03:36 DEBUG CommonBackend: platform=win32
05-03 03:36 DEBUG CommonBackend: osname=nt
05-03 03:36 DEBUG CommonBackend: language=en_US
05-03 03:36 DEBUG CommonBackend: encoding=cp1252
05-03 03:36 DEBUG WindowsBackend: arch=amd64
05-03 03:36 DEBUG CommonBackend: Parsing isolist=C:\Users\George\AppData\Local\Temp\pylD068.tmp\data\isolist.ini
05-03 03:36 DEBUG CommonBackend: Adding distro Xubuntu-i386
05-03 03:36 DEBUG CommonBackend: Adding distro Xubuntu-amd64
05-03 03:36 DEBUG CommonBackend: Adding distro Kubuntu-amd64
05-03 03:36 DEBUG CommonBackend: Adding distro Mythbuntu-i386
05-03 03:36 DEBUG CommonBackend: Adding distro Ubuntu-amd64
05-03 03:36 DEBUG CommonBackend: Adding distro Ubuntu-i386
05-03 03:36 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
05-03 03:36 DEBUG CommonBackend: Adding distro Kubuntu-i386
05-03 03:36 DEBUG WindowsBackend: Fetching host info...
05-03 03:36 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-03 03:36 DEBUG WindowsBackend: windows version=vista
05-03 03:36 DEBUG WindowsBackend: windows_version2=Windows 7 Ultimate
05-03 03:36 DEBUG WindowsBackend: windows_sp=None
05-03 03:36 DEBUG WindowsBackend: windows_build=7000
05-03 03:36 DEBUG WindowsBackend: gmt=-5
05-03 03:36 DEBUG WindowsBackend: country=US
05-03 03:36 DEBUG WindowsBackend: timezone=America/New_York
05-03 03:36 DEBUG WindowsBackend: windows_username=George
05-03 03:36 DEBUG WindowsBackend: user_full_name=George
05-03 03:36 DEBUG WindowsBackend: user_directory=George
05-03 03:36 DEBUG WindowsBackend: windows_language_code=1033
05-03 03:36 DEBUG WindowsBackend: windows_language=English
05-03 03:36 DEBUG WindowsBackend: processor_name=Intel(R) Core(TM) i7 CPU 920 @ 2.67GHz
05-03 03:36 DEBUG WindowsBackend: bootloader=vista
05-03 03:36 DEBUG WindowsBackend: system_drive=Drive(C: hd 123708.5 mb free )
05-03 03:36 DEBUG WindowsBackend: drive=Drive(C: hd 123708.5 mb free )
05-03 03:36 DEBUG WindowsBackend: drive=Drive(D: cd 2.5 mb free udf)
05-03 03:36 DEBUG WindowsBackend: drive=Drive(E: cd 0.0 mb free )
05-03 03:36 DEBUG WindowsBackend: drive=Drive(F: removable 95.08203125 mb free fat32)
05-03 03:36 DEBUG WindowsBackend: uninstaller_path=None
05-03 03:36 DEBUG WindowsBackend: previous_target_dir=None
05-03 03:36 DEBUG WindowsBackend: previous_distro_name=None
05-03 03:36 DEBUG WindowsBackend: keyboard_id=67699721
05-03 03:36 DEBUG WindowsBackend: keyboard_layout=us
05-03 03:36 DEBUG WindowsBackend: keyboard_variant=
05-03 03:36 DEBUG CommonBackend: locale=en_US.UTF-8
05-03 03:36 DEBUG WindowsBackend: total_memory_mb=4095.99999905
05-03 03:36 DEBUG CommonBackend: Searching ISOs on USB devices
05-03 03:36 DEBUG CommonBackend: Searching for local CDs
05-03 03:36 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pylD068.tmp is a valid Ubuntu CD
05-03 03:36 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pylD068.tmp\casper\filesystem.squashfs
05-03 03:36 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pylD068.tmp is a valid Ubuntu CD
05-03 03:36 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pylD068.tmp\casper\filesystem.squashfs
05-03 03:36 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pylD068.tmp is a valid Kubuntu CD
05-03 03:36 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pylD068.tmp\casper\filesystem.squashfs
05-03 03:36 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pylD068.tmp is a valid Kubuntu CD
05-03 03:36 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pylD068.tmp\casper\filesystem.squashfs
05-03 03:36 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pylD068.tmp is a valid Xubuntu CD
05-03 03:36 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pylD068.tmp\casper\filesystem.squashfs
05-03 03:36 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pylD068.tmp is a valid Xubuntu CD
05-03 03:36 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pylD068.tmp\casper\filesystem.squashfs
05-03 03:36 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pylD068.tmp is a valid Mythbuntu CD
05-03 03:36 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pylD068.tmp\casper\filesystem.squashfs
05-03 03:36 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pylD068.tmp is a valid Mythbuntu CD
05-03 03:36 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pylD068.tmp\casper\filesystem.squashfs
05-03 03:36 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
05-03 03:36 DEBUG Distro: info=Kubuntu 9.04 "Jaunty Jackalope" - Release amd64 (20090420.1)
05-03 03:36 DEBUG Distro: parsed info={'name': 'Kubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'amd64'}
05-03 03:36 DEBUG Distro: wrong name: Kubuntu != Ubuntu
05-03 03:36 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
05-03 03:36 DEBUG Distro: wrong name: Kubuntu != Ubuntu
05-03 03:36 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
05-03 03:36 INFO Distro: Found a valid CD for Kubuntu: D:\
05-03 03:36 INFO root: Running the CD menu...
05-03 03:36 DEBUG WindowsFrontend: __init__...
05-03 03:36 DEBUG WindowsFrontend: on_init...
05-03 03:37 DEBUG root: application.quit
05-03 03:37 DEBUG WindowsFrontend: frontend.quit
05-03 03:37 DEBUG WindowsFrontend: frontend.on_quit
05-03 03:37 DEBUG root: application.on_quit
05-03 03:37 INFO root: sys.exit
05-03 03:37 INFO root: === wubi 9.04 rev128 ===
05-03 03:37 DEBUG root: Logfile is c:\users\george\appdata\local\temp\wubi-9.04-rev128.log
05-03 03:37 DEBUG root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
05-03 03:37 DEBUG CommonBackend: data_dir=C:\Users\George\AppData\Local\Temp\pyl361D.tmp\data
05-03 03:37 DEBUG WindowsBackend: 7z=C:\Users\George\AppData\Local\Temp\pyl361D.tmp\bin\7z.exe
05-03 03:37 DEBUG CommonBackend: Fetching basic info...
05-03 03:37 DEBUG CommonBackend: original_exe=D:\wubi.exe
05-03 03:37 DEBUG CommonBackend: platform=win32
05-03 03:37 DEBUG CommonBackend: osname=nt
05-03 03:37 DEBUG CommonBackend: language=en_US
05-03 03:37 DEBUG CommonBackend: encoding=cp1252
05-03 03:37 DEBUG WindowsBackend: arch=amd64
05-03 03:37 DEBUG CommonBackend: Parsing isolist=C:\Users\George\AppData\Local\Temp\pyl361D.tmp\data\isolist.ini
05-03 03:37 DEBUG CommonBackend: Adding distro Xubuntu-i386
05-03 03:37 DEBUG CommonBackend: Adding distro Xubuntu-amd64
05-03 03:37 DEBUG CommonBackend: Adding distro Kubuntu-amd64
05-03 03:37 DEBUG CommonBackend: Adding distro Mythbuntu-i386
05-03 03:37 DEBUG CommonBackend: Adding distro Ubuntu-amd64
05-03 03:37 DEBUG CommonBackend: Adding distro Ubuntu-i386
05-03 03:37 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
05-03 03:37 DEBUG CommonBackend: Adding distro Kubuntu-i386
05-03 03:37 DEBUG WindowsBackend: Fetching host info...
05-03 03:37 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-03 03:37 DEBUG WindowsBackend: windows version=vista
05-03 03:37 DEBUG WindowsBackend: windows_version2=Windows 7 Ultimate
05-03 03:37 DEBUG WindowsBackend: windows_sp=None
05-03 03:37 DEBUG WindowsBackend: windows_build=7000
05-03 03:37 DEBUG WindowsBackend: gmt=-5
05-03 03:37 DEBUG WindowsBackend: country=US
05-03 03:37 DEBUG WindowsBackend: timezone=America/New_York
05-03 03:37 DEBUG WindowsBackend: windows_username=George
05-03 03:37 DEBUG WindowsBackend: user_full_name=George
05-03 03:37 DEBUG WindowsBackend: user_directory=George
05-03 03:37 DEBUG WindowsBackend: windows_language_code=1033
05-03 03:37 DEBUG WindowsBackend: windows_language=English
05-03 03:37 DEBUG WindowsBackend: processor_name=Intel(R) Core(TM) i7 CPU 920 @ 2.67GHz
05-03 03:37 DEBUG WindowsBackend: bootloader=vista
05-03 03:37 DEBUG WindowsBackend: system_drive=Drive(C: hd 123707.855469 mb free )
05-03 03:37 DEBUG WindowsBackend: drive=Drive(C: hd 123707.855469 mb free )
05-03 03:37 DEBUG WindowsBackend: drive=Drive(D: cd 2.5 mb free udf)
05-03 03:37 DEBUG WindowsBackend: drive=Drive(E: cd 0.0 mb free )
05-03 03:37 DEBUG WindowsBackend: drive=Drive(F: removable 95.08203125 mb free fat32)
05-03 03:37 DEBUG WindowsBackend: uninstaller_path=None
05-03 03:37 DEBUG WindowsBackend: previous_target_dir=None
05-03 03:37 DEBUG WindowsBackend: previous_distro_name=None
05-03 03:37 DEBUG WindowsBackend: keyboard_id=67699721
05-03 03:37 DEBUG WindowsBackend: keyboard_layout=us
05-03 03:37 DEBUG WindowsBackend: keyboard_variant=
05-03 03:37 DEBUG CommonBackend: locale=en_US.UTF-8
05-03 03:37 DEBUG WindowsBackend: total_memory_mb=4095.99999905
05-03 03:37 DEBUG CommonBackend: Searching ISOs on USB devices
05-03 03:37 DEBUG CommonBackend: Searching for local CDs
05-03 03:37 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pyl361D.tmp is a valid Ubuntu CD
05-03 03:37 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pyl361D.tmp\casper\filesystem.squashfs
05-03 03:37 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pyl361D.tmp is a valid Ubuntu CD
05-03 03:37 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pyl361D.tmp\casper\filesystem.squashfs
05-03 03:37 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pyl361D.tmp is a valid Kubuntu CD
05-03 03:37 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pyl361D.tmp\casper\filesystem.squashfs
05-03 03:37 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pyl361D.tmp is a valid Kubuntu CD
05-03 03:37 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pyl361D.tmp\casper\filesystem.squashfs
05-03 03:37 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pyl361D.tmp is a valid Xubuntu CD
05-03 03:37 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pyl361D.tmp\casper\filesystem.squashfs
05-03 03:37 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pyl361D.tmp is a valid Xubuntu CD
05-03 03:37 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pyl361D.tmp\casper\filesystem.squashfs
05-03 03:37 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pyl361D.tmp is a valid Mythbuntu CD
05-03 03:37 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pyl361D.tmp\casper\filesystem.squashfs
05-03 03:37 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pyl361D.tmp is a valid Mythbuntu CD
05-03 03:37 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pyl361D.tmp\casper\filesystem.squashfs
05-03 03:37 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
05-03 03:37 DEBUG Distro: info=Kubuntu 9.04 "Jaunty Jackalope" - Release amd64 (20090420.1)
05-03 03:37 DEBUG Distro: parsed info={'name': 'Kubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'amd64'}
05-03 03:37 DEBUG Distro: wrong name: Kubuntu != Ubuntu
05-03 03:37 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
05-03 03:37 DEBUG Distro: wrong name: Kubuntu != Ubuntu
05-03 03:37 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
05-03 03:37 INFO Distro: Found a valid CD for Kubuntu: D:\
05-03 03:37 INFO root: Running the CD menu...
05-03 03:37 DEBUG WindowsFrontend: __init__...
05-03 03:37 DEBUG WindowsFrontend: on_init...
05-03 03:37 INFO root: CD menu finished
05-03 03:37 INFO root: Running the installer...
05-03 03:40 DEBUG WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Kubuntu, language=English, username=george
05-03 03:40 INFO root: Received settings
05-03 03:40 DEBUG TaskList: # Running tasklist...
05-03 03:40 DEBUG TaskList: ## Running select_target_dir...
05-03 03:40 INFO WindowsBackend: Installing into C:\ubuntu
05-03 03:40 DEBUG TaskList: ## Finished select_target_dir
05-03 03:40 DEBUG TaskList: ## Running create_dir_structure...
05-03 03:40 DEBUG CommonBackend: Creating dir C:\ubuntu
05-03 03:40 DEBUG CommonBackend: Creating dir C:\ubuntu\disks
05-03 03:40 DEBUG CommonBackend: Creating dir C:\ubuntu\install
05-03 03:40 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot
05-03 03:40 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot
05-03 03:40 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-03 03:40 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-03 03:40 DEBUG TaskList: ## Finished create_dir_structure
05-03 03:40 DEBUG TaskList: ## Running uncompress_target_dir...
05-03 03:40 DEBUG TaskList: ## Finished uncompress_target_dir
05-03 03:40 DEBUG TaskList: ## Running create_uninstaller...
05-03 03:40 DEBUG WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
05-03 03:40 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-03 03:40 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-03 03:40 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Kubuntu
05-03 03:40 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Kubuntu.ico
05-03 03:40 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
05-03 03:40 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Kubuntu
05-03 03:40 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.kubuntu.org](http://www.kubuntu.org)
05-03 03:40 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-03 03:40 DEBUG TaskList: ## Finished create_uninstaller
05-03 03:40 DEBUG TaskList: ## Running copy_installation_files...
05-03 03:40 DEBUG WindowsBackend: Copying C:\Users\George\AppData\Local\Temp\pyl361D.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-03 03:40 DEBUG WindowsBackend: Copying C:\Users\George\AppData\Local\Temp\pyl361D.tmp\winboot -> C:\ubuntu\winboot
05-03 03:40 DEBUG WindowsBackend: Copying C:\Users\George\AppData\Local\Temp\pyl361D.tmp\data\images\Kubuntu.ico -> C:\ubuntu\Kubuntu.ico
05-03 03:40 DEBUG TaskList: ## Finished copy_installation_files
05-03 03:40 DEBUG TaskList: ## Running get_iso...
05-03 03:40 DEBUG TaskList: New task copy_file
05-03 03:40 DEBUG TaskList: ### Running copy_file...
05-03 03:40 ERROR TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 13] Permission denied
05-03 03:40 DEBUG TaskList: # Cancelling tasklist
05-03 03:40 ERROR root: [Errno 13] Permission denied
Traceback (most recent call last):
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 13] Permission denied
05-03 03:40 DEBUG TaskList: New task check_iso
05-03 03:40 DEBUG CommonBackend: Searching for local ISO
05-03 03:40 DEBUG CommonBackend: Could not find any ISO or CD, downloading one now
05-03 03:40 DEBUG TaskList: New task get_metalink
05-03 03:40 ERROR TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
05-03 03:40 DEBUG TaskList: # Cancelling tasklist
05-03 03:40 DEBUG TaskList: # Finished tasklist
05-03 03:42 INFO root: === wubi 9.04 rev128 ===
05-03 03:42 DEBUG root: Logfile is c:\users\george\appdata\local\temp\wubi-9.04-rev128.log
05-03 03:42 DEBUG root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
05-03 03:42 DEBUG CommonBackend: data_dir=C:\Users\George\AppData\Local\Temp\pyl41E0.tmp\data
05-03 03:42 DEBUG WindowsBackend: 7z=C:\Users\George\AppData\Local\Temp\pyl41E0.tmp\bin\7z.exe
05-03 03:42 DEBUG CommonBackend: Fetching basic info...
05-03 03:42 DEBUG CommonBackend: original_exe=D:\wubi.exe
05-03 03:42 DEBUG CommonBackend: platform=win32
05-03 03:42 DEBUG CommonBackend: osname=nt
05-03 03:42 DEBUG CommonBackend: language=en_US
05-03 03:42 DEBUG CommonBackend: encoding=cp1252
05-03 03:42 DEBUG WindowsBackend: arch=amd64
05-03 03:42 DEBUG CommonBackend: Parsing isolist=C:\Users\George\AppData\Local\Temp\pyl41E0.tmp\data\isolist.ini
05-03 03:42 DEBUG CommonBackend: Adding distro Xubuntu-i386
05-03 03:42 DEBUG CommonBackend: Adding distro Xubuntu-amd64
05-03 03:42 DEBUG CommonBackend: Adding distro Kubuntu-amd64
05-03 03:42 DEBUG CommonBackend: Adding distro Mythbuntu-i386
05-03 03:42 DEBUG CommonBackend: Adding distro Ubuntu-amd64
05-03 03:42 DEBUG CommonBackend: Adding distro Ubuntu-i386
05-03 03:42 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
05-03 03:42 DEBUG CommonBackend: Adding distro Kubuntu-i386
05-03 03:42 DEBUG WindowsBackend: Fetching host info...
05-03 03:42 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-03 03:42 DEBUG WindowsBackend: windows version=vista
05-03 03:42 DEBUG WindowsBackend: windows_version2=Windows 7 Ultimate
05-03 03:42 DEBUG WindowsBackend: windows_sp=None
05-03 03:42 DEBUG WindowsBackend: windows_build=7000
05-03 03:42 DEBUG WindowsBackend: gmt=-5
05-03 03:42 DEBUG WindowsBackend: country=US
05-03 03:42 DEBUG WindowsBackend: timezone=America/New_York
05-03 03:42 DEBUG WindowsBackend: windows_username=George
05-03 03:42 DEBUG WindowsBackend: user_full_name=George
05-03 03:42 DEBUG WindowsBackend: user_directory=George
05-03 03:42 DEBUG WindowsBackend: windows_language_code=1033
05-03 03:42 DEBUG WindowsBackend: windows_language=English
05-03 03:42 DEBUG WindowsBackend: processor_name=Intel(R) Core(TM) i7 CPU 920 @ 2.67GHz
05-03 03:42 DEBUG WindowsBackend: bootloader=vista
05-03 03:42 DEBUG WindowsBackend: system_drive=Drive(C: hd 123704.726563 mb free )
05-03 03:42 DEBUG WindowsBackend: drive=Drive(C: hd 123704.726563 mb free )
05-03 03:42 DEBUG WindowsBackend: drive=Drive(D: cd 2.5 mb free udf)
05-03 03:42 DEBUG WindowsBackend: drive=Drive(E: cd 0.0 mb free )
05-03 03:42 DEBUG WindowsBackend: drive=Drive(F: removable 3325.19140625 mb free fat32)
05-03 03:42 DEBUG WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-03 03:42 DEBUG WindowsBackend: previous_target_dir=C:\ubuntu
05-03 03:42 DEBUG WindowsBackend: previous_distro_name=Kubuntu
05-03 03:42 DEBUG WindowsBackend: keyboard_id=67699721
05-03 03:42 DEBUG WindowsBackend: keyboard_layout=us
05-03 03:42 DEBUG WindowsBackend: keyboard_variant=
05-03 03:42 DEBUG CommonBackend: locale=en_US.UTF-8
05-03 03:42 DEBUG WindowsBackend: total_memory_mb=4095.99999905
05-03 03:42 DEBUG CommonBackend: Searching ISOs on USB devices
05-03 03:42 DEBUG CommonBackend: Searching for local CDs
05-03 03:42 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pyl41E0.tmp is a valid Ubuntu CD
05-03 03:42 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pyl41E0.tmp\casper\filesystem.squashfs
05-03 03:42 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pyl41E0.tmp is a valid Ubuntu CD
05-03 03:42 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pyl41E0.tmp\casper\filesystem.squashfs
05-03 03:42 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pyl41E0.tmp is a valid Kubuntu CD
05-03 03:42 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pyl41E0.tmp\casper\filesystem.squashfs
05-03 03:42 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pyl41E0.tmp is a valid Kubuntu CD
05-03 03:42 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pyl41E0.tmp\casper\filesystem.squashfs
05-03 03:42 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pyl41E0.tmp is a valid Xubuntu CD
05-03 03:42 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pyl41E0.tmp\casper\filesystem.squashfs
05-03 03:42 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pyl41E0.tmp is a valid Xubuntu CD
05-03 03:42 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pyl41E0.tmp\casper\filesystem.squashfs
05-03 03:42 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pyl41E0.tmp is a valid Mythbuntu CD
05-03 03:42 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pyl41E0.tmp\casper\filesystem.squashfs
05-03 03:42 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pyl41E0.tmp is a valid Mythbuntu CD
05-03 03:42 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pyl41E0.tmp\casper\filesystem.squashfs
05-03 03:42 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
05-03 03:42 DEBUG Distro: info=Kubuntu 9.04 "Jaunty Jackalope" - Release amd64 (20090420.1)
05-03 03:42 DEBUG Distro: parsed info={'name': 'Kubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'amd64'}
05-03 03:42 DEBUG Distro: wrong name: Kubuntu != Ubuntu
05-03 03:42 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
05-03 03:42 DEBUG Distro: wrong name: Kubuntu != Ubuntu
05-03 03:42 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
05-03 03:42 INFO Distro: Found a valid CD for Kubuntu: D:\
05-03 03:42 INFO root: Running the CD menu...
05-03 03:42 DEBUG WindowsFrontend: __init__...
05-03 03:42 DEBUG WindowsFrontend: on_init...
05-03 03:42 INFO root: CD menu finished
05-03 03:42 INFO root: Already installed, running the uninstaller...
05-03 03:42 INFO root: Running the uninstaller...
05-03 03:42 INFO CommonBackend: This is the uninstaller running
05-03 03:42 INFO root: Received settings
05-03 03:42 DEBUG TaskList: # Running tasklist...
05-03 03:42 DEBUG TaskList: ## Running Backup ISO...
05-03 03:42 DEBUG TaskList: ## Finished Backup ISO
05-03 03:42 DEBUG TaskList: ## Running Remove bootloader entry...
05-03 03:42 DEBUG WindowsBackend: Could not find bcd id
05-03 03:42 DEBUG WindowsBackend: undo_bootini C:
05-03 03:42 DEBUG WindowsBackend: undo_configsys Drive(C: hd 123704.726563 mb free )
05-03 03:42 DEBUG WindowsBackend: undo_bootini F:
05-03 03:42 DEBUG WindowsBackend: undo_configsys Drive(F: removable 3325.19140625 mb free fat32)
05-03 03:42 DEBUG TaskList: ## Finished Remove bootloader entry
05-03 03:42 DEBUG TaskList: ## Running Remove target dir...
05-03 03:42 DEBUG CommonBackend: Deleting C:\ubuntu
05-03 03:42 DEBUG TaskList: ## Finished Remove target dir
05-03 03:42 DEBUG TaskList: ## Running Remove registry key...
05-03 03:42 DEBUG TaskList: ## Finished Remove registry key
05-03 03:42 DEBUG TaskList: # Finished tasklist
05-03 03:42 INFO root: Almost finished uninstalling
05-03 03:42 INFO root: Finished uninstallation
05-03 03:42 DEBUG CommonBackend: Fetching basic info...
05-03 03:42 DEBUG CommonBackend: original_exe=D:\wubi.exe
05-03 03:42 DEBUG CommonBackend: platform=win32
05-03 03:42 DEBUG CommonBackend: osname=nt
05-03 03:42 DEBUG CommonBackend: language=en_US
05-03 03:42 DEBUG CommonBackend: encoding=cp1252
05-03 03:42 DEBUG WindowsBackend: arch=amd64
05-03 03:42 DEBUG CommonBackend: Parsing isolist=C:\Users\George\AppData\Local\Temp\pyl41E0.tmp\data\isolist.ini
05-03 03:42 DEBUG CommonBackend: Adding distro Xubuntu-i386
05-03 03:42 DEBUG CommonBackend: Adding distro Xubuntu-amd64
05-03 03:42 DEBUG CommonBackend: Adding distro Kubuntu-amd64
05-03 03:42 DEBUG CommonBackend: Adding distro Mythbuntu-i386
05-03 03:42 DEBUG CommonBackend: Adding distro Ubuntu-amd64
05-03 03:42 DEBUG CommonBackend: Adding distro Ubuntu-i386
05-03 03:42 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
05-03 03:42 DEBUG CommonBackend: Adding distro Kubuntu-i386
05-03 03:42 DEBUG WindowsBackend: Fetching host info...
05-03 03:42 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-03 03:42 DEBUG WindowsBackend: windows version=vista
05-03 03:42 DEBUG WindowsBackend: windows_version2=Windows 7 Ultimate
05-03 03:42 DEBUG WindowsBackend: windows_sp=None
05-03 03:42 DEBUG WindowsBackend: windows_build=7000
05-03 03:42 DEBUG WindowsBackend: gmt=-5
05-03 03:42 DEBUG WindowsBackend: country=US
05-03 03:42 DEBUG WindowsBackend: timezone=America/New_York
05-03 03:42 DEBUG WindowsBackend: windows_username=George
05-03 03:42 DEBUG WindowsBackend: user_full_name=George
05-03 03:42 DEBUG WindowsBackend: user_directory=George
05-03 03:42 DEBUG WindowsBackend: windows_language_code=1033
05-03 03:42 DEBUG WindowsBackend: windows_language=English
05-03 03:42 DEBUG WindowsBackend: processor_name=Intel(R) Core(TM) i7 CPU 920 @ 2.67GHz
05-03 03:42 DEBUG WindowsBackend: bootloader=vista
05-03 03:42 DEBUG WindowsBackend: system_drive=Drive(C: hd 123706.621094 mb free )
05-03 03:42 DEBUG WindowsBackend: drive=Drive(C: hd 123706.621094 mb free )
05-03 03:42 DEBUG WindowsBackend: drive=Drive(D: cd 2.5 mb free udf)
05-03 03:42 DEBUG WindowsBackend: drive=Drive(E: cd 0.0 mb free )
05-03 03:42 DEBUG WindowsBackend: drive=Drive(F: removable 3325.19140625 mb free fat32)
05-03 03:42 DEBUG WindowsBackend: uninstaller_path=None
05-03 03:42 DEBUG WindowsBackend: previous_target_dir=None
05-03 03:42 DEBUG WindowsBackend: previous_distro_name=None
05-03 03:42 DEBUG WindowsBackend: keyboard_id=67699721
05-03 03:42 DEBUG WindowsBackend: keyboard_layout=us
05-03 03:42 DEBUG WindowsBackend: keyboard_variant=
05-03 03:42 DEBUG CommonBackend: locale=en_US.UTF-8
05-03 03:42 DEBUG WindowsBackend: total_memory_mb=4095.99999905
05-03 03:42 DEBUG CommonBackend: Searching ISOs on USB devices
05-03 03:42 DEBUG CommonBackend: Searching for local CDs
05-03 03:42 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pyl41E0.tmp is a valid Ubuntu CD
05-03 03:42 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pyl41E0.tmp\casper\filesystem.squashfs
05-03 03:42 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pyl41E0.tmp is a valid Ubuntu CD
05-03 03:42 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pyl41E0.tmp\casper\filesystem.squashfs
05-03 03:42 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pyl41E0.tmp is a valid Kubuntu CD
05-03 03:42 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pyl41E0.tmp\casper\filesystem.squashfs
05-03 03:42 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pyl41E0.tmp is a valid Kubuntu CD
05-03 03:42 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pyl41E0.tmp\casper\filesystem.squashfs
05-03 03:42 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pyl41E0.tmp is a valid Xubuntu CD
05-03 03:42 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pyl41E0.tmp\casper\filesystem.squashfs
05-03 03:42 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pyl41E0.tmp is a valid Xubuntu CD
05-03 03:42 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pyl41E0.tmp\casper\filesystem.squashfs
05-03 03:42 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pyl41E0.tmp is a valid Mythbuntu CD
05-03 03:42 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pyl41E0.tmp\casper\filesystem.squashfs
05-03 03:42 DEBUG Distro: checking whether C:\Users\George\AppData\Local\Temp\pyl41E0.tmp is a valid Mythbuntu CD
05-03 03:42 DEBUG Distro: does not contain C:\Users\George\AppData\Local\Temp\pyl41E0.tmp\casper\filesystem.squashfs
05-03 03:42 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
05-03 03:42 DEBUG Distro: wrong name: Kubuntu != Ubuntu
05-03 03:42 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
05-03 03:42 DEBUG Distro: wrong name: Kubuntu != Ubuntu
05-03 03:42 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
05-03 03:42 INFO Distro: Found a valid CD for Kubuntu: D:\
05-03 03:42 INFO root: Running the installer...
05-03 03:43 DEBUG WinuiInstallationPage: target_drive=C:, installation_size=30000MB, distro_name=Kubuntu, language=English, username=george
05-03 03:43 INFO root: Received settings
05-03 03:43 DEBUG TaskList: # Running tasklist...
05-03 03:43 DEBUG TaskList: ## Running select_target_dir...
05-03 03:43 INFO WindowsBackend: Installing into C:\ubuntu
05-03 03:43 DEBUG TaskList: ## Finished select_target_dir
05-03 03:43 DEBUG TaskList: ## Running create_dir_structure...
05-03 03:43 DEBUG CommonBackend: Creating dir C:\ubuntu
05-03 03:43 DEBUG CommonBackend: Creating dir C:\ubuntu\disks
05-03 03:43 DEBUG CommonBackend: Creating dir C:\ubuntu\install
05-03 03:43 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot
05-03 03:43 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot
05-03 03:43 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-03 03:43 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-03 03:43 DEBUG TaskList: ## Finished create_dir_structure
05-03 03:43 DEBUG TaskList: ## Running uncompress_target_dir...
05-03 03:43 DEBUG TaskList: ## Finished uncompress_target_dir
05-03 03:43 DEBUG TaskList: ## Running create_uninstaller...
05-03 03:43 DEBUG WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
05-03 03:43 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-03 03:43 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-03 03:43 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Kubuntu
05-03 03:43 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Kubuntu.ico
05-03 03:43 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
05-03 03:43 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Kubuntu
05-03 03:43 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.kubuntu.org](http://www.kubuntu.org)
05-03 03:43 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-03 03:43 DEBUG TaskList: ## Finished create_uninstaller
05-03 03:43 DEBUG TaskList: ## Running copy_installation_files...
05-03 03:43 DEBUG WindowsBackend: Copying C:\Users\George\AppData\Local\Temp\pyl41E0.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-03 03:43 DEBUG WindowsBackend: Copying C:\Users\George\AppData\Local\Temp\pyl41E0.tmp\winboot -> C:\ubuntu\winboot
05-03 03:43 DEBUG WindowsBackend: Copying C:\Users\George\AppData\Local\Temp\pyl41E0.tmp\data\images\Kubuntu.ico -> C:\ubuntu\Kubuntu.ico
05-03 03:43 DEBUG TaskList: ## Finished copy_installation_files
05-03 03:43 DEBUG TaskList: ## Running get_iso...
05-03 03:43 DEBUG TaskList: New task copy_file
05-03 03:43 DEBUG TaskList: ### Running copy_file...
05-03 03:43 ERROR TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 13] Permission denied
05-03 03:43 DEBUG TaskList: # Cancelling tasklist
05-03 03:43 DEBUG TaskList: New task check_iso
05-03 03:43 ERROR root: [Errno 13] Permission denied
Traceback (most recent call last):
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 13] Permission denied
05-03 03:43 DEBUG CommonBackend: Searching for local ISO
05-03 03:43 DEBUG CommonBackend: Could not find any ISO or CD, downloading one now
05-03 03:43 DEBUG TaskList: New task get_metalink
05-03 03:43 ERROR TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
05-03 03:43 DEBUG TaskList: # Cancelling tasklist
05-03 03:43 DEBUG TaskList: # Finished tasklist
 
 
Can anyone tell me about the failure to get the linkage to metalink or the error 13 mesage or anything else that might make sense out of this : ^ ((
 
 
Thanks
:(

---

