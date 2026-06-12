---
title: "wubi installation problems"
date: 2009-07-31
forum: Installation &amp; Upgrades
---

### Post by RMD94 on 2009-07-31
everytime i try to install ubuntu inside windows (wubi) it always give's me an error during the installation "error: 4 more info wubi-9.04-rev128.log" and surprisingly a lot of people have the bery same problem but i didn't find a solution yet, and i have installed ubuntu 9.04 inside windows b4 but then i had to restore my xp to factory default and all my data was erased, and now when i try to insatlling it inside windows i get an error as i mentioned earlier. plz help me his is my last HOPE!!!

---

### Post by Danbo19 on 2009-07-31
I had a similar problem where wubi couldn't find the right Ubuntu .iso, I decided to dual boot, and that's been serving me fine ever since. I never did figure out my wubi problems, have you considered dual booting?

---

### Post by RMD94 on 2009-07-31
a year b4 i use to dual boot but after i figured out that i could install ubuntu in windows like an program i started doing it like that.

---

### Post by RMD94 on 2009-07-31
can some1 plz help me??? anyone???

---

### Post by lisati on 2009-07-31
The Wubi log is usually stored in the temp directory, which can be accessed within Windows by clicking Start->Run, typing in "%temp%" (without the quotes but with the %) and pressing Enter. If you are able to upload the log as an attachment, maybe someone will be able to help you interpret it.

---

### Post by RMD94 on 2009-07-31
this is my log. i'm not so great at this stuff, i cant understand anything in this log :(

