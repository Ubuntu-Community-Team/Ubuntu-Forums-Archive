---
title: "can't install wubi on windows 7 64bit"
date: 2009-09-14
forum: Installation &amp; Upgrades
---

### Post by steve51184 on 2009-09-14
hey all i can't install wubi on windows 7 64bit i'm using an official ubuntu 9.04 disk and get this error:

[IMG]http://i27.tinypic.com/9tn052.png[/IMG]

and the log files reads:

> 09-14 22:45 INFO   root: === wubi 9.04 rev128 ===
09-14 22:45 DEBUG  root: Logfile is c:\users\steve\appdata\local\temp\wubi-9.04-rev128.log
09-14 22:45 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
09-14 22:45 DEBUG  CommonBackend: data_dir=C:\Users\steve\AppData\Local\Temp\pylF5CD.tmp\data
09-14 22:45 DEBUG  WindowsBackend: 7z=C:\Users\steve\AppData\Local\Temp\pylF5CD.tmp\bin\7z.exe
09-14 22:45 DEBUG  CommonBackend: Fetching basic info...
09-14 22:45 DEBUG  CommonBackend: original_exe=D:\wubi.exe
09-14 22:45 DEBUG  CommonBackend: platform=win32
09-14 22:45 DEBUG  CommonBackend: osname=nt
09-14 22:45 DEBUG  CommonBackend: language=en_GB
09-14 22:45 DEBUG  CommonBackend: encoding=cp1252
09-14 22:45 DEBUG  WindowsBackend: arch=amd64
09-14 22:45 DEBUG  CommonBackend: Parsing isolist=C:\Users\steve\AppData\Local\Temp\pylF5CD.tmp\data\isolist.ini
09-14 22:45 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-14 22:45 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-14 22:45 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-14 22:45 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-14 22:45 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-14 22:45 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-14 22:45 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-14 22:45 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-14 22:45 DEBUG  WindowsBackend: Fetching host info...
09-14 22:45 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-14 22:45 DEBUG  WindowsBackend: windows version=vista
09-14 22:45 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
09-14 22:45 DEBUG  WindowsBackend: windows_sp=None
09-14 22:45 DEBUG  WindowsBackend: windows_build=7600
09-14 22:45 DEBUG  WindowsBackend: gmt=0
09-14 22:45 DEBUG  WindowsBackend: country=GB
09-14 22:45 DEBUG  WindowsBackend: timezone=Europe/London
09-14 22:45 DEBUG  WindowsBackend: windows_username=steve
09-14 22:45 DEBUG  WindowsBackend: user_full_name=steve
09-14 22:45 DEBUG  WindowsBackend: user_directory=steve
09-14 22:45 DEBUG  WindowsBackend: windows_language_code=1033
09-14 22:45 DEBUG  WindowsBackend: windows_language=English
09-14 22:45 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
09-14 22:45 DEBUG  WindowsBackend: bootloader=vista
09-14 22:45 DEBUG  WindowsBackend: system_drive=Drive(C: hd 60272.84375 mb free )
09-14 22:45 DEBUG  WindowsBackend: drive=Drive(C: hd 60272.84375 mb free )
09-14 22:45 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
09-14 22:45 DEBUG  WindowsBackend: drive=Drive(E: hd 138726.996094 mb free ntfs)
09-14 22:45 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
09-14 22:45 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
09-14 22:45 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
09-14 22:45 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-14 22:45 DEBUG  WindowsBackend: keyboard_id=134809609
09-14 22:45 DEBUG  WindowsBackend: keyboard_layout=gb
09-14 22:45 DEBUG  WindowsBackend: keyboard_variant=
09-14 22:45 DEBUG  CommonBackend: locale=en_GB.UTF-8
09-14 22:45 DEBUG  WindowsBackend: total_memory_mb=2047.3046875
09-14 22:45 DEBUG  CommonBackend: Searching ISOs on USB devices
09-14 22:45 DEBUG  CommonBackend: Searching for local CDs
09-14 22:45 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pylF5CD.tmp is a valid Ubuntu CD
09-14 22:45 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pylF5CD.tmp\casper\filesystem.squashfs
09-14 22:45 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pylF5CD.tmp is a valid Ubuntu CD
09-14 22:45 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pylF5CD.tmp\casper\filesystem.squashfs
09-14 22:45 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pylF5CD.tmp is a valid Kubuntu CD
09-14 22:45 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pylF5CD.tmp\casper\filesystem.squashfs
09-14 22:45 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pylF5CD.tmp is a valid Kubuntu CD
09-14 22:45 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pylF5CD.tmp\casper\filesystem.squashfs
09-14 22:45 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pylF5CD.tmp is a valid Xubuntu CD
09-14 22:45 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pylF5CD.tmp\casper\filesystem.squashfs
09-14 22:45 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pylF5CD.tmp is a valid Xubuntu CD
09-14 22:45 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pylF5CD.tmp\casper\filesystem.squashfs
09-14 22:45 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pylF5CD.tmp is a valid Mythbuntu CD
09-14 22:45 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pylF5CD.tmp\casper\filesystem.squashfs
09-14 22:45 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pylF5CD.tmp is a valid Mythbuntu CD
09-14 22:45 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pylF5CD.tmp\casper\filesystem.squashfs
09-14 22:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-14 22:45 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
09-14 22:45 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
09-14 22:45 INFO   Distro: Found a valid CD for Ubuntu: D:\
09-14 22:45 INFO   root: Running the CD menu...
09-14 22:45 DEBUG  WindowsFrontend: __init__...
09-14 22:45 DEBUG  WindowsFrontend: on_init...
09-14 22:45 INFO   root: CD menu finished
09-14 22:45 INFO   root: Already installed, running the uninstaller...
09-14 22:45 INFO   root: Running the uninstaller...
09-14 22:45 INFO   CommonBackend: This is the uninstaller running
09-14 22:45 INFO   root: Received settings
09-14 22:45 DEBUG  TaskList: # Running tasklist...
09-14 22:45 DEBUG  TaskList: ## Running Backup ISO...
09-14 22:45 DEBUG  TaskList: ## Finished Backup ISO
09-14 22:45 DEBUG  TaskList: ## Running Remove bootloader entry...
09-14 22:45 DEBUG  WindowsBackend: Could not find bcd id
09-14 22:45 DEBUG  WindowsBackend: undo_bootini C:
09-14 22:45 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 60272.84375 mb free )
09-14 22:45 DEBUG  WindowsBackend: undo_bootini E:
09-14 22:45 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 138726.996094 mb free ntfs)
09-14 22:45 DEBUG  WindowsBackend: undo_bootini F:
09-14 22:45 DEBUG  WindowsBackend: undo_configsys Drive(F: removable 0.0 mb free )
09-14 22:45 DEBUG  TaskList: ## Finished Remove bootloader entry
09-14 22:45 DEBUG  TaskList: ## Running Remove target dir...
09-14 22:45 DEBUG  CommonBackend: Deleting C:\ubuntu
09-14 22:45 DEBUG  TaskList: ## Finished Remove target dir
09-14 22:45 DEBUG  TaskList: ## Running Remove registry key...
09-14 22:45 DEBUG  TaskList: ## Finished Remove registry key
09-14 22:45 DEBUG  TaskList: # Finished tasklist
09-14 22:45 INFO   root: Almost finished uninstalling
09-14 22:45 INFO   root: Finished uninstallation
09-14 22:45 DEBUG  CommonBackend: Fetching basic info...
09-14 22:45 DEBUG  CommonBackend: original_exe=D:\wubi.exe
09-14 22:45 DEBUG  CommonBackend: platform=win32
09-14 22:45 DEBUG  CommonBackend: osname=nt
09-14 22:45 DEBUG  CommonBackend: language=en_GB
09-14 22:45 DEBUG  CommonBackend: encoding=cp1252
09-14 22:45 DEBUG  WindowsBackend: arch=amd64
09-14 22:45 DEBUG  CommonBackend: Parsing isolist=C:\Users\steve\AppData\Local\Temp\pylF5CD.tmp\data\isolist.ini
09-14 22:45 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-14 22:45 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-14 22:45 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-14 22:45 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-14 22:45 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-14 22:45 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-14 22:45 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-14 22:45 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-14 22:45 DEBUG  WindowsBackend: Fetching host info...
09-14 22:45 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-14 22:45 DEBUG  WindowsBackend: windows version=vista
09-14 22:45 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
09-14 22:45 DEBUG  WindowsBackend: windows_sp=None
09-14 22:45 DEBUG  WindowsBackend: windows_build=7600
09-14 22:45 DEBUG  WindowsBackend: gmt=0
09-14 22:45 DEBUG  WindowsBackend: country=GB
09-14 22:45 DEBUG  WindowsBackend: timezone=Europe/London
09-14 22:45 DEBUG  WindowsBackend: windows_username=steve
09-14 22:45 DEBUG  WindowsBackend: user_full_name=steve
09-14 22:45 DEBUG  WindowsBackend: user_directory=steve
09-14 22:45 DEBUG  WindowsBackend: windows_language_code=1033
09-14 22:45 DEBUG  WindowsBackend: windows_language=English
09-14 22:45 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
09-14 22:45 DEBUG  WindowsBackend: bootloader=vista
09-14 22:45 DEBUG  WindowsBackend: system_drive=Drive(C: hd 60348.7148438 mb free )
09-14 22:45 DEBUG  WindowsBackend: drive=Drive(C: hd 60348.7148438 mb free )
09-14 22:45 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
09-14 22:45 DEBUG  WindowsBackend: drive=Drive(E: hd 138726.996094 mb free ntfs)
09-14 22:45 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
09-14 22:45 DEBUG  WindowsBackend: uninstaller_path=None
09-14 22:45 DEBUG  WindowsBackend: previous_target_dir=None
09-14 22:45 DEBUG  WindowsBackend: previous_distro_name=None
09-14 22:45 DEBUG  WindowsBackend: keyboard_id=134809609
09-14 22:45 DEBUG  WindowsBackend: keyboard_layout=gb
09-14 22:45 DEBUG  WindowsBackend: keyboard_variant=
09-14 22:45 DEBUG  CommonBackend: locale=en_GB.UTF-8
09-14 22:45 DEBUG  WindowsBackend: total_memory_mb=2047.3046875
09-14 22:45 DEBUG  CommonBackend: Searching ISOs on USB devices
09-14 22:45 DEBUG  CommonBackend: Searching for local CDs
09-14 22:45 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pylF5CD.tmp is a valid Ubuntu CD
09-14 22:45 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pylF5CD.tmp\casper\filesystem.squashfs
09-14 22:45 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pylF5CD.tmp is a valid Ubuntu CD
09-14 22:45 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pylF5CD.tmp\casper\filesystem.squashfs
09-14 22:45 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pylF5CD.tmp is a valid Kubuntu CD
09-14 22:45 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pylF5CD.tmp\casper\filesystem.squashfs
09-14 22:45 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pylF5CD.tmp is a valid Kubuntu CD
09-14 22:45 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pylF5CD.tmp\casper\filesystem.squashfs
09-14 22:45 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pylF5CD.tmp is a valid Xubuntu CD
09-14 22:45 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pylF5CD.tmp\casper\filesystem.squashfs
09-14 22:45 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pylF5CD.tmp is a valid Xubuntu CD
09-14 22:45 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pylF5CD.tmp\casper\filesystem.squashfs
09-14 22:45 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pylF5CD.tmp is a valid Mythbuntu CD
09-14 22:45 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pylF5CD.tmp\casper\filesystem.squashfs
09-14 22:45 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pylF5CD.tmp is a valid Mythbuntu CD
09-14 22:45 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pylF5CD.tmp\casper\filesystem.squashfs
09-14 22:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-14 22:45 INFO   Distro: Found a valid CD for Ubuntu: D:\
09-14 22:45 INFO   root: Running the installer...
09-14 22:45 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=English, username=steve
09-14 22:45 INFO   root: Received settings
09-14 22:45 DEBUG  TaskList: # Running tasklist...
09-14 22:45 DEBUG  TaskList: ## Running select_target_dir...
09-14 22:45 INFO   WindowsBackend: Installing into C:\ubuntu
09-14 22:45 DEBUG  TaskList: ## Finished select_target_dir
09-14 22:45 DEBUG  TaskList: ## Running create_dir_structure...
09-14 22:45 DEBUG  CommonBackend: Creating dir C:\ubuntu
09-14 22:45 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
09-14 22:45 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
09-14 22:45 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
09-14 22:45 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
09-14 22:45 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
09-14 22:45 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
09-14 22:45 DEBUG  TaskList: ## Finished create_dir_structure
09-14 22:45 DEBUG  TaskList: ## Running uncompress_target_dir...
09-14 22:45 DEBUG  TaskList: ## Finished uncompress_target_dir
09-14 22:45 DEBUG  TaskList: ## Running create_uninstaller...
09-14 22:45 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
09-14 22:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
09-14 22:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
09-14 22:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
09-14 22:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
09-14 22:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
09-14 22:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
09-14 22:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
09-14 22:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
09-14 22:45 DEBUG  TaskList: ## Finished create_uninstaller
09-14 22:45 DEBUG  TaskList: ## Running copy_installation_files...
09-14 22:45 DEBUG  WindowsBackend: Copying C:\Users\steve\AppData\Local\Temp\pylF5CD.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
09-14 22:45 DEBUG  WindowsBackend: Copying C:\Users\steve\AppData\Local\Temp\pylF5CD.tmp\winboot -> C:\ubuntu\winboot
09-14 22:45 DEBUG  WindowsBackend: Copying C:\Users\steve\AppData\Local\Temp\pylF5CD.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
09-14 22:45 DEBUG  TaskList: ## Finished copy_installation_files
09-14 22:45 DEBUG  TaskList: ## Running get_iso...
09-14 22:45 DEBUG  TaskList: New task copy_file
09-14 22:45 DEBUG  TaskList: ### Running copy_file...
09-14 22:46 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 13] Permission denied
09-14 22:46 DEBUG  TaskList: # Cancelling tasklist
09-14 22:46 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 13] Permission denied
09-14 22:46 DEBUG  TaskList: New task check_iso
09-14 22:46 DEBUG  CommonBackend: Searching for local ISO
09-14 22:46 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
09-14 22:46 DEBUG  TaskList: New task get_metalink
09-14 22:46 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
09-14 22:46 DEBUG  TaskList: # Cancelling tasklist
09-14 22:46 DEBUG  TaskList: # Finished tasklist


any ideas what the problem is and how to fix it?

p.s. i have no idea what the "Z:\home\evan" stuff at the end is.. i don't even have a Z drive :\

---

### Post by Mark Phelps on 2009-09-15
According to the Wubi wiki, Windows 7 is not listed as being supported yet. There have been some threads about various hacks folks have done to get it by some of its problems.  Suggest you search for these to see if any of them help, but as to official support, it's not available yet.

---

### Post by steve51184 on 2009-09-15
can you point me to the topics as i can't find them.. all i need to do is add the line to my bootloader right?

---

### Post by steve51184 on 2009-09-17
any help people?

---

### Post by steve51184 on 2009-09-17
i've got it installed now by downloading the latest 9.04 iso and mounting it.. which is weird as i was using the official 9.04 cd before :\

---

