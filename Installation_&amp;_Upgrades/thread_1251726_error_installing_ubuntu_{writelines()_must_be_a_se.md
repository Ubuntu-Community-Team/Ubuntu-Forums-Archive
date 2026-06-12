---
title: "error installing ubuntu {writelines() must be a sequence of strings} installing on xp"
date: 2009-08-28
forum: Installation &amp; Upgrades
---

### Post by Muff on 2009-08-28
hello i was trying to install ubuntu from windows xp service pack 2 jsut after downloading it and making an cd image and i got that error writelines() must be a sequence of strings, then it tells me to check wubi-9.04-rev129.log and after that i dont know whats wrong im posting what is says on the doc

[COLOR=Red]
08-28 01:32 INFO   root: === wubi 9.04 rev129 ===
08-28 01:32 DEBUG  root: Logfile is c:\docume~1\administrador\datos de usuario\archivos transitorios\wubi-9.04-rev129.log
08-28 01:32 DEBUG  root: sys.argv = ['main.pyo', '--exefile="K:\\Downloads\\wubi.exe"']
08-28 01:32 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Administrador\Datos de Usuario\Archivos Transitorios\pyl26F9.tmp\data
08-28 01:32 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Administrador\Datos de Usuario\Archivos Transitorios\pyl26F9.tmp\bin\7z.exe
08-28 01:32 DEBUG  CommonBackend: Fetching basic info...
08-28 01:32 DEBUG  CommonBackend: original_exe=K:\Downloads\wubi.exe
08-28 01:32 DEBUG  CommonBackend: platform=win32
08-28 01:32 DEBUG  CommonBackend: osname=nt
08-28 01:32 DEBUG  CommonBackend: language=es_ES
08-28 01:32 DEBUG  CommonBackend: encoding=cp1252
08-28 01:32 DEBUG  WindowsBackend: arch=amd64
08-28 01:32 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Administrador\Datos de Usuario\Archivos Transitorios\pyl26F9.tmp\data\isolist.ini
08-28 01:32 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-28 01:32 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-28 01:32 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-28 01:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-28 01:32 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-28 01:32 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-28 01:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-28 01:32 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-28 01:32 DEBUG  WindowsBackend: Fetching host info...
08-28 01:32 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-28 01:32 DEBUG  WindowsBackend: windows version=xp
08-28 01:32 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
08-28 01:32 DEBUG  WindowsBackend: windows_sp=Service Pack 2
08-28 01:32 DEBUG  WindowsBackend: windows_build=2600
08-28 01:32 DEBUG  WindowsBackend: gmt=1
08-28 01:32 DEBUG  WindowsBackend: country=IT
08-28 01:32 DEBUG  WindowsBackend: timezone=Europe/Rome
08-28 01:32 DEBUG  WindowsBackend: windows_username=Administrador
08-28 01:32 DEBUG  WindowsBackend: user_full_name=Administrador
08-28 01:32 DEBUG  WindowsBackend: user_directory=Administrador
08-28 01:32 DEBUG  WindowsBackend: windows_language_code=1034
08-28 01:32 DEBUG  WindowsBackend: windows_language=Spanish
08-28 01:32 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
08-28 01:32 DEBUG  WindowsBackend: bootloader=xp
08-28 01:32 DEBUG  WindowsBackend: system_drive=Drive(C: hd 4062.8125 mb free )
08-28 01:32 DEBUG  WindowsBackend: drive=Drive(C: hd 4062.8125 mb free )
08-28 01:32 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
08-28 01:32 DEBUG  WindowsBackend: drive=Drive(E: removable 0.0 mb free )
08-28 01:32 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
08-28 01:32 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
08-28 01:32 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
08-28 01:32 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
08-28 01:32 DEBUG  WindowsBackend: drive=Drive(J: removable 0.0 mb free )
08-28 01:32 DEBUG  WindowsBackend: drive=Drive(K: hd 120564.105469 mb free ntfs)
08-28 01:32 DEBUG  WindowsBackend: drive=Drive(L: cd 0.0 mb free )
08-28 01:32 DEBUG  WindowsBackend: drive=Drive(M: cd 0.0 mb free )
08-28 01:32 DEBUG  WindowsBackend: uninstaller_path=None
08-28 01:32 DEBUG  WindowsBackend: previous_target_dir=None
08-28 01:32 DEBUG  WindowsBackend: previous_distro_name=None
08-28 01:32 DEBUG  WindowsBackend: keyboard_id=67707913
08-28 01:32 DEBUG  WindowsBackend: keyboard_layout=it
08-28 01:32 DEBUG  WindowsBackend: keyboard_variant=
08-28 01:32 DEBUG  CommonBackend: locale=es_ES.UTF-8
08-28 01:32 DEBUG  WindowsBackend: total_memory_mb=2046.48046875
08-28 01:32 DEBUG  CommonBackend: Searching ISOs on USB devices
08-28 01:32 DEBUG  CommonBackend: Searching for local CDs
08-28 01:32 DEBUG  Distro:   checking whether C:\DOCUME~1\Administrador\Datos de Usuario\Archivos Transitorios\pyl26F9.tmp is a valid Ubuntu CD
08-28 01:32 DEBUG  Distro:     does not contain C:\DOCUME~1\Administrador\Datos de Usuario\Archivos Transitorios\pyl26F9.tmp\casper\filesystem.squashfs
08-28 01:32 DEBUG  Distro:   checking whether C:\DOCUME~1\Administrador\Datos de Usuario\Archivos Transitorios\pyl26F9.tmp is a valid Ubuntu CD
08-28 01:32 DEBUG  Distro:     does not contain C:\DOCUME~1\Administrador\Datos de Usuario\Archivos Transitorios\pyl26F9.tmp\casper\filesystem.squashfs
08-28 01:32 DEBUG  Distro:   checking whether C:\DOCUME~1\Administrador\Datos de Usuario\Archivos Transitorios\pyl26F9.tmp is a valid Kubuntu CD
08-28 01:32 DEBUG  Distro:     does not contain C:\DOCUME~1\Administrador\Datos de Usuario\Archivos Transitorios\pyl26F9.tmp\casper\filesystem.squashfs
08-28 01:32 DEBUG  Distro:   checking whether C:\DOCUME~1\Administrador\Datos de Usuario\Archivos Transitorios\pyl26F9.tmp is a valid Kubuntu CD
08-28 01:32 DEBUG  Distro:     does not contain C:\DOCUME~1\Administrador\Datos de Usuario\Archivos Transitorios\pyl26F9.tmp\casper\filesystem.squashfs
08-28 01:32 DEBUG  Distro:   checking whether C:\DOCUME~1\Administrador\Datos de Usuario\Archivos Transitorios\pyl26F9.tmp is a valid Xubuntu CD
08-28 01:32 DEBUG  Distro:     does not contain C:\DOCUME~1\Administrador\Datos de Usuario\Archivos Transitorios\pyl26F9.tmp\casper\filesystem.squashfs
08-28 01:32 DEBUG  Distro:   checking whether C:\DOCUME~1\Administrador\Datos de Usuario\Archivos Transitorios\pyl26F9.tmp is a valid Xubuntu CD
08-28 01:32 DEBUG  Distro:     does not contain C:\DOCUME~1\Administrador\Datos de Usuario\Archivos Transitorios\pyl26F9.tmp\casper\filesystem.squashfs
08-28 01:32 DEBUG  Distro:   checking whether C:\DOCUME~1\Administrador\Datos de Usuario\Archivos Transitorios\pyl26F9.tmp is a valid Mythbuntu CD
08-28 01:32 DEBUG  Distro:     does not contain C:\DOCUME~1\Administrador\Datos de Usuario\Archivos Transitorios\pyl26F9.tmp\casper\filesystem.squashfs
08-28 01:32 DEBUG  Distro:   checking whether C:\DOCUME~1\Administrador\Datos de Usuario\Archivos Transitorios\pyl26F9.tmp is a valid Mythbuntu CD
08-28 01:32 DEBUG  Distro:     does not contain C:\DOCUME~1\Administrador\Datos de Usuario\Archivos Transitorios\pyl26F9.tmp\casper\filesystem.squashfs
08-28 01:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-28 01:32 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
08-28 01:32 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
08-28 01:32 INFO   Distro: Found a valid CD for Ubuntu: D:\
08-28 01:32 INFO   root: Running the CD menu...
08-28 01:32 DEBUG  WindowsFrontend: __init__...
08-28 01:32 DEBUG  WindowsFrontend: on_init...
08-28 01:32 INFO   root: CD menu finished
08-28 01:32 INFO   root: Running the installer...
08-28 01:32 DEBUG  WinuiInstallationPage: target_drive=K:, installation_size=20000MB, distro_name=Ubuntu, language=English, username=ivan
08-28 01:32 INFO   root: Received settings
08-28 01:32 DEBUG  TaskList: # Running tasklist...
08-28 01:32 DEBUG  TaskList: ## Running select_target_dir...
08-28 01:32 INFO   WindowsBackend: Installing into K:\ubuntu
08-28 01:32 DEBUG  TaskList: ## Finished select_target_dir
08-28 01:32 DEBUG  TaskList: ## Running create_dir_structure...
08-28 01:32 DEBUG  CommonBackend: Creating dir K:\ubuntu
08-28 01:32 DEBUG  CommonBackend: Creating dir K:\ubuntu\disks
08-28 01:32 DEBUG  CommonBackend: Creating dir K:\ubuntu\install
08-28 01:32 DEBUG  CommonBackend: Creating dir K:\ubuntu\install\boot
08-28 01:32 DEBUG  CommonBackend: Creating dir K:\ubuntu\disks\boot
08-28 01:32 DEBUG  CommonBackend: Creating dir K:\ubuntu\disks\boot\grub
08-28 01:32 DEBUG  CommonBackend: Creating dir K:\ubuntu\install\boot\grub
08-28 01:32 DEBUG  TaskList: ## Finished create_dir_structure
08-28 01:32 DEBUG  TaskList: ## Running uncompress_target_dir...
08-28 01:32 DEBUG  TaskList: ## Finished uncompress_target_dir
08-28 01:32 DEBUG  TaskList: ## Running create_uninstaller...
08-28 01:32 DEBUG  WindowsBackend: Copying uninstaller K:\Downloads\wubi.exe -> K:\ubuntu\uninstall-wubi.exe
08-28 01:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString K:\ubuntu\uninstall-wubi.exe
08-28 01:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir K:\ubuntu
08-28 01:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
08-28 01:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon K:\ubuntu\Ubuntu.ico
08-28 01:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev129
08-28 01:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
08-28 01:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
08-28 01:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
08-28 01:32 DEBUG  TaskList: ## Finished create_uninstaller
08-28 01:32 DEBUG  TaskList: ## Running copy_installation_files...
08-28 01:32 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Administrador\Datos de Usuario\Archivos Transitorios\pyl26F9.tmp\data\custom-installation -> K:\ubuntu\install\custom-installation
08-28 01:32 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Administrador\Datos de Usuario\Archivos Transitorios\pyl26F9.tmp\winboot -> K:\ubuntu\winboot
08-28 01:32 ERROR  TaskList: writelines() argument must be a sequence of strings
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\win32\backend.py", line 152, in copy_installation_files
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 257, in replace_line_in_file
TypeError: writelines() argument must be a sequence of strings
08-28 01:32 DEBUG  TaskList: # Cancelling tasklist
08-28 01:32 ERROR  root: writelines() argument must be a sequence of strings
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
TypeError: writelines() argument must be a sequence of strings
08-28 01:32 DEBUG  TaskList: # Finished tasklist
08-28 01:32 INFO   root: === wubi 9.04 rev129 ===
08-28 01:32 DEBUG  root: Logfile is c:\docume~1\administrador\datos de usuario\archivos transitorios\wubi-9.04-rev129.log
08-28 01:32 DEBUG  root: sys.argv = ['main.pyo', '--exefile="K:\\ubuntu\\uninstall-wubi.exe"', '--uninstall']
08-28 01:32 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Administrador\Datos de Usuario\Archivos Transitorios\pyl2859.tmp\data
08-28 01:32 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Administrador\Datos de Usuario\Archivos Transitorios\pyl2859.tmp\bin\7z.exe
08-28 01:32 DEBUG  CommonBackend: Fetching basic info...
08-28 01:32 DEBUG  CommonBackend: original_exe=K:\ubuntu\uninstall-wubi.exe
08-28 01:32 DEBUG  CommonBackend: platform=win32
08-28 01:32 DEBUG  CommonBackend: osname=nt
08-28 01:32 DEBUG  CommonBackend: language=es_ES
08-28 01:32 DEBUG  CommonBackend: encoding=cp1252
08-28 01:32 DEBUG  WindowsBackend: arch=amd64
08-28 01:32 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Administrador\Datos de Usuario\Archivos Transitorios\pyl2859.tmp\data\isolist.ini
08-28 01:32 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-28 01:32 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-28 01:32 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-28 01:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-28 01:32 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-28 01:32 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-28 01:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-28 01:32 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-28 01:32 DEBUG  WindowsBackend: Fetching host info...
08-28 01:32 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-28 01:32 DEBUG  WindowsBackend: windows version=xp
08-28 01:32 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
08-28 01:32 DEBUG  WindowsBackend: windows_sp=Service Pack 2
08-28 01:32 DEBUG  WindowsBackend: windows_build=2600
08-28 01:32 DEBUG  WindowsBackend: gmt=1
08-28 01:32 DEBUG  WindowsBackend: country=IT
08-28 01:32 DEBUG  WindowsBackend: timezone=Europe/Rome
08-28 01:32 DEBUG  WindowsBackend: windows_username=Administrador
08-28 01:32 DEBUG  WindowsBackend: user_full_name=Administrador
08-28 01:32 DEBUG  WindowsBackend: user_directory=Administrador
08-28 01:32 DEBUG  WindowsBackend: windows_language_code=1034
08-28 01:32 DEBUG  WindowsBackend: windows_language=Spanish
08-28 01:32 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
08-28 01:32 DEBUG  WindowsBackend: bootloader=xp
08-28 01:32 DEBUG  WindowsBackend: system_drive=Drive(C: hd 4056.15234375 mb free )
08-28 01:32 DEBUG  WindowsBackend: drive=Drive(C: hd 4056.15234375 mb free )
08-28 01:32 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
08-28 01:32 DEBUG  WindowsBackend: drive=Drive(E: removable 0.0 mb free )
08-28 01:32 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
08-28 01:32 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
08-28 01:32 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
08-28 01:32 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
08-28 01:32 DEBUG  WindowsBackend: drive=Drive(J: removable 0.0 mb free )
08-28 01:32 DEBUG  WindowsBackend: drive=Drive(K: hd 120562.222656 mb free ntfs)
08-28 01:32 DEBUG  WindowsBackend: drive=Drive(L: cd 0.0 mb free )
08-28 01:32 DEBUG  WindowsBackend: drive=Drive(M: cd 0.0 mb free )
08-28 01:32 DEBUG  WindowsBackend: uninstaller_path=K:\ubuntu\uninstall-wubi.exe
08-28 01:32 DEBUG  WindowsBackend: previous_target_dir=K:\ubuntu
08-28 01:32 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
08-28 01:32 DEBUG  WindowsBackend: keyboard_id=67707913
08-28 01:32 DEBUG  WindowsBackend: keyboard_layout=it
08-28 01:32 DEBUG  WindowsBackend: keyboard_variant=
08-28 01:32 DEBUG  CommonBackend: locale=es_ES.UTF-8
08-28 01:32 DEBUG  WindowsBackend: total_memory_mb=2046.48046875
08-28 01:32 DEBUG  CommonBackend: Searching ISOs on USB devices
08-28 01:32 DEBUG  CommonBackend: Searching for local CDs
08-28 01:32 DEBUG  Distro:   checking whether C:\DOCUME~1\Administrador\Datos de Usuario\Archivos Transitorios\pyl2859.tmp is a valid Ubuntu CD
08-28 01:32 DEBUG  Distro:     does not contain C:\DOCUME~1\Administrador\Datos de Usuario\Archivos Transitorios\pyl2859.tmp\casper\filesystem.squashfs
08-28 01:32 DEBUG  Distro:   checking whether C:\DOCUME~1\Administrador\Datos de Usuario\Archivos Transitorios\pyl2859.tmp is a valid Ubuntu CD
08-28 01:32 DEBUG  Distro:     does not contain C:\DOCUME~1\Administrador\Datos de Usuario\Archivos Transitorios\pyl2859.tmp\casper\filesystem.squashfs
08-28 01:32 DEBUG  Distro:   checking whether C:\DOCUME~1\Administrador\Datos de Usuario\Archivos Transitorios\pyl2859.tmp is a valid Kubuntu CD
08-28 01:32 DEBUG  Distro:     does not contain C:\DOCUME~1\Administrador\Datos de Usuario\Archivos Transitorios\pyl2859.tmp\casper\filesystem.squashfs
08-28 01:32 DEBUG  Distro:   checking whether C:\DOCUME~1\Administrador\Datos de Usuario\Archivos Transitorios\pyl2859.tmp is a valid Kubuntu CD
08-28 01:32 DEBUG  Distro:     does not contain C:\DOCUME~1\Administrador\Datos de Usuario\Archivos Transitorios\pyl2859.tmp\casper\filesystem.squashfs
08-28 01:32 DEBUG  Distro:   checking whether C:\DOCUME~1\Administrador\Datos de Usuario\Archivos Transitorios\pyl2859.tmp is a valid Xubuntu CD
08-28 01:32 DEBUG  Distro:     does not contain C:\DOCUME~1\Administrador\Datos de Usuario\Archivos Transitorios\pyl2859.tmp\casper\filesystem.squashfs
08-28 01:32 DEBUG  Distro:   checking whether C:\DOCUME~1\Administrador\Datos de Usuario\Archivos Transitorios\pyl2859.tmp is a valid Xubuntu CD
08-28 01:32 DEBUG  Distro:     does not contain C:\DOCUME~1\Administrador\Datos de Usuario\Archivos Transitorios\pyl2859.tmp\casper\filesystem.squashfs
08-28 01:32 DEBUG  Distro:   checking whether C:\DOCUME~1\Administrador\Datos de Usuario\Archivos Transitorios\pyl2859.tmp is a valid Mythbuntu CD
08-28 01:32 DEBUG  Distro:     does not contain C:\DOCUME~1\Administrador\Datos de Usuario\Archivos Transitorios\pyl2859.tmp\casper\filesystem.squashfs
08-28 01:32 DEBUG  Distro:   checking whether C:\DOCUME~1\Administrador\Datos de Usuario\Archivos Transitorios\pyl2859.tmp is a valid Mythbuntu CD
08-28 01:32 DEBUG  Distro:     does not contain C:\DOCUME~1\Administrador\Datos de Usuario\Archivos Transitorios\pyl2859.tmp\casper\filesystem.squashfs
08-28 01:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-28 01:32 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
08-28 01:32 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
08-28 01:32 INFO   Distro: Found a valid CD for Ubuntu: D:\
08-28 01:32 INFO   root: Running the uninstaller...
08-28 01:32 INFO   CommonBackend: This is the uninstaller running
08-28 01:32 DEBUG  WindowsFrontend: __init__...
08-28 01:32 DEBUG  WindowsFrontend: on_init...
08-28 01:32 INFO   root: Received settings
08-28 01:32 DEBUG  TaskList: # Running tasklist...
08-28 01:32 DEBUG  TaskList: ## Running Backup ISO...
08-28 01:32 DEBUG  TaskList: ## Finished Backup ISO
08-28 01:32 DEBUG  TaskList: ## Running Remove bootloader entry...
08-28 01:32 ERROR  WindowsBackend: Cannot find bcdedit
08-28 01:32 DEBUG  WindowsBackend: undo_bootini C:
08-28 01:32 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 4056.15234375 mb free )
08-28 01:32 DEBUG  WindowsBackend: undo_bootini E:
08-28 01:32 DEBUG  WindowsBackend: undo_configsys Drive(E: removable 0.0 mb free )
08-28 01:32 DEBUG  WindowsBackend: undo_bootini F:
08-28 01:32 DEBUG  WindowsBackend: undo_configsys Drive(F: removable 0.0 mb free )
08-28 01:32 DEBUG  WindowsBackend: undo_bootini G:
08-28 01:32 DEBUG  WindowsBackend: undo_configsys Drive(G: removable 0.0 mb free )
08-28 01:32 DEBUG  WindowsBackend: undo_bootini J:
08-28 01:32 DEBUG  WindowsBackend: undo_configsys Drive(J: removable 0.0 mb free )
08-28 01:32 DEBUG  WindowsBackend: undo_bootini K:
08-28 01:32 DEBUG  WindowsBackend: undo_configsys Drive(K: hd 120562.222656 mb free ntfs)
08-28 01:32 DEBUG  TaskList: ## Finished Remove bootloader entry
08-28 01:32 DEBUG  TaskList: ## Running Remove target dir...
08-28 01:32 DEBUG  CommonBackend: Deleting K:\ubuntu
08-28 01:32 DEBUG  TaskList: ## Finished Remove target dir
08-28 01:32 DEBUG  TaskList: ## Running Remove registry key...
08-28 01:32 DEBUG  TaskList: ## Finished Remove registry key
08-28 01:32 DEBUG  TaskList: # Finished tasklist
08-28 01:32 INFO   root: Almost finished uninstalling
08-28 01:32 INFO   root: Finished uninstallation
08-28 01:32 DEBUG  root: application.quit
08-28 01:32 DEBUG  WindowsFrontend: frontend.quit
08-28 01:32 DEBUG  WindowsFrontend: frontend.on_quit
08-28 01:32 DEBUG  root: application.on_quit
08-28 01:32 INFO   root: sys.exit[/COLOR]

---