> 07-31 01:41 INFO   root: === wubi 9.04 rev129 ===
07-31 01:41 DEBUG  root: Logfile is c:\docume~1\ram_boy\locals~1\temp\wubi-9.04-rev129.log
07-31 01:41 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\ram_boy\\My Documents\\Downloads\\wubi.exe"']
07-31 01:41 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl30.tmp\data
07-31 01:41 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl30.tmp\bin\7z.exe
07-31 01:41 DEBUG  CommonBackend: Fetching basic info...
07-31 01:41 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\ram_boy\My Documents\Downloads\wubi.exe
07-31 01:41 DEBUG  CommonBackend: platform=win32
07-31 01:41 DEBUG  CommonBackend: osname=nt
07-31 01:41 DEBUG  CommonBackend: language=en_US
07-31 01:41 DEBUG  CommonBackend: encoding=cp1252
07-31 01:41 DEBUG  WindowsBackend: arch=amd64
07-31 01:41 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl30.tmp\data\isolist.ini
07-31 01:41 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-31 01:41 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-31 01:41 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-31 01:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-31 01:41 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-31 01:41 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-31 01:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-31 01:41 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-31 01:41 DEBUG  WindowsBackend: Fetching host info...
07-31 01:41 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-31 01:41 DEBUG  WindowsBackend: windows version=xp
07-31 01:41 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
07-31 01:41 DEBUG  WindowsBackend: windows_sp=Service Pack 2
07-31 01:41 DEBUG  WindowsBackend: windows_build=2600
07-31 01:41 DEBUG  WindowsBackend: gmt=-5
07-31 01:41 DEBUG  WindowsBackend: country=US
07-31 01:41 DEBUG  WindowsBackend: timezone=America/New_York
07-31 01:41 DEBUG  WindowsBackend: windows_username=ram_boy
07-31 01:41 DEBUG  WindowsBackend: user_full_name=ram_boy
07-31 01:41 DEBUG  WindowsBackend: user_directory=ram_boy
07-31 01:41 DEBUG  WindowsBackend: windows_language_code=1033
07-31 01:41 DEBUG  WindowsBackend: windows_language=English
07-31 01:41 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
07-31 01:41 DEBUG  WindowsBackend: bootloader=xp
07-31 01:41 DEBUG  WindowsBackend: system_drive=Drive(C: hd 102162.945313 mb free )
07-31 01:41 DEBUG  WindowsBackend: drive=Drive(C: hd 102162.945313 mb free )
07-31 01:41 DEBUG  WindowsBackend: drive=Drive(D: hd 62172.4179688 mb free ntfs)
07-31 01:41 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
07-31 01:41 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
07-31 01:41 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
07-31 01:41 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
07-31 01:41 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
07-31 01:41 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
07-31 01:41 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
07-31 01:41 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
07-31 01:41 DEBUG  WindowsBackend: keyboard_id=67699721
07-31 01:41 DEBUG  WindowsBackend: keyboard_layout=us
07-31 01:41 DEBUG  WindowsBackend: keyboard_variant=
07-31 01:41 DEBUG  CommonBackend: locale=en_US.UTF-8
07-31 01:41 DEBUG  WindowsBackend: total_memory_mb=767.48046875
07-31 01:41 DEBUG  CommonBackend: Searching ISOs on USB devices
07-31 01:41 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu-8.10-desktop-i386.iso
07-31 01:41 DEBUG  WindowsBackend:   extracting .disk\info from D:\ubuntu-8.10-desktop-i386.iso
07-31 01:41 DEBUG  Distro:   info=Ubuntu 8.10 "Intrepid Ibex" - Release i386 (20081029.5)
07-31 01:41 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '8.10', 'build': '20081029.5', 'codename': 'Intrepid Ibex', 'arch': 'i386'}
07-31 01:41 DEBUG  Distro: wrong version: 8.10 != 9.04
07-31 01:41 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu-8.10-desktop-i386.iso
07-31 01:41 DEBUG  Distro: wrong version: 8.10 != 9.04
07-31 01:41 DEBUG  Distro:   checking Kubuntu ISO D:\ubuntu-8.10-desktop-i386.iso
07-31 01:41 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
07-31 01:41 DEBUG  Distro:   checking Kubuntu ISO D:\ubuntu-8.10-desktop-i386.iso
07-31 01:41 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
07-31 01:41 DEBUG  Distro:   checking Xubuntu ISO D:\ubuntu-8.10-desktop-i386.iso
07-31 01:41 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
07-31 01:41 DEBUG  Distro:   checking Xubuntu ISO D:\ubuntu-8.10-desktop-i386.iso
07-31 01:41 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
07-31 01:41 DEBUG  Distro:   checking Mythbuntu ISO D:\ubuntu-8.10-desktop-i386.iso
07-31 01:41 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
07-31 01:41 DEBUG  Distro:   checking Mythbuntu ISO D:\ubuntu-8.10-desktop-i386.iso
07-31 01:41 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
07-31 01:41 DEBUG  CommonBackend: Searching for local CDs
07-31 01:41 DEBUG  Distro:   checking whether C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl30.tmp is a valid Ubuntu CD
07-31 01:41 DEBUG  Distro:     does not contain C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl30.tmp\casper\filesystem.squashfs
07-31 01:41 DEBUG  Distro:   checking whether C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl30.tmp is a valid Ubuntu CD
07-31 01:41 DEBUG  Distro:     does not contain C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl30.tmp\casper\filesystem.squashfs
07-31 01:41 DEBUG  Distro:   checking whether C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl30.tmp is a valid Kubuntu CD
07-31 01:41 DEBUG  Distro:     does not contain C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl30.tmp\casper\filesystem.squashfs
07-31 01:41 DEBUG  Distro:   checking whether C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl30.tmp is a valid Kubuntu CD
07-31 01:41 DEBUG  Distro:     does not contain C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl30.tmp\casper\filesystem.squashfs
07-31 01:41 DEBUG  Distro:   checking whether C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl30.tmp is a valid Xubuntu CD
07-31 01:41 DEBUG  Distro:     does not contain C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl30.tmp\casper\filesystem.squashfs
07-31 01:41 DEBUG  Distro:   checking whether C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl30.tmp is a valid Xubuntu CD
07-31 01:41 DEBUG  Distro:     does not contain C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl30.tmp\casper\filesystem.squashfs
07-31 01:41 DEBUG  Distro:   checking whether C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl30.tmp is a valid Mythbuntu CD
07-31 01:41 DEBUG  Distro:     does not contain C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl30.tmp\casper\filesystem.squashfs
07-31 01:41 DEBUG  Distro:   checking whether C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl30.tmp is a valid Mythbuntu CD
07-31 01:41 DEBUG  Distro:     does not contain C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl30.tmp\casper\filesystem.squashfs
07-31 01:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 01:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 01:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 01:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 01:41 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 01:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 01:41 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 01:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 01:41 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 01:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 01:41 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 01:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 01:41 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 01:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 01:41 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 01:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 01:41 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 01:41 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release amd64 (20090420.1)
07-31 01:41 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'amd64'}
07-31 01:41 INFO   Distro: Found a valid CD for Ubuntu: E:\
07-31 01:41 INFO   root: Running the CD menu...
07-31 01:41 DEBUG  WindowsFrontend: __init__...
07-31 01:41 DEBUG  WindowsFrontend: on_init...
07-31 01:41 INFO   root: CD menu finished
07-31 01:41 INFO   root: Already installed, running the uninstaller...
07-31 01:41 INFO   root: Running the uninstaller...
07-31 01:41 INFO   CommonBackend: Launching previous uninestaller D:\ubuntu\uninstall-wubi.exe
07-31 01:41 DEBUG  root: application.quit
07-31 01:41 DEBUG  WindowsFrontend: frontend.quit
07-31 01:41 DEBUG  WindowsFrontend: frontend.on_quit
07-31 01:41 DEBUG  root: application.on_quit
07-31 01:41 INFO   root: sys.exit
07-31 01:41 INFO   root: === wubi 9.04 rev129 ===
07-31 01:41 DEBUG  root: Logfile is c:\docume~1\ram_boy\locals~1\temp\wubi-9.04-rev129.log
07-31 01:41 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\ram_boy\\My Documents\\Downloads\\wubi.exe"']
07-31 01:41 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl32.tmp\data
07-31 01:41 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl32.tmp\bin\7z.exe
07-31 01:41 DEBUG  CommonBackend: Fetching basic info...
07-31 01:41 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\ram_boy\My Documents\Downloads\wubi.exe
07-31 01:41 DEBUG  CommonBackend: platform=win32
07-31 01:41 DEBUG  CommonBackend: osname=nt
07-31 01:41 DEBUG  CommonBackend: language=en_US
07-31 01:41 DEBUG  CommonBackend: encoding=cp1252
07-31 01:41 DEBUG  WindowsBackend: arch=amd64
07-31 01:41 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl32.tmp\data\isolist.ini
07-31 01:41 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-31 01:41 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-31 01:41 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-31 01:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-31 01:41 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-31 01:41 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-31 01:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-31 01:41 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-31 01:41 DEBUG  WindowsBackend: Fetching host info...
07-31 01:41 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-31 01:41 DEBUG  WindowsBackend: windows version=xp
07-31 01:41 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
07-31 01:41 DEBUG  WindowsBackend: windows_sp=Service Pack 2
07-31 01:41 DEBUG  WindowsBackend: windows_build=2600
07-31 01:41 DEBUG  WindowsBackend: gmt=-5
07-31 01:41 DEBUG  WindowsBackend: country=US
07-31 01:41 DEBUG  WindowsBackend: timezone=America/New_York
07-31 01:41 DEBUG  WindowsBackend: windows_username=ram_boy
07-31 01:41 DEBUG  WindowsBackend: user_full_name=ram_boy
07-31 01:41 DEBUG  WindowsBackend: user_directory=ram_boy
07-31 01:41 DEBUG  WindowsBackend: windows_language_code=1033
07-31 01:41 DEBUG  WindowsBackend: windows_language=English
07-31 01:41 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
07-31 01:41 DEBUG  WindowsBackend: bootloader=xp
07-31 01:41 DEBUG  WindowsBackend: system_drive=Drive(C: hd 102168.660156 mb free )
07-31 01:41 DEBUG  WindowsBackend: drive=Drive(C: hd 102168.660156 mb free )
07-31 01:41 DEBUG  WindowsBackend: drive=Drive(D: hd 62870.3320313 mb free ntfs)
07-31 01:41 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
07-31 01:41 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
07-31 01:41 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
07-31 01:41 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
07-31 01:41 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
07-31 01:41 DEBUG  WindowsBackend: uninstaller_path=None
07-31 01:41 DEBUG  WindowsBackend: previous_target_dir=None
07-31 01:41 DEBUG  WindowsBackend: previous_distro_name=None
07-31 01:41 DEBUG  WindowsBackend: keyboard_id=67699721
07-31 01:41 DEBUG  WindowsBackend: keyboard_layout=us
07-31 01:41 DEBUG  WindowsBackend: keyboard_variant=
07-31 01:41 DEBUG  CommonBackend: locale=en_US.UTF-8
07-31 01:41 DEBUG  WindowsBackend: total_memory_mb=767.48046875
07-31 01:41 DEBUG  CommonBackend: Searching ISOs on USB devices
07-31 01:41 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu-8.10-desktop-i386.iso
07-31 01:41 DEBUG  WindowsBackend:   extracting .disk\info from D:\ubuntu-8.10-desktop-i386.iso
07-31 01:41 DEBUG  Distro:   info=Ubuntu 8.10 "Intrepid Ibex" - Release i386 (20081029.5)
07-31 01:41 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '8.10', 'build': '20081029.5', 'codename': 'Intrepid Ibex', 'arch': 'i386'}
07-31 01:41 DEBUG  Distro: wrong version: 8.10 != 9.04
07-31 01:41 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu-8.10-desktop-i386.iso
07-31 01:41 DEBUG  Distro: wrong version: 8.10 != 9.04
07-31 01:41 DEBUG  Distro:   checking Kubuntu ISO D:\ubuntu-8.10-desktop-i386.iso
07-31 01:41 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
07-31 01:41 DEBUG  Distro:   checking Kubuntu ISO D:\ubuntu-8.10-desktop-i386.iso
07-31 01:41 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
07-31 01:41 DEBUG  Distro:   checking Xubuntu ISO D:\ubuntu-8.10-desktop-i386.iso
07-31 01:41 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
07-31 01:41 DEBUG  Distro:   checking Xubuntu ISO D:\ubuntu-8.10-desktop-i386.iso
07-31 01:41 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
07-31 01:41 DEBUG  Distro:   checking Mythbuntu ISO D:\ubuntu-8.10-desktop-i386.iso
07-31 01:41 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
07-31 01:41 DEBUG  Distro:   checking Mythbuntu ISO D:\ubuntu-8.10-desktop-i386.iso
07-31 01:41 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
07-31 01:42 DEBUG  CommonBackend: Searching for local CDs
07-31 01:42 DEBUG  Distro:   checking whether C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl32.tmp is a valid Ubuntu CD
07-31 01:42 DEBUG  Distro:     does not contain C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl32.tmp\casper\filesystem.squashfs
07-31 01:42 DEBUG  Distro:   checking whether C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl32.tmp is a valid Ubuntu CD
07-31 01:42 DEBUG  Distro:     does not contain C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl32.tmp\casper\filesystem.squashfs
07-31 01:42 DEBUG  Distro:   checking whether C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl32.tmp is a valid Kubuntu CD
07-31 01:42 DEBUG  Distro:     does not contain C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl32.tmp\casper\filesystem.squashfs
07-31 01:42 DEBUG  Distro:   checking whether C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl32.tmp is a valid Kubuntu CD
07-31 01:42 DEBUG  Distro:     does not contain C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl32.tmp\casper\filesystem.squashfs
07-31 01:42 DEBUG  Distro:   checking whether C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl32.tmp is a valid Xubuntu CD
07-31 01:42 DEBUG  Distro:     does not contain C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl32.tmp\casper\filesystem.squashfs
07-31 01:42 DEBUG  Distro:   checking whether C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl32.tmp is a valid Xubuntu CD
07-31 01:42 DEBUG  Distro:     does not contain C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl32.tmp\casper\filesystem.squashfs
07-31 01:42 DEBUG  Distro:   checking whether C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl32.tmp is a valid Mythbuntu CD
07-31 01:42 DEBUG  Distro:     does not contain C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl32.tmp\casper\filesystem.squashfs
07-31 01:42 DEBUG  Distro:   checking whether C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl32.tmp is a valid Mythbuntu CD
07-31 01:42 DEBUG  Distro:     does not contain C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl32.tmp\casper\filesystem.squashfs
07-31 01:42 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 01:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 01:42 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 01:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 01:42 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 01:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 01:42 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 01:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 01:42 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 01:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 01:42 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 01:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 01:42 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 01:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 01:42 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 01:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 01:42 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 01:42 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release amd64 (20090420.1)
07-31 01:42 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'amd64'}
07-31 01:42 INFO   Distro: Found a valid CD for Ubuntu: E:\
07-31 01:42 INFO   root: Running the CD menu...
07-31 01:42 DEBUG  WindowsFrontend: __init__...
07-31 01:42 DEBUG  WindowsFrontend: on_init...
07-31 01:42 INFO   root: CD menu finished
07-31 01:42 INFO   root: Running the installer...
07-31 01:42 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=30000MB, distro_name=Ubuntu, language=English, username=ramboy
07-31 01:42 INFO   root: Received settings
07-31 01:42 DEBUG  TaskList: # Running tasklist...
07-31 01:42 DEBUG  TaskList: ## Running select_target_dir...
07-31 01:42 INFO   WindowsBackend: Installing into D:\ubuntu
07-31 01:42 DEBUG  TaskList: ## Finished select_target_dir
07-31 01:42 DEBUG  TaskList: ## Running create_dir_structure...
07-31 01:42 DEBUG  CommonBackend: Creating dir D:\ubuntu
07-31 01:42 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
07-31 01:42 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
07-31 01:42 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
07-31 01:42 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
07-31 01:42 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
07-31 01:42 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
07-31 01:42 DEBUG  TaskList: ## Finished create_dir_structure
07-31 01:42 DEBUG  TaskList: ## Running uncompress_target_dir...
07-31 01:42 DEBUG  TaskList: ## Finished uncompress_target_dir
07-31 01:42 DEBUG  TaskList: ## Running create_uninstaller...
07-31 01:42 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\ram_boy\My Documents\Downloads\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
07-31 01:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
07-31 01:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
07-31 01:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-31 01:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
07-31 01:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev129
07-31 01:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-31 01:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
07-31 01:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
07-31 01:42 DEBUG  TaskList: ## Finished create_uninstaller
07-31 01:42 DEBUG  TaskList: ## Running copy_installation_files...
07-31 01:42 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl32.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
07-31 01:42 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl32.tmp\winboot -> D:\ubuntu\winboot
07-31 01:42 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl32.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
07-31 01:42 DEBUG  TaskList: ## Finished copy_installation_files
07-31 01:42 DEBUG  TaskList: ## Running get_iso...
07-31 01:42 DEBUG  TaskList: New task copy_file
07-31 01:42 DEBUG  TaskList: ### Running copy_file...
07-31 01:49 DEBUG  TaskList: ### Finished copy_file
07-31 01:49 ERROR  TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 22] Invalid argument
07-31 01:49 DEBUG  TaskList: # Cancelling tasklist
07-31 01:49 ERROR  root: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 22] Invalid argument
07-31 01:49 DEBUG  TaskList: New task check_iso
07-31 01:49 DEBUG  CommonBackend: Searching for local ISO
07-31 01:49 DEBUG  Distro:   checking Ubuntu ISO C:\Documents and Settings\ram_boy\My Documents\Downloads\ubuntu-9.04-desktop-amd64.iso
07-31 01:49 DEBUG  WindowsBackend:   extracting .disk\info from C:\Documents and Settings\ram_boy\My Documents\Downloads\ubuntu-9.04-desktop-amd64.iso
07-31 01:49 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release amd64 (20090420.1)
07-31 01:49 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'amd64'}
07-31 01:49 INFO   Distro: Found a valid iso for Ubuntu: C:\Documents and Settings\ram_boy\My Documents\Downloads\ubuntu-9.04-desktop-amd64.iso
07-31 01:49 DEBUG  CommonBackend: Trying to use ISO C:\Documents and Settings\ram_boy\My Documents\Downloads\ubuntu-9.04-desktop-amd64.iso
07-31 01:49 DEBUG  TaskList: New task check_iso
07-31 01:49 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
07-31 01:49 DEBUG  TaskList: New task get_metalink
07-31 01:49 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
07-31 01:49 DEBUG  TaskList: # Cancelling tasklist
07-31 01:49 DEBUG  TaskList: # Finished tasklist
07-31 14:08 INFO   root: === wubi 9.04 rev129 ===
07-31 14:08 DEBUG  root: Logfile is c:\docume~1\ram_boy\locals~1\temp\wubi-9.04-rev129.log
07-31 14:08 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\ubuntu\\uninstall-wubi.exe"']
07-31 14:08 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl9.tmp\data
07-31 14:08 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl9.tmp\bin\7z.exe
07-31 14:08 DEBUG  CommonBackend: Fetching basic info...
07-31 14:08 DEBUG  CommonBackend: original_exe=D:\ubuntu\uninstall-wubi.exe
07-31 14:08 DEBUG  CommonBackend: platform=win32
07-31 14:08 DEBUG  CommonBackend: osname=nt
07-31 14:08 DEBUG  CommonBackend: language=en_US
07-31 14:08 DEBUG  CommonBackend: encoding=cp1252
07-31 14:08 DEBUG  WindowsBackend: arch=amd64
07-31 14:08 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl9.tmp\data\isolist.ini
07-31 14:08 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-31 14:08 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-31 14:08 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-31 14:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-31 14:08 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-31 14:08 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-31 14:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-31 14:08 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-31 14:08 DEBUG  WindowsBackend: Fetching host info...
07-31 14:08 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-31 14:08 DEBUG  WindowsBackend: windows version=xp
07-31 14:08 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
07-31 14:08 DEBUG  WindowsBackend: windows_sp=Service Pack 2
07-31 14:08 DEBUG  WindowsBackend: windows_build=2600
07-31 14:08 DEBUG  WindowsBackend: gmt=-5
07-31 14:08 DEBUG  WindowsBackend: country=US
07-31 14:08 DEBUG  WindowsBackend: timezone=America/New_York
07-31 14:08 DEBUG  WindowsBackend: windows_username=ram_boy
07-31 14:08 DEBUG  WindowsBackend: user_full_name=ram_boy
07-31 14:08 DEBUG  WindowsBackend: user_directory=ram_boy
07-31 14:08 DEBUG  WindowsBackend: windows_language_code=1033
07-31 14:08 DEBUG  WindowsBackend: windows_language=English
07-31 14:08 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
07-31 14:08 DEBUG  WindowsBackend: bootloader=xp
07-31 14:08 DEBUG  WindowsBackend: system_drive=Drive(C: hd 101880.628906 mb free )
07-31 14:08 DEBUG  WindowsBackend: drive=Drive(C: hd 101880.628906 mb free )
07-31 14:08 DEBUG  WindowsBackend: drive=Drive(D: hd 62371.1289063 mb free ntfs)
07-31 14:08 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free udf)
07-31 14:08 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
07-31 14:08 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
07-31 14:08 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
07-31 14:08 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
07-31 14:08 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
07-31 14:08 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
07-31 14:08 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
07-31 14:08 DEBUG  WindowsBackend: keyboard_id=67699721
07-31 14:08 DEBUG  WindowsBackend: keyboard_layout=us
07-31 14:08 DEBUG  WindowsBackend: keyboard_variant=
07-31 14:08 DEBUG  CommonBackend: locale=en_US.UTF-8
07-31 14:08 DEBUG  WindowsBackend: total_memory_mb=767.48046875
07-31 14:08 DEBUG  CommonBackend: Searching ISOs on USB devices
07-31 14:08 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu-8.10-desktop-i386.iso
07-31 14:08 DEBUG  WindowsBackend:   extracting .disk\info from D:\ubuntu-8.10-desktop-i386.iso
07-31 14:08 DEBUG  Distro:   info=Ubuntu 8.10 "Intrepid Ibex" - Release i386 (20081029.5)
07-31 14:08 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '8.10', 'build': '20081029.5', 'codename': 'Intrepid Ibex', 'arch': 'i386'}
07-31 14:08 DEBUG  Distro: wrong version: 8.10 != 9.04
07-31 14:08 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu-8.10-desktop-i386.iso
07-31 14:08 DEBUG  Distro: wrong version: 8.10 != 9.04
07-31 14:08 DEBUG  Distro:   checking Kubuntu ISO D:\ubuntu-8.10-desktop-i386.iso
07-31 14:08 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
07-31 14:08 DEBUG  Distro:   checking Kubuntu ISO D:\ubuntu-8.10-desktop-i386.iso
07-31 14:08 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
07-31 14:08 DEBUG  Distro:   checking Xubuntu ISO D:\ubuntu-8.10-desktop-i386.iso
07-31 14:08 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
07-31 14:08 DEBUG  Distro:   checking Xubuntu ISO D:\ubuntu-8.10-desktop-i386.iso
07-31 14:08 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
07-31 14:08 DEBUG  Distro:   checking Mythbuntu ISO D:\ubuntu-8.10-desktop-i386.iso
07-31 14:08 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
07-31 14:08 DEBUG  Distro:   checking Mythbuntu ISO D:\ubuntu-8.10-desktop-i386.iso
07-31 14:08 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
07-31 14:08 DEBUG  CommonBackend: Searching for local CDs
07-31 14:08 DEBUG  Distro:   checking whether C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl9.tmp is a valid Ubuntu CD
07-31 14:08 DEBUG  Distro:     does not contain C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl9.tmp is a valid Ubuntu CD
07-31 14:08 DEBUG  Distro:     does not contain C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl9.tmp is a valid Kubuntu CD
07-31 14:08 DEBUG  Distro:     does not contain C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl9.tmp is a valid Kubuntu CD
07-31 14:08 DEBUG  Distro:     does not contain C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl9.tmp is a valid Xubuntu CD
07-31 14:08 DEBUG  Distro:     does not contain C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl9.tmp is a valid Xubuntu CD
07-31 14:08 DEBUG  Distro:     does not contain C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl9.tmp is a valid Mythbuntu CD
07-31 14:08 DEBUG  Distro:     does not contain C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl9.tmp is a valid Mythbuntu CD
07-31 14:08 DEBUG  Distro:     does not contain C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 14:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 14:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 14:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 14:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 14:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 14:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 14:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 14:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 14:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 14:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-31 14:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-31 14:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-31 14:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-31 14:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-31 14:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-31 14:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-31 14:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-31 14:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-31 14:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-31 14:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-31 14:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-31 14:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-31 14:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-31 14:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-31 14:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-31 14:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-31 14:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-31 14:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-31 14:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-31 14:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-31 14:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-31 14:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-31 14:08 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-31 14:08 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-31 14:08 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-31 14:08 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-31 14:08 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-31 14:08 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-31 14:08 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-31 14:08 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
07-31 14:08 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
07-31 14:08 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
07-31 14:08 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
07-31 14:08 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
07-31 14:08 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
07-31 14:08 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
07-31 14:08 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-31 14:08 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
07-31 14:08 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-31 14:08 INFO   root: Running the uninstaller...
07-31 14:08 INFO   CommonBackend: This is the uninstaller running
07-31 14:08 DEBUG  WindowsFrontend: __init__...
07-31 14:08 DEBUG  WindowsFrontend: on_init...
07-31 14:08 INFO   root: Received settings
07-31 14:08 DEBUG  TaskList: # Running tasklist...
07-31 14:08 DEBUG  TaskList: ## Running Backup ISO...
07-31 14:08 DEBUG  TaskList: ## Finished Backup ISO
07-31 14:08 DEBUG  TaskList: ## Running Remove bootloader entry...
07-31 14:08 ERROR  WindowsBackend: Cannot find bcdedit
07-31 14:08 DEBUG  WindowsBackend: undo_bootini C:
07-31 14:08 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 101880.628906 mb free )
07-31 14:08 DEBUG  WindowsBackend: undo_bootini D:
07-31 14:08 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 62371.1289063 mb free ntfs)
07-31 14:08 DEBUG  WindowsBackend: undo_bootini F:
07-31 14:08 DEBUG  WindowsBackend: undo_configsys Drive(F: removable 0.0 mb free )
07-31 14:08 DEBUG  WindowsBackend: undo_bootini G:
07-31 14:08 DEBUG  WindowsBackend: undo_configsys Drive(G: removable 0.0 mb free )
07-31 14:08 DEBUG  WindowsBackend: undo_bootini H:
07-31 14:08 DEBUG  WindowsBackend: undo_configsys Drive(H: removable 0.0 mb free )
07-31 14:08 DEBUG  WindowsBackend: undo_bootini I:
07-31 14:08 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 0.0 mb free )
07-31 14:08 DEBUG  TaskList: ## Finished Remove bootloader entry
07-31 14:08 DEBUG  TaskList: ## Running Remove target dir...
07-31 14:08 DEBUG  CommonBackend: Deleting D:\ubuntu
07-31 14:08 DEBUG  TaskList: ## Finished Remove target dir
07-31 14:08 DEBUG  TaskList: ## Running Remove registry key...
07-31 14:08 DEBUG  TaskList: ## Finished Remove registry key
07-31 14:08 DEBUG  TaskList: # Finished tasklist
07-31 14:08 INFO   root: Almost finished uninstalling
07-31 14:08 INFO   root: Finished uninstallation
07-31 14:08 DEBUG  root: application.quit
07-31 14:08 DEBUG  WindowsFrontend: frontend.quit
07-31 14:08 DEBUG  WindowsFrontend: frontend.on_quit
07-31 14:08 DEBUG  root: application.on_quit
07-31 14:08 INFO   root: sys.exit


