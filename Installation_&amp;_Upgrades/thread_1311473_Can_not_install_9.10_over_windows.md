---
title: "Can not install 9.10 over windows"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by millsware on 2009-11-02
I have an emachines T3085. I am trying to be able to have both Windows and Ubuntu on this computer. I've tried several times to install Ubuntu from the boot disk, and with Wubi, without success. When I try to install from the disk, it goes to the white logo on a black screen for a while, then switches to a screen with just a cursor. When I try to install with Wubi, I get the log file at the bottom. 
 
I do have to say that I am constantly getting a scsi/raid host controller warning on my computer, which I am also trying to figure out. It's not affecting how the computer works. Thanks for you help.
 
>  
11-01 20:18 INFO root: === wubi 9.10ubuntu1 rev160 ===
11-01 20:18 DEBUG root: Logfile is c:\docume~1\computer\locals~1\temp\wubi-9.10ubuntu1-rev160.log
11-01 20:18 DEBUG root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
11-01 20:18 DEBUG CommonBackend: data_dir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\data
11-01 20:18 DEBUG WindowsBackend: 7z=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\bin\7z.exe
11-01 20:18 DEBUG CommonBackend: Fetching basic info...
11-01 20:18 DEBUG CommonBackend: original_exe=D:\wubi.exe
11-01 20:18 DEBUG CommonBackend: platform=win32
11-01 20:18 DEBUG CommonBackend: osname=nt
11-01 20:18 DEBUG CommonBackend: language=en_US
11-01 20:18 DEBUG CommonBackend: encoding=cp1252
11-01 20:18 DEBUG WindowsBackend: arch=i386
11-01 20:18 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\data\isolist.ini
11-01 20:18 DEBUG CommonBackend: Adding distro Xubuntu-i386
11-01 20:18 DEBUG CommonBackend: Adding distro Xubuntu-amd64
11-01 20:18 DEBUG CommonBackend: Adding distro Kubuntu-amd64
11-01 20:18 DEBUG CommonBackend: Adding distro Mythbuntu-i386
11-01 20:18 DEBUG CommonBackend: Adding distro Ubuntu-amd64
11-01 20:18 DEBUG CommonBackend: Adding distro Ubuntu-i386
11-01 20:18 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
11-01 20:18 DEBUG CommonBackend: Adding distro Kubuntu-i386
11-01 20:18 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386
11-01 20:18 DEBUG CommonBackend: Adding distro UbuntuNetbookRemix-i386
11-01 20:18 DEBUG WindowsBackend: Fetching host info...
11-01 20:18 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-01 20:18 DEBUG WindowsBackend: windows version=xp
11-01 20:18 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
11-01 20:18 DEBUG WindowsBackend: windows_sp=Service Pack 3
11-01 20:18 DEBUG WindowsBackend: windows_build=2600
11-01 20:18 DEBUG WindowsBackend: gmt=-5
11-01 20:18 DEBUG WindowsBackend: country=US
11-01 20:18 DEBUG WindowsBackend: timezone=America/New_York
11-01 20:18 DEBUG WindowsBackend: windows_username=Computer
11-01 20:18 DEBUG WindowsBackend: user_full_name=Computer
11-01 20:18 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Computer
11-01 20:18 DEBUG WindowsBackend: windows_language_code=1033
11-01 20:18 DEBUG WindowsBackend: windows_language=English
11-01 20:18 DEBUG WindowsBackend: processor_name=AMD Athlon(tm) XP 3000+
11-01 20:18 DEBUG WindowsBackend: bootloader=xp
11-01 20:18 DEBUG WindowsBackend: system_drive=Drive(C: hd 101656.714844 mb free ntfs)
11-01 20:18 DEBUG WindowsBackend: drive=Drive(C: hd 101656.714844 mb free ntfs)
11-01 20:18 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
11-01 20:18 DEBUG WindowsBackend: drive=Drive(F: removable 0.0 mb free )
11-01 20:18 DEBUG WindowsBackend: drive=Drive(G: removable 0.0 mb free )
11-01 20:18 DEBUG WindowsBackend: drive=Drive(H: removable 0.0 mb free )
11-01 20:18 DEBUG WindowsBackend: drive=Drive(I: removable 0.0 mb free )
11-01 20:18 DEBUG WindowsBackend: drive=Drive(J: cd 0.0 mb free )
11-01 20:18 DEBUG WindowsBackend: uninstaller_path=None
11-01 20:18 DEBUG WindowsBackend: previous_target_dir=None
11-01 20:18 DEBUG WindowsBackend: previous_distro_name=None
11-01 20:18 DEBUG WindowsBackend: keyboard_id=67699721
11-01 20:18 DEBUG WindowsBackend: keyboard_layout=us
11-01 20:18 DEBUG WindowsBackend: keyboard_variant=
11-01 20:18 DEBUG CommonBackend: python locale=('en_US', 'cp1252')
11-01 20:18 DEBUG CommonBackend: locale=en_US.UTF-8
11-01 20:18 DEBUG WindowsBackend: total_memory_mb=1471.484375
11-01 20:18 DEBUG CommonBackend: Searching ISOs on USB devices
11-01 20:18 DEBUG CommonBackend: Searching for local CDs
11-01 20:18 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu CD
11-01 20:18 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-01 20:18 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu CD
11-01 20:18 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-01 20:18 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu Netbook Remix CD
11-01 20:18 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-01 20:18 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu CD
11-01 20:18 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-01 20:18 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu CD
11-01 20:18 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-01 20:18 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu Netbook CD
11-01 20:18 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-01 20:18 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Xubuntu CD
11-01 20:18 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-01 20:18 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Xubuntu CD
11-01 20:18 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-01 20:18 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Mythbuntu CD
11-01 20:18 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-01 20:18 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Mythbuntu CD
11-01 20:18 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-01 20:18 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
11-01 20:18 DEBUG Distro: parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
11-01 20:18 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
11-01 20:18 DEBUG Distro: wrong arch: i386 != amd64
11-01 20:18 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
11-01 20:18 INFO Distro: Found a valid CD for Ubuntu: D:\
11-01 20:18 INFO root: Running the CD menu...
11-01 20:18 DEBUG WindowsFrontend: __init__...
11-01 20:18 DEBUG WindowsFrontend: on_init...
11-01 20:18 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\translations, languages=['en_US', 'en']
11-01 20:18 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\translations, languages=['en_US', 'en']
11-01 20:19 INFO root: CD menu finished
11-01 20:19 INFO root: Running the CD menu...
11-01 20:19 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\translations, languages=['en_US', 'en']
11-01 20:19 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\translations, languages=['en_US', 'en']
11-01 20:19 INFO root: CD menu finished
11-01 20:19 INFO root: Running the CD menu...
11-01 20:19 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\translations, languages=['en_US', 'en']
11-01 20:19 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\translations, languages=['en_US', 'en']
11-01 20:19 INFO WindowsFrontend: Operation cancelled
11-01 20:19 DEBUG WindowsFrontend: frontend.quit
11-01 20:19 DEBUG WindowsFrontend: frontend.on_quit
11-01 20:19 DEBUG root: application.on_quit
11-01 20:19 INFO root: sys.exit
11-01 21:38 INFO root: === wubi 9.10ubuntu1 rev160 ===
11-01 21:38 DEBUG root: Logfile is c:\docume~1\computer\locals~1\temp\wubi-9.10ubuntu1-rev160.log
11-01 21:38 DEBUG root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
11-01 21:38 DEBUG CommonBackend: data_dir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\data
11-01 21:38 DEBUG WindowsBackend: 7z=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\bin\7z.exe
11-01 21:38 DEBUG CommonBackend: Fetching basic info...
11-01 21:38 DEBUG CommonBackend: original_exe=D:\wubi.exe
11-01 21:38 DEBUG CommonBackend: platform=win32
11-01 21:38 DEBUG CommonBackend: osname=nt
11-01 21:38 DEBUG CommonBackend: language=en_US
11-01 21:38 DEBUG CommonBackend: encoding=cp1252
11-01 21:38 DEBUG WindowsBackend: arch=i386
11-01 21:38 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\data\isolist.ini
11-01 21:38 DEBUG CommonBackend: Adding distro Xubuntu-i386
11-01 21:38 DEBUG CommonBackend: Adding distro Xubuntu-amd64
11-01 21:38 DEBUG CommonBackend: Adding distro Kubuntu-amd64
11-01 21:38 DEBUG CommonBackend: Adding distro Mythbuntu-i386
11-01 21:38 DEBUG CommonBackend: Adding distro Ubuntu-amd64
11-01 21:38 DEBUG CommonBackend: Adding distro Ubuntu-i386
11-01 21:38 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
11-01 21:38 DEBUG CommonBackend: Adding distro Kubuntu-i386
11-01 21:38 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386
11-01 21:38 DEBUG CommonBackend: Adding distro UbuntuNetbookRemix-i386
11-01 21:38 DEBUG WindowsBackend: Fetching host info...
11-01 21:38 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-01 21:38 DEBUG WindowsBackend: windows version=xp
11-01 21:38 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
11-01 21:38 DEBUG WindowsBackend: windows_sp=Service Pack 3
11-01 21:38 DEBUG WindowsBackend: windows_build=2600
11-01 21:38 DEBUG WindowsBackend: gmt=-5
11-01 21:38 DEBUG WindowsBackend: country=US
11-01 21:38 DEBUG WindowsBackend: timezone=America/New_York
11-01 21:38 DEBUG WindowsBackend: windows_username=Computer
11-01 21:38 DEBUG WindowsBackend: user_full_name=Computer
11-01 21:38 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Computer
11-01 21:38 DEBUG WindowsBackend: windows_language_code=1033
11-01 21:38 DEBUG WindowsBackend: windows_language=English
11-01 21:38 DEBUG WindowsBackend: processor_name=AMD Athlon(tm) XP 3000+
11-01 21:38 DEBUG WindowsBackend: bootloader=xp
11-01 21:38 DEBUG WindowsBackend: system_drive=Drive(C: hd 101627.203125 mb free ntfs)
11-01 21:38 DEBUG WindowsBackend: drive=Drive(C: hd 101627.203125 mb free ntfs)
11-01 21:38 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
11-01 21:38 DEBUG WindowsBackend: drive=Drive(F: removable 0.0 mb free )
11-01 21:38 DEBUG WindowsBackend: drive=Drive(G: removable 0.0 mb free )
11-01 21:38 DEBUG WindowsBackend: drive=Drive(H: removable 0.0 mb free )
11-01 21:38 DEBUG WindowsBackend: drive=Drive(I: removable 0.0 mb free )
11-01 21:38 DEBUG WindowsBackend: drive=Drive(J: cd 0.0 mb free )
11-01 21:38 DEBUG WindowsBackend: uninstaller_path=None
11-01 21:38 DEBUG WindowsBackend: previous_target_dir=None
11-01 21:38 DEBUG WindowsBackend: previous_distro_name=None
11-01 21:38 DEBUG WindowsBackend: keyboard_id=67699721
11-01 21:38 DEBUG WindowsBackend: keyboard_layout=us
11-01 21:38 DEBUG WindowsBackend: keyboard_variant=
11-01 21:38 DEBUG CommonBackend: python locale=('en_US', 'cp1252')
11-01 21:38 DEBUG CommonBackend: locale=en_US.UTF-8
11-01 21:38 DEBUG WindowsBackend: total_memory_mb=1471.484375
11-01 21:38 DEBUG CommonBackend: Searching ISOs on USB devices
11-01 21:38 DEBUG CommonBackend: Searching for local CDs
11-01 21:38 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu CD
11-01 21:38 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-01 21:38 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu CD
11-01 21:38 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-01 21:38 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu Netbook Remix CD
11-01 21:38 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-01 21:38 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu CD
11-01 21:38 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-01 21:38 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu CD
11-01 21:38 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-01 21:38 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu Netbook CD
11-01 21:38 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-01 21:38 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Xubuntu CD
11-01 21:38 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-01 21:38 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Xubuntu CD
11-01 21:38 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-01 21:38 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Mythbuntu CD
11-01 21:38 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-01 21:38 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Mythbuntu CD
11-01 21:38 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-01 21:38 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
11-01 21:38 DEBUG Distro: parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
11-01 21:38 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
11-01 21:38 DEBUG Distro: wrong arch: i386 != amd64
11-01 21:38 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
11-01 21:38 INFO Distro: Found a valid CD for Ubuntu: D:\
11-01 21:38 INFO root: Running the CD menu...
11-01 21:38 DEBUG WindowsFrontend: __init__...
11-01 21:38 DEBUG WindowsFrontend: on_init...
11-01 21:38 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\translations, languages=['en_US', 'en']
11-01 21:38 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\translations, languages=['en_US', 'en']
11-01 21:48 INFO WindowsFrontend: Operation cancelled
11-01 21:48 DEBUG WindowsFrontend: frontend.quit
11-01 21:48 DEBUG WindowsFrontend: frontend.on_quit
11-01 21:48 DEBUG root: application.on_quit
11-01 21:48 INFO root: sys.exit
11-01 21:50 INFO root: === wubi 9.10ubuntu1 rev160 ===
11-01 21:50 DEBUG root: Logfile is c:\docume~1\computer\locals~1\temp\wubi-9.10ubuntu1-rev160.log
11-01 21:50 DEBUG root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
11-01 21:50 DEBUG CommonBackend: data_dir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp\data
11-01 21:50 DEBUG WindowsBackend: 7z=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp\bin\7z.exe
11-01 21:50 DEBUG CommonBackend: Fetching basic info...
11-01 21:50 DEBUG CommonBackend: original_exe=D:\wubi.exe
11-01 21:50 DEBUG CommonBackend: platform=win32
11-01 21:50 DEBUG CommonBackend: osname=nt
11-01 21:50 DEBUG CommonBackend: language=en_US
11-01 21:50 DEBUG CommonBackend: encoding=cp1252
11-01 21:50 DEBUG WindowsBackend: arch=i386
11-01 21:50 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp\data\isolist.ini
11-01 21:50 DEBUG CommonBackend: Adding distro Xubuntu-i386
11-01 21:50 DEBUG CommonBackend: Adding distro Xubuntu-amd64
11-01 21:50 DEBUG CommonBackend: Adding distro Kubuntu-amd64
11-01 21:50 DEBUG CommonBackend: Adding distro Mythbuntu-i386
11-01 21:50 DEBUG CommonBackend: Adding distro Ubuntu-amd64
11-01 21:50 DEBUG CommonBackend: Adding distro Ubuntu-i386
11-01 21:50 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
11-01 21:50 DEBUG CommonBackend: Adding distro Kubuntu-i386
11-01 21:50 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386
11-01 21:50 DEBUG CommonBackend: Adding distro UbuntuNetbookRemix-i386
11-01 21:50 DEBUG WindowsBackend: Fetching host info...
11-01 21:50 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-01 21:50 DEBUG WindowsBackend: windows version=xp
11-01 21:50 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
11-01 21:50 DEBUG WindowsBackend: windows_sp=Service Pack 3
11-01 21:50 DEBUG WindowsBackend: windows_build=2600
11-01 21:50 DEBUG WindowsBackend: gmt=-5
11-01 21:50 DEBUG WindowsBackend: country=US
11-01 21:50 DEBUG WindowsBackend: timezone=America/New_York
11-01 21:50 DEBUG WindowsBackend: windows_username=Computer
11-01 21:50 DEBUG WindowsBackend: user_full_name=Computer
11-01 21:50 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Computer
11-01 21:50 DEBUG WindowsBackend: windows_language_code=1033
11-01 21:50 DEBUG WindowsBackend: windows_language=English
11-01 21:50 DEBUG WindowsBackend: processor_name=AMD Athlon(tm) XP 3000+
11-01 21:50 DEBUG WindowsBackend: bootloader=xp
11-01 21:50 DEBUG WindowsBackend: system_drive=Drive(C: hd 101625.660156 mb free ntfs)
11-01 21:50 DEBUG WindowsBackend: drive=Drive(C: hd 101625.660156 mb free ntfs)
11-01 21:50 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
11-01 21:50 DEBUG WindowsBackend: drive=Drive(F: removable 0.0 mb free )
11-01 21:50 DEBUG WindowsBackend: drive=Drive(G: removable 0.0 mb free )
11-01 21:50 DEBUG WindowsBackend: drive=Drive(H: removable 0.0 mb free )
11-01 21:50 DEBUG WindowsBackend: drive=Drive(I: removable 0.0 mb free )
11-01 21:50 DEBUG WindowsBackend: drive=Drive(J: cd 0.0 mb free )
11-01 21:50 DEBUG WindowsBackend: uninstaller_path=None
11-01 21:50 DEBUG WindowsBackend: previous_target_dir=None
11-01 21:50 DEBUG WindowsBackend: previous_distro_name=None
11-01 21:50 DEBUG WindowsBackend: keyboard_id=67699721
11-01 21:50 DEBUG WindowsBackend: keyboard_layout=us
11-01 21:50 DEBUG WindowsBackend: keyboard_variant=
11-01 21:50 DEBUG CommonBackend: python locale=('en_US', 'cp1252')
11-01 21:50 DEBUG CommonBackend: locale=en_US.UTF-8
11-01 21:50 DEBUG WindowsBackend: total_memory_mb=1471.484375
11-01 21:50 DEBUG CommonBackend: Searching ISOs on USB devices
11-01 21:50 DEBUG CommonBackend: Searching for local CDs
11-01 21:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp is a valid Ubuntu CD
11-01 21:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
11-01 21:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp is a valid Ubuntu CD
11-01 21:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
11-01 21:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp is a valid Ubuntu Netbook Remix CD
11-01 21:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
11-01 21:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp is a valid Kubuntu CD
11-01 21:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
11-01 21:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp is a valid Kubuntu CD
11-01 21:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
11-01 21:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp is a valid Kubuntu Netbook CD
11-01 21:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
11-01 21:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp is a valid Xubuntu CD
11-01 21:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
11-01 21:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp is a valid Xubuntu CD
11-01 21:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
11-01 21:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp is a valid Mythbuntu CD
11-01 21:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
11-01 21:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp is a valid Mythbuntu CD
11-01 21:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
11-01 21:50 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
11-01 21:50 DEBUG Distro: parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
11-01 21:50 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
11-01 21:50 DEBUG Distro: wrong arch: i386 != amd64
11-01 21:50 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
11-01 21:50 INFO Distro: Found a valid CD for Ubuntu: D:\
11-01 21:50 INFO root: Running the CD menu...
11-01 21:50 DEBUG WindowsFrontend: __init__...
11-01 21:50 DEBUG WindowsFrontend: on_init...
11-01 21:50 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp\translations, languages=['en_US', 'en']
11-01 21:50 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp\translations, languages=['en_US', 'en']
11-01 21:50 INFO root: CD menu finished
11-01 21:50 INFO root: Running the installer...
11-01 21:50 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp\translations, languages=['en_US', 'en']
11-01 21:50 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp\translations, languages=['en_US', 'en']
11-01 21:50 DEBUG WinuiInstallationPage: target_drive=C:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=computer
11-01 21:50 INFO root: Received settings
11-01 21:50 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp\translations, languages=['en_US', 'en']
11-01 21:50 DEBUG TaskList: # Running tasklist...
11-01 21:50 DEBUG TaskList: ## Running select_target_dir...
11-01 21:50 INFO WindowsBackend: Installing into C:\ubuntu
11-01 21:50 DEBUG TaskList: ## Finished select_target_dir
11-01 21:50 DEBUG TaskList: ## Running create_dir_structure...
11-01 21:50 DEBUG CommonBackend: Creating dir C:\ubuntu
11-01 21:50 DEBUG CommonBackend: Creating dir C:\ubuntu\disks
11-01 21:50 DEBUG CommonBackend: Creating dir C:\ubuntu\install
11-01 21:50 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot
11-01 21:50 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot
11-01 21:50 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
11-01 21:50 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot\grub
11-01 21:50 DEBUG TaskList: ## Finished create_dir_structure
11-01 21:50 DEBUG TaskList: ## Running uncompress_target_dir...
11-01 21:50 DEBUG TaskList: ## Finished uncompress_target_dir
11-01 21:50 DEBUG TaskList: ## Running create_uninstaller...
11-01 21:50 DEBUG WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
11-01 21:50 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
11-01 21:50 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
11-01 21:50 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
11-01 21:50 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
11-01 21:50 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
11-01 21:50 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
11-01 21:50 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com]("http://www.ubuntu.com/")
11-01 21:50 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
11-01 21:50 DEBUG TaskList: ## Finished create_uninstaller
11-01 21:50 DEBUG TaskList: ## Running copy_installation_files...
11-01 21:50 DEBUG WindowsBackend: Copying C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
11-01 21:50 DEBUG WindowsBackend: Copying C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp\winboot -> C:\ubuntu\winboot
11-01 21:50 DEBUG WindowsBackend: Copying C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
11-01 21:50 DEBUG TaskList: ## Finished copy_installation_files
11-01 21:50 DEBUG TaskList: ## Running get_iso...
11-01 21:50 DEBUG TaskList: New task copy_file
11-01 21:50 DEBUG TaskList: ### Running copy_file...
11-01 21:51 ERROR TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 22] Invalid argument
11-01 21:51 DEBUG TaskList: # Cancelling tasklist
11-01 21:51 ERROR root: [Errno 22] Invalid argument
Traceback (most recent call last):
File "\lib\wubi\application.py", line 56, in run
File "\lib\wubi\application.py", line 126, in select_task
File "\lib\wubi\application.py", line 194, in run_cd_menu
File "\lib\wubi\application.py", line 118, in select_task
File "\lib\wubi\application.py", line 156, in run_installer
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 22] Invalid argument
11-01 21:51 DEBUG TaskList: New task check_iso
11-01 21:51 DEBUG CommonBackend: Searching for local ISO
11-01 21:51 DEBUG CommonBackend: Could not find any ISO or CD, downloading one now
11-01 21:51 DEBUG TaskList: New task get_metalink
11-01 21:51 ERROR TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
11-01 21:51 DEBUG TaskList: # Cancelling tasklist
11-01 21:51 DEBUG TaskList: # Finished tasklist
11-02 13:48 INFO root: === wubi 9.10ubuntu1 rev160 ===
11-02 13:48 DEBUG root: Logfile is c:\docume~1\computer\locals~1\temp\wubi-9.10ubuntu1-rev160.log
11-02 13:48 DEBUG root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
11-02 13:48 DEBUG CommonBackend: data_dir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\data
11-02 13:48 DEBUG WindowsBackend: 7z=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\bin\7z.exe
11-02 13:48 DEBUG CommonBackend: Fetching basic info...
11-02 13:48 DEBUG CommonBackend: original_exe=D:\wubi.exe
11-02 13:48 DEBUG CommonBackend: platform=win32
11-02 13:48 DEBUG CommonBackend: osname=nt
11-02 13:48 DEBUG CommonBackend: language=en_US
11-02 13:48 DEBUG CommonBackend: encoding=cp1252
11-02 13:48 DEBUG WindowsBackend: arch=i386
11-02 13:48 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\data\isolist.ini
11-02 13:48 DEBUG CommonBackend: Adding distro Xubuntu-i386
11-02 13:48 DEBUG CommonBackend: Adding distro Xubuntu-amd64
11-02 13:48 DEBUG CommonBackend: Adding distro Kubuntu-amd64
11-02 13:48 DEBUG CommonBackend: Adding distro Mythbuntu-i386
11-02 13:48 DEBUG CommonBackend: Adding distro Ubuntu-amd64
11-02 13:48 DEBUG CommonBackend: Adding distro Ubuntu-i386
11-02 13:48 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
11-02 13:48 DEBUG CommonBackend: Adding distro Kubuntu-i386
11-02 13:48 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386
11-02 13:48 DEBUG CommonBackend: Adding distro UbuntuNetbookRemix-i386
11-02 13:48 DEBUG WindowsBackend: Fetching host info...
11-02 13:48 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-02 13:48 DEBUG WindowsBackend: windows version=xp
11-02 13:48 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
11-02 13:48 DEBUG WindowsBackend: windows_sp=Service Pack 3
11-02 13:48 DEBUG WindowsBackend: windows_build=2600
11-02 13:48 DEBUG WindowsBackend: gmt=-5
11-02 13:48 DEBUG WindowsBackend: country=US
11-02 13:48 DEBUG WindowsBackend: timezone=America/New_York
11-02 13:48 DEBUG WindowsBackend: windows_username=Computer
11-02 13:48 DEBUG WindowsBackend: user_full_name=Computer
11-02 13:48 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Computer
11-02 13:48 DEBUG WindowsBackend: windows_language_code=1033
11-02 13:48 DEBUG WindowsBackend: windows_language=English
11-02 13:48 DEBUG WindowsBackend: processor_name=AMD Athlon(tm) XP 3000+
11-02 13:48 DEBUG WindowsBackend: bootloader=xp
11-02 13:48 DEBUG WindowsBackend: system_drive=Drive(C: hd 101460.84375 mb free ntfs)
11-02 13:48 DEBUG WindowsBackend: drive=Drive(C: hd 101460.84375 mb free ntfs)
11-02 13:48 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
11-02 13:48 DEBUG WindowsBackend: drive=Drive(F: removable 0.0 mb free )
11-02 13:48 DEBUG WindowsBackend: drive=Drive(G: removable 0.0 mb free )
11-02 13:48 DEBUG WindowsBackend: drive=Drive(H: removable 0.0 mb free )
11-02 13:48 DEBUG WindowsBackend: drive=Drive(I: removable 0.0 mb free )
11-02 13:48 DEBUG WindowsBackend: drive=Drive(J: cd 0.0 mb free )
11-02 13:48 DEBUG WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
11-02 13:48 DEBUG WindowsBackend: previous_target_dir=C:\ubuntu
11-02 13:48 DEBUG WindowsBackend: previous_distro_name=Ubuntu
11-02 13:48 DEBUG WindowsBackend: keyboard_id=67699721
11-02 13:48 DEBUG WindowsBackend: keyboard_layout=us
11-02 13:48 DEBUG WindowsBackend: keyboard_variant=
11-02 13:48 DEBUG CommonBackend: python locale=('en_US', 'cp1252')
11-02 13:48 DEBUG CommonBackend: locale=en_US.UTF-8
11-02 13:48 DEBUG WindowsBackend: total_memory_mb=1471.484375
11-02 13:48 DEBUG CommonBackend: Searching ISOs on USB devices
11-02 13:48 DEBUG CommonBackend: Searching for local CDs
11-02 13:48 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
11-02 13:48 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
11-02 13:48 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
11-02 13:48 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
11-02 13:48 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu Netbook Remix CD
11-02 13:48 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
11-02 13:48 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
11-02 13:48 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
11-02 13:48 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
11-02 13:48 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
11-02 13:48 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu Netbook CD
11-02 13:48 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
11-02 13:48 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
11-02 13:48 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
11-02 13:48 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
11-02 13:48 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
11-02 13:48 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
11-02 13:48 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
11-02 13:48 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
11-02 13:48 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
11-02 13:48 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
11-02 13:48 DEBUG Distro: parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
11-02 13:48 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
11-02 13:48 DEBUG Distro: wrong arch: i386 != amd64
11-02 13:48 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
11-02 13:48 INFO Distro: Found a valid CD for Ubuntu: D:\
11-02 13:48 INFO root: Running the CD menu...
11-02 13:48 DEBUG WindowsFrontend: __init__...
11-02 13:48 DEBUG WindowsFrontend: on_init...
11-02 13:48 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
11-02 13:48 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
11-02 13:48 INFO root: CD menu finished
11-02 13:48 INFO root: Already installed, running the uninstaller...
11-02 13:48 INFO root: Running the uninstaller...
11-02 13:48 INFO CommonBackend: This is the uninstaller running
11-02 13:48 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
11-02 13:48 INFO root: Received settings
11-02 13:48 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
11-02 13:48 DEBUG TaskList: # Running tasklist...
11-02 13:48 DEBUG TaskList: ## Running Backup ISO...
11-02 13:48 DEBUG TaskList: ## Finished Backup ISO
11-02 13:48 DEBUG TaskList: ## Running Remove bootloader entry...
11-02 13:48 ERROR WindowsBackend: Cannot find bcdedit
11-02 13:48 DEBUG WindowsBackend: undo_bootini C:
11-02 13:48 DEBUG WindowsBackend: undo_configsys Drive(C: hd 101460.84375 mb free ntfs)
11-02 13:48 DEBUG WindowsBackend: undo_bootini F:
11-02 13:48 DEBUG WindowsBackend: undo_configsys Drive(F: removable 0.0 mb free )
11-02 13:48 DEBUG WindowsBackend: undo_bootini G:
11-02 13:48 DEBUG WindowsBackend: undo_configsys Drive(G: removable 0.0 mb free )
11-02 13:48 DEBUG WindowsBackend: undo_bootini H:
11-02 13:48 DEBUG WindowsBackend: undo_configsys Drive(H: removable 0.0 mb free )
11-02 13:48 DEBUG WindowsBackend: undo_bootini I:
11-02 13:48 DEBUG WindowsBackend: undo_configsys Drive(I: removable 0.0 mb free )
11-02 13:48 DEBUG TaskList: ## Finished Remove bootloader entry
11-02 13:48 DEBUG TaskList: ## Running Remove target dir...
11-02 13:48 DEBUG CommonBackend: Deleting C:\ubuntu
11-02 13:48 DEBUG TaskList: ## Finished Remove target dir
11-02 13:48 DEBUG TaskList: ## Running Remove registry key...
11-02 13:48 DEBUG TaskList: ## Finished Remove registry key
11-02 13:48 DEBUG TaskList: # Finished tasklist
11-02 13:48 INFO root: Almost finished uninstalling
11-02 13:48 INFO root: Finished uninstallation
11-02 13:48 DEBUG CommonBackend: Fetching basic info...
11-02 13:48 DEBUG CommonBackend: original_exe=D:\wubi.exe
11-02 13:48 DEBUG CommonBackend: platform=win32
11-02 13:48 DEBUG CommonBackend: osname=nt
11-02 13:48 DEBUG WindowsBackend: arch=i386
11-02 13:48 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\data\isolist.ini
11-02 13:48 DEBUG CommonBackend: Adding distro Xubuntu-i386
11-02 13:48 DEBUG CommonBackend: Adding distro Xubuntu-amd64
11-02 13:48 DEBUG CommonBackend: Adding distro Kubuntu-amd64
11-02 13:48 DEBUG CommonBackend: Adding distro Mythbuntu-i386
11-02 13:48 DEBUG CommonBackend: Adding distro Ubuntu-amd64
11-02 13:48 DEBUG CommonBackend: Adding distro Ubuntu-i386
11-02 13:48 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
11-02 13:48 DEBUG CommonBackend: Adding distro Kubuntu-i386
11-02 13:48 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386
11-02 13:48 DEBUG CommonBackend: Adding distro UbuntuNetbookRemix-i386
11-02 13:48 DEBUG WindowsBackend: Fetching host info...
11-02 13:48 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-02 13:48 DEBUG WindowsBackend: windows version=xp
11-02 13:48 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
11-02 13:48 DEBUG WindowsBackend: windows_sp=Service Pack 3
11-02 13:48 DEBUG WindowsBackend: windows_build=2600
11-02 13:48 DEBUG WindowsBackend: gmt=-5
11-02 13:48 DEBUG WindowsBackend: country=US
11-02 13:48 DEBUG WindowsBackend: timezone=America/New_York
11-02 13:48 DEBUG WindowsBackend: windows_username=Computer
11-02 13:48 DEBUG WindowsBackend: user_full_name=Computer
11-02 13:48 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Computer
11-02 13:48 DEBUG WindowsBackend: windows_language_code=1033
11-02 13:48 DEBUG WindowsBackend: windows_language=English
11-02 13:48 DEBUG WindowsBackend: processor_name=AMD Athlon(tm) XP 3000+
11-02 13:48 DEBUG WindowsBackend: bootloader=xp
11-02 13:48 DEBUG WindowsBackend: system_drive=Drive(C: hd 101558.917969 mb free ntfs)
11-02 13:48 DEBUG WindowsBackend: drive=Drive(C: hd 101558.917969 mb free ntfs)
11-02 13:48 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
11-02 13:48 DEBUG WindowsBackend: drive=Drive(F: removable 0.0 mb free )
11-02 13:48 DEBUG WindowsBackend: drive=Drive(G: removable 0.0 mb free )
11-02 13:48 DEBUG WindowsBackend: drive=Drive(H: removable 0.0 mb free )
11-02 13:48 DEBUG WindowsBackend: drive=Drive(I: removable 0.0 mb free )
11-02 13:48 DEBUG WindowsBackend: drive=Drive(J: cd 0.0 mb free )
11-02 13:48 DEBUG WindowsBackend: uninstaller_path=None
11-02 13:48 DEBUG WindowsBackend: previous_target_dir=None
11-02 13:48 DEBUG WindowsBackend: previous_distro_name=None
11-02 13:48 DEBUG WindowsBackend: keyboard_id=67699721
11-02 13:48 DEBUG WindowsBackend: keyboard_layout=us
11-02 13:48 DEBUG WindowsBackend: keyboard_variant=
11-02 13:48 DEBUG WindowsBackend: total_memory_mb=1471.484375
11-02 13:48 DEBUG CommonBackend: Searching ISOs on USB devices
11-02 13:48 DEBUG CommonBackend: Searching for local CDs
11-02 13:48 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
11-02 13:48 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
11-02 13:48 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
11-02 13:48 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
11-02 13:48 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu Netbook Remix CD
11-02 13:48 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
11-02 13:48 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
11-02 13:48 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
11-02 13:48 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
11-02 13:48 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
11-02 13:48 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu Netbook CD
11-02 13:48 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
11-02 13:48 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
11-02 13:48 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
11-02 13:48 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
11-02 13:48 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
11-02 13:48 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
11-02 13:48 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
11-02 13:48 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
11-02 13:48 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
11-02 13:48 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
11-02 13:48 DEBUG Distro: wrong arch: i386 != amd64
11-02 13:48 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
11-02 13:48 INFO Distro: Found a valid CD for Ubuntu: D:\
11-02 13:48 INFO root: Running the installer...
11-02 13:48 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
11-02 13:48 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
11-02 13:49 DEBUG WinuiInstallationPage: target_drive=C:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=computer
11-02 13:49 INFO root: Received settings
11-02 13:49 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
11-02 13:49 DEBUG TaskList: # Running tasklist...
11-02 13:49 DEBUG TaskList: ## Running select_target_dir...
11-02 13:49 INFO WindowsBackend: Installing into C:\ubuntu
11-02 13:49 DEBUG TaskList: ## Finished select_target_dir
11-02 13:49 DEBUG TaskList: ## Running create_dir_structure...
11-02 13:49 DEBUG CommonBackend: Creating dir C:\ubuntu
11-02 13:49 DEBUG CommonBackend: Creating dir C:\ubuntu\disks
11-02 13:49 DEBUG CommonBackend: Creating dir C:\ubuntu\install
11-02 13:49 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot
11-02 13:49 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot
11-02 13:49 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
11-02 13:49 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot\grub
11-02 13:49 DEBUG TaskList: ## Finished create_dir_structure
11-02 13:49 DEBUG TaskList: ## Running uncompress_target_dir...
11-02 13:49 DEBUG TaskList: ## Finished uncompress_target_dir
11-02 13:49 DEBUG TaskList: ## Running create_uninstaller...
11-02 13:49 DEBUG WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
11-02 13:49 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
11-02 13:49 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
11-02 13:49 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
11-02 13:49 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
11-02 13:49 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
11-02 13:49 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
11-02 13:49 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com]("http://www.ubuntu.com/")
11-02 13:49 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
11-02 13:49 DEBUG TaskList: ## Finished create_uninstaller
11-02 13:49 DEBUG TaskList: ## Running copy_installation_files...
11-02 13:49 DEBUG WindowsBackend: Copying C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
11-02 13:49 DEBUG WindowsBackend: Copying C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\winboot -> C:\ubuntu\winboot
11-02 13:49 DEBUG WindowsBackend: Copying C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
11-02 13:49 DEBUG TaskList: ## Finished copy_installation_files
11-02 13:49 DEBUG TaskList: ## Running get_iso...
11-02 13:49 DEBUG TaskList: New task copy_file
11-02 13:49 DEBUG TaskList: ### Running copy_file...
11-02 13:49 ERROR TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 22] Invalid argument
11-02 13:49 DEBUG TaskList: # Cancelling tasklist
11-02 13:49 ERROR root: [Errno 22] Invalid argument
Traceback (most recent call last):
File "\lib\wubi\application.py", line 56, in run
File "\lib\wubi\application.py", line 126, in select_task
File "\lib\wubi\application.py", line 194, in run_cd_menu
File "\lib\wubi\application.py", line 118, in select_task
File "\lib\wubi\application.py", line 156, in run_installer
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 22] Invalid argument
11-02 13:49 DEBUG TaskList: New task check_iso
11-02 13:49 DEBUG CommonBackend: Searching for local ISO
11-02 13:49 DEBUG CommonBackend: Could not find any ISO or CD, downloading one now
11-02 13:49 DEBUG TaskList: New task get_metalink
11-02 13:49 ERROR TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
11-02 13:49 DEBUG TaskList: # Cancelling tasklist
11-02 13:49 DEBUG TaskList: # Finished tasklist
11-02 13:50 INFO root: === wubi 9.10ubuntu1 rev160 ===
11-02 13:50 DEBUG root: Logfile is c:\docume~1\computer\locals~1\temp\wubi-9.10ubuntu1-rev160.log
11-02 13:50 DEBUG root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
11-02 13:50 DEBUG CommonBackend: data_dir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\data
11-02 13:50 DEBUG WindowsBackend: 7z=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\bin\7z.exe
11-02 13:50 DEBUG CommonBackend: Fetching basic info...
11-02 13:50 DEBUG CommonBackend: original_exe=D:\wubi.exe
11-02 13:50 DEBUG CommonBackend: platform=win32
11-02 13:50 DEBUG CommonBackend: osname=nt
11-02 13:50 DEBUG CommonBackend: language=en_US
11-02 13:50 DEBUG CommonBackend: encoding=cp1252
11-02 13:50 DEBUG WindowsBackend: arch=i386
11-02 13:50 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\data\isolist.ini
11-02 13:50 DEBUG CommonBackend: Adding distro Xubuntu-i386
11-02 13:50 DEBUG CommonBackend: Adding distro Xubuntu-amd64
11-02 13:50 DEBUG CommonBackend: Adding distro Kubuntu-amd64
11-02 13:50 DEBUG CommonBackend: Adding distro Mythbuntu-i386
11-02 13:50 DEBUG CommonBackend: Adding distro Ubuntu-amd64
11-02 13:50 DEBUG CommonBackend: Adding distro Ubuntu-i386
11-02 13:50 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
11-02 13:50 DEBUG CommonBackend: Adding distro Kubuntu-i386
11-02 13:50 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386
11-02 13:50 DEBUG CommonBackend: Adding distro UbuntuNetbookRemix-i386
11-02 13:50 DEBUG WindowsBackend: Fetching host info...
11-02 13:50 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-02 13:50 DEBUG WindowsBackend: windows version=xp
11-02 13:50 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
11-02 13:50 DEBUG WindowsBackend: windows_sp=Service Pack 3
11-02 13:50 DEBUG WindowsBackend: windows_build=2600
11-02 13:50 DEBUG WindowsBackend: gmt=-5
11-02 13:50 DEBUG WindowsBackend: country=US
11-02 13:50 DEBUG WindowsBackend: timezone=America/New_York
11-02 13:50 DEBUG WindowsBackend: windows_username=Computer
11-02 13:50 DEBUG WindowsBackend: user_full_name=Computer
11-02 13:50 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Computer
11-02 13:50 DEBUG WindowsBackend: windows_language_code=1033
11-02 13:50 DEBUG WindowsBackend: windows_language=English
11-02 13:50 DEBUG WindowsBackend: processor_name=AMD Athlon(tm) XP 3000+
11-02 13:50 DEBUG WindowsBackend: bootloader=xp
11-02 13:50 DEBUG WindowsBackend: system_drive=Drive(C: hd 101459.375 mb free ntfs)
11-02 13:50 DEBUG WindowsBackend: drive=Drive(C: hd 101459.375 mb free ntfs)
11-02 13:50 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
11-02 13:50 DEBUG WindowsBackend: drive=Drive(F: removable 0.0 mb free )
11-02 13:50 DEBUG WindowsBackend: drive=Drive(G: removable 0.0 mb free )
11-02 13:50 DEBUG WindowsBackend: drive=Drive(H: removable 0.0 mb free )
11-02 13:50 DEBUG WindowsBackend: drive=Drive(I: removable 0.0 mb free )
11-02 13:50 DEBUG WindowsBackend: drive=Drive(J: cd 0.0 mb free )
11-02 13:50 DEBUG WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
11-02 13:50 DEBUG WindowsBackend: previous_target_dir=C:\ubuntu
11-02 13:50 DEBUG WindowsBackend: previous_distro_name=Ubuntu
11-02 13:50 DEBUG WindowsBackend: keyboard_id=67699721
11-02 13:50 DEBUG WindowsBackend: keyboard_layout=us
11-02 13:50 DEBUG WindowsBackend: keyboard_variant=
11-02 13:50 DEBUG CommonBackend: python locale=('en_US', 'cp1252')
11-02 13:50 DEBUG CommonBackend: locale=en_US.UTF-8
11-02 13:50 DEBUG WindowsBackend: total_memory_mb=1471.484375
11-02 13:50 DEBUG CommonBackend: Searching ISOs on USB devices
11-02 13:50 DEBUG CommonBackend: Searching for local CDs
11-02 13:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu CD
11-02 13:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-02 13:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu CD
11-02 13:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-02 13:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu Netbook Remix CD
11-02 13:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-02 13:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu CD
11-02 13:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-02 13:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu CD
11-02 13:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-02 13:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu Netbook CD
11-02 13:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-02 13:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Xubuntu CD
11-02 13:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-02 13:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Xubuntu CD
11-02 13:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-02 13:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Mythbuntu CD
11-02 13:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-02 13:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Mythbuntu CD
11-02 13:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-02 13:50 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
11-02 13:50 DEBUG Distro: parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
11-02 13:50 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
11-02 13:50 DEBUG Distro: wrong arch: i386 != amd64
11-02 13:50 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
11-02 13:50 INFO Distro: Found a valid CD for Ubuntu: D:\
11-02 13:50 INFO root: Running the CD menu...
11-02 13:50 DEBUG WindowsFrontend: __init__...
11-02 13:50 DEBUG WindowsFrontend: on_init...
11-02 13:50 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\translations, languages=['en_US', 'en']
11-02 13:50 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\translations, languages=['en_US', 'en']
11-02 13:50 INFO root: CD menu finished
11-02 13:50 INFO root: Already installed, running the uninstaller...
11-02 13:50 INFO root: Running the uninstaller...
11-02 13:50 INFO CommonBackend: This is the uninstaller running
11-02 13:50 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\translations, languages=['en_US', 'en']
11-02 13:50 INFO root: Received settings
11-02 13:50 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\translations, languages=['en_US', 'en']
11-02 13:50 DEBUG TaskList: # Running tasklist...
11-02 13:50 DEBUG TaskList: ## Running Backup ISO...
11-02 13:50 DEBUG TaskList: ## Finished Backup ISO
11-02 13:50 DEBUG TaskList: ## Running Remove bootloader entry...
11-02 13:50 ERROR WindowsBackend: Cannot find bcdedit
11-02 13:50 DEBUG WindowsBackend: undo_bootini C:
11-02 13:50 DEBUG WindowsBackend: undo_configsys Drive(C: hd 101459.375 mb free ntfs)
11-02 13:50 DEBUG WindowsBackend: undo_bootini F:
11-02 13:50 DEBUG WindowsBackend: undo_configsys Drive(F: removable 0.0 mb free )
11-02 13:50 DEBUG WindowsBackend: undo_bootini G:
11-02 13:50 DEBUG WindowsBackend: undo_configsys Drive(G: removable 0.0 mb free )
11-02 13:50 DEBUG WindowsBackend: undo_bootini H:
11-02 13:50 DEBUG WindowsBackend: undo_configsys Drive(H: removable 0.0 mb free )
11-02 13:50 DEBUG WindowsBackend: undo_bootini I:
11-02 13:50 DEBUG WindowsBackend: undo_configsys Drive(I: removable 0.0 mb free )
11-02 13:50 DEBUG TaskList: ## Finished Remove bootloader entry
11-02 13:50 DEBUG TaskList: ## Running Remove target dir...
11-02 13:50 DEBUG CommonBackend: Deleting C:\ubuntu
11-02 13:50 DEBUG TaskList: ## Finished Remove target dir
11-02 13:50 DEBUG TaskList: ## Running Remove registry key...
11-02 13:50 DEBUG TaskList: ## Finished Remove registry key
11-02 13:50 DEBUG TaskList: # Finished tasklist
11-02 13:50 INFO root: Almost finished uninstalling
11-02 13:50 INFO root: Finished uninstallation
11-02 13:50 DEBUG CommonBackend: Fetching basic info...
11-02 13:50 DEBUG CommonBackend: original_exe=D:\wubi.exe
11-02 13:50 DEBUG CommonBackend: platform=win32
11-02 13:50 DEBUG CommonBackend: osname=nt
11-02 13:50 DEBUG WindowsBackend: arch=i386
11-02 13:50 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\data\isolist.ini
11-02 13:50 DEBUG CommonBackend: Adding distro Xubuntu-i386
11-02 13:50 DEBUG CommonBackend: Adding distro Xubuntu-amd64
11-02 13:50 DEBUG CommonBackend: Adding distro Kubuntu-amd64
11-02 13:50 DEBUG CommonBackend: Adding distro Mythbuntu-i386
11-02 13:50 DEBUG CommonBackend: Adding distro Ubuntu-amd64
11-02 13:50 DEBUG CommonBackend: Adding distro Ubuntu-i386
11-02 13:50 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
11-02 13:50 DEBUG CommonBackend: Adding distro Kubuntu-i386
11-02 13:50 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386
11-02 13:50 DEBUG CommonBackend: Adding distro UbuntuNetbookRemix-i386
11-02 13:50 DEBUG WindowsBackend: Fetching host info...
11-02 13:50 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-02 13:50 DEBUG WindowsBackend: windows version=xp
11-02 13:50 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
11-02 13:50 DEBUG WindowsBackend: windows_sp=Service Pack 3
11-02 13:50 DEBUG WindowsBackend: windows_build=2600
11-02 13:50 DEBUG WindowsBackend: gmt=-5
11-02 13:50 DEBUG WindowsBackend: country=US
11-02 13:50 DEBUG WindowsBackend: timezone=America/New_York
11-02 13:50 DEBUG WindowsBackend: windows_username=Computer
11-02 13:50 DEBUG WindowsBackend: user_full_name=Computer
11-02 13:50 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Computer
11-02 13:50 DEBUG WindowsBackend: windows_language_code=1033
11-02 13:50 DEBUG WindowsBackend: windows_language=English
11-02 13:50 DEBUG WindowsBackend: processor_name=AMD Athlon(tm) XP 3000+
11-02 13:50 DEBUG WindowsBackend: bootloader=xp
11-02 13:50 DEBUG WindowsBackend: system_drive=Drive(C: hd 101558.894531 mb free ntfs)
11-02 13:50 DEBUG WindowsBackend: drive=Drive(C: hd 101558.894531 mb free ntfs)
11-02 13:50 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
11-02 13:50 DEBUG WindowsBackend: drive=Drive(F: removable 0.0 mb free )
11-02 13:50 DEBUG WindowsBackend: drive=Drive(G: removable 0.0 mb free )
11-02 13:50 DEBUG WindowsBackend: drive=Drive(H: removable 0.0 mb free )
11-02 13:50 DEBUG WindowsBackend: drive=Drive(I: removable 0.0 mb free )
11-02 13:50 DEBUG WindowsBackend: drive=Drive(J: cd 0.0 mb free )
11-02 13:50 DEBUG WindowsBackend: uninstaller_path=None
11-02 13:50 DEBUG WindowsBackend: previous_target_dir=None
11-02 13:50 DEBUG WindowsBackend: previous_distro_name=None
11-02 13:50 DEBUG WindowsBackend: keyboard_id=67699721
11-02 13:50 DEBUG WindowsBackend: keyboard_layout=us
11-02 13:50 DEBUG WindowsBackend: keyboard_variant=
11-02 13:50 DEBUG WindowsBackend: total_memory_mb=1471.484375
11-02 13:50 DEBUG CommonBackend: Searching ISOs on USB devices
11-02 13:50 DEBUG CommonBackend: Searching for local CDs
11-02 13:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu CD
11-02 13:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-02 13:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu CD
11-02 13:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-02 13:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu Netbook Remix CD
11-02 13:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-02 13:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu CD
11-02 13:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-02 13:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu CD
11-02 13:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-02 13:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu Netbook CD
11-02 13:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-02 13:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Xubuntu CD
11-02 13:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-02 13:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Xubuntu CD
11-02 13:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-02 13:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Mythbuntu CD
11-02 13:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-02 13:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Mythbuntu CD
11-02 13:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-02 13:50 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
11-02 13:50 DEBUG Distro: wrong arch: i386 != amd64
11-02 13:50 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
11-02 13:50 INFO Distro: Found a valid CD for Ubuntu: D:\
11-02 13:50 INFO root: Running the installer...
11-02 13:50 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\translations, languages=['en_US', 'en']
11-02 13:50 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\translations, languages=['en_US', 'en']
11-02 13:50 DEBUG WinuiInstallationPage: target_drive=C:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=computer
11-02 13:50 INFO root: Received settings
11-02 13:50 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\translations, languages=['en_US', 'en']
11-02 13:50 DEBUG TaskList: # Running tasklist...
11-02 13:50 DEBUG TaskList: ## Running select_target_dir...
11-02 13:50 INFO WindowsBackend: Installing into C:\ubuntu
11-02 13:50 DEBUG TaskList: ## Finished select_target_dir
11-02 13:50 DEBUG TaskList: ## Running create_dir_structure...
11-02 13:50 DEBUG CommonBackend: Creating dir C:\ubuntu
11-02 13:50 DEBUG CommonBackend: Creating dir C:\ubuntu\disks
11-02 13:50 DEBUG CommonBackend: Creating dir C:\ubuntu\install
11-02 13:50 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot
11-02 13:50 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot
11-02 13:50 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
11-02 13:50 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot\grub
11-02 13:50 DEBUG TaskList: ## Finished create_dir_structure
11-02 13:50 DEBUG TaskList: ## Running uncompress_target_dir...
11-02 13:50 DEBUG TaskList: ## Finished uncompress_target_dir
11-02 13:50 DEBUG TaskList: ## Running create_uninstaller...
11-02 13:50 DEBUG WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
11-02 13:50 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
11-02 13:50 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
11-02 13:50 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
11-02 13:50 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
11-02 13:50 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
11-02 13:50 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
11-02 13:50 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com]("http://www.ubuntu.com/")
11-02 13:50 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
11-02 13:50 DEBUG TaskList: ## Finished create_uninstaller
11-02 13:50 DEBUG TaskList: ## Running copy_installation_files...
11-02 13:50 DEBUG WindowsBackend: Copying C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
11-02 13:50 DEBUG WindowsBackend: Copying C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\winboot -> C:\ubuntu\winboot
11-02 13:50 DEBUG WindowsBackend: Copying C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
11-02 13:50 DEBUG TaskList: ## Finished copy_installation_files
11-02 13:50 DEBUG TaskList: ## Running get_iso...
11-02 13:50 DEBUG TaskList: New task copy_file
11-02 13:50 DEBUG TaskList: ### Running copy_file...
11-02 13:52 ERROR TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 22] Invalid argument
11-02 13:52 DEBUG TaskList: # Cancelling tasklist
11-02 13:52 ERROR root: [Errno 22] Invalid argument
Traceback (most recent call last):
File "\lib\wubi\application.py", line 56, in run
File "\lib\wubi\application.py", line 126, in select_task
File "\lib\wubi\application.py", line 194, in run_cd_menu
File "\lib\wubi\application.py", line 118, in select_task
File "\lib\wubi\application.py", line 156, in run_installer
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 22] Invalid argument
11-02 13:52 DEBUG TaskList: New task check_iso
11-02 13:52 DEBUG CommonBackend: Searching for local ISO
11-02 13:52 DEBUG CommonBackend: Could not find any ISO or CD, downloading one now
11-02 13:52 DEBUG TaskList: New task get_metalink
11-02 13:52 ERROR TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
11-02 13:52 DEBUG TaskList: # Cancelling tasklist
11-02 13:52 DEBUG TaskList: # Finished tasklist


