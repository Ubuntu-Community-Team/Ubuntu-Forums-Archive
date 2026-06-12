---
title: "Error installing Ubuntu using Wubi"
date: 2009-09-19
forum: Installation &amp; Upgrades
---

### Post by xov12 on 2009-09-19
Hello everyone,

When I try to install Ubuntu 9.04 inside Windows i get and error at the end of the installation.

An error ocurred:

Invalid argument

For more information, please see the log file: c:\docume~1\xov12\locals~1\temp\wubi-9.04-rev128.log

This is what the log file say:

09-19 20:51 INFO   root: === wubi 9.04 rev129 ===
09-19 20:51 DEBUG  root: Logfile is c:\docume~1\xov12\locals~1\temp\wubi-9.04-rev129.log
09-19 20:51 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\xov12\\My Documents\\Downloads\\wubi.exe"']
09-19 20:51 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\xov12\LOCALS~1\Temp\pyl137.tmp\data
09-19 20:51 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\xov12\LOCALS~1\Temp\pyl137.tmp\bin\7z.exe
09-19 20:51 DEBUG  CommonBackend: Fetching basic info...
09-19 20:51 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\xov12\My Documents\Downloads\wubi.exe
09-19 20:51 DEBUG  CommonBackend: platform=win32
09-19 20:51 DEBUG  CommonBackend: osname=nt
09-19 20:51 DEBUG  CommonBackend: language=en_US
09-19 20:51 DEBUG  CommonBackend: encoding=cp1252
09-19 20:51 DEBUG  WindowsBackend: arch=amd64
09-19 20:51 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\xov12\LOCALS~1\Temp\pyl137.tmp\data\isolist.ini
09-19 20:51 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-19 20:51 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-19 20:51 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-19 20:51 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-19 20:51 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-19 20:51 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-19 20:51 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-19 20:51 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-19 20:51 DEBUG  WindowsBackend: Fetching host info...
09-19 20:51 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-19 20:51 DEBUG  WindowsBackend: windows version=xp
09-19 20:51 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
09-19 20:51 DEBUG  WindowsBackend: windows_sp=Service Pack 3
09-19 20:51 DEBUG  WindowsBackend: windows_build=2600
09-19 20:51 DEBUG  WindowsBackend: gmt=-5
09-19 20:51 DEBUG  WindowsBackend: country=US
09-19 20:51 DEBUG  WindowsBackend: timezone=America/New_York
09-19 20:51 DEBUG  WindowsBackend: windows_username=xov12
09-19 20:51 DEBUG  WindowsBackend: user_full_name=xov12
09-19 20:51 DEBUG  WindowsBackend: user_directory=xov12
09-19 20:51 DEBUG  WindowsBackend: windows_language_code=1033
09-19 20:51 DEBUG  WindowsBackend: windows_language=English
09-19 20:51 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 Processor 3500+
09-19 20:51 DEBUG  WindowsBackend: bootloader=xp
09-19 20:51 DEBUG  WindowsBackend: system_drive=Drive(C: hd 90090.5703125 mb free )
09-19 20:51 DEBUG  WindowsBackend: drive=Drive(C: hd 90090.5703125 mb free )
09-19 20:51 DEBUG  WindowsBackend: drive=Drive(D: removable 0.0 mb free )
09-19 20:51 DEBUG  WindowsBackend: drive=Drive(E: removable 0.0 mb free )
09-19 20:51 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
09-19 20:51 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
09-19 20:51 DEBUG  WindowsBackend: drive=Drive(H: hd 1350.78125 mb free fat32)
09-19 20:51 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
09-19 20:51 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
09-19 20:51 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
09-19 20:51 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-19 20:51 DEBUG  WindowsBackend: keyboard_id=67699721
09-19 20:51 DEBUG  WindowsBackend: keyboard_layout=us
09-19 20:51 DEBUG  WindowsBackend: keyboard_variant=
09-19 20:51 DEBUG  CommonBackend: locale=en_US.UTF-8
09-19 20:51 DEBUG  WindowsBackend: total_memory_mb=2046.484375
09-19 20:51 DEBUG  CommonBackend: Searching ISOs on USB devices
09-19 20:51 DEBUG  CommonBackend: Searching for local CDs
09-19 20:51 DEBUG  Distro:   checking whether C:\DOCUME~1\xov12\LOCALS~1\Temp\pyl137.tmp is a valid Ubuntu CD
09-19 20:51 DEBUG  Distro:     does not contain C:\DOCUME~1\xov12\LOCALS~1\Temp\pyl137.tmp\casper\filesystem.squashfs
09-19 20:51 DEBUG  Distro:   checking whether C:\DOCUME~1\xov12\LOCALS~1\Temp\pyl137.tmp is a valid Ubuntu CD
09-19 20:51 DEBUG  Distro:     does not contain C:\DOCUME~1\xov12\LOCALS~1\Temp\pyl137.tmp\casper\filesystem.squashfs
09-19 20:51 DEBUG  Distro:   checking whether C:\DOCUME~1\xov12\LOCALS~1\Temp\pyl137.tmp is a valid Kubuntu CD
09-19 20:51 DEBUG  Distro:     does not contain C:\DOCUME~1\xov12\LOCALS~1\Temp\pyl137.tmp\casper\filesystem.squashfs
09-19 20:51 DEBUG  Distro:   checking whether C:\DOCUME~1\xov12\LOCALS~1\Temp\pyl137.tmp is a valid Kubuntu CD
09-19 20:51 DEBUG  Distro:     does not contain C:\DOCUME~1\xov12\LOCALS~1\Temp\pyl137.tmp\casper\filesystem.squashfs
09-19 20:51 DEBUG  Distro:   checking whether C:\DOCUME~1\xov12\LOCALS~1\Temp\pyl137.tmp is a valid Xubuntu CD
09-19 20:51 DEBUG  Distro:     does not contain C:\DOCUME~1\xov12\LOCALS~1\Temp\pyl137.tmp\casper\filesystem.squashfs
09-19 20:51 DEBUG  Distro:   checking whether C:\DOCUME~1\xov12\LOCALS~1\Temp\pyl137.tmp is a valid Xubuntu CD
09-19 20:51 DEBUG  Distro:     does not contain C:\DOCUME~1\xov12\LOCALS~1\Temp\pyl137.tmp\casper\filesystem.squashfs
09-19 20:51 DEBUG  Distro:   checking whether C:\DOCUME~1\xov12\LOCALS~1\Temp\pyl137.tmp is a valid Mythbuntu CD
09-19 20:51 DEBUG  Distro:     does not contain C:\DOCUME~1\xov12\LOCALS~1\Temp\pyl137.tmp\casper\filesystem.squashfs
09-19 20:51 DEBUG  Distro:   checking whether C:\DOCUME~1\xov12\LOCALS~1\Temp\pyl137.tmp is a valid Mythbuntu CD
09-19 20:51 DEBUG  Distro:     does not contain C:\DOCUME~1\xov12\LOCALS~1\Temp\pyl137.tmp\casper\filesystem.squashfs
09-19 20:51 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 20:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 20:51 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 20:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 20:51 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 20:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 20:51 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 20:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 20:51 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 20:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 20:51 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 20:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 20:51 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 20:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 20:51 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 20:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 20:51 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 20:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 20:52 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 20:52 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 20:52 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 20:52 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 20:52 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 20:52 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 20:52 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 20:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 20:52 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 20:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 20:52 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 20:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 20:52 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 20:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 20:52 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 20:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 20:52 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 20:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 20:52 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 20:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 20:52 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 20:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 20:52 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 20:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 20:52 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 20:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 20:52 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 20:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 20:52 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 20:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 20:52 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 20:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 20:52 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 20:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 20:52 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 20:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 20:52 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 20:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 20:52 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 20:52 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 20:52 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 20:52 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 20:52 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 20:52 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 20:52 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 20:52 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 20:52 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 20:52 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 20:52 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 20:52 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 20:52 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 20:52 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 20:52 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 20:52 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 20:52 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-19 20:52 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release amd64 (20090420.1)
09-19 20:52 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'amd64'}
09-19 20:52 INFO   Distro: Found a valid CD for Ubuntu: I:\
09-19 20:52 INFO   root: Running the CD menu...
09-19 20:52 DEBUG  WindowsFrontend: __init__...
09-19 20:52 DEBUG  WindowsFrontend: on_init...
09-19 20:52 INFO   WindowsFrontend: Operation cancelled
09-19 20:52 DEBUG  WindowsFrontend: frontend.quit
09-19 20:52 DEBUG  WindowsFrontend: frontend.on_quit
09-19 20:52 DEBUG  root: application.on_quit
09-19 20:52 INFO   root: sys.exit

Any help on how to fix this will be very appreciated.

PS: I tried installing Full Ubuntu but when the installation loads the screen goes all black.

---

### Post by stlsaint on 2009-09-20
few questions...what type of distro are you using for wubi...ie jaunty 9.04 etc etc
2) is it 64bit or 32bit you are trying to install?
3) what type of system you are trying to install on?

---

### Post by xov12 on 2009-09-20
1) I have no idea i just burned the ISO on a blank disc then runned wubi.
2) My procesor is AMD 64 but i tried both Ubuntu's(32 bit & 64 bit)
3) My OS is WindowsXP

---

### Post by CS_Tux on 2009-09-20
I have the same problem!When I am going to use Wubi the last version from the site i have the same error.
I am using Win Vista x32 with Intel Centrino 2(laptop)

---