---

### Post by RJ12 on 2009-07-31
In the error log it says that you are using the wubi 9.04 with the 8.10 iso

---

### Post by RMD94 on 2009-08-01
how is that possible? i downloaded ubuntu 9.04 form ubuntu's official website and as i mentioned earlier it worked b4 i resotred my computer.

---

### Post by presence1960 on 2009-08-01
next time you paste a lot of text on here highlight all text after pasting then click the # sign on the toolbar to place code tags around the text...like this:
```
07-31 01:41 INFO root: === wubi 9.04 rev129 ===
07-31 01:41 DEBUG root: Logfile is c:\docume~1\ram_boy\locals~1\temp\wubi-9.04-rev129.log
07-31 01:41 DEBUG root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\ram_boy\\My Documents\\Downloads\\wubi.exe"']
07-31 01:41 DEBUG CommonBackend: data_dir=C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl30.t mp\data
07-31 01:41 DEBUG WindowsBackend: 7z=C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl30.tmp\bin \7z.exe
07-31 01:41 DEBUG CommonBackend: Fetching basic info...
07-31 01:41 DEBUG CommonBackend: original_exe=C:\Documents and Settings\ram_boy\My Documents\Downloads\wubi.exe
07-31 01:41 DEBUG CommonBackend: platform=win32
07-31 01:41 DEBUG CommonBackend: osname=nt
07-31 01:41 DEBUG CommonBackend: language=en_US
07-31 01:41 DEBUG CommonBackend: encoding=cp1252
07-31 01:41 DEBUG WindowsBackend: arch=amd64
07-31 01:41 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl30.tm p\data\isolist.ini
07-31 01:41 DEBUG CommonBackend: Adding distro Xubuntu-i386
07-31 01:41 DEBUG CommonBackend: Adding distro Xubuntu-amd64
07-31 01:41 DEBUG CommonBackend: Adding distro Kubuntu-amd64
07-31 01:41 DEBUG CommonBackend: Adding distro Mythbuntu-i386
07-31 01:41 DEBUG CommonBackend: Adding distro Ubuntu-amd64
07-31 01:41 DEBUG CommonBackend: Adding distro Ubuntu-i386
07-31 01:41 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
07-31 01:41 DEBUG CommonBackend: Adding distro Kubuntu-i386
07-31 01:41 DEBUG WindowsBackend: Fetching host info...
07-31 01:41 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVer sion\Uninstall\Wubi
07-31 01:41 DEBUG WindowsBackend: windows version=xp
07-31 01:41 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
07-31 01:41 DEBUG WindowsBackend: windows_sp=Service Pack 2
07-31 01:41 DEBUG WindowsBackend: windows_build=2600
07-31 01:41 DEBUG WindowsBackend: gmt=-5
07-31 01:41 DEBUG WindowsBackend: country=US
07-31 01:41 DEBUG WindowsBackend: timezone=America/New_York
07-31 01:41 DEBUG WindowsBackend: windows_username=ram_boy
07-31 01:41 DEBUG WindowsBackend: user_full_name=ram_boy
07-31 01:41 DEBUG WindowsBackend: user_directory=ram_boy
07-31 01:41 DEBUG WindowsBackend: windows_language_code=1033
07-31 01:41 DEBUG WindowsBackend: windows_language=English
07-31 01:41 DEBUG WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
07-31 01:41 DEBUG WindowsBackend: bootloader=xp
07-31 01:41 DEBUG WindowsBackend: system_drive=Drive(C: hd 102162.945313 mb free )
07-31 01:41 DEBUG WindowsBackend: drive=Drive(C: hd 102162.945313 mb free )
07-31 01:41 DEBUG WindowsBackend: drive=Drive(D: hd 62172.4179688 mb free ntfs)
07-31 01:41 DEBUG WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
07-31 01:41 DEBUG WindowsBackend: drive=Drive(F: removable 0.0 mb free )
07-31 01:41 DEBUG WindowsBackend: drive=Drive(G: removable 0.0 mb free )
07-31 01:41 DEBUG WindowsBackend: drive=Drive(H: removable 0.0 mb free )
07-31 01:41 DEBUG WindowsBackend: drive=Drive(I: removable 0.0 mb free )
07-31 01:41 DEBUG WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
07-31 01:41 DEBUG WindowsBackend: previous_target_dir=D:\ubuntu
07-31 01:41 DEBUG WindowsBackend: previous_distro_name=Ubuntu
07-31 01:41 DEBUG WindowsBackend: keyboard_id=67699721
07-31 01:41 DEBUG WindowsBackend: keyboard_layout=us
07-31 01:41 DEBUG WindowsBackend: keyboard_variant=
07-31 01:41 DEBUG CommonBackend: locale=en_US.UTF-8
07-31 01:41 DEBUG WindowsBackend: total_memory_mb=767.48046875
07-31 01:41 DEBUG CommonBackend: Searching ISOs on USB devices
07-31 01:41 DEBUG Distro: checking Ubuntu ISO D:\ubuntu-8.10-desktop-i386.iso
07-31 01:41 DEBUG WindowsBackend: extracting .disk\info from D:\ubuntu-8.10-desktop-i386.iso
07-31 01:41 DEBUG Distro: info=Ubuntu 8.10 "Intrepid Ibex" - Release i386 (20081029.5)
07-31 01:41 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '8.10', 'build': '20081029.5', 'codename': 'Intrepid Ibex', 'arch': 'i386'}
07-31 01:41 DEBUG Distro: wrong version: 8.10 != 9.04
07-31 01:41 DEBUG Distro: checking Ubuntu ISO D:\ubuntu-8.10-desktop-i386.iso
07-31 01:41 DEBUG Distro: wrong version: 8.10 != 9.04
07-31 01:41 DEBUG Distro: checking Kubuntu ISO D:\ubuntu-8.10-desktop-i386.iso
07-31 01:41 DEBUG Distro: wrong name: Ubuntu != Kubuntu
07-31 01:41 DEBUG Distro: checking Kubuntu ISO D:\ubuntu-8.10-desktop-i386.iso
07-31 01:41 DEBUG Distro: wrong name: Ubuntu != Kubuntu
07-31 01:41 DEBUG Distro: checking Xubuntu ISO D:\ubuntu-8.10-desktop-i386.iso
07-31 01:41 DEBUG Distro: wrong name: Ubuntu != Xubuntu
07-31 01:41 DEBUG Distro: checking Xubuntu ISO D:\ubuntu-8.10-desktop-i386.iso
07-31 01:41 DEBUG Distro: wrong name: Ubuntu != Xubuntu
07-31 01:41 DEBUG Distro: checking Mythbuntu ISO D:\ubuntu-8.10-desktop-i386.iso
07-31 01:41 DEBUG Distro: wrong name: Ubuntu != Mythbuntu
07-31 01:41 DEBUG Distro: checking Mythbuntu ISO D:\ubuntu-8.10-desktop-i386.iso
07-31 01:41 DEBUG Distro: wrong name: Ubuntu != Mythbuntu
07-31 01:41 DEBUG CommonBackend: Searching for local CDs
07-31 01:41 DEBUG Distro: checking whether C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl30.tmp is a valid Ubuntu CD
07-31 01:41 DEBUG Distro: does not contain C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl30.tmp\casper \filesystem.squashfs
07-31 01:41 DEBUG Distro: checking whether C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl30.tmp is a valid Ubuntu CD
07-31 01:41 DEBUG Distro: does not contain C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl30.tmp\casper \filesystem.squashfs
07-31 01:41 DEBUG Distro: checking whether C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl30.tmp is a valid Kubuntu CD
07-31 01:41 DEBUG Distro: does not contain C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl30.tmp\casper \filesystem.squashfs
07-31 01:41 DEBUG Distro: checking whether C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl30.tmp is a valid Kubuntu CD
07-31 01:41 DEBUG Distro: does not contain C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl30.tmp\casper \filesystem.squashfs
07-31 01:41 DEBUG Distro: checking whether C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl30.tmp is a valid Xubuntu CD
07-31 01:41 DEBUG Distro: does not contain C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl30.tmp\casper \filesystem.squashfs
07-31 01:41 DEBUG Distro: checking whether C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl30.tmp is a valid Xubuntu CD
07-31 01:41 DEBUG Distro: does not contain C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl30.tmp\casper \filesystem.squashfs
07-31 01:41 DEBUG Distro: checking whether C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl30.tmp is a valid Mythbuntu CD
07-31 01:41 DEBUG Distro: does not contain C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl30.tmp\casper \filesystem.squashfs
07-31 01:41 DEBUG Distro: checking whether C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl30.tmp is a valid Mythbuntu CD
07-31 01:41 DEBUG Distro: does not contain C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl30.tmp\casper \filesystem.squashfs
07-31 01:41 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-31 01:41 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-31 01:41 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-31 01:41 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-31 01:41 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
07-31 01:41 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-31 01:41 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
07-31 01:41 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-31 01:41 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
07-31 01:41 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-31 01:41 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
07-31 01:41 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-31 01:41 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
07-31 01:41 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-31 01:41 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
07-31 01:41 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-31 01:41 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
07-31 01:41 DEBUG Distro: info=Ubuntu 9.04 "Jaunty Jackalope" - Release amd64 (20090420.1)
07-31 01:41 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'amd64'}
07-31 01:41 INFO Distro: Found a valid CD for Ubuntu: E:\
07-31 01:41 INFO root: Running the CD menu...
07-31 01:41 DEBUG WindowsFrontend: __init__...
07-31 01:41 DEBUG WindowsFrontend: on_init...
07-31 01:41 INFO root: CD menu finished
07-31 01:41 INFO root: Already installed, running the uninstaller...
07-31 01:41 INFO root: Running the uninstaller...
07-31 01:41 INFO CommonBackend: Launching previous uninestaller D:\ubuntu\uninstall-wubi.exe
07-31 01:41 DEBUG root: application.quit
07-31 01:41 DEBUG WindowsFrontend: frontend.quit
07-31 01:41 DEBUG WindowsFrontend: frontend.on_quit
07-31 01:41 DEBUG root: application.on_quit
07-31 01:41 INFO root: sys.exit
07-31 01:41 INFO root: === wubi 9.04 rev129 ===
07-31 01:41 DEBUG root: Logfile is c:\docume~1\ram_boy\locals~1\temp\wubi-9.04-rev129.log
07-31 01:41 DEBUG root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\ram_boy\\My Documents\\Downloads\\wubi.exe"']
07-31 01:41 DEBUG CommonBackend: data_dir=C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl32.t mp\data
07-31 01:41 DEBUG WindowsBackend: 7z=C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl32.tmp\bin \7z.exe
07-31 01:41 DEBUG CommonBackend: Fetching basic info...
07-31 01:41 DEBUG CommonBackend: original_exe=C:\Documents and Settings\ram_boy\My Documents\Downloads\wubi.exe
07-31 01:41 DEBUG CommonBackend: platform=win32
07-31 01:41 DEBUG CommonBackend: osname=nt
07-31 01:41 DEBUG CommonBackend: language=en_US
07-31 01:41 DEBUG CommonBackend: encoding=cp1252
07-31 01:41 DEBUG WindowsBackend: arch=amd64
07-31 01:41 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl32.tm p\data\isolist.ini
07-31 01:41 DEBUG CommonBackend: Adding distro Xubuntu-i386
07-31 01:41 DEBUG CommonBackend: Adding distro Xubuntu-amd64
07-31 01:41 DEBUG CommonBackend: Adding distro Kubuntu-amd64
07-31 01:41 DEBUG CommonBackend: Adding distro Mythbuntu-i386
07-31 01:41 DEBUG CommonBackend: Adding distro Ubuntu-amd64
07-31 01:41 DEBUG CommonBackend: Adding distro Ubuntu-i386
07-31 01:41 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
07-31 01:41 DEBUG CommonBackend: Adding distro Kubuntu-i386
07-31 01:41 DEBUG WindowsBackend: Fetching host info...
07-31 01:41 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVer sion\Uninstall\Wubi
07-31 01:41 DEBUG WindowsBackend: windows version=xp
07-31 01:41 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
07-31 01:41 DEBUG WindowsBackend: windows_sp=Service Pack 2
07-31 01:41 DEBUG WindowsBackend: windows_build=2600
07-31 01:41 DEBUG WindowsBackend: gmt=-5
07-31 01:41 DEBUG WindowsBackend: country=US
07-31 01:41 DEBUG WindowsBackend: timezone=America/New_York
07-31 01:41 DEBUG WindowsBackend: windows_username=ram_boy
07-31 01:41 DEBUG WindowsBackend: user_full_name=ram_boy
07-31 01:41 DEBUG WindowsBackend: user_directory=ram_boy
07-31 01:41 DEBUG WindowsBackend: windows_language_code=1033
07-31 01:41 DEBUG WindowsBackend: windows_language=English
07-31 01:41 DEBUG WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
07-31 01:41 DEBUG WindowsBackend: bootloader=xp
07-31 01:41 DEBUG WindowsBackend: system_drive=Drive(C: hd 102168.660156 mb free )
07-31 01:41 DEBUG WindowsBackend: drive=Drive(C: hd 102168.660156 mb free )
07-31 01:41 DEBUG WindowsBackend: drive=Drive(D: hd 62870.3320313 mb free ntfs)
07-31 01:41 DEBUG WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
07-31 01:41 DEBUG WindowsBackend: drive=Drive(F: removable 0.0 mb free )
07-31 01:41 DEBUG WindowsBackend: drive=Drive(G: removable 0.0 mb free )
07-31 01:41 DEBUG WindowsBackend: drive=Drive(H: removable 0.0 mb free )
07-31 01:41 DEBUG WindowsBackend: drive=Drive(I: removable 0.0 mb free )
07-31 01:41 DEBUG WindowsBackend: uninstaller_path=None
07-31 01:41 DEBUG WindowsBackend: previous_target_dir=None
07-31 01:41 DEBUG WindowsBackend: previous_distro_name=None
07-31 01:41 DEBUG WindowsBackend: keyboard_id=67699721
07-31 01:41 DEBUG WindowsBackend: keyboard_layout=us
07-31 01:41 DEBUG WindowsBackend: keyboard_variant=
07-31 01:41 DEBUG CommonBackend: locale=en_US.UTF-8
07-31 01:41 DEBUG WindowsBackend: total_memory_mb=767.48046875
07-31 01:41 DEBUG CommonBackend: Searching ISOs on USB devices
07-31 01:41 DEBUG Distro: checking Ubuntu ISO D:\ubuntu-8.10-desktop-i386.iso
07-31 01:41 DEBUG WindowsBackend: extracting .disk\info from D:\ubuntu-8.10-desktop-i386.iso
07-31 01:41 DEBUG Distro: info=Ubuntu 8.10 "Intrepid Ibex" - Release i386 (20081029.5)
07-31 01:41 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '8.10', 'build': '20081029.5', 'codename': 'Intrepid Ibex', 'arch': 'i386'}
07-31 01:41 DEBUG Distro: wrong version: 8.10 != 9.04
07-31 01:41 DEBUG Distro: checking Ubuntu ISO D:\ubuntu-8.10-desktop-i386.iso
07-31 01:41 DEBUG Distro: wrong version: 8.10 != 9.04
07-31 01:41 DEBUG Distro: checking Kubuntu ISO D:\ubuntu-8.10-desktop-i386.iso
07-31 01:41 DEBUG Distro: wrong name: Ubuntu != Kubuntu
07-31 01:41 DEBUG Distro: checking Kubuntu ISO D:\ubuntu-8.10-desktop-i386.iso
07-31 01:41 DEBUG Distro: wrong name: Ubuntu != Kubuntu
07-31 01:41 DEBUG Distro: checking Xubuntu ISO D:\ubuntu-8.10-desktop-i386.iso
07-31 01:41 DEBUG Distro: wrong name: Ubuntu != Xubuntu
07-31 01:41 DEBUG Distro: checking Xubuntu ISO D:\ubuntu-8.10-desktop-i386.iso
07-31 01:41 DEBUG Distro: wrong name: Ubuntu != Xubuntu
07-31 01:41 DEBUG Distro: checking Mythbuntu ISO D:\ubuntu-8.10-desktop-i386.iso
07-31 01:41 DEBUG Distro: wrong name: Ubuntu != Mythbuntu
07-31 01:41 DEBUG Distro: checking Mythbuntu ISO D:\ubuntu-8.10-desktop-i386.iso
07-31 01:41 DEBUG Distro: wrong name: Ubuntu != Mythbuntu
07-31 01:42 DEBUG CommonBackend: Searching for local CDs
07-31 01:42 DEBUG Distro: checking whether C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl32.tmp is a valid Ubuntu CD
07-31 01:42 DEBUG Distro: does not contain C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl32.tmp\casper \filesystem.squashfs
07-31 01:42 DEBUG Distro: checking whether C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl32.tmp is a valid Ubuntu CD
07-31 01:42 DEBUG Distro: does not contain C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl32.tmp\casper \filesystem.squashfs
07-31 01:42 DEBUG Distro: checking whether C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl32.tmp is a valid Kubuntu CD
07-31 01:42 DEBUG Distro: does not contain C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl32.tmp\casper \filesystem.squashfs
07-31 01:42 DEBUG Distro: checking whether C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl32.tmp is a valid Kubuntu CD
07-31 01:42 DEBUG Distro: does not contain C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl32.tmp\casper \filesystem.squashfs
07-31 01:42 DEBUG Distro: checking whether C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl32.tmp is a valid Xubuntu CD
07-31 01:42 DEBUG Distro: does not contain C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl32.tmp\casper \filesystem.squashfs
07-31 01:42 DEBUG Distro: checking whether C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl32.tmp is a valid Xubuntu CD
07-31 01:42 DEBUG Distro: does not contain C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl32.tmp\casper \filesystem.squashfs
07-31 01:42 DEBUG Distro: checking whether C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl32.tmp is a valid Mythbuntu CD
07-31 01:42 DEBUG Distro: does not contain C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl32.tmp\casper \filesystem.squashfs
07-31 01:42 DEBUG Distro: checking whether C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl32.tmp is a valid Mythbuntu CD
07-31 01:42 DEBUG Distro: does not contain C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl32.tmp\casper \filesystem.squashfs
07-31 01:42 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-31 01:42 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-31 01:42 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-31 01:42 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-31 01:42 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
07-31 01:42 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-31 01:42 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
07-31 01:42 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-31 01:42 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
07-31 01:42 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-31 01:42 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
07-31 01:42 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-31 01:42 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
07-31 01:42 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-31 01:42 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
07-31 01:42 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-31 01:42 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
07-31 01:42 DEBUG Distro: info=Ubuntu 9.04 "Jaunty Jackalope" - Release amd64 (20090420.1)
07-31 01:42 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'amd64'}
07-31 01:42 INFO Distro: Found a valid CD for Ubuntu: E:\
07-31 01:42 INFO root: Running the CD menu...
07-31 01:42 DEBUG WindowsFrontend: __init__...
07-31 01:42 DEBUG WindowsFrontend: on_init...
07-31 01:42 INFO root: CD menu finished
07-31 01:42 INFO root: Running the installer...
07-31 01:42 DEBUG WinuiInstallationPage: target_drive=D:, installation_size=30000MB, distro_name=Ubuntu, language=English, username=ramboy
07-31 01:42 INFO root: Received settings
07-31 01:42 DEBUG TaskList: # Running tasklist...
07-31 01:42 DEBUG TaskList: ## Running select_target_dir...
07-31 01:42 INFO WindowsBackend: Installing into D:\ubuntu
07-31 01:42 DEBUG TaskList: ## Finished select_target_dir
07-31 01:42 DEBUG TaskList: ## Running create_dir_structure...
07-31 01:42 DEBUG CommonBackend: Creating dir D:\ubuntu
07-31 01:42 DEBUG CommonBackend: Creating dir D:\ubuntu\disks
07-31 01:42 DEBUG CommonBackend: Creating dir D:\ubuntu\install
07-31 01:42 DEBUG CommonBackend: Creating dir D:\ubuntu\install\boot
07-31 01:42 DEBUG CommonBackend: Creating dir D:\ubuntu\disks\boot
07-31 01:42 DEBUG CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
07-31 01:42 DEBUG CommonBackend: Creating dir D:\ubuntu\install\boot\grub
07-31 01:42 DEBUG TaskList: ## Finished create_dir_structure
07-31 01:42 DEBUG TaskList: ## Running uncompress_target_dir...
07-31 01:42 DEBUG TaskList: ## Finished uncompress_target_dir
07-31 01:42 DEBUG TaskList: ## Running create_uninstaller...
07-31 01:42 DEBUG WindowsBackend: Copying uninstaller C:\Documents and Settings\ram_boy\My Documents\Downloads\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
07-31 01:42 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
07-31 01:42 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi InstallationDir D:\ubuntu
07-31 01:42 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi DisplayName Ubuntu
07-31 01:42 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
07-31 01:42 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi DisplayVersion 9.04-rev129
07-31 01:42 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi Publisher Ubuntu
07-31 01:42 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi URLInfoAbout http://www.ubuntu.com
07-31 01:42 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi HelpLink http://www.ubuntu.com/support
07-31 01:42 DEBUG TaskList: ## Finished create_uninstaller
07-31 01:42 DEBUG TaskList: ## Running copy_installation_files...
07-31 01:42 DEBUG WindowsBackend: Copying C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl32.tmp\data\c ustom-installation -> D:\ubuntu\install\custom-installation
07-31 01:42 DEBUG WindowsBackend: Copying C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl32.tmp\winboo t -> D:\ubuntu\winboot
07-31 01:42 DEBUG WindowsBackend: Copying C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl32.tmp\data\i mages\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
07-31 01:42 DEBUG TaskList: ## Finished copy_installation_files
07-31 01:42 DEBUG TaskList: ## Running get_iso...
07-31 01:42 DEBUG TaskList: New task copy_file
07-31 01:42 DEBUG TaskList: ### Running copy_file...
07-31 01:49 DEBUG TaskList: ### Finished copy_file
07-31 01:49 ERROR TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\ wubi\backends\common\tasklist.py", line 196, in __call__
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\ wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 22] Invalid argument
07-31 01:49 DEBUG TaskList: # Cancelling tasklist
07-31 01:49 ERROR root: [Errno 22] Invalid argument
Traceback (most recent call last):
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\ wubi\application.py", line 55, in run
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\ wubi\application.py", line 125, in select_task
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\ wubi\application.py", line 193, in run_cd_menu
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\ wubi\application.py", line 117, in select_task
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\ wubi\application.py", line 155, in run_installer
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\ wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 22] Invalid argument
07-31 01:49 DEBUG TaskList: New task check_iso
07-31 01:49 DEBUG CommonBackend: Searching for local ISO
07-31 01:49 DEBUG Distro: checking Ubuntu ISO C:\Documents and Settings\ram_boy\My Documents\Downloads\ubuntu-9.04-desktop-amd64.iso
07-31 01:49 DEBUG WindowsBackend: extracting .disk\info from C:\Documents and Settings\ram_boy\My Documents\Downloads\ubuntu-9.04-desktop-amd64.iso
07-31 01:49 DEBUG Distro: info=Ubuntu 9.04 "Jaunty Jackalope" - Release amd64 (20090420.1)
07-31 01:49 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'amd64'}
07-31 01:49 INFO Distro: Found a valid iso for Ubuntu: C:\Documents and Settings\ram_boy\My Documents\Downloads\ubuntu-9.04-desktop-amd64.iso
07-31 01:49 DEBUG CommonBackend: Trying to use ISO C:\Documents and Settings\ram_boy\My Documents\Downloads\ubuntu-9.04-desktop-amd64.iso
07-31 01:49 DEBUG TaskList: New task check_iso
07-31 01:49 DEBUG CommonBackend: Could not find any ISO or CD, downloading one now
07-31 01:49 DEBUG TaskList: New task get_metalink
07-31 01:49 ERROR TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\ wubi\backends\common\tasklist.py", line 196, in __call__
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\ wubi\backends\common\backend.py", line 482, in get_iso
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\ wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
07-31 01:49 DEBUG TaskList: # Cancelling tasklist
07-31 01:49 DEBUG TaskList: # Finished tasklist
07-31 14:08 INFO root: === wubi 9.04 rev129 ===
07-31 14:08 DEBUG root: Logfile is c:\docume~1\ram_boy\locals~1\temp\wubi-9.04-rev129.log
07-31 14:08 DEBUG root: sys.argv = ['main.pyo', '--exefile="D:\\ubuntu\\uninstall-wubi.exe"']
07-31 14:08 DEBUG CommonBackend: data_dir=C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl9.tm p\data
07-31 14:08 DEBUG WindowsBackend: 7z=C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl9.tmp\bin\ 7z.exe
07-31 14:08 DEBUG CommonBackend: Fetching basic info...
07-31 14:08 DEBUG CommonBackend: original_exe=D:\ubuntu\uninstall-wubi.exe
07-31 14:08 DEBUG CommonBackend: platform=win32
07-31 14:08 DEBUG CommonBackend: osname=nt
07-31 14:08 DEBUG CommonBackend: language=en_US
07-31 14:08 DEBUG CommonBackend: encoding=cp1252
07-31 14:08 DEBUG WindowsBackend: arch=amd64
07-31 14:08 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl9.tmp \data\isolist.ini
07-31 14:08 DEBUG CommonBackend: Adding distro Xubuntu-i386
07-31 14:08 DEBUG CommonBackend: Adding distro Xubuntu-amd64
07-31 14:08 DEBUG CommonBackend: Adding distro Kubuntu-amd64
07-31 14:08 DEBUG CommonBackend: Adding distro Mythbuntu-i386
07-31 14:08 DEBUG CommonBackend: Adding distro Ubuntu-amd64
07-31 14:08 DEBUG CommonBackend: Adding distro Ubuntu-i386
07-31 14:08 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
07-31 14:08 DEBUG CommonBackend: Adding distro Kubuntu-i386
07-31 14:08 DEBUG WindowsBackend: Fetching host info...
07-31 14:08 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVer sion\Uninstall\Wubi
07-31 14:08 DEBUG WindowsBackend: windows version=xp
07-31 14:08 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
07-31 14:08 DEBUG WindowsBackend: windows_sp=Service Pack 2
07-31 14:08 DEBUG WindowsBackend: windows_build=2600
07-31 14:08 DEBUG WindowsBackend: gmt=-5
07-31 14:08 DEBUG WindowsBackend: country=US
07-31 14:08 DEBUG WindowsBackend: timezone=America/New_York
07-31 14:08 DEBUG WindowsBackend: windows_username=ram_boy
07-31 14:08 DEBUG WindowsBackend: user_full_name=ram_boy
07-31 14:08 DEBUG WindowsBackend: user_directory=ram_boy
07-31 14:08 DEBUG WindowsBackend: windows_language_code=1033
07-31 14:08 DEBUG WindowsBackend: windows_language=English
07-31 14:08 DEBUG WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
07-31 14:08 DEBUG WindowsBackend: bootloader=xp
07-31 14:08 DEBUG WindowsBackend: system_drive=Drive(C: hd 101880.628906 mb free )
07-31 14:08 DEBUG WindowsBackend: drive=Drive(C: hd 101880.628906 mb free )
07-31 14:08 DEBUG WindowsBackend: drive=Drive(D: hd 62371.1289063 mb free ntfs)
07-31 14:08 DEBUG WindowsBackend: drive=Drive(E: cd 0.0 mb free udf)
07-31 14:08 DEBUG WindowsBackend: drive=Drive(F: removable 0.0 mb free )
07-31 14:08 DEBUG WindowsBackend: drive=Drive(G: removable 0.0 mb free )
07-31 14:08 DEBUG WindowsBackend: drive=Drive(H: removable 0.0 mb free )
07-31 14:08 DEBUG WindowsBackend: drive=Drive(I: removable 0.0 mb free )
07-31 14:08 DEBUG WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
07-31 14:08 DEBUG WindowsBackend: previous_target_dir=D:\ubuntu
07-31 14:08 DEBUG WindowsBackend: previous_distro_name=Ubuntu
07-31 14:08 DEBUG WindowsBackend: keyboard_id=67699721
07-31 14:08 DEBUG WindowsBackend: keyboard_layout=us
07-31 14:08 DEBUG WindowsBackend: keyboard_variant=
07-31 14:08 DEBUG CommonBackend: locale=en_US.UTF-8
07-31 14:08 DEBUG WindowsBackend: total_memory_mb=767.48046875
07-31 14:08 DEBUG CommonBackend: Searching ISOs on USB devices
07-31 14:08 DEBUG Distro: checking Ubuntu ISO D:\ubuntu-8.10-desktop-i386.iso
07-31 14:08 DEBUG WindowsBackend: extracting .disk\info from D:\ubuntu-8.10-desktop-i386.iso
07-31 14:08 DEBUG Distro: info=Ubuntu 8.10 "Intrepid Ibex" - Release i386 (20081029.5)
07-31 14:08 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '8.10', 'build': '20081029.5', 'codename': 'Intrepid Ibex', 'arch': 'i386'}
07-31 14:08 DEBUG Distro: wrong version: 8.10 != 9.04
07-31 14:08 DEBUG Distro: checking Ubuntu ISO D:\ubuntu-8.10-desktop-i386.iso
07-31 14:08 DEBUG Distro: wrong version: 8.10 != 9.04
07-31 14:08 DEBUG Distro: checking Kubuntu ISO D:\ubuntu-8.10-desktop-i386.iso
07-31 14:08 DEBUG Distro: wrong name: Ubuntu != Kubuntu
07-31 14:08 DEBUG Distro: checking Kubuntu ISO D:\ubuntu-8.10-desktop-i386.iso
07-31 14:08 DEBUG Distro: wrong name: Ubuntu != Kubuntu
07-31 14:08 DEBUG Distro: checking Xubuntu ISO D:\ubuntu-8.10-desktop-i386.iso
07-31 14:08 DEBUG Distro: wrong name: Ubuntu != Xubuntu
07-31 14:08 DEBUG Distro: checking Xubuntu ISO D:\ubuntu-8.10-desktop-i386.iso
07-31 14:08 DEBUG Distro: wrong name: Ubuntu != Xubuntu
07-31 14:08 DEBUG Distro: checking Mythbuntu ISO D:\ubuntu-8.10-desktop-i386.iso
07-31 14:08 DEBUG Distro: wrong name: Ubuntu != Mythbuntu
07-31 14:08 DEBUG Distro: checking Mythbuntu ISO D:\ubuntu-8.10-desktop-i386.iso
07-31 14:08 DEBUG Distro: wrong name: Ubuntu != Mythbuntu
07-31 14:08 DEBUG CommonBackend: Searching for local CDs
07-31 14:08 DEBUG Distro: checking whether C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl9.tmp is a valid Ubuntu CD
07-31 14:08 DEBUG Distro: does not contain C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl9.tmp\casper\ filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl9.tmp is a valid Ubuntu CD
07-31 14:08 DEBUG Distro: does not contain C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl9.tmp\casper\ filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl9.tmp is a valid Kubuntu CD
07-31 14:08 DEBUG Distro: does not contain C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl9.tmp\casper\ filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl9.tmp is a valid Kubuntu CD
07-31 14:08 DEBUG Distro: does not contain C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl9.tmp\casper\ filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl9.tmp is a valid Xubuntu CD
07-31 14:08 DEBUG Distro: does not contain C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl9.tmp\casper\ filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl9.tmp is a valid Xubuntu CD
07-31 14:08 DEBUG Distro: does not contain C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl9.tmp\casper\ filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl9.tmp is a valid Mythbuntu CD
07-31 14:08 DEBUG Distro: does not contain C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl9.tmp\casper\ filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl9.tmp is a valid Mythbuntu CD
07-31 14:08 DEBUG Distro: does not contain C:\DOCUME~1\ram_boy\LOCALS~1\Temp\pyl9.tmp\casper\ filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-31 14:08 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-31 14:08 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
07-31 14:08 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
07-31 14:08 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
07-31 14:08 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
07-31 14:08 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
07-31 14:08 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
07-31 14:08 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
07-31 14:08 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
07-31 14:08 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
07-31 14:08 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
07-31 14:08 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
07-31 14:08 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
07-31 14:08 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
07-31 14:08 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
07-31 14:08 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
07-31 14:08 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
07-31 14:08 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether F:\ is a valid Kubuntu CD
07-31 14:08 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether F:\ is a valid Kubuntu CD
07-31 14:08 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether F:\ is a valid Xubuntu CD
07-31 14:08 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether F:\ is a valid Xubuntu CD
07-31 14:08 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether F:\ is a valid Mythbuntu CD
07-31 14:08 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether F:\ is a valid Mythbuntu CD
07-31 14:08 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether G:\ is a valid Ubuntu CD
07-31 14:08 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether G:\ is a valid Ubuntu CD
07-31 14:08 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether G:\ is a valid Kubuntu CD
07-31 14:08 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether G:\ is a valid Kubuntu CD
07-31 14:08 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether G:\ is a valid Xubuntu CD
07-31 14:08 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether G:\ is a valid Xubuntu CD
07-31 14:08 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether G:\ is a valid Mythbuntu CD
07-31 14:08 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether G:\ is a valid Mythbuntu CD
07-31 14:08 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether H:\ is a valid Ubuntu CD
07-31 14:08 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether H:\ is a valid Ubuntu CD
07-31 14:08 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether H:\ is a valid Kubuntu CD
07-31 14:08 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether H:\ is a valid Kubuntu CD
07-31 14:08 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether H:\ is a valid Xubuntu CD
07-31 14:08 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether H:\ is a valid Xubuntu CD
07-31 14:08 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether H:\ is a valid Mythbuntu CD
07-31 14:08 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether H:\ is a valid Mythbuntu CD
07-31 14:08 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether I:\ is a valid Ubuntu CD
07-31 14:08 DEBUG Distro: does not contain I:\casper\filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether I:\ is a valid Ubuntu CD
07-31 14:08 DEBUG Distro: does not contain I:\casper\filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether I:\ is a valid Kubuntu CD
07-31 14:08 DEBUG Distro: does not contain I:\casper\filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether I:\ is a valid Kubuntu CD
07-31 14:08 DEBUG Distro: does not contain I:\casper\filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether I:\ is a valid Xubuntu CD
07-31 14:08 DEBUG Distro: does not contain I:\casper\filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether I:\ is a valid Xubuntu CD
07-31 14:08 DEBUG Distro: does not contain I:\casper\filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether I:\ is a valid Mythbuntu CD
07-31 14:08 DEBUG Distro: does not contain I:\casper\filesystem.squashfs
07-31 14:08 DEBUG Distro: checking whether I:\ is a valid Mythbuntu CD
07-31 14:08 DEBUG Distro: does not contain I:\casper\filesystem.squashfs
07-31 14:08 INFO root: Running the uninstaller...
07-31 14:08 INFO CommonBackend: This is the uninstaller running
07-31 14:08 DEBUG WindowsFrontend: __init__...
07-31 14:08 DEBUG WindowsFrontend: on_init...
07-31 14:08 INFO root: Received settings
07-31 14:08 DEBUG TaskList: # Running tasklist...
07-31 14:08 DEBUG TaskList: ## Running Backup ISO...
07-31 14:08 DEBUG TaskList: ## Finished Backup ISO
07-31 14:08 DEBUG TaskList: ## Running Remove bootloader entry...
07-31 14:08 ERROR WindowsBackend: Cannot find bcdedit
07-31 14:08 DEBUG WindowsBackend: undo_bootini C:
07-31 14:08 DEBUG WindowsBackend: undo_configsys Drive(C: hd 101880.628906 mb free )
07-31 14:08 DEBUG WindowsBackend: undo_bootini D:
07-31 14:08 DEBUG WindowsBackend: undo_configsys Drive(D: hd 62371.1289063 mb free ntfs)
07-31 14:08 DEBUG WindowsBackend: undo_bootini F:
07-31 14:08 DEBUG WindowsBackend: undo_configsys Drive(F: removable 0.0 mb free )
07-31 14:08 DEBUG WindowsBackend: undo_bootini G:
07-31 14:08 DEBUG WindowsBackend: undo_configsys Drive(G: removable 0.0 mb free )
07-31 14:08 DEBUG WindowsBackend: undo_bootini H:
07-31 14:08 DEBUG WindowsBackend: undo_configsys Drive(H: removable 0.0 mb free )
07-31 14:08 DEBUG WindowsBackend: undo_bootini I:
07-31 14:08 DEBUG WindowsBackend: undo_configsys Drive(I: removable 0.0 mb free )
07-31 14:08 DEBUG TaskList: ## Finished Remove bootloader entry
07-31 14:08 DEBUG TaskList: ## Running Remove target dir...
07-31 14:08 DEBUG CommonBackend: Deleting D:\ubuntu
07-31 14:08 DEBUG TaskList: ## Finished Remove target dir
07-31 14:08 DEBUG TaskList: ## Running Remove registry key...
07-31 14:08 DEBUG TaskList: ## Finished Remove registry key
07-31 14:08 DEBUG TaskList: # Finished tasklist
07-31 14:08 INFO root: Almost finished uninstalling
07-31 14:08 INFO root: Finished uninstallation
07-31 14:08 DEBUG root: application.quit
07-31 14:08 DEBUG WindowsFrontend: frontend.quit
07-31 14:08 DEBUG WindowsFrontend: frontend.on_quit
07-31 14:08 DEBUG root: application.on_quit
07-31 14:08 INFO root: sys.exit 
```

