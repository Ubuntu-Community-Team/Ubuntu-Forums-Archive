---
title: "Installing 9.04 inside windows - Invalid argument error... needed help!"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by gozzilla on 2009-04-26
I am trying to install ubuntu 9.04 inside windows XP.

Steps followed: 
 - downloaded ISO file
 - burned CD
 - run wubi.exe
 - select inside windows
 - select d:\ with 10 GB

After finishing the extracting, I get the following error: Invalid Argument. 

Thanks in advance.

This is the log file:

[INDENT]04-26 09:17 DEBUG  TaskList: ### Finished copy_file
04-26 09:17 ERROR  TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 22] Invalid argument
04-26 09:17 DEBUG  TaskList: # Cancelling tasklist
04-26 09:17 ERROR  root: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 22] Invalid argument
04-26 09:17 DEBUG  TaskList: New task check_iso
04-26 09:17 DEBUG  CommonBackend: Searching for local ISO
04-26 09:17 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
04-26 09:17 DEBUG  TaskList: New task get_metalink
04-26 09:17 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
04-26 09:17 DEBUG  TaskList: # Cancelling tasklist
04-26 09:17 DEBUG  TaskList: # Finished tasklist
04-26 09:30 INFO   root: === wubi 9.04 rev128 ===
04-26 09:30 DEBUG  root: Logfile is d:\temp\wubi-9.04-rev128.log
04-26 09:30 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu']
04-26 09:30 DEBUG  CommonBackend: data_dir=D:\Temp\pyl55.tmp\data
04-26 09:30 DEBUG  WindowsBackend: 7z=D:\Temp\pyl55.tmp\bin\7z.exe
04-26 09:30 DEBUG  CommonBackend: Fetching basic info...
04-26 09:30 DEBUG  CommonBackend: original_exe=E:\wubi.exe
04-26 09:30 DEBUG  CommonBackend: platform=win32
04-26 09:30 DEBUG  CommonBackend: osname=nt
04-26 09:30 DEBUG  CommonBackend: language=es_ES
04-26 09:30 DEBUG  CommonBackend: encoding=cp1252
04-26 09:30 DEBUG  WindowsBackend: arch=i386
04-26 09:30 DEBUG  CommonBackend: Parsing isolist=D:\Temp\pyl55.tmp\data\isolist.ini
04-26 09:30 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-26 09:30 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-26 09:30 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-26 09:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-26 09:30 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-26 09:30 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-26 09:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-26 09:30 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-26 09:30 DEBUG  WindowsBackend: Fetching host info...
04-26 09:30 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-26 09:30 DEBUG  WindowsBackend: windows version=xp
04-26 09:30 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-26 09:30 DEBUG  WindowsBackend: windows_sp=Service Pack 3
04-26 09:30 DEBUG  WindowsBackend: windows_build=2600
04-26 09:30 DEBUG  WindowsBackend: gmt=-4
04-26 09:30 DEBUG  WindowsBackend: country=AR
04-26 09:30 DEBUG  WindowsBackend: timezone=America/Argentina/Buenos_Aires
04-26 09:30 DEBUG  WindowsBackend: windows_username=Administrador
04-26 09:30 DEBUG  WindowsBackend: user_full_name=Administrador
04-26 09:30 DEBUG  WindowsBackend: user_directory=Administrador
04-26 09:30 DEBUG  WindowsBackend: windows_language_code=1034
04-26 09:30 DEBUG  WindowsBackend: windows_language=Spanish
04-26 09:30 DEBUG  WindowsBackend: processor_name=Genuine Intel(R) CPU           T2500  @ 2.00GHz
04-26 09:30 DEBUG  WindowsBackend: bootloader=xp
04-26 09:30 DEBUG  WindowsBackend: system_drive=Drive(C: hd 2058.84765625 mb free ntfs)
04-26 09:30 DEBUG  WindowsBackend: drive=Drive(C: hd 2058.84765625 mb free ntfs)
04-26 09:30 DEBUG  WindowsBackend: drive=Drive(D: hd 22407.8671875 mb free )
04-26 09:30 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
04-26 09:30 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
04-26 09:30 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
04-26 09:30 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-26 09:30 DEBUG  WindowsBackend: keyboard_id=67767306
04-26 09:30 DEBUG  WindowsBackend: keyboard_layout=ar
04-26 09:30 DEBUG  WindowsBackend: keyboard_variant=
04-26 09:30 DEBUG  CommonBackend: locale=es_ES.UTF-8
04-26 09:30 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
04-26 09:30 DEBUG  CommonBackend: Searching ISOs on USB devices
04-26 09:30 DEBUG  CommonBackend: Searching for local CDs
04-26 09:30 DEBUG  Distro:   checking whether C:\ is a valid Ubuntu CD
04-26 09:30 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
04-26 09:30 DEBUG  Distro:   checking whether C:\ is a valid Ubuntu CD
04-26 09:30 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
04-26 09:30 DEBUG  Distro:   checking whether C:\ is a valid Kubuntu CD
04-26 09:30 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
04-26 09:30 DEBUG  Distro:   checking whether C:\ is a valid Kubuntu CD
04-26 09:30 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
04-26 09:30 DEBUG  Distro:   checking whether C:\ is a valid Xubuntu CD
04-26 09:30 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
04-26 09:30 DEBUG  Distro:   checking whether C:\ is a valid Xubuntu CD
04-26 09:30 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
04-26 09:30 DEBUG  Distro:   checking whether C:\ is a valid Mythbuntu CD
04-26 09:30 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
04-26 09:30 DEBUG  Distro:   checking whether C:\ is a valid Mythbuntu CD
04-26 09:30 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
04-26 09:30 DEBUG  Distro:   checking whether D:\Temp\pyl55.tmp is a valid Ubuntu CD
04-26 09:30 DEBUG  Distro:     does not contain D:\Temp\pyl55.tmp\casper\filesystem.squashfs
04-26 09:30 DEBUG  Distro:   checking whether D:\Temp\pyl55.tmp is a valid Ubuntu CD
04-26 09:30 DEBUG  Distro:     does not contain D:\Temp\pyl55.tmp\casper\filesystem.squashfs
04-26 09:30 DEBUG  Distro:   checking whether D:\Temp\pyl55.tmp is a valid Kubuntu CD
04-26 09:30 DEBUG  Distro:     does not contain D:\Temp\pyl55.tmp\casper\filesystem.squashfs
04-26 09:30 DEBUG  Distro:   checking whether D:\Temp\pyl55.tmp is a valid Kubuntu CD
04-26 09:30 DEBUG  Distro:     does not contain D:\Temp\pyl55.tmp\casper\filesystem.squashfs
04-26 09:30 DEBUG  Distro:   checking whether D:\Temp\pyl55.tmp is a valid Xubuntu CD
04-26 09:30 DEBUG  Distro:     does not contain D:\Temp\pyl55.tmp\casper\filesystem.squashfs
04-26 09:30 DEBUG  Distro:   checking whether D:\Temp\pyl55.tmp is a valid Xubuntu CD
04-26 09:30 DEBUG  Distro:     does not contain D:\Temp\pyl55.tmp\casper\filesystem.squashfs
04-26 09:30 DEBUG  Distro:   checking whether D:\Temp\pyl55.tmp is a valid Mythbuntu CD
04-26 09:30 DEBUG  Distro:     does not contain D:\Temp\pyl55.tmp\casper\filesystem.squashfs
04-26 09:30 DEBUG  Distro:   checking whether D:\Temp\pyl55.tmp is a valid Mythbuntu CD
04-26 09:30 DEBUG  Distro:     does not contain D:\Temp\pyl55.tmp\casper\filesystem.squashfs
04-26 09:30 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-26 09:30 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
04-26 09:30 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
04-26 09:30 DEBUG  Distro: wrong arch: i386 != amd64
04-26 09:30 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-26 09:30 INFO   Distro: Found a valid CD for Ubuntu: E:\
04-26 09:30 INFO   root: Running the CD menu...
04-26 09:30 DEBUG  WindowsFrontend: __init__...
04-26 09:30 DEBUG  WindowsFrontend: on_init...
04-26 09:31 DEBUG  WindowsFrontend: frontend.on_quit
04-26 09:31 DEBUG  root: application.on_quit
04-26 09:31 INFO   root: sys.exit
[/INDENT]

---

### Post by demon36 on 2009-06-20
um having the same problem .. I have no solution yet .

---

### Post by demon36 on 2009-06-20
Hey .. I had the same problem but I have found a solution .. jst download this wubi 

[http://releases.ubuntu.com/9.04/wubi.exe](http://releases.ubuntu.com/9.04/wubi.exe)

and install it from the iso file without the cd
it worked for me

---