---

### Post by Mark Phelps on 2009-11-02
Log says you're running Windows XP SP3, but an error message points to an incompatibility of trying to install 32-bit vs 64-bit.

So, are you running Windows XP 64-bit? 

Or did you try to install 64-bit Wubi inside Windows XP 32-bit?

---

### Post by presence1960 on 2009-11-02
```

11-01 20:18 INFO root: === wubi 9.10ubuntu1 rev160 ===
11-01 20:18 DEBUG root: Logfile is c:\docume~1\computer\locals~1\temp\wubi-9.10ubuntu1-rev160.log
11-01 20:18 DEBUG root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
11-01 20:18 DEBUG CommonBackend: data_dir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.t mp\data
11-01 20:18 DEBUG WindowsBackend: 7z=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\bin \7z.exe
11-01 20:18 DEBUG CommonBackend: Fetching basic info...
11-01 20:18 DEBUG CommonBackend: original_exe=D:\wubi.exe
11-01 20:18 DEBUG CommonBackend: platform=win32
11-01 20:18 DEBUG CommonBackend: osname=nt
11-01 20:18 DEBUG CommonBackend: language=en_US
11-01 20:18 DEBUG CommonBackend: encoding=cp1252
11-01 20:18 DEBUG WindowsBackend: arch=i386
11-01 20:18 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tm p\data\isolist.ini
11-01 20:18 DEBUG CommonBackend: Adding distro Xubuntu-i386
11-01 20:18 DEBUG CommonBackend: Adding distro Xubuntu-amd64
11-01 20:18 DEBUG CommonBackend: Adding distro Kubuntu-amd64
11-01 20:18 DEBUG CommonBackend: Adding distro Mythbuntu-i386
11-01 20:18 DEBUG CommonBackend: Adding distro Ubuntu-amd64
11-01 20:18 DEBUG CommonBackend: Adding distro Ubuntu-i386
11-01 20:18 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
11-01 20:18 DEBUG CommonBackend: Adding distro Kubuntu-i386
11-01 20:18 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386
11-01 20:18 DEBUG CommonBackend: Adding distro UbuntuNetbookRemix-i386
11-01 20:18 DEBUG WindowsBackend: Fetching host info...
11-01 20:18 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVer sion\Uninstall\Wubi
11-01 20:18 DEBUG WindowsBackend: windows version=xp
11-01 20:18 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
11-01 20:18 DEBUG WindowsBackend: windows_sp=Service Pack 3
11-01 20:18 DEBUG WindowsBackend: windows_build=2600
11-01 20:18 DEBUG WindowsBackend: gmt=-5
11-01 20:18 DEBUG WindowsBackend: country=US
11-01 20:18 DEBUG WindowsBackend: timezone=America/New_York
11-01 20:18 DEBUG WindowsBackend: windows_username=Computer
11-01 20:18 DEBUG WindowsBackend: user_full_name=Computer
11-01 20:18 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Computer
11-01 20:18 DEBUG WindowsBackend: windows_language_code=1033
11-01 20:18 DEBUG WindowsBackend: windows_language=English
11-01 20:18 DEBUG WindowsBackend: processor_name=AMD Athlon(tm) XP 3000+
11-01 20:18 DEBUG WindowsBackend: bootloader=xp
11-01 20:18 DEBUG WindowsBackend: system_drive=Drive(C: hd 101656.714844 mb free ntfs)
11-01 20:18 DEBUG WindowsBackend: drive=Drive(C: hd 101656.714844 mb free ntfs)
11-01 20:18 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
11-01 20:18 DEBUG WindowsBackend: drive=Drive(F: removable 0.0 mb free )
11-01 20:18 DEBUG WindowsBackend: drive=Drive(G: removable 0.0 mb free )
11-01 20:18 DEBUG WindowsBackend: drive=Drive(H: removable 0.0 mb free )
11-01 20:18 DEBUG WindowsBackend: drive=Drive(I: removable 0.0 mb free )
11-01 20:18 DEBUG WindowsBackend: drive=Drive(J: cd 0.0 mb free )
11-01 20:18 DEBUG WindowsBackend: uninstaller_path=None
11-01 20:18 DEBUG WindowsBackend: previous_target_dir=None
11-01 20:18 DEBUG WindowsBackend: previous_distro_name=None
11-01 20:18 DEBUG WindowsBackend: keyboard_id=67699721
11-01 20:18 DEBUG WindowsBackend: keyboard_layout=us
11-01 20:18 DEBUG WindowsBackend: keyboard_variant=
11-01 20:18 DEBUG CommonBackend: python locale=('en_US', 'cp1252')
11-01 20:18 DEBUG CommonBackend: locale=en_US.UTF-8
11-01 20:18 DEBUG WindowsBackend: total_memory_mb=1471.484375
11-01 20:18 DEBUG CommonBackend: Searching ISOs on USB devices
11-01 20:18 DEBUG CommonBackend: Searching for local CDs
11-01 20:18 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu CD
11-01 20:18 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper \filesystem.squashfs
11-01 20:18 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu CD
11-01 20:18 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper \filesystem.squashfs
11-01 20:18 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu Netbook Remix CD
11-01 20:18 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper \filesystem.squashfs
11-01 20:18 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu CD
11-01 20:18 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper \filesystem.squashfs
11-01 20:18 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu CD
11-01 20:18 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper \filesystem.squashfs
11-01 20:18 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu Netbook CD
11-01 20:18 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper \filesystem.squashfs
11-01 20:18 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Xubuntu CD
11-01 20:18 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper \filesystem.squashfs
11-01 20:18 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Xubuntu CD
11-01 20:18 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper \filesystem.squashfs
11-01 20:18 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Mythbuntu CD
11-01 20:18 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper \filesystem.squashfs
11-01 20:18 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Mythbuntu CD
11-01 20:18 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper \filesystem.squashfs
11-01 20:18 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
11-01 20:18 DEBUG Distro: parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
11-01 20:18 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
11-01 20:18 DEBUG Distro: wrong arch: i386 != amd64
11-01 20:18 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
11-01 20:18 INFO Distro: Found a valid CD for Ubuntu: D:\
11-01 20:18 INFO root: Running the CD menu...
11-01 20:18 DEBUG WindowsFrontend: __init__...
11-01 20:18 DEBUG WindowsFrontend: on_init...
11-01 20:18 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2. tmp\translations, languages=['en_US', 'en']
11-01 20:18 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2. tmp\translations, languages=['en_US', 'en']
11-01 20:19 INFO root: CD menu finished
11-01 20:19 INFO root: Running the CD menu...
11-01 20:19 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2. tmp\translations, languages=['en_US', 'en']
11-01 20:19 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2. tmp\translations, languages=['en_US', 'en']
11-01 20:19 INFO root: CD menu finished
11-01 20:19 INFO root: Running the CD menu...
11-01 20:19 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2. tmp\translations, languages=['en_US', 'en']
11-01 20:19 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2. tmp\translations, languages=['en_US', 'en']
11-01 20:19 INFO WindowsFrontend: Operation cancelled
11-01 20:19 DEBUG WindowsFrontend: frontend.quit
11-01 20:19 DEBUG WindowsFrontend: frontend.on_quit
11-01 20:19 DEBUG root: application.on_quit
11-01 20:19 INFO root: sys.exit
11-01 21:38 INFO root: === wubi 9.10ubuntu1 rev160 ===
11-01 21:38 DEBUG root: Logfile is c:\docume~1\computer\locals~1\temp\wubi-9.10ubuntu1-rev160.log
11-01 21:38 DEBUG root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
11-01 21:38 DEBUG CommonBackend: data_dir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.t mp\data
11-01 21:38 DEBUG WindowsBackend: 7z=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\bin \7z.exe
11-01 21:38 DEBUG CommonBackend: Fetching basic info...
11-01 21:38 DEBUG CommonBackend: original_exe=D:\wubi.exe
11-01 21:38 DEBUG CommonBackend: platform=win32
11-01 21:38 DEBUG CommonBackend: osname=nt
11-01 21:38 DEBUG CommonBackend: language=en_US
11-01 21:38 DEBUG CommonBackend: encoding=cp1252
11-01 21:38 DEBUG WindowsBackend: arch=i386
11-01 21:38 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tm p\data\isolist.ini
11-01 21:38 DEBUG CommonBackend: Adding distro Xubuntu-i386
11-01 21:38 DEBUG CommonBackend: Adding distro Xubuntu-amd64
11-01 21:38 DEBUG CommonBackend: Adding distro Kubuntu-amd64
11-01 21:38 DEBUG CommonBackend: Adding distro Mythbuntu-i386
11-01 21:38 DEBUG CommonBackend: Adding distro Ubuntu-amd64
11-01 21:38 DEBUG CommonBackend: Adding distro Ubuntu-i386
11-01 21:38 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
11-01 21:38 DEBUG CommonBackend: Adding distro Kubuntu-i386
11-01 21:38 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386
11-01 21:38 DEBUG CommonBackend: Adding distro UbuntuNetbookRemix-i386
11-01 21:38 DEBUG WindowsBackend: Fetching host info...
11-01 21:38 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVer sion\Uninstall\Wubi
11-01 21:38 DEBUG WindowsBackend: windows version=xp
11-01 21:38 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
11-01 21:38 DEBUG WindowsBackend: windows_sp=Service Pack 3
11-01 21:38 DEBUG WindowsBackend: windows_build=2600
11-01 21:38 DEBUG WindowsBackend: gmt=-5
11-01 21:38 DEBUG WindowsBackend: country=US
11-01 21:38 DEBUG WindowsBackend: timezone=America/New_York
11-01 21:38 DEBUG WindowsBackend: windows_username=Computer
11-01 21:38 DEBUG WindowsBackend: user_full_name=Computer
11-01 21:38 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Computer
11-01 21:38 DEBUG WindowsBackend: windows_language_code=1033
11-01 21:38 DEBUG WindowsBackend: windows_language=English
11-01 21:38 DEBUG WindowsBackend: processor_name=AMD Athlon(tm) XP 3000+
11-01 21:38 DEBUG WindowsBackend: bootloader=xp
11-01 21:38 DEBUG WindowsBackend: system_drive=Drive(C: hd 101627.203125 mb free ntfs)
11-01 21:38 DEBUG WindowsBackend: drive=Drive(C: hd 101627.203125 mb free ntfs)
11-01 21:38 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
11-01 21:38 DEBUG WindowsBackend: drive=Drive(F: removable 0.0 mb free )
11-01 21:38 DEBUG WindowsBackend: drive=Drive(G: removable 0.0 mb free )
11-01 21:38 DEBUG WindowsBackend: drive=Drive(H: removable 0.0 mb free )
11-01 21:38 DEBUG WindowsBackend: drive=Drive(I: removable 0.0 mb free )
11-01 21:38 DEBUG WindowsBackend: drive=Drive(J: cd 0.0 mb free )
11-01 21:38 DEBUG WindowsBackend: uninstaller_path=None
11-01 21:38 DEBUG WindowsBackend: previous_target_dir=None
11-01 21:38 DEBUG WindowsBackend: previous_distro_name=None
11-01 21:38 DEBUG WindowsBackend: keyboard_id=67699721
11-01 21:38 DEBUG WindowsBackend: keyboard_layout=us
11-01 21:38 DEBUG WindowsBackend: keyboard_variant=
11-01 21:38 DEBUG CommonBackend: python locale=('en_US', 'cp1252')
11-01 21:38 DEBUG CommonBackend: locale=en_US.UTF-8
11-01 21:38 DEBUG WindowsBackend: total_memory_mb=1471.484375
11-01 21:38 DEBUG CommonBackend: Searching ISOs on USB devices
11-01 21:38 DEBUG CommonBackend: Searching for local CDs
11-01 21:38 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu CD
11-01 21:38 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper \filesystem.squashfs
11-01 21:38 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu CD
11-01 21:38 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper \filesystem.squashfs
11-01 21:38 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu Netbook Remix CD
11-01 21:38 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper \filesystem.squashfs
11-01 21:38 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu CD
11-01 21:38 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper \filesystem.squashfs
11-01 21:38 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu CD
11-01 21:38 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper \filesystem.squashfs
11-01 21:38 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu Netbook CD
11-01 21:38 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper \filesystem.squashfs
11-01 21:38 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Xubuntu CD
11-01 21:38 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper \filesystem.squashfs
11-01 21:38 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Xubuntu CD
11-01 21:38 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper \filesystem.squashfs
11-01 21:38 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Mythbuntu CD
11-01 21:38 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper \filesystem.squashfs
11-01 21:38 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Mythbuntu CD
11-01 21:38 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper \filesystem.squashfs
11-01 21:38 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
11-01 21:38 DEBUG Distro: parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
11-01 21:38 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
11-01 21:38 DEBUG Distro: wrong arch: i386 != amd64
11-01 21:38 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
11-01 21:38 INFO Distro: Found a valid CD for Ubuntu: D:\
11-01 21:38 INFO root: Running the CD menu...
11-01 21:38 DEBUG WindowsFrontend: __init__...
11-01 21:38 DEBUG WindowsFrontend: on_init...
11-01 21:38 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2. tmp\translations, languages=['en_US', 'en']
11-01 21:38 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2. tmp\translations, languages=['en_US', 'en']
11-01 21:48 INFO WindowsFrontend: Operation cancelled
11-01 21:48 DEBUG WindowsFrontend: frontend.quit
11-01 21:48 DEBUG WindowsFrontend: frontend.on_quit
11-01 21:48 DEBUG root: application.on_quit
11-01 21:48 INFO root: sys.exit
11-01 21:50 INFO root: === wubi 9.10ubuntu1 rev160 ===
11-01 21:50 DEBUG root: Logfile is c:\docume~1\computer\locals~1\temp\wubi-9.10ubuntu1-rev160.log
11-01 21:50 DEBUG root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
11-01 21:50 DEBUG CommonBackend: data_dir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.t mp\data
11-01 21:50 DEBUG WindowsBackend: 7z=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp\bin \7z.exe
11-01 21:50 DEBUG CommonBackend: Fetching basic info...
11-01 21:50 DEBUG CommonBackend: original_exe=D:\wubi.exe
11-01 21:50 DEBUG CommonBackend: platform=win32
11-01 21:50 DEBUG CommonBackend: osname=nt
11-01 21:50 DEBUG CommonBackend: language=en_US
11-01 21:50 DEBUG CommonBackend: encoding=cp1252
11-01 21:50 DEBUG WindowsBackend: arch=i386
11-01 21:50 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tm p\data\isolist.ini
11-01 21:50 DEBUG CommonBackend: Adding distro Xubuntu-i386
11-01 21:50 DEBUG CommonBackend: Adding distro Xubuntu-amd64
11-01 21:50 DEBUG CommonBackend: Adding distro Kubuntu-amd64
11-01 21:50 DEBUG CommonBackend: Adding distro Mythbuntu-i386
11-01 21:50 DEBUG CommonBackend: Adding distro Ubuntu-amd64
11-01 21:50 DEBUG CommonBackend: Adding distro Ubuntu-i386
11-01 21:50 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
11-01 21:50 DEBUG CommonBackend: Adding distro Kubuntu-i386
11-01 21:50 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386
11-01 21:50 DEBUG CommonBackend: Adding distro UbuntuNetbookRemix-i386
11-01 21:50 DEBUG WindowsBackend: Fetching host info...
11-01 21:50 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVer sion\Uninstall\Wubi
11-01 21:50 DEBUG WindowsBackend: windows version=xp
11-01 21:50 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
11-01 21:50 DEBUG WindowsBackend: windows_sp=Service Pack 3
11-01 21:50 DEBUG WindowsBackend: windows_build=2600
11-01 21:50 DEBUG WindowsBackend: gmt=-5
11-01 21:50 DEBUG WindowsBackend: country=US
11-01 21:50 DEBUG WindowsBackend: timezone=America/New_York
11-01 21:50 DEBUG WindowsBackend: windows_username=Computer
11-01 21:50 DEBUG WindowsBackend: user_full_name=Computer
11-01 21:50 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Computer
11-01 21:50 DEBUG WindowsBackend: windows_language_code=1033
11-01 21:50 DEBUG WindowsBackend: windows_language=English
11-01 21:50 DEBUG WindowsBackend: processor_name=AMD Athlon(tm) XP 3000+
11-01 21:50 DEBUG WindowsBackend: bootloader=xp
11-01 21:50 DEBUG WindowsBackend: system_drive=Drive(C: hd 101625.660156 mb free ntfs)
11-01 21:50 DEBUG WindowsBackend: drive=Drive(C: hd 101625.660156 mb free ntfs)
11-01 21:50 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
11-01 21:50 DEBUG WindowsBackend: drive=Drive(F: removable 0.0 mb free )
11-01 21:50 DEBUG WindowsBackend: drive=Drive(G: removable 0.0 mb free )
11-01 21:50 DEBUG WindowsBackend: drive=Drive(H: removable 0.0 mb free )
11-01 21:50 DEBUG WindowsBackend: drive=Drive(I: removable 0.0 mb free )
11-01 21:50 DEBUG WindowsBackend: drive=Drive(J: cd 0.0 mb free )
11-01 21:50 DEBUG WindowsBackend: uninstaller_path=None
11-01 21:50 DEBUG WindowsBackend: previous_target_dir=None
11-01 21:50 DEBUG WindowsBackend: previous_distro_name=None
11-01 21:50 DEBUG WindowsBackend: keyboard_id=67699721
11-01 21:50 DEBUG WindowsBackend: keyboard_layout=us
11-01 21:50 DEBUG WindowsBackend: keyboard_variant=
11-01 21:50 DEBUG CommonBackend: python locale=('en_US', 'cp1252')
11-01 21:50 DEBUG CommonBackend: locale=en_US.UTF-8
11-01 21:50 DEBUG WindowsBackend: total_memory_mb=1471.484375
11-01 21:50 DEBUG CommonBackend: Searching ISOs on USB devices
11-01 21:50 DEBUG CommonBackend: Searching for local CDs
11-01 21:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp is a valid Ubuntu CD
11-01 21:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp\casper \filesystem.squashfs
11-01 21:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp is a valid Ubuntu CD
11-01 21:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp\casper \filesystem.squashfs
11-01 21:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp is a valid Ubuntu Netbook Remix CD
11-01 21:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp\casper \filesystem.squashfs
11-01 21:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp is a valid Kubuntu CD
11-01 21:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp\casper \filesystem.squashfs
11-01 21:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp is a valid Kubuntu CD
11-01 21:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp\casper \filesystem.squashfs
11-01 21:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp is a valid Kubuntu Netbook CD
11-01 21:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp\casper \filesystem.squashfs
11-01 21:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp is a valid Xubuntu CD
11-01 21:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp\casper \filesystem.squashfs
11-01 21:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp is a valid Xubuntu CD
11-01 21:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp\casper \filesystem.squashfs
11-01 21:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp is a valid Mythbuntu CD
11-01 21:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp\casper \filesystem.squashfs
11-01 21:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp is a valid Mythbuntu CD
11-01 21:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp\casper \filesystem.squashfs
11-01 21:50 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
11-01 21:50 DEBUG Distro: parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
11-01 21:50 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
11-01 21:50 DEBUG Distro: wrong arch: i386 != amd64
11-01 21:50 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
11-01 21:50 INFO Distro: Found a valid CD for Ubuntu: D:\
11-01 21:50 INFO root: Running the CD menu...
11-01 21:50 DEBUG WindowsFrontend: __init__...
11-01 21:50 DEBUG WindowsFrontend: on_init...
11-01 21:50 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3. tmp\translations, languages=['en_US', 'en']
11-01 21:50 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3. tmp\translations, languages=['en_US', 'en']
11-01 21:50 INFO root: CD menu finished
11-01 21:50 INFO root: Running the installer...
11-01 21:50 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3. tmp\translations, languages=['en_US', 'en']
11-01 21:50 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3. tmp\translations, languages=['en_US', 'en']
11-01 21:50 DEBUG WinuiInstallationPage: target_drive=C:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=computer
11-01 21:50 INFO root: Received settings
11-01 21:50 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3. tmp\translations, languages=['en_US', 'en']
11-01 21:50 DEBUG TaskList: # Running tasklist...
11-01 21:50 DEBUG TaskList: ## Running select_target_dir...
11-01 21:50 INFO WindowsBackend: Installing into C:\ubuntu
11-01 21:50 DEBUG TaskList: ## Finished select_target_dir
11-01 21:50 DEBUG TaskList: ## Running create_dir_structure...
11-01 21:50 DEBUG CommonBackend: Creating dir C:\ubuntu
11-01 21:50 DEBUG CommonBackend: Creating dir C:\ubuntu\disks
11-01 21:50 DEBUG CommonBackend: Creating dir C:\ubuntu\install
11-01 21:50 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot
11-01 21:50 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot
11-01 21:50 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
11-01 21:50 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot\grub
11-01 21:50 DEBUG TaskList: ## Finished create_dir_structure
11-01 21:50 DEBUG TaskList: ## Running uncompress_target_dir...
11-01 21:50 DEBUG TaskList: ## Finished uncompress_target_dir
11-01 21:50 DEBUG TaskList: ## Running create_uninstaller...
11-01 21:50 DEBUG WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
11-01 21:50 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
11-01 21:50 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi InstallationDir C:\ubuntu
11-01 21:50 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi DisplayName Ubuntu
11-01 21:50 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
11-01 21:50 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi DisplayVersion 9.10ubuntu1-rev160
11-01 21:50 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi Publisher Ubuntu
11-01 21:50 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi URLInfoAbout http://www.ubuntu.com
11-01 21:50 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi HelpLink http://www.ubuntu.com/support
11-01 21:50 DEBUG TaskList: ## Finished create_uninstaller
11-01 21:50 DEBUG TaskList: ## Running copy_installation_files...
11-01 21:50 DEBUG WindowsBackend: Copying C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp\data\c ustom-installation -> C:\ubuntu\install\custom-installation
11-01 21:50 DEBUG WindowsBackend: Copying C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp\winboo t -> C:\ubuntu\winboot
11-01 21:50 DEBUG WindowsBackend: Copying C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl3.tmp\data\i mages\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
11-01 21:50 DEBUG TaskList: ## Finished copy_installation_files
11-01 21:50 DEBUG TaskList: ## Running get_iso...
11-01 21:50 DEBUG TaskList: New task copy_file
11-01 21:50 DEBUG TaskList: ### Running copy_file...
11-01 21:51 ERROR TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 22] Invalid argument
11-01 21:51 DEBUG TaskList: # Cancelling tasklist
11-01 21:51 ERROR root: [Errno 22] Invalid argument
Traceback (most recent call last):
File "\lib\wubi\application.py", line 56, in run
File "\lib\wubi\application.py", line 126, in select_task
File "\lib\wubi\application.py", line 194, in run_cd_menu
File "\lib\wubi\application.py", line 118, in select_task
File "\lib\wubi\application.py", line 156, in run_installer
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 22] Invalid argument
11-01 21:51 DEBUG TaskList: New task check_iso
11-01 21:51 DEBUG CommonBackend: Searching for local ISO
11-01 21:51 DEBUG CommonBackend: Could not find any ISO or CD, downloading one now
11-01 21:51 DEBUG TaskList: New task get_metalink
11-01 21:51 ERROR TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
11-01 21:51 DEBUG TaskList: # Cancelling tasklist
11-01 21:51 DEBUG TaskList: # Finished tasklist
11-02 13:48 INFO root: === wubi 9.10ubuntu1 rev160 ===
11-02 13:48 DEBUG root: Logfile is c:\docume~1\computer\locals~1\temp\wubi-9.10ubuntu1-rev160.log
11-02 13:48 DEBUG root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
11-02 13:48 DEBUG CommonBackend: data_dir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.t mp\data
11-02 13:48 DEBUG WindowsBackend: 7z=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\bin \7z.exe
11-02 13:48 DEBUG CommonBackend: Fetching basic info...
11-02 13:48 DEBUG CommonBackend: original_exe=D:\wubi.exe
11-02 13:48 DEBUG CommonBackend: platform=win32
11-02 13:48 DEBUG CommonBackend: osname=nt
11-02 13:48 DEBUG CommonBackend: language=en_US
11-02 13:48 DEBUG CommonBackend: encoding=cp1252
11-02 13:48 DEBUG WindowsBackend: arch=i386
11-02 13:48 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tm p\data\isolist.ini
11-02 13:48 DEBUG CommonBackend: Adding distro Xubuntu-i386
11-02 13:48 DEBUG CommonBackend: Adding distro Xubuntu-amd64
11-02 13:48 DEBUG CommonBackend: Adding distro Kubuntu-amd64
11-02 13:48 DEBUG CommonBackend: Adding distro Mythbuntu-i386
11-02 13:48 DEBUG CommonBackend: Adding distro Ubuntu-amd64
11-02 13:48 DEBUG CommonBackend: Adding distro Ubuntu-i386
11-02 13:48 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
11-02 13:48 DEBUG CommonBackend: Adding distro Kubuntu-i386
11-02 13:48 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386
11-02 13:48 DEBUG CommonBackend: Adding distro UbuntuNetbookRemix-i386
11-02 13:48 DEBUG WindowsBackend: Fetching host info...
11-02 13:48 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVer sion\Uninstall\Wubi
11-02 13:48 DEBUG WindowsBackend: windows version=xp
11-02 13:48 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
11-02 13:48 DEBUG WindowsBackend: windows_sp=Service Pack 3
11-02 13:48 DEBUG WindowsBackend: windows_build=2600
11-02 13:48 DEBUG WindowsBackend: gmt=-5
11-02 13:48 DEBUG WindowsBackend: country=US
11-02 13:48 DEBUG WindowsBackend: timezone=America/New_York
11-02 13:48 DEBUG WindowsBackend: windows_username=Computer
11-02 13:48 DEBUG WindowsBackend: user_full_name=Computer
11-02 13:48 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Computer
11-02 13:48 DEBUG WindowsBackend: windows_language_code=1033
11-02 13:48 DEBUG WindowsBackend: windows_language=English
11-02 13:48 DEBUG WindowsBackend: processor_name=AMD Athlon(tm) XP 3000+
11-02 13:48 DEBUG WindowsBackend: bootloader=xp
11-02 13:48 DEBUG WindowsBackend: system_drive=Drive(C: hd 101460.84375 mb free ntfs)
11-02 13:48 DEBUG WindowsBackend: drive=Drive(C: hd 101460.84375 mb free ntfs)
11-02 13:48 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
11-02 13:48 DEBUG WindowsBackend: drive=Drive(F: removable 0.0 mb free )
11-02 13:48 DEBUG WindowsBackend: drive=Drive(G: removable 0.0 mb free )
11-02 13:48 DEBUG WindowsBackend: drive=Drive(H: removable 0.0 mb free )
11-02 13:48 DEBUG WindowsBackend: drive=Drive(I: removable 0.0 mb free )
11-02 13:48 DEBUG WindowsBackend: drive=Drive(J: cd 0.0 mb free )
11-02 13:48 DEBUG WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
11-02 13:48 DEBUG WindowsBackend: previous_target_dir=C:\ubuntu
11-02 13:48 DEBUG WindowsBackend: previous_distro_name=Ubuntu
11-02 13:48 DEBUG WindowsBackend: keyboard_id=67699721
11-02 13:48 DEBUG WindowsBackend: keyboard_layout=us
11-02 13:48 DEBUG WindowsBackend: keyboard_variant=
11-02 13:48 DEBUG CommonBackend: python locale=('en_US', 'cp1252')
11-02 13:48 DEBUG CommonBackend: locale=en_US.UTF-8
11-02 13:48 DEBUG WindowsBackend: total_memory_mb=1471.484375
11-02 13:48 DEBUG CommonBackend: Searching ISOs on USB devices
11-02 13:48 DEBUG CommonBackend: Searching for local CDs
11-02 13:48 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
11-02 13:48 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\casper \filesystem.squashfs
11-02 13:48 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
11-02 13:48 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\casper \filesystem.squashfs
11-02 13:48 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu Netbook Remix CD
11-02 13:48 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\casper \filesystem.squashfs
11-02 13:48 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
11-02 13:48 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\casper \filesystem.squashfs
11-02 13:48 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
11-02 13:48 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\casper \filesystem.squashfs
11-02 13:48 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu Netbook CD
11-02 13:48 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\casper \filesystem.squashfs
11-02 13:48 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
11-02 13:48 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\casper \filesystem.squashfs
11-02 13:48 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
11-02 13:48 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\casper \filesystem.squashfs
11-02 13:48 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
11-02 13:48 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\casper \filesystem.squashfs
11-02 13:48 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
11-02 13:48 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\casper \filesystem.squashfs
11-02 13:48 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
11-02 13:48 DEBUG Distro: parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
11-02 13:48 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
11-02 13:48 DEBUG Distro: wrong arch: i386 != amd64
11-02 13:48 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
11-02 13:48 INFO Distro: Found a valid CD for Ubuntu: D:\
11-02 13:48 INFO root: Running the CD menu...
11-02 13:48 DEBUG WindowsFrontend: __init__...
11-02 13:48 DEBUG WindowsFrontend: on_init...
11-02 13:48 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1. tmp\translations, languages=['en_US', 'en']
11-02 13:48 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1. tmp\translations, languages=['en_US', 'en']
11-02 13:48 INFO root: CD menu finished
11-02 13:48 INFO root: Already installed, running the uninstaller...
11-02 13:48 INFO root: Running the uninstaller...
11-02 13:48 INFO CommonBackend: This is the uninstaller running
11-02 13:48 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1. tmp\translations, languages=['en_US', 'en']
11-02 13:48 INFO root: Received settings
11-02 13:48 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1. tmp\translations, languages=['en_US', 'en']
11-02 13:48 DEBUG TaskList: # Running tasklist...
11-02 13:48 DEBUG TaskList: ## Running Backup ISO...
11-02 13:48 DEBUG TaskList: ## Finished Backup ISO
11-02 13:48 DEBUG TaskList: ## Running Remove bootloader entry...
11-02 13:48 ERROR WindowsBackend: Cannot find bcdedit
11-02 13:48 DEBUG WindowsBackend: undo_bootini C:
11-02 13:48 DEBUG WindowsBackend: undo_configsys Drive(C: hd 101460.84375 mb free ntfs)
11-02 13:48 DEBUG WindowsBackend: undo_bootini F:
11-02 13:48 DEBUG WindowsBackend: undo_configsys Drive(F: removable 0.0 mb free )
11-02 13:48 DEBUG WindowsBackend: undo_bootini G:
11-02 13:48 DEBUG WindowsBackend: undo_configsys Drive(G: removable 0.0 mb free )
11-02 13:48 DEBUG WindowsBackend: undo_bootini H:
11-02 13:48 DEBUG WindowsBackend: undo_configsys Drive(H: removable 0.0 mb free )
11-02 13:48 DEBUG WindowsBackend: undo_bootini I:
11-02 13:48 DEBUG WindowsBackend: undo_configsys Drive(I: removable 0.0 mb free )
11-02 13:48 DEBUG TaskList: ## Finished Remove bootloader entry
11-02 13:48 DEBUG TaskList: ## Running Remove target dir...
11-02 13:48 DEBUG CommonBackend: Deleting C:\ubuntu
11-02 13:48 DEBUG TaskList: ## Finished Remove target dir
11-02 13:48 DEBUG TaskList: ## Running Remove registry key...
11-02 13:48 DEBUG TaskList: ## Finished Remove registry key
11-02 13:48 DEBUG TaskList: # Finished tasklist
11-02 13:48 INFO root: Almost finished uninstalling
11-02 13:48 INFO root: Finished uninstallation
11-02 13:48 DEBUG CommonBackend: Fetching basic info...
11-02 13:48 DEBUG CommonBackend: original_exe=D:\wubi.exe
11-02 13:48 DEBUG CommonBackend: platform=win32
11-02 13:48 DEBUG CommonBackend: osname=nt
11-02 13:48 DEBUG WindowsBackend: arch=i386
11-02 13:48 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tm p\data\isolist.ini
11-02 13:48 DEBUG CommonBackend: Adding distro Xubuntu-i386
11-02 13:48 DEBUG CommonBackend: Adding distro Xubuntu-amd64
11-02 13:48 DEBUG CommonBackend: Adding distro Kubuntu-amd64
11-02 13:48 DEBUG CommonBackend: Adding distro Mythbuntu-i386
11-02 13:48 DEBUG CommonBackend: Adding distro Ubuntu-amd64
11-02 13:48 DEBUG CommonBackend: Adding distro Ubuntu-i386
11-02 13:48 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
11-02 13:48 DEBUG CommonBackend: Adding distro Kubuntu-i386
11-02 13:48 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386
11-02 13:48 DEBUG CommonBackend: Adding distro UbuntuNetbookRemix-i386
11-02 13:48 DEBUG WindowsBackend: Fetching host info...
11-02 13:48 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVer sion\Uninstall\Wubi
11-02 13:48 DEBUG WindowsBackend: windows version=xp
11-02 13:48 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
11-02 13:48 DEBUG WindowsBackend: windows_sp=Service Pack 3
11-02 13:48 DEBUG WindowsBackend: windows_build=2600
11-02 13:48 DEBUG WindowsBackend: gmt=-5
11-02 13:48 DEBUG WindowsBackend: country=US
11-02 13:48 DEBUG WindowsBackend: timezone=America/New_York
11-02 13:48 DEBUG WindowsBackend: windows_username=Computer
11-02 13:48 DEBUG WindowsBackend: user_full_name=Computer
11-02 13:48 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Computer
11-02 13:48 DEBUG WindowsBackend: windows_language_code=1033
11-02 13:48 DEBUG WindowsBackend: windows_language=English
11-02 13:48 DEBUG WindowsBackend: processor_name=AMD Athlon(tm) XP 3000+
11-02 13:48 DEBUG WindowsBackend: bootloader=xp
11-02 13:48 DEBUG WindowsBackend: system_drive=Drive(C: hd 101558.917969 mb free ntfs)
11-02 13:48 DEBUG WindowsBackend: drive=Drive(C: hd 101558.917969 mb free ntfs)
11-02 13:48 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
11-02 13:48 DEBUG WindowsBackend: drive=Drive(F: removable 0.0 mb free )
11-02 13:48 DEBUG WindowsBackend: drive=Drive(G: removable 0.0 mb free )
11-02 13:48 DEBUG WindowsBackend: drive=Drive(H: removable 0.0 mb free )
11-02 13:48 DEBUG WindowsBackend: drive=Drive(I: removable 0.0 mb free )
11-02 13:48 DEBUG WindowsBackend: drive=Drive(J: cd 0.0 mb free )
11-02 13:48 DEBUG WindowsBackend: uninstaller_path=None
11-02 13:48 DEBUG WindowsBackend: previous_target_dir=None
11-02 13:48 DEBUG WindowsBackend: previous_distro_name=None
11-02 13:48 DEBUG WindowsBackend: keyboard_id=67699721
11-02 13:48 DEBUG WindowsBackend: keyboard_layout=us
11-02 13:48 DEBUG WindowsBackend: keyboard_variant=
11-02 13:48 DEBUG WindowsBackend: total_memory_mb=1471.484375
11-02 13:48 DEBUG CommonBackend: Searching ISOs on USB devices
11-02 13:48 DEBUG CommonBackend: Searching for local CDs
11-02 13:48 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
11-02 13:48 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\casper \filesystem.squashfs
11-02 13:48 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
11-02 13:48 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\casper \filesystem.squashfs
11-02 13:48 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu Netbook Remix CD
11-02 13:48 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\casper \filesystem.squashfs
11-02 13:48 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
11-02 13:48 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\casper \filesystem.squashfs
11-02 13:48 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
11-02 13:48 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\casper \filesystem.squashfs
11-02 13:48 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu Netbook CD
11-02 13:48 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\casper \filesystem.squashfs
11-02 13:48 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
11-02 13:48 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\casper \filesystem.squashfs
11-02 13:48 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
11-02 13:48 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\casper \filesystem.squashfs
11-02 13:48 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
11-02 13:48 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\casper \filesystem.squashfs
11-02 13:48 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
11-02 13:48 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\casper \filesystem.squashfs
11-02 13:48 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
11-02 13:48 DEBUG Distro: wrong arch: i386 != amd64
11-02 13:48 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
11-02 13:48 INFO Distro: Found a valid CD for Ubuntu: D:\
11-02 13:48 INFO root: Running the installer...
11-02 13:48 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1. tmp\translations, languages=['en_US', 'en']
11-02 13:48 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1. tmp\translations, languages=['en_US', 'en']
11-02 13:49 DEBUG WinuiInstallationPage: target_drive=C:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=computer
11-02 13:49 INFO root: Received settings
11-02 13:49 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1. tmp\translations, languages=['en_US', 'en']
11-02 13:49 DEBUG TaskList: # Running tasklist...
11-02 13:49 DEBUG TaskList: ## Running select_target_dir...
11-02 13:49 INFO WindowsBackend: Installing into C:\ubuntu
11-02 13:49 DEBUG TaskList: ## Finished select_target_dir
11-02 13:49 DEBUG TaskList: ## Running create_dir_structure...
11-02 13:49 DEBUG CommonBackend: Creating dir C:\ubuntu
11-02 13:49 DEBUG CommonBackend: Creating dir C:\ubuntu\disks
11-02 13:49 DEBUG CommonBackend: Creating dir C:\ubuntu\install
11-02 13:49 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot
11-02 13:49 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot
11-02 13:49 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
11-02 13:49 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot\grub
11-02 13:49 DEBUG TaskList: ## Finished create_dir_structure
11-02 13:49 DEBUG TaskList: ## Running uncompress_target_dir...
11-02 13:49 DEBUG TaskList: ## Finished uncompress_target_dir
11-02 13:49 DEBUG TaskList: ## Running create_uninstaller...
11-02 13:49 DEBUG WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
11-02 13:49 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
11-02 13:49 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi InstallationDir C:\ubuntu
11-02 13:49 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi DisplayName Ubuntu
11-02 13:49 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
11-02 13:49 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi DisplayVersion 9.10ubuntu1-rev160
11-02 13:49 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi Publisher Ubuntu
11-02 13:49 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi URLInfoAbout http://www.ubuntu.com
11-02 13:49 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi HelpLink http://www.ubuntu.com/support
11-02 13:49 DEBUG TaskList: ## Finished create_uninstaller
11-02 13:49 DEBUG TaskList: ## Running copy_installation_files...
11-02 13:49 DEBUG WindowsBackend: Copying C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\data\c ustom-installation -> C:\ubuntu\install\custom-installation
11-02 13:49 DEBUG WindowsBackend: Copying C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\winboo t -> C:\ubuntu\winboot
11-02 13:49 DEBUG WindowsBackend: Copying C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl1.tmp\data\i mages\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
11-02 13:49 DEBUG TaskList: ## Finished copy_installation_files
11-02 13:49 DEBUG TaskList: ## Running get_iso...
11-02 13:49 DEBUG TaskList: New task copy_file
11-02 13:49 DEBUG TaskList: ### Running copy_file...
11-02 13:49 ERROR TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 22] Invalid argument
11-02 13:49 DEBUG TaskList: # Cancelling tasklist
11-02 13:49 ERROR root: [Errno 22] Invalid argument
Traceback (most recent call last):
File "\lib\wubi\application.py", line 56, in run
File "\lib\wubi\application.py", line 126, in select_task
File "\lib\wubi\application.py", line 194, in run_cd_menu
File "\lib\wubi\application.py", line 118, in select_task
File "\lib\wubi\application.py", line 156, in run_installer
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 22] Invalid argument
11-02 13:49 DEBUG TaskList: New task check_iso
11-02 13:49 DEBUG CommonBackend: Searching for local ISO
11-02 13:49 DEBUG CommonBackend: Could not find any ISO or CD, downloading one now
11-02 13:49 DEBUG TaskList: New task get_metalink
11-02 13:49 ERROR TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
11-02 13:49 DEBUG TaskList: # Cancelling tasklist
11-02 13:49 DEBUG TaskList: # Finished tasklist
11-02 13:50 INFO root: === wubi 9.10ubuntu1 rev160 ===
11-02 13:50 DEBUG root: Logfile is c:\docume~1\computer\locals~1\temp\wubi-9.10ubuntu1-rev160.log
11-02 13:50 DEBUG root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
11-02 13:50 DEBUG CommonBackend: data_dir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.t mp\data
11-02 13:50 DEBUG WindowsBackend: 7z=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\bin \7z.exe
11-02 13:50 DEBUG CommonBackend: Fetching basic info...
11-02 13:50 DEBUG CommonBackend: original_exe=D:\wubi.exe
11-02 13:50 DEBUG CommonBackend: platform=win32
11-02 13:50 DEBUG CommonBackend: osname=nt
11-02 13:50 DEBUG CommonBackend: language=en_US
11-02 13:50 DEBUG CommonBackend: encoding=cp1252
11-02 13:50 DEBUG WindowsBackend: arch=i386
11-02 13:50 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tm p\data\isolist.ini
11-02 13:50 DEBUG CommonBackend: Adding distro Xubuntu-i386
11-02 13:50 DEBUG CommonBackend: Adding distro Xubuntu-amd64
11-02 13:50 DEBUG CommonBackend: Adding distro Kubuntu-amd64
11-02 13:50 DEBUG CommonBackend: Adding distro Mythbuntu-i386
11-02 13:50 DEBUG CommonBackend: Adding distro Ubuntu-amd64
11-02 13:50 DEBUG CommonBackend: Adding distro Ubuntu-i386
11-02 13:50 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
11-02 13:50 DEBUG CommonBackend: Adding distro Kubuntu-i386
11-02 13:50 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386
11-02 13:50 DEBUG CommonBackend: Adding distro UbuntuNetbookRemix-i386
11-02 13:50 DEBUG WindowsBackend: Fetching host info...
11-02 13:50 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVer sion\Uninstall\Wubi
11-02 13:50 DEBUG WindowsBackend: windows version=xp
11-02 13:50 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
11-02 13:50 DEBUG WindowsBackend: windows_sp=Service Pack 3
11-02 13:50 DEBUG WindowsBackend: windows_build=2600
11-02 13:50 DEBUG WindowsBackend: gmt=-5
11-02 13:50 DEBUG WindowsBackend: country=US
11-02 13:50 DEBUG WindowsBackend: timezone=America/New_York
11-02 13:50 DEBUG WindowsBackend: windows_username=Computer
11-02 13:50 DEBUG WindowsBackend: user_full_name=Computer
11-02 13:50 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Computer
11-02 13:50 DEBUG WindowsBackend: windows_language_code=1033
11-02 13:50 DEBUG WindowsBackend: windows_language=English
11-02 13:50 DEBUG WindowsBackend: processor_name=AMD Athlon(tm) XP 3000+
11-02 13:50 DEBUG WindowsBackend: bootloader=xp
11-02 13:50 DEBUG WindowsBackend: system_drive=Drive(C: hd 101459.375 mb free ntfs)
11-02 13:50 DEBUG WindowsBackend: drive=Drive(C: hd 101459.375 mb free ntfs)
11-02 13:50 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
11-02 13:50 DEBUG WindowsBackend: drive=Drive(F: removable 0.0 mb free )
11-02 13:50 DEBUG WindowsBackend: drive=Drive(G: removable 0.0 mb free )
11-02 13:50 DEBUG WindowsBackend: drive=Drive(H: removable 0.0 mb free )
11-02 13:50 DEBUG WindowsBackend: drive=Drive(I: removable 0.0 mb free )
11-02 13:50 DEBUG WindowsBackend: drive=Drive(J: cd 0.0 mb free )
11-02 13:50 DEBUG WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
11-02 13:50 DEBUG WindowsBackend: previous_target_dir=C:\ubuntu
11-02 13:50 DEBUG WindowsBackend: previous_distro_name=Ubuntu
11-02 13:50 DEBUG WindowsBackend: keyboard_id=67699721
11-02 13:50 DEBUG WindowsBackend: keyboard_layout=us
11-02 13:50 DEBUG WindowsBackend: keyboard_variant=
11-02 13:50 DEBUG CommonBackend: python locale=('en_US', 'cp1252')
11-02 13:50 DEBUG CommonBackend: locale=en_US.UTF-8
11-02 13:50 DEBUG WindowsBackend: total_memory_mb=1471.484375
11-02 13:50 DEBUG CommonBackend: Searching ISOs on USB devices
11-02 13:50 DEBUG CommonBackend: Searching for local CDs
11-02 13:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu CD
11-02 13:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper \filesystem.squashfs
11-02 13:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu CD
11-02 13:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper \filesystem.squashfs
11-02 13:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu Netbook Remix CD
11-02 13:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper \filesystem.squashfs
11-02 13:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu CD
11-02 13:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper \filesystem.squashfs
11-02 13:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu CD
11-02 13:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper \filesystem.squashfs
11-02 13:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu Netbook CD
11-02 13:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper \filesystem.squashfs
11-02 13:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Xubuntu CD
11-02 13:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper \filesystem.squashfs
11-02 13:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Xubuntu CD
11-02 13:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper \filesystem.squashfs
11-02 13:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Mythbuntu CD
11-02 13:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper \filesystem.squashfs
11-02 13:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Mythbuntu CD
11-02 13:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper \filesystem.squashfs
11-02 13:50 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
11-02 13:50 DEBUG Distro: parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
11-02 13:50 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
11-02 13:50 DEBUG Distro: wrong arch: i386 != amd64
11-02 13:50 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
11-02 13:50 INFO Distro: Found a valid CD for Ubuntu: D:\
11-02 13:50 INFO root: Running the CD menu...
11-02 13:50 DEBUG WindowsFrontend: __init__...
11-02 13:50 DEBUG WindowsFrontend: on_init...
11-02 13:50 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2. tmp\translations, languages=['en_US', 'en']
11-02 13:50 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2. tmp\translations, languages=['en_US', 'en']
11-02 13:50 INFO root: CD menu finished
11-02 13:50 INFO root: Already installed, running the uninstaller...
11-02 13:50 INFO root: Running the uninstaller...
11-02 13:50 INFO CommonBackend: This is the uninstaller running
11-02 13:50 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2. tmp\translations, languages=['en_US', 'en']
11-02 13:50 INFO root: Received settings
11-02 13:50 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2. tmp\translations, languages=['en_US', 'en']
11-02 13:50 DEBUG TaskList: # Running tasklist...
11-02 13:50 DEBUG TaskList: ## Running Backup ISO...
11-02 13:50 DEBUG TaskList: ## Finished Backup ISO
11-02 13:50 DEBUG TaskList: ## Running Remove bootloader entry...
11-02 13:50 ERROR WindowsBackend: Cannot find bcdedit
11-02 13:50 DEBUG WindowsBackend: undo_bootini C:
11-02 13:50 DEBUG WindowsBackend: undo_configsys Drive(C: hd 101459.375 mb free ntfs)
11-02 13:50 DEBUG WindowsBackend: undo_bootini F:
11-02 13:50 DEBUG WindowsBackend: undo_configsys Drive(F: removable 0.0 mb free )
11-02 13:50 DEBUG WindowsBackend: undo_bootini G:
11-02 13:50 DEBUG WindowsBackend: undo_configsys Drive(G: removable 0.0 mb free )
11-02 13:50 DEBUG WindowsBackend: undo_bootini H:
11-02 13:50 DEBUG WindowsBackend: undo_configsys Drive(H: removable 0.0 mb free )
11-02 13:50 DEBUG WindowsBackend: undo_bootini I:
11-02 13:50 DEBUG WindowsBackend: undo_configsys Drive(I: removable 0.0 mb free )
11-02 13:50 DEBUG TaskList: ## Finished Remove bootloader entry
11-02 13:50 DEBUG TaskList: ## Running Remove target dir...
11-02 13:50 DEBUG CommonBackend: Deleting C:\ubuntu
11-02 13:50 DEBUG TaskList: ## Finished Remove target dir
11-02 13:50 DEBUG TaskList: ## Running Remove registry key...
11-02 13:50 DEBUG TaskList: ## Finished Remove registry key
11-02 13:50 DEBUG TaskList: # Finished tasklist
11-02 13:50 INFO root: Almost finished uninstalling
11-02 13:50 INFO root: Finished uninstallation
11-02 13:50 DEBUG CommonBackend: Fetching basic info...
11-02 13:50 DEBUG CommonBackend: original_exe=D:\wubi.exe
11-02 13:50 DEBUG CommonBackend: platform=win32
11-02 13:50 DEBUG CommonBackend: osname=nt
11-02 13:50 DEBUG WindowsBackend: arch=i386
11-02 13:50 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tm p\data\isolist.ini
11-02 13:50 DEBUG CommonBackend: Adding distro Xubuntu-i386
11-02 13:50 DEBUG CommonBackend: Adding distro Xubuntu-amd64
11-02 13:50 DEBUG CommonBackend: Adding distro Kubuntu-amd64
11-02 13:50 DEBUG CommonBackend: Adding distro Mythbuntu-i386
11-02 13:50 DEBUG CommonBackend: Adding distro Ubuntu-amd64
11-02 13:50 DEBUG CommonBackend: Adding distro Ubuntu-i386
11-02 13:50 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
11-02 13:50 DEBUG CommonBackend: Adding distro Kubuntu-i386
11-02 13:50 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386
11-02 13:50 DEBUG CommonBackend: Adding distro UbuntuNetbookRemix-i386
11-02 13:50 DEBUG WindowsBackend: Fetching host info...
11-02 13:50 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVer sion\Uninstall\Wubi
11-02 13:50 DEBUG WindowsBackend: windows version=xp
11-02 13:50 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
11-02 13:50 DEBUG WindowsBackend: windows_sp=Service Pack 3
11-02 13:50 DEBUG WindowsBackend: windows_build=2600
11-02 13:50 DEBUG WindowsBackend: gmt=-5
11-02 13:50 DEBUG WindowsBackend: country=US
11-02 13:50 DEBUG WindowsBackend: timezone=America/New_York
11-02 13:50 DEBUG WindowsBackend: windows_username=Computer
11-02 13:50 DEBUG WindowsBackend: user_full_name=Computer
11-02 13:50 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Computer
11-02 13:50 DEBUG WindowsBackend: windows_language_code=1033
11-02 13:50 DEBUG WindowsBackend: windows_language=English
11-02 13:50 DEBUG WindowsBackend: processor_name=AMD Athlon(tm) XP 3000+
11-02 13:50 DEBUG WindowsBackend: bootloader=xp
11-02 13:50 DEBUG WindowsBackend: system_drive=Drive(C: hd 101558.894531 mb free ntfs)
11-02 13:50 DEBUG WindowsBackend: drive=Drive(C: hd 101558.894531 mb free ntfs)
11-02 13:50 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
11-02 13:50 DEBUG WindowsBackend: drive=Drive(F: removable 0.0 mb free )
11-02 13:50 DEBUG WindowsBackend: drive=Drive(G: removable 0.0 mb free )
11-02 13:50 DEBUG WindowsBackend: drive=Drive(H: removable 0.0 mb free )
11-02 13:50 DEBUG WindowsBackend: drive=Drive(I: removable 0.0 mb free )
11-02 13:50 DEBUG WindowsBackend: drive=Drive(J: cd 0.0 mb free )
11-02 13:50 DEBUG WindowsBackend: uninstaller_path=None
11-02 13:50 DEBUG WindowsBackend: previous_target_dir=None
11-02 13:50 DEBUG WindowsBackend: previous_distro_name=None
11-02 13:50 DEBUG WindowsBackend: keyboard_id=67699721
11-02 13:50 DEBUG WindowsBackend: keyboard_layout=us
11-02 13:50 DEBUG WindowsBackend: keyboard_variant=
11-02 13:50 DEBUG WindowsBackend: total_memory_mb=1471.484375
11-02 13:50 DEBUG CommonBackend: Searching ISOs on USB devices
11-02 13:50 DEBUG CommonBackend: Searching for local CDs
11-02 13:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu CD
11-02 13:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper \filesystem.squashfs
11-02 13:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu CD
11-02 13:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper \filesystem.squashfs
11-02 13:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu Netbook Remix CD
11-02 13:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper \filesystem.squashfs
11-02 13:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu CD
11-02 13:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper \filesystem.squashfs
11-02 13:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu CD
11-02 13:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper \filesystem.squashfs
11-02 13:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu Netbook CD
11-02 13:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper \filesystem.squashfs
11-02 13:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Xubuntu CD
11-02 13:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper \filesystem.squashfs
11-02 13:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Xubuntu CD
11-02 13:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper \filesystem.squashfs
11-02 13:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Mythbuntu CD
11-02 13:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper \filesystem.squashfs
11-02 13:50 DEBUG Distro: checking whether C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp is a valid Mythbuntu CD
11-02 13:50 DEBUG Distro: does not contain C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\casper \filesystem.squashfs
11-02 13:50 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
11-02 13:50 DEBUG Distro: wrong arch: i386 != amd64
11-02 13:50 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
11-02 13:50 INFO Distro: Found a valid CD for Ubuntu: D:\
11-02 13:50 INFO root: Running the installer...
11-02 13:50 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2. tmp\translations, languages=['en_US', 'en']
11-02 13:50 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2. tmp\translations, languages=['en_US', 'en']
11-02 13:50 DEBUG WinuiInstallationPage: target_drive=C:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=computer
11-02 13:50 INFO root: Received settings
11-02 13:50 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2. tmp\translations, languages=['en_US', 'en']
11-02 13:50 DEBUG TaskList: # Running tasklist...
11-02 13:50 DEBUG TaskList: ## Running select_target_dir...
11-02 13:50 INFO WindowsBackend: Installing into C:\ubuntu
11-02 13:50 DEBUG TaskList: ## Finished select_target_dir
11-02 13:50 DEBUG TaskList: ## Running create_dir_structure...
11-02 13:50 DEBUG CommonBackend: Creating dir C:\ubuntu
11-02 13:50 DEBUG CommonBackend: Creating dir C:\ubuntu\disks
11-02 13:50 DEBUG CommonBackend: Creating dir C:\ubuntu\install
11-02 13:50 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot
11-02 13:50 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot
11-02 13:50 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
11-02 13:50 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot\grub
11-02 13:50 DEBUG TaskList: ## Finished create_dir_structure
11-02 13:50 DEBUG TaskList: ## Running uncompress_target_dir...
11-02 13:50 DEBUG TaskList: ## Finished uncompress_target_dir
11-02 13:50 DEBUG TaskList: ## Running create_uninstaller...
11-02 13:50 DEBUG WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
11-02 13:50 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
11-02 13:50 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi InstallationDir C:\ubuntu
11-02 13:50 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi DisplayName Ubuntu
11-02 13:50 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
11-02 13:50 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi DisplayVersion 9.10ubuntu1-rev160
11-02 13:50 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi Publisher Ubuntu
11-02 13:50 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi URLInfoAbout http://www.ubuntu.com
11-02 13:50 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi HelpLink http://www.ubuntu.com/support
11-02 13:50 DEBUG TaskList: ## Finished create_uninstaller
11-02 13:50 DEBUG TaskList: ## Running copy_installation_files...
11-02 13:50 DEBUG WindowsBackend: Copying C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\data\c ustom-installation -> C:\ubuntu\install\custom-installation
11-02 13:50 DEBUG WindowsBackend: Copying C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\winboo t -> C:\ubuntu\winboot
11-02 13:50 DEBUG WindowsBackend: Copying C:\DOCUME~1\Computer\LOCALS~1\Temp\pyl2.tmp\data\i mages\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
11-02 13:50 DEBUG TaskList: ## Finished copy_installation_files
11-02 13:50 DEBUG TaskList: ## Running get_iso...
11-02 13:50 DEBUG TaskList: New task copy_file
11-02 13:50 DEBUG TaskList: ### Running copy_file...
11-02 13:52 ERROR TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 22] Invalid argument
11-02 13:52 DEBUG TaskList: # Cancelling tasklist
11-02 13:52 ERROR root: [Errno 22] Invalid argument
Traceback (most recent call last):
File "\lib\wubi\application.py", line 56, in run
File "\lib\wubi\application.py", line 126, in select_task
File "\lib\wubi\application.py", line 194, in run_cd_menu
File "\lib\wubi\application.py", line 118, in select_task
File "\lib\wubi\application.py", line 156, in run_installer
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 22] Invalid argument
11-02 13:52 DEBUG TaskList: New task check_iso
11-02 13:52 DEBUG CommonBackend: Searching for local ISO
11-02 13:52 DEBUG CommonBackend: Could not find any ISO or CD, downloading one now
11-02 13:52 DEBUG TaskList: New task get_metalink
11-02 13:52 ERROR TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
11-02 13:52 DEBUG TaskList: # Cancelling tasklist
11-02 13:52 DEBUG TaskList: # Finished tasklist
```

Next time you have a lot of text, highlight all the text after pasting it to the forum and click the # sign in the top toolbar which will put code tags around the text. it is really annoying to look at it the way you have it because it takes up the whole page.

---

### Post by millsware on 2009-11-03
Okay, I'll use that next time, but...
 
does anybody have any help for this problem.  I downloaded the 32-bit ubuntu iso, so that shouldn't be it.

---

### Post by wilee-nilee on 2009-11-03
You may have a corrupted burn or download. Make sure you burn it at the slowest speed. I am not familiar with raid but I see posts that have a adjustment I believe in bios, I don't know if this is your problem so get answers from the people who know. Also when you say install from the boot disc are you talking about from the desktop installer or installing straight from the boot gui try without installing or install.

---

### Post by millsware on 2009-11-06
Thanks for the help.  Burning at the slowest speed possible worked.  I've now seen this as advice in several places.  Ubuntu should put that in as part of the basic directions.

---