Just a pointer for next time! That is a lot better isn't it?

---

### Post by RMD94 on 2009-08-03
yea it is, thx 4 the advise but u got any solution 4 my problem :) lol

---

### Post by IBamBam on 2009-08-19
I am having the exact same problem. Has anyone found a solution?
Sorry for the long post but the log text file was to large to attach
 
```
 
08-19 11:15 INFO   root: === wubi 9.04 rev128 ===
08-19 11:15 DEBUG  root: Logfile is c:\docume~1\jenny\locals~1\temp\wubi-9.04-rev128.log
08-19 11:15 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
08-19 11:15 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl7C.tmp\data
08-19 11:15 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl7C.tmp\bin\7z.exe
08-19 11:15 DEBUG  CommonBackend: Fetching basic info...
08-19 11:15 DEBUG  CommonBackend: original_exe=D:\wubi.exe
08-19 11:15 DEBUG  CommonBackend: platform=win32
08-19 11:15 DEBUG  CommonBackend: osname=nt
08-19 11:15 DEBUG  CommonBackend: language=en_US
08-19 11:15 DEBUG  CommonBackend: encoding=cp1252
08-19 11:15 DEBUG  WindowsBackend: arch=amd64
08-19 11:15 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl7C.tmp\data\isolist.ini
08-19 11:15 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-19 11:15 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-19 11:15 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-19 11:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-19 11:15 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-19 11:15 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-19 11:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-19 11:15 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-19 11:15 DEBUG  WindowsBackend: Fetching host info...
08-19 11:15 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-19 11:15 DEBUG  WindowsBackend: windows version=xp
08-19 11:15 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
08-19 11:15 DEBUG  WindowsBackend: windows_sp=Service Pack 2
08-19 11:15 DEBUG  WindowsBackend: windows_build=2600
08-19 11:15 DEBUG  WindowsBackend: gmt=-5
08-19 11:15 DEBUG  WindowsBackend: country=US
08-19 11:15 DEBUG  WindowsBackend: timezone=America/New_York
08-19 11:15 DEBUG  WindowsBackend: windows_username=Jenny
08-19 11:15 DEBUG  WindowsBackend: user_full_name=Jenny
08-19 11:15 DEBUG  WindowsBackend: user_directory=Jenny
08-19 11:15 DEBUG  WindowsBackend: windows_language_code=1033
08-19 11:15 DEBUG  WindowsBackend: windows_language=English
08-19 11:15 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
08-19 11:15 DEBUG  WindowsBackend: bootloader=xp
08-19 11:15 DEBUG  WindowsBackend: system_drive=Drive(C: hd 154024.289063 mb free )
08-19 11:15 DEBUG  WindowsBackend: drive=Drive(C: hd 154024.289063 mb free )
08-19 11:15 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
08-19 11:15 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
08-19 11:15 DEBUG  WindowsBackend: drive=Drive(F: hd 51882.171875 mb free ntfs)
08-19 11:15 DEBUG  WindowsBackend: drive=Drive(G: hd 9471.9453125 mb free ntfs)
08-19 11:15 DEBUG  WindowsBackend: drive=Drive(H: hd 96784.9648438 mb free ntfs)
08-19 11:15 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
08-19 11:15 DEBUG  WindowsBackend: drive=Drive(L: cd 0.0 mb free cdfs)
08-19 11:15 DEBUG  WindowsBackend: drive=Drive(M: removable 17.24609375 mb free fat)
08-19 11:15 DEBUG  WindowsBackend: uninstaller_path=None
08-19 11:15 DEBUG  WindowsBackend: previous_target_dir=None
08-19 11:15 DEBUG  WindowsBackend: previous_distro_name=None
08-19 11:15 DEBUG  WindowsBackend: keyboard_id=67699721
08-19 11:15 DEBUG  WindowsBackend: keyboard_layout=us
08-19 11:15 DEBUG  WindowsBackend: keyboard_variant=
08-19 11:15 DEBUG  CommonBackend: locale=en_US.UTF-8
08-19 11:15 DEBUG  WindowsBackend: total_memory_mb=2046.41796875
08-19 11:15 DEBUG  CommonBackend: Searching ISOs on USB devices
08-19 11:15 DEBUG  CommonBackend: Searching for local CDs
08-19 11:15 DEBUG  Distro:   checking whether C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl7C.tmp is a valid Ubuntu CD
08-19 11:15 DEBUG  Distro:     does not contain C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl7C.tmp\casper\filesystem.squashfs
08-19 11:15 DEBUG  Distro:   checking whether C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl7C.tmp is a valid Ubuntu CD
08-19 11:15 DEBUG  Distro:     does not contain C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl7C.tmp\casper\filesystem.squashfs
08-19 11:15 DEBUG  Distro:   checking whether C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl7C.tmp is a valid Kubuntu CD
08-19 11:15 DEBUG  Distro:     does not contain C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl7C.tmp\casper\filesystem.squashfs
08-19 11:15 DEBUG  Distro:   checking whether C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl7C.tmp is a valid Kubuntu CD
08-19 11:15 DEBUG  Distro:     does not contain C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl7C.tmp\casper\filesystem.squashfs
08-19 11:15 DEBUG  Distro:   checking whether C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl7C.tmp is a valid Xubuntu CD
08-19 11:15 DEBUG  Distro:     does not contain C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl7C.tmp\casper\filesystem.squashfs
08-19 11:15 DEBUG  Distro:   checking whether C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl7C.tmp is a valid Xubuntu CD
08-19 11:15 DEBUG  Distro:     does not contain C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl7C.tmp\casper\filesystem.squashfs
08-19 11:15 DEBUG  Distro:   checking whether C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl7C.tmp is a valid Mythbuntu CD
08-19 11:15 DEBUG  Distro:     does not contain C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl7C.tmp\casper\filesystem.squashfs
08-19 11:15 DEBUG  Distro:   checking whether C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl7C.tmp is a valid Mythbuntu CD
08-19 11:15 DEBUG  Distro:     does not contain C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl7C.tmp\casper\filesystem.squashfs
08-19 11:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-19 11:15 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
08-19 11:15 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
08-19 11:15 INFO   Distro: Found a valid CD for Ubuntu: D:\
08-19 11:15 INFO   root: Running the CD menu...
08-19 11:15 DEBUG  WindowsFrontend: __init__...
08-19 11:15 DEBUG  WindowsFrontend: on_init...
08-19 11:16 INFO   root: CD menu finished
08-19 11:16 INFO   root: Running the installer...
08-19 11:18 DEBUG  WinuiInstallationPage: target_drive=H:, installation_size=30000MB, distro_name=Ubuntu, language=English, username=james
08-19 11:18 INFO   root: Received settings
08-19 11:18 DEBUG  TaskList: # Running tasklist...
08-19 11:18 DEBUG  TaskList: ## Running select_target_dir...
08-19 11:18 INFO   WindowsBackend: Installing into H:\ubuntu
08-19 11:18 DEBUG  TaskList: ## Finished select_target_dir
08-19 11:18 DEBUG  TaskList: ## Running create_dir_structure...
08-19 11:18 DEBUG  CommonBackend: Creating dir H:\ubuntu
08-19 11:18 DEBUG  CommonBackend: Creating dir H:\ubuntu\disks
08-19 11:18 DEBUG  CommonBackend: Creating dir H:\ubuntu\install
08-19 11:18 DEBUG  CommonBackend: Creating dir H:\ubuntu\install\boot
08-19 11:18 DEBUG  CommonBackend: Creating dir H:\ubuntu\disks\boot
08-19 11:18 DEBUG  CommonBackend: Creating dir H:\ubuntu\disks\boot\grub
08-19 11:18 DEBUG  CommonBackend: Creating dir H:\ubuntu\install\boot\grub
08-19 11:18 DEBUG  TaskList: ## Finished create_dir_structure
08-19 11:18 DEBUG  TaskList: ## Running uncompress_target_dir...
08-19 11:18 DEBUG  TaskList: ## Finished uncompress_target_dir
08-19 11:18 DEBUG  TaskList: ## Running create_uninstaller...
08-19 11:18 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> H:\ubuntu\uninstall-wubi.exe
08-19 11:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString H:\ubuntu\uninstall-wubi.exe
08-19 11:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir H:\ubuntu
08-19 11:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
08-19 11:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon H:\ubuntu\Ubuntu.ico
08-19 11:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
08-19 11:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
08-19 11:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com]("http://www.ubuntu.com/")
08-19 11:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
08-19 11:18 DEBUG  TaskList: ## Finished create_uninstaller
08-19 11:18 DEBUG  TaskList: ## Running copy_installation_files...
08-19 11:18 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl7C.tmp\data\custom-installation -> H:\ubuntu\install\custom-installation
08-19 11:18 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl7C.tmp\winboot -> H:\ubuntu\winboot
08-19 11:18 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl7C.tmp\data\images\Ubuntu.ico -> H:\ubuntu\Ubuntu.ico
08-19 11:18 DEBUG  TaskList: ## Finished copy_installation_files
08-19 11:18 DEBUG  TaskList: ## Running get_iso...
08-19 11:18 DEBUG  TaskList: New task copy_file
08-19 11:18 DEBUG  TaskList: ### Running copy_file...
08-19 11:20 DEBUG  TaskList: ### Finished copy_file
08-19 11:20 ERROR  TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 22] Invalid argument
08-19 11:20 DEBUG  TaskList: # Cancelling tasklist
08-19 11:20 ERROR  root: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 22] Invalid argument
08-19 11:20 DEBUG  TaskList: New task check_iso
08-19 11:20 DEBUG  CommonBackend: Searching for local ISO
08-19 11:20 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
08-19 11:20 DEBUG  TaskList: New task get_metalink
08-19 11:20 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
08-19 11:20 DEBUG  TaskList: # Cancelling tasklist
08-19 11:20 DEBUG  TaskList: # Finished tasklist
08-19 11:28 INFO   root: === wubi 9.04 rev128 ===
08-19 11:28 DEBUG  root: Logfile is c:\docume~1\jenny\locals~1\temp\wubi-9.04-rev128.log
08-19 11:28 DEBUG  root: sys.argv = ['main.pyo', '--exefile="H:\\ubuntu\\uninstall-wubi.exe"']
08-19 11:28 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl26.tmp\data
08-19 11:28 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl26.tmp\bin\7z.exe
08-19 11:28 DEBUG  CommonBackend: Fetching basic info...
08-19 11:28 DEBUG  CommonBackend: original_exe=H:\ubuntu\uninstall-wubi.exe
08-19 11:28 DEBUG  CommonBackend: platform=win32
08-19 11:28 DEBUG  CommonBackend: osname=nt
08-19 11:28 DEBUG  CommonBackend: language=en_US
08-19 11:28 DEBUG  CommonBackend: encoding=cp1252
08-19 11:28 DEBUG  WindowsBackend: arch=amd64
08-19 11:28 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl26.tmp\data\isolist.ini
08-19 11:28 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-19 11:28 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-19 11:28 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-19 11:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-19 11:28 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-19 11:28 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-19 11:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-19 11:28 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-19 11:28 DEBUG  WindowsBackend: Fetching host info...
08-19 11:28 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-19 11:28 DEBUG  WindowsBackend: windows version=xp
08-19 11:28 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
08-19 11:28 DEBUG  WindowsBackend: windows_sp=Service Pack 2
08-19 11:28 DEBUG  WindowsBackend: windows_build=2600
08-19 11:28 DEBUG  WindowsBackend: gmt=-5
08-19 11:28 DEBUG  WindowsBackend: country=US
08-19 11:28 DEBUG  WindowsBackend: timezone=America/New_York
08-19 11:28 DEBUG  WindowsBackend: windows_username=Jenny
08-19 11:28 DEBUG  WindowsBackend: user_full_name=Jenny
08-19 11:28 DEBUG  WindowsBackend: user_directory=Jenny
08-19 11:28 DEBUG  WindowsBackend: windows_language_code=1033
08-19 11:28 DEBUG  WindowsBackend: windows_language=English
08-19 11:28 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
08-19 11:28 DEBUG  WindowsBackend: bootloader=xp
08-19 11:28 DEBUG  WindowsBackend: system_drive=Drive(C: hd 153922.675781 mb free )
08-19 11:28 DEBUG  WindowsBackend: drive=Drive(C: hd 153922.675781 mb free )
08-19 11:28 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
08-19 11:28 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
08-19 11:28 DEBUG  WindowsBackend: drive=Drive(F: hd 51882.171875 mb free ntfs)
08-19 11:28 DEBUG  WindowsBackend: drive=Drive(G: hd 9471.9453125 mb free ntfs)
08-19 11:28 DEBUG  WindowsBackend: drive=Drive(H: hd 96085.0039063 mb free ntfs)
08-19 11:28 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
08-19 11:28 DEBUG  WindowsBackend: drive=Drive(L: cd 0.0 mb free cdfs)
08-19 11:28 DEBUG  WindowsBackend: drive=Drive(M: removable 17.24609375 mb free fat)
08-19 11:28 DEBUG  WindowsBackend: uninstaller_path=H:\ubuntu\uninstall-wubi.exe
08-19 11:28 DEBUG  WindowsBackend: previous_target_dir=H:\ubuntu
08-19 11:28 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
08-19 11:28 DEBUG  WindowsBackend: keyboard_id=67699721
08-19 11:28 DEBUG  WindowsBackend: keyboard_layout=us
08-19 11:28 DEBUG  WindowsBackend: keyboard_variant=
08-19 11:28 DEBUG  CommonBackend: locale=en_US.UTF-8
08-19 11:28 DEBUG  WindowsBackend: total_memory_mb=2046.41796875
08-19 11:28 DEBUG  CommonBackend: Searching ISOs on USB devices
08-19 11:28 DEBUG  CommonBackend: Searching for local CDs
08-19 11:28 DEBUG  Distro:   checking whether C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl26.tmp is a valid Ubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl26.tmp\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl26.tmp is a valid Ubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl26.tmp\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl26.tmp is a valid Kubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl26.tmp\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl26.tmp is a valid Kubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl26.tmp\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl26.tmp is a valid Xubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl26.tmp\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl26.tmp is a valid Xubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl26.tmp\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl26.tmp is a valid Mythbuntu CD
08-19 11:28 DEBUG  Distro:     does not contain C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl26.tmp\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl26.tmp is a valid Mythbuntu CD
08-19 11:28 DEBUG  Distro:     does not contain C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl26.tmp\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-19 11:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-19 11:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-19 11:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-19 11:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-19 11:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-19 11:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-19 11:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-19 11:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-19 11:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-19 11:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-19 11:28 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-19 11:28 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
08-19 11:28 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
08-19 11:28 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether M:\ is a valid Xubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether M:\ is a valid Xubuntu CD
08-19 11:28 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
08-19 11:28 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
08-19 11:28 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
08-19 11:28 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
08-19 11:28 INFO   root: Running the uninstaller...
08-19 11:28 INFO   CommonBackend: This is the uninstaller running
08-19 11:28 DEBUG  WindowsFrontend: __init__...
08-19 11:28 DEBUG  WindowsFrontend: on_init...
08-19 11:28 INFO   root: Received settings
08-19 11:28 DEBUG  TaskList: # Running tasklist...
08-19 11:28 DEBUG  TaskList: ## Running Backup ISO...
08-19 11:28 DEBUG  TaskList: ## Finished Backup ISO
08-19 11:28 DEBUG  TaskList: ## Running Remove bootloader entry...
08-19 11:28 ERROR  WindowsBackend: Cannot find bcdedit
08-19 11:28 DEBUG  WindowsBackend: undo_bootini C:
08-19 11:28 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 153922.675781 mb free )
08-19 11:28 DEBUG  WindowsBackend: undo_bootini F:
08-19 11:28 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 51882.171875 mb free ntfs)
08-19 11:28 DEBUG  WindowsBackend: undo_bootini G:
08-19 11:28 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 9471.9453125 mb free ntfs)
08-19 11:28 DEBUG  WindowsBackend: undo_bootini H:
08-19 11:28 DEBUG  WindowsBackend: undo_configsys Drive(H: hd 96085.0039063 mb free ntfs)
08-19 11:28 DEBUG  WindowsBackend: undo_bootini M:
08-19 11:28 DEBUG  WindowsBackend: undo_configsys Drive(M: removable 17.24609375 mb free fat)
08-19 11:28 DEBUG  TaskList: ## Finished Remove bootloader entry
08-19 11:28 DEBUG  TaskList: ## Running Remove target dir...
08-19 11:28 DEBUG  CommonBackend: Deleting H:\ubuntu
08-19 11:28 DEBUG  TaskList: ## Finished Remove target dir
08-19 11:28 DEBUG  TaskList: ## Running Remove registry key...
08-19 11:28 DEBUG  TaskList: ## Finished Remove registry key
08-19 11:28 DEBUG  TaskList: # Finished tasklist
08-19 11:28 INFO   root: Almost finished uninstalling
08-19 11:28 INFO   root: Finished uninstallation
08-19 11:28 DEBUG  root: application.quit
08-19 11:28 DEBUG  WindowsFrontend: frontend.quit
08-19 11:28 DEBUG  WindowsFrontend: frontend.on_quit
08-19 11:28 DEBUG  root: application.on_quit
08-19 11:28 INFO   root: sys.exit
08-19 11:32 INFO   root: === wubi 9.04 rev128 ===
08-19 11:32 DEBUG  root: Logfile is c:\docume~1\jenny\locals~1\temp\wubi-9.04-rev128.log
08-19 11:32 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
08-19 11:32 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl27.tmp\data
08-19 11:32 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl27.tmp\bin\7z.exe
08-19 11:32 DEBUG  CommonBackend: Fetching basic info...
08-19 11:32 DEBUG  CommonBackend: original_exe=D:\wubi.exe
08-19 11:32 DEBUG  CommonBackend: platform=win32
08-19 11:32 DEBUG  CommonBackend: osname=nt
08-19 11:32 DEBUG  CommonBackend: language=en_US
08-19 11:32 DEBUG  CommonBackend: encoding=cp1252
08-19 11:32 DEBUG  WindowsBackend: arch=amd64
08-19 11:32 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl27.tmp\data\isolist.ini
08-19 11:32 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-19 11:32 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-19 11:32 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-19 11:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-19 11:32 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-19 11:32 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-19 11:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-19 11:32 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-19 11:32 DEBUG  WindowsBackend: Fetching host info...
08-19 11:32 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-19 11:32 DEBUG  WindowsBackend: windows version=xp
08-19 11:32 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
08-19 11:32 DEBUG  WindowsBackend: windows_sp=Service Pack 2
08-19 11:32 DEBUG  WindowsBackend: windows_build=2600
08-19 11:32 DEBUG  WindowsBackend: gmt=-5
08-19 11:32 DEBUG  WindowsBackend: country=US
08-19 11:32 DEBUG  WindowsBackend: timezone=America/New_York
08-19 11:32 DEBUG  WindowsBackend: windows_username=Jenny
08-19 11:32 DEBUG  WindowsBackend: user_full_name=Jenny
08-19 11:32 DEBUG  WindowsBackend: user_directory=Jenny
08-19 11:32 DEBUG  WindowsBackend: windows_language_code=1033
08-19 11:32 DEBUG  WindowsBackend: windows_language=English
08-19 11:32 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
08-19 11:32 DEBUG  WindowsBackend: bootloader=xp
08-19 11:32 DEBUG  WindowsBackend: system_drive=Drive(C: hd 153924.988281 mb free )
08-19 11:32 DEBUG  WindowsBackend: drive=Drive(C: hd 153924.988281 mb free )
08-19 11:32 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
08-19 11:32 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
08-19 11:32 DEBUG  WindowsBackend: drive=Drive(F: hd 51882.171875 mb free ntfs)
08-19 11:32 DEBUG  WindowsBackend: drive=Drive(G: hd 9471.9453125 mb free ntfs)
08-19 11:32 DEBUG  WindowsBackend: drive=Drive(H: hd 96783.2109375 mb free ntfs)
08-19 11:32 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
08-19 11:32 DEBUG  WindowsBackend: drive=Drive(L: cd 0.0 mb free cdfs)
08-19 11:32 DEBUG  WindowsBackend: drive=Drive(M: removable 17.24609375 mb free fat)
08-19 11:32 DEBUG  WindowsBackend: uninstaller_path=None
08-19 11:32 DEBUG  WindowsBackend: previous_target_dir=None
08-19 11:32 DEBUG  WindowsBackend: previous_distro_name=None
08-19 11:32 DEBUG  WindowsBackend: keyboard_id=67699721
08-19 11:32 DEBUG  WindowsBackend: keyboard_layout=us
08-19 11:32 DEBUG  WindowsBackend: keyboard_variant=
08-19 11:32 DEBUG  CommonBackend: locale=en_US.UTF-8
08-19 11:32 DEBUG  WindowsBackend: total_memory_mb=2046.41796875
08-19 11:32 DEBUG  CommonBackend: Searching ISOs on USB devices
08-19 11:32 DEBUG  CommonBackend: Searching for local CDs
08-19 11:32 DEBUG  Distro:   checking whether C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl27.tmp is a valid Ubuntu CD
08-19 11:32 DEBUG  Distro:     does not contain C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl27.tmp\casper\filesystem.squashfs
08-19 11:32 DEBUG  Distro:   checking whether C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl27.tmp is a valid Ubuntu CD
08-19 11:32 DEBUG  Distro:     does not contain C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl27.tmp\casper\filesystem.squashfs
08-19 11:32 DEBUG  Distro:   checking whether C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl27.tmp is a valid Kubuntu CD
08-19 11:32 DEBUG  Distro:     does not contain C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl27.tmp\casper\filesystem.squashfs
08-19 11:32 DEBUG  Distro:   checking whether C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl27.tmp is a valid Kubuntu CD
08-19 11:32 DEBUG  Distro:     does not contain C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl27.tmp\casper\filesystem.squashfs
08-19 11:32 DEBUG  Distro:   checking whether C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl27.tmp is a valid Xubuntu CD
08-19 11:32 DEBUG  Distro:     does not contain C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl27.tmp\casper\filesystem.squashfs
08-19 11:32 DEBUG  Distro:   checking whether C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl27.tmp is a valid Xubuntu CD
08-19 11:32 DEBUG  Distro:     does not contain C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl27.tmp\casper\filesystem.squashfs
08-19 11:32 DEBUG  Distro:   checking whether C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl27.tmp is a valid Mythbuntu CD
08-19 11:32 DEBUG  Distro:     does not contain C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl27.tmp\casper\filesystem.squashfs
08-19 11:32 DEBUG  Distro:   checking whether C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl27.tmp is a valid Mythbuntu CD
08-19 11:32 DEBUG  Distro:     does not contain C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl27.tmp\casper\filesystem.squashfs
08-19 11:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-19 11:32 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
08-19 11:32 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
08-19 11:32 INFO   Distro: Found a valid CD for Ubuntu: D:\
08-19 11:32 INFO   root: Running the CD menu...
08-19 11:32 DEBUG  WindowsFrontend: __init__...
08-19 11:32 DEBUG  WindowsFrontend: on_init...
08-19 11:32 INFO   root: CD menu finished
08-19 11:32 INFO   root: Running the installer...
08-19 11:33 DEBUG  WinuiInstallationPage: target_drive=H:, installation_size=30000MB, distro_name=Ubuntu, language=English, username=james
08-19 11:33 INFO   root: Received settings
08-19 11:33 DEBUG  TaskList: # Running tasklist...
08-19 11:33 DEBUG  TaskList: ## Running select_target_dir...
08-19 11:33 INFO   WindowsBackend: Installing into H:\ubuntu
08-19 11:33 DEBUG  TaskList: ## Finished select_target_dir
08-19 11:33 DEBUG  TaskList: ## Running create_dir_structure...
08-19 11:33 DEBUG  CommonBackend: Creating dir H:\ubuntu
08-19 11:33 DEBUG  CommonBackend: Creating dir H:\ubuntu\disks
08-19 11:33 DEBUG  CommonBackend: Creating dir H:\ubuntu\install
08-19 11:33 DEBUG  CommonBackend: Creating dir H:\ubuntu\install\boot
08-19 11:33 DEBUG  CommonBackend: Creating dir H:\ubuntu\disks\boot
08-19 11:33 DEBUG  CommonBackend: Creating dir H:\ubuntu\disks\boot\grub
08-19 11:33 DEBUG  CommonBackend: Creating dir H:\ubuntu\install\boot\grub
08-19 11:33 DEBUG  TaskList: ## Finished create_dir_structure
08-19 11:33 DEBUG  TaskList: ## Running uncompress_target_dir...
08-19 11:33 DEBUG  TaskList: ## Finished uncompress_target_dir
08-19 11:33 DEBUG  TaskList: ## Running create_uninstaller...
08-19 11:33 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> H:\ubuntu\uninstall-wubi.exe
08-19 11:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString H:\ubuntu\uninstall-wubi.exe
08-19 11:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir H:\ubuntu
08-19 11:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
08-19 11:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon H:\ubuntu\Ubuntu.ico
08-19 11:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
08-19 11:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
08-19 11:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com]("http://www.ubuntu.com/")
08-19 11:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
08-19 11:33 DEBUG  TaskList: ## Finished create_uninstaller
08-19 11:33 DEBUG  TaskList: ## Running copy_installation_files...
08-19 11:33 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl27.tmp\data\custom-installation -> H:\ubuntu\install\custom-installation
08-19 11:33 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl27.tmp\winboot -> H:\ubuntu\winboot
08-19 11:33 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Jenny\LOCALS~1\Temp\pyl27.tmp\data\images\Ubuntu.ico -> H:\ubuntu\Ubuntu.ico
08-19 11:33 DEBUG  TaskList: ## Finished copy_installation_files
08-19 11:33 DEBUG  TaskList: ## Running get_iso...
08-19 11:33 DEBUG  TaskList: New task copy_file
08-19 11:33 DEBUG  TaskList: ### Running copy_file...
08-19 11:35 DEBUG  TaskList: ### Finished copy_file
08-19 11:35 ERROR  TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 22] Invalid argument
08-19 11:35 DEBUG  TaskList: # Cancelling tasklist
08-19 11:35 ERROR  root: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 22] Invalid argument
08-19 11:35 DEBUG  TaskList: New task check_iso
08-19 11:35 DEBUG  CommonBackend: Searching for local ISO
08-19 11:35 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
08-19 11:35 DEBUG  TaskList: New task get_metalink
08-19 11:35 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
08-19 11:35 DEBUG  TaskList: # Cancelling tasklist
08-19 11:35 DEBUG  TaskList: # Finished tasklist
 
 

```

---

### Post by junji on 2009-08-29
I have a similar issue. I tried to do this on a fresh windows xp sp2 install and I got some similar logs. Actually what I want is only an ubuntu install but its not letting me do that.

with regards to the timezone I get 8 and the country is US but I am in the Philippines and I've already set up my system to my region and somehow the logs says otherwise.

do you guys need me to attach the log here?

---

