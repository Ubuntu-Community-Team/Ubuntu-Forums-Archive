---
title: "Wubi installation error access is denied"
date: 2009-08-12
forum: Installation &amp; Upgrades
---

### Post by wubi-lucy on 2009-08-12
Hi,
 
I am having trouble installing Wubi. After selecting Download - Run - Run, the following error comes up:
 
Access is denied
For more information, please see the log file : C:\docume~1\user\temp\wubi-9.04-rev129.log
 
Can anyone please advise me on how to stop this error?
 
Thanks
Lucy

---

### Post by wubi-lucy on 2009-08-12
08-12 14:56 INFO   root: === wubi 9.04 rev129 ===
08-12 14:56 DEBUG  root: Logfile is c:\docume~1\lcorco~1\locals~1\temp\wubi-9.04-rev129.log
08-12 14:56 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\lcorcoran\\Local Settings\\Temporary Internet Files\\Content.IE5\\ATUNA1IJ\\wubi[1].exe"']
08-12 14:56 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\LCORCO~1\LOCALS~1\Temp\pylC.tmp\data
08-12 14:56 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\LCORCO~1\LOCALS~1\Temp\pylC.tmp\bin\7z.exe
08-12 14:56 DEBUG  CommonBackend: Fetching basic info...
08-12 14:56 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\lcorcoran\Local Settings\Temporary Internet Files\Content.IE5\ATUNA1IJ\wubi[1].exe
08-12 14:56 DEBUG  CommonBackend: platform=win32
08-12 14:56 DEBUG  CommonBackend: osname=nt
08-12 14:56 DEBUG  CommonBackend: language=en_IE
08-12 14:56 DEBUG  CommonBackend: encoding=cp1252
08-12 14:56 DEBUG  WindowsBackend: arch=amd64
08-12 14:56 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\LCORCO~1\LOCALS~1\Temp\pylC.tmp\data\isolist.ini
08-12 14:56 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-12 14:56 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-12 14:56 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-12 14:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-12 14:56 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-12 14:56 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-12 14:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-12 14:56 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-12 14:56 DEBUG  WindowsBackend: Fetching host info...
08-12 14:56 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-12 14:56 DEBUG  WindowsBackend: windows version=xp
08-12 14:56 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
08-12 14:56 DEBUG  WindowsBackend: windows_sp=Service Pack 3
08-12 14:56 DEBUG  WindowsBackend: windows_build=2600
08-12 14:56 DEBUG  WindowsBackend: gmt=0
08-12 14:56 DEBUG  WindowsBackend: country=IE
08-12 14:56 DEBUG  WindowsBackend: timezone=Europe/Dublin
08-12 14:56 DEBUG  WindowsBackend: windows_username=lcorcoran
08-12 14:56 DEBUG  WindowsBackend: user_full_name=lcorcoran
08-12 14:56 DEBUG  WindowsBackend: user_directory=lcorcoran
08-12 14:56 DEBUG  WindowsBackend: windows_language_code=1033
08-12 14:56 DEBUG  WindowsBackend: windows_language=English
08-12 14:56 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz
08-12 14:56 DEBUG  WindowsBackend: bootloader=xp
08-12 14:56 DEBUG  WindowsBackend: system_drive=Drive(C: hd 92317.515625 mb free )
08-12 14:56 DEBUG  WindowsBackend: drive=Drive(C: hd 92317.515625 mb free )
08-12 14:56 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
08-12 14:56 DEBUG  WindowsBackend: drive=Drive(G: remote 152444.773438 mb free ntfs)
08-12 14:56 DEBUG  WindowsBackend: drive=Drive(H: remote 152444.773438 mb free ntfs)
08-12 14:56 DEBUG  WindowsBackend: drive=Drive(P: remote 108893.21875 mb free ntfs)
08-12 14:56 DEBUG  WindowsBackend: drive=Drive(Q: remote 108893.21875 mb free ntfs)
08-12 14:56 DEBUG  WindowsBackend: uninstaller_path=None
08-12 14:56 DEBUG  WindowsBackend: previous_target_dir=None
08-12 14:56 DEBUG  WindowsBackend: previous_distro_name=None
08-12 14:56 DEBUG  WindowsBackend: keyboard_id=403249161
08-12 14:56 DEBUG  WindowsBackend: keyboard_layout=ie
08-12 14:56 DEBUG  WindowsBackend: keyboard_variant=
08-12 14:56 DEBUG  CommonBackend: locale=en_IE.UTF-8
08-12 14:56 DEBUG  WindowsBackend: total_memory_mb=1021.8984375
08-12 14:56 DEBUG  CommonBackend: Searching ISOs on USB devices
08-12 14:56 DEBUG  CommonBackend: Searching for local CDs
08-12 14:56 DEBUG  Distro:   checking whether C:\DOCUME~1\LCORCO~1\LOCALS~1\Temp\pylC.tmp is a valid Ubuntu CD
08-12 14:56 DEBUG  Distro:     does not contain C:\DOCUME~1\LCORCO~1\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
08-12 14:56 DEBUG  Distro:   checking whether C:\DOCUME~1\LCORCO~1\LOCALS~1\Temp\pylC.tmp is a valid Ubuntu CD
08-12 14:56 DEBUG  Distro:     does not contain C:\DOCUME~1\LCORCO~1\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
08-12 14:56 DEBUG  Distro:   checking whether C:\DOCUME~1\LCORCO~1\LOCALS~1\Temp\pylC.tmp is a valid Kubuntu CD
08-12 14:56 DEBUG  Distro:     does not contain C:\DOCUME~1\LCORCO~1\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
08-12 14:56 DEBUG  Distro:   checking whether C:\DOCUME~1\LCORCO~1\LOCALS~1\Temp\pylC.tmp is a valid Kubuntu CD
08-12 14:56 DEBUG  Distro:     does not contain C:\DOCUME~1\LCORCO~1\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
08-12 14:56 DEBUG  Distro:   checking whether C:\DOCUME~1\LCORCO~1\LOCALS~1\Temp\pylC.tmp is a valid Xubuntu CD
08-12 14:56 DEBUG  Distro:     does not contain C:\DOCUME~1\LCORCO~1\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
08-12 14:56 DEBUG  Distro:   checking whether C:\DOCUME~1\LCORCO~1\LOCALS~1\Temp\pylC.tmp is a valid Xubuntu CD
08-12 14:56 DEBUG  Distro:     does not contain C:\DOCUME~1\LCORCO~1\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
08-12 14:56 DEBUG  Distro:   checking whether C:\DOCUME~1\LCORCO~1\LOCALS~1\Temp\pylC.tmp is a valid Mythbuntu CD
08-12 14:56 DEBUG  Distro:     does not contain C:\DOCUME~1\LCORCO~1\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
08-12 14:56 DEBUG  Distro:   checking whether C:\DOCUME~1\LCORCO~1\LOCALS~1\Temp\pylC.tmp is a valid Mythbuntu CD
08-12 14:56 DEBUG  Distro:     does not contain C:\DOCUME~1\LCORCO~1\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
08-12 14:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-12 14:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-12 14:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-12 14:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-12 14:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-12 14:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-12 14:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-12 14:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-12 14:56 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-12 14:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-12 14:56 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-12 14:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-12 14:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-12 14:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-12 14:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-12 14:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-12 14:56 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-12 14:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-12 14:56 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-12 14:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-12 14:56 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-12 14:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-12 14:56 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-12 14:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-12 14:56 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-12 14:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-12 14:56 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-12 14:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-12 14:56 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-12 14:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-12 14:56 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-12 14:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-12 14:56 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-12 14:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-12 14:56 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-12 14:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-12 14:56 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-12 14:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-12 14:56 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-12 14:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-12 14:56 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-12 14:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-12 14:56 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-12 14:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-12 14:56 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-12 14:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-12 14:56 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-12 14:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-12 14:56 DEBUG  Distro:   checking whether P:\ is a valid Ubuntu CD
08-12 14:56 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
08-12 14:56 DEBUG  Distro:   checking whether P:\ is a valid Ubuntu CD
08-12 14:56 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
08-12 14:56 DEBUG  Distro:   checking whether P:\ is a valid Kubuntu CD
08-12 14:56 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
08-12 14:56 DEBUG  Distro:   checking whether P:\ is a valid Kubuntu CD
08-12 14:56 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
08-12 14:56 DEBUG  Distro:   checking whether P:\ is a valid Xubuntu CD
08-12 14:56 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
08-12 14:56 DEBUG  Distro:   checking whether P:\ is a valid Xubuntu CD
08-12 14:56 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
08-12 14:56 DEBUG  Distro:   checking whether P:\ is a valid Mythbuntu CD
08-12 14:56 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
08-12 14:56 DEBUG  Distro:   checking whether P:\ is a valid Mythbuntu CD
08-12 14:56 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
08-12 14:56 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
08-12 14:56 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
08-12 14:56 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
08-12 14:56 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
08-12 14:56 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
08-12 14:56 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
08-12 14:56 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
08-12 14:56 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
08-12 14:56 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
08-12 14:56 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
08-12 14:56 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
08-12 14:56 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
08-12 14:56 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
08-12 14:56 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
08-12 14:56 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
08-12 14:56 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
08-12 14:56 INFO   root: Running the installer...
08-12 14:56 DEBUG  WindowsFrontend: __init__...
08-12 14:56 DEBUG  WindowsFrontend: on_init...
08-12 14:56 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Mythbuntu, language=English, username=lcorcoran
08-12 14:56 INFO   root: Received settings
08-12 14:56 DEBUG  TaskList: # Running tasklist...
08-12 14:56 DEBUG  TaskList: ## Running select_target_dir...
08-12 14:56 INFO   WindowsBackend: Installing into C:\ubuntu
08-12 14:56 DEBUG  TaskList: ## Finished select_target_dir
08-12 14:56 DEBUG  TaskList: ## Running create_dir_structure...
08-12 14:56 DEBUG  CommonBackend: Creating dir C:\ubuntu
08-12 14:56 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
08-12 14:56 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
08-12 14:56 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
08-12 14:56 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
08-12 14:56 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
08-12 14:56 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
08-12 14:56 DEBUG  TaskList: ## Finished create_dir_structure
08-12 14:56 DEBUG  TaskList: ## Running uncompress_target_dir...
08-12 14:56 DEBUG  TaskList: ## Finished uncompress_target_dir
08-12 14:56 DEBUG  TaskList: ## Running create_uninstaller...
08-12 14:56 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\lcorcoran\Local Settings\Temporary Internet Files\Content.IE5\ATUNA1IJ\wubi[1].exe -> C:\ubuntu\uninstall-wubi.exe
08-12 14:56 ERROR  TaskList: [Errno 5] Access is denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\win32\backend.py", line 115, in create_uninstaller
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\win32\registry.py", line 43, in set_value
WindowsError: [Errno 5] Access is denied
08-12 14:56 DEBUG  TaskList: # Cancelling tasklist
08-12 14:56 DEBUG  TaskList: # Finished tasklist
08-12 14:56 ERROR  root: [Errno 5] Access is denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 129, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
WindowsError: [Errno 5] Access is denied

---

### Post by wubi-lucy on 2009-08-12
Anyone any ideas? Would really appreciate any advice!!!!

---

### Post by Mark Phelps on 2009-08-13
The log references Mythbuntu.  Are you trying to install Mythbuntu in wubi?

---

