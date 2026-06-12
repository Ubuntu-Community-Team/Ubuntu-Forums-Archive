---
title: "Error while trying to install"
date: 2009-07-21
forum: Installation &amp; Upgrades
---

### Post by frz on 2009-07-21
While triying to install Ubuntu desktop 9.04 using Wubi the following error message appears:

>     ---------------------------
  Ubuntu Installer
  ---------------------------
  An error occurred:
   
   
   
  For more information, please see the log file: c:\docume~1\felipe\config~1\temp\wubi-9.04-rev129.log
  ---------------------------
  Aceptar   
  ---------------------------
  and the following log file is created:

```
07-21 20:56 INFO   root: === wubi 9.04 rev129 ===
07-21 20:56 DEBUG  root: Logfile is c:\docume~1\felipe\config~1\temp\wubi-9.04-rev129.log
07-21 20:56 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Felipe\\Escritorio\\wubi.exe"']
07-21 20:56 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7D.tmp\data
07-21 20:56 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7D.tmp\bin\7z.exe
07-21 20:56 DEBUG  CommonBackend: Fetching basic info...
07-21 20:56 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Felipe\Escritorio\wubi.exe
07-21 20:56 DEBUG  CommonBackend: platform=win32
07-21 20:56 DEBUG  CommonBackend: osname=nt
07-21 20:56 DEBUG  CommonBackend: language=es_CL
07-21 20:56 DEBUG  CommonBackend: encoding=cp1252
07-21 20:56 DEBUG  WindowsBackend: arch=i386
07-21 20:56 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7D.tmp\data\isolist.ini
07-21 20:56 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-21 20:56 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-21 20:56 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-21 20:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-21 20:56 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-21 20:56 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-21 20:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-21 20:56 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-21 20:56 DEBUG  WindowsBackend: Fetching host info...
07-21 20:56 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-21 20:56 DEBUG  WindowsBackend: windows version=xp
07-21 20:56 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
07-21 20:56 DEBUG  WindowsBackend: windows_sp=Service Pack 3
07-21 20:56 DEBUG  WindowsBackend: windows_build=2600
07-21 20:56 DEBUG  WindowsBackend: gmt=-4
07-21 20:56 DEBUG  WindowsBackend: country=CL
07-21 20:56 DEBUG  WindowsBackend: timezone=America/Santiago
07-21 20:56 DEBUG  WindowsBackend: windows_username=Felipe
07-21 20:56 DEBUG  WindowsBackend: user_full_name=Felipe
07-21 20:56 DEBUG  WindowsBackend: user_directory=Felipe
07-21 20:56 DEBUG  WindowsBackend: windows_language_code=1034
07-21 20:56 DEBUG  WindowsBackend: windows_language=Spanish
07-21 20:56 DEBUG  WindowsBackend: processor_name=         Intel(R) Atom(TM) CPU N270   @ 1.60GHz
07-21 20:56 DEBUG  WindowsBackend: bootloader=xp
07-21 20:56 DEBUG  WindowsBackend: system_drive=Drive(C: hd 39910.3789063 mb free )
07-21 20:56 DEBUG  WindowsBackend: drive=Drive(C: hd 39910.3789063 mb free )
07-21 20:56 DEBUG  WindowsBackend: uninstaller_path=None
07-21 20:56 DEBUG  WindowsBackend: previous_target_dir=None
07-21 20:56 DEBUG  WindowsBackend: previous_distro_name=None
07-21 20:56 DEBUG  WindowsBackend: keyboard_id=134886410
07-21 20:56 DEBUG  WindowsBackend: keyboard_layout=cl
07-21 20:56 DEBUG  WindowsBackend: keyboard_variant=
07-21 20:56 DEBUG  CommonBackend: locale=es_CL.UTF-8
07-21 20:56 DEBUG  WindowsBackend: total_memory_mb=1015.23046875
07-21 20:56 DEBUG  CommonBackend: Searching ISOs on USB devices
07-21 20:56 DEBUG  CommonBackend: Searching for local CDs
07-21 20:56 DEBUG  Distro:   checking whether C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7D.tmp is a valid Ubuntu CD
07-21 20:56 DEBUG  Distro:     does not contain C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7D.tmp\casper\filesystem.squashfs
07-21 20:56 DEBUG  Distro:   checking whether C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7D.tmp is a valid Ubuntu CD
07-21 20:56 DEBUG  Distro:     does not contain C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7D.tmp\casper\filesystem.squashfs
07-21 20:56 DEBUG  Distro:   checking whether C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7D.tmp is a valid Kubuntu CD
07-21 20:56 DEBUG  Distro:     does not contain C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7D.tmp\casper\filesystem.squashfs
07-21 20:56 DEBUG  Distro:   checking whether C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7D.tmp is a valid Kubuntu CD
07-21 20:56 DEBUG  Distro:     does not contain C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7D.tmp\casper\filesystem.squashfs
07-21 20:56 DEBUG  Distro:   checking whether C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7D.tmp is a valid Xubuntu CD
07-21 20:56 DEBUG  Distro:     does not contain C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7D.tmp\casper\filesystem.squashfs
07-21 20:56 DEBUG  Distro:   checking whether C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7D.tmp is a valid Xubuntu CD
07-21 20:56 DEBUG  Distro:     does not contain C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7D.tmp\casper\filesystem.squashfs
07-21 20:56 DEBUG  Distro:   checking whether C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7D.tmp is a valid Mythbuntu CD
07-21 20:56 DEBUG  Distro:     does not contain C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7D.tmp\casper\filesystem.squashfs
07-21 20:56 DEBUG  Distro:   checking whether C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7D.tmp is a valid Mythbuntu CD
07-21 20:56 DEBUG  Distro:     does not contain C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7D.tmp\casper\filesystem.squashfs
07-21 20:56 INFO   root: Running the installer...
07-21 20:56 DEBUG  WindowsFrontend: __init__...
07-21 20:56 DEBUG  WindowsFrontend: on_init...
07-21 21:01 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=15000MB, distro_name=Ubuntu, language=Spanish, username=felipe
07-21 21:01 INFO   root: Received settings
07-21 21:01 DEBUG  TaskList: # Running tasklist...
07-21 21:01 DEBUG  TaskList: ## Running select_target_dir...
07-21 21:01 INFO   WindowsBackend: Installing into C:\ubuntu
07-21 21:01 DEBUG  TaskList: ## Finished select_target_dir
07-21 21:01 DEBUG  TaskList: ## Running create_dir_structure...
07-21 21:01 DEBUG  CommonBackend: Creating dir C:\ubuntu
07-21 21:01 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
07-21 21:01 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
07-21 21:01 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
07-21 21:01 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
07-21 21:01 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
07-21 21:01 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
07-21 21:01 DEBUG  TaskList: ## Finished create_dir_structure
07-21 21:01 DEBUG  TaskList: ## Running uncompress_target_dir...
07-21 21:01 DEBUG  TaskList: ## Finished uncompress_target_dir
07-21 21:01 DEBUG  TaskList: ## Running create_uninstaller...
07-21 21:01 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\Felipe\Escritorio\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
07-21 21:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
07-21 21:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
07-21 21:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-21 21:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
07-21 21:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev129
07-21 21:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-21 21:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
07-21 21:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
07-21 21:01 DEBUG  TaskList: ## Finished create_uninstaller
07-21 21:01 DEBUG  TaskList: ## Running copy_installation_files...
07-21 21:01 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7D.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
07-21 21:01 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7D.tmp\winboot -> C:\ubuntu\winboot
07-21 21:01 ERROR  TaskList: [('C:\\DOCUME~1\\Felipe\\CONFIG~1\\Temp\\pyl7D.tmp\\winboot\\wubildr.exe', 'C:\\ubuntu\\winboot\\wubildr.exe', <exceptions.OSError instance at 0x00F0E148>)]
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\win32\backend.py", line 146, in copy_installation_files
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\shutil.py", line 119, in copytree
Error: [('C:\\DOCUME~1\\Felipe\\CONFIG~1\\Temp\\pyl7D.tmp\\winboot\\wubildr.exe', 'C:\\ubuntu\\winboot\\wubildr.exe', <exceptions.OSError instance at 0x00F0E148>)]
07-21 21:01 DEBUG  TaskList: # Cancelling tasklist
07-21 21:01 DEBUG  TaskList: # Finished tasklist
07-21 21:01 ERROR  root: [('C:\\DOCUME~1\\Felipe\\CONFIG~1\\Temp\\pyl7D.tmp\\winboot\\wubildr.exe', 'C:\\ubuntu\\winboot\\wubildr.exe', <exceptions.OSError instance at 0x00F0E148>)]
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 129, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
Error: [('C:\\DOCUME~1\\Felipe\\CONFIG~1\\Temp\\pyl7D.tmp\\winboot\\wubildr.exe', 'C:\\ubuntu\\winboot\\wubildr.exe', <exceptions.OSError instance at 0x00F0E148>)]
07-21 21:02 INFO   root: === wubi 9.04 rev129 ===
07-21 21:02 DEBUG  root: Logfile is c:\docume~1\felipe\config~1\temp\wubi-9.04-rev129.log
07-21 21:02 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Felipe\\Escritorio\\wubi.exe"']
07-21 21:02 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7E.tmp\data
07-21 21:02 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7E.tmp\bin\7z.exe
07-21 21:02 DEBUG  CommonBackend: Fetching basic info...
07-21 21:02 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Felipe\Escritorio\wubi.exe
07-21 21:02 DEBUG  CommonBackend: platform=win32
07-21 21:02 DEBUG  CommonBackend: osname=nt
07-21 21:02 DEBUG  CommonBackend: language=es_CL
07-21 21:02 DEBUG  CommonBackend: encoding=cp1252
07-21 21:02 DEBUG  WindowsBackend: arch=i386
07-21 21:02 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7E.tmp\data\isolist.ini
07-21 21:02 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-21 21:02 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-21 21:02 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-21 21:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-21 21:02 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-21 21:02 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-21 21:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-21 21:02 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-21 21:02 DEBUG  WindowsBackend: Fetching host info...
07-21 21:02 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-21 21:02 DEBUG  WindowsBackend: windows version=xp
07-21 21:02 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
07-21 21:02 DEBUG  WindowsBackend: windows_sp=Service Pack 3
07-21 21:02 DEBUG  WindowsBackend: windows_build=2600
07-21 21:02 DEBUG  WindowsBackend: gmt=-4
07-21 21:02 DEBUG  WindowsBackend: country=CL
07-21 21:02 DEBUG  WindowsBackend: timezone=America/Santiago
07-21 21:02 DEBUG  WindowsBackend: windows_username=Felipe
07-21 21:02 DEBUG  WindowsBackend: user_full_name=Felipe
07-21 21:02 DEBUG  WindowsBackend: user_directory=Felipe
07-21 21:02 DEBUG  WindowsBackend: windows_language_code=1034
07-21 21:02 DEBUG  WindowsBackend: windows_language=Spanish
07-21 21:02 DEBUG  WindowsBackend: processor_name=         Intel(R) Atom(TM) CPU N270   @ 1.60GHz
07-21 21:02 DEBUG  WindowsBackend: bootloader=xp
07-21 21:02 DEBUG  WindowsBackend: system_drive=Drive(C: hd 39907.9453125 mb free )
07-21 21:02 DEBUG  WindowsBackend: drive=Drive(C: hd 39907.9453125 mb free )
07-21 21:02 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
07-21 21:02 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
07-21 21:02 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
07-21 21:02 DEBUG  WindowsBackend: keyboard_id=134886410
07-21 21:02 DEBUG  WindowsBackend: keyboard_layout=cl
07-21 21:02 DEBUG  WindowsBackend: keyboard_variant=
07-21 21:02 DEBUG  CommonBackend: locale=es_CL.UTF-8
07-21 21:02 DEBUG  WindowsBackend: total_memory_mb=1015.23046875
07-21 21:02 DEBUG  CommonBackend: Searching ISOs on USB devices
07-21 21:02 DEBUG  CommonBackend: Searching for local CDs
07-21 21:02 DEBUG  Distro:   checking whether C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7E.tmp is a valid Ubuntu CD
07-21 21:02 DEBUG  Distro:     does not contain C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7E.tmp\casper\filesystem.squashfs
07-21 21:02 DEBUG  Distro:   checking whether C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7E.tmp is a valid Ubuntu CD
07-21 21:02 DEBUG  Distro:     does not contain C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7E.tmp\casper\filesystem.squashfs
07-21 21:02 DEBUG  Distro:   checking whether C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7E.tmp is a valid Kubuntu CD
07-21 21:02 DEBUG  Distro:     does not contain C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7E.tmp\casper\filesystem.squashfs
07-21 21:02 DEBUG  Distro:   checking whether C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7E.tmp is a valid Kubuntu CD
07-21 21:02 DEBUG  Distro:     does not contain C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7E.tmp\casper\filesystem.squashfs
07-21 21:02 DEBUG  Distro:   checking whether C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7E.tmp is a valid Xubuntu CD
07-21 21:02 DEBUG  Distro:     does not contain C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7E.tmp\casper\filesystem.squashfs
07-21 21:02 DEBUG  Distro:   checking whether C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7E.tmp is a valid Xubuntu CD
07-21 21:02 DEBUG  Distro:     does not contain C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7E.tmp\casper\filesystem.squashfs
07-21 21:02 DEBUG  Distro:   checking whether C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7E.tmp is a valid Mythbuntu CD
07-21 21:02 DEBUG  Distro:     does not contain C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7E.tmp\casper\filesystem.squashfs
07-21 21:02 DEBUG  Distro:   checking whether C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7E.tmp is a valid Mythbuntu CD
07-21 21:02 DEBUG  Distro:     does not contain C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7E.tmp\casper\filesystem.squashfs
07-21 21:02 INFO   root: Already installed, running the uninstaller...
07-21 21:02 INFO   root: Running the uninstaller...
07-21 21:02 INFO   CommonBackend: This is the uninstaller running
07-21 21:02 DEBUG  WindowsFrontend: __init__...
07-21 21:02 DEBUG  WindowsFrontend: on_init...
07-21 21:02 INFO   root: Received settings
07-21 21:02 DEBUG  TaskList: # Running tasklist...
07-21 21:02 DEBUG  TaskList: ## Running Backup ISO...
07-21 21:02 DEBUG  TaskList: ## Finished Backup ISO
07-21 21:02 DEBUG  TaskList: ## Running Remove bootloader entry...
07-21 21:02 ERROR  WindowsBackend: Cannot find bcdedit
07-21 21:02 DEBUG  WindowsBackend: undo_bootini C:
07-21 21:02 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 39907.9453125 mb free )
07-21 21:02 DEBUG  TaskList: ## Finished Remove bootloader entry
07-21 21:02 DEBUG  TaskList: ## Running Remove target dir...
07-21 21:02 DEBUG  CommonBackend: Deleting C:\ubuntu
07-21 21:02 DEBUG  TaskList: ## Finished Remove target dir
07-21 21:02 DEBUG  TaskList: ## Running Remove registry key...
07-21 21:02 DEBUG  TaskList: ## Finished Remove registry key
07-21 21:02 DEBUG  TaskList: # Finished tasklist
07-21 21:02 INFO   root: Almost finished uninstalling
07-21 21:02 INFO   root: Finished uninstallation
07-21 21:02 DEBUG  CommonBackend: Fetching basic info...
07-21 21:02 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Felipe\Escritorio\wubi.exe
07-21 21:02 DEBUG  CommonBackend: platform=win32
07-21 21:02 DEBUG  CommonBackend: osname=nt
07-21 21:02 DEBUG  CommonBackend: language=es_CL
07-21 21:02 DEBUG  CommonBackend: encoding=cp1252
07-21 21:02 DEBUG  WindowsBackend: arch=i386
07-21 21:02 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7E.tmp\data\isolist.ini
07-21 21:02 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-21 21:02 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-21 21:02 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-21 21:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-21 21:02 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-21 21:02 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-21 21:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-21 21:02 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-21 21:02 DEBUG  WindowsBackend: Fetching host info...
07-21 21:02 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-21 21:02 DEBUG  WindowsBackend: windows version=xp
07-21 21:02 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
07-21 21:02 DEBUG  WindowsBackend: windows_sp=Service Pack 3
07-21 21:02 DEBUG  WindowsBackend: windows_build=2600
07-21 21:02 DEBUG  WindowsBackend: gmt=-4
07-21 21:02 DEBUG  WindowsBackend: country=CL
07-21 21:02 DEBUG  WindowsBackend: timezone=America/Santiago
07-21 21:02 DEBUG  WindowsBackend: windows_username=Felipe
07-21 21:02 DEBUG  WindowsBackend: user_full_name=Felipe
07-21 21:02 DEBUG  WindowsBackend: user_directory=Felipe
07-21 21:02 DEBUG  WindowsBackend: windows_language_code=1034
07-21 21:02 DEBUG  WindowsBackend: windows_language=Spanish
07-21 21:02 DEBUG  WindowsBackend: processor_name=         Intel(R) Atom(TM) CPU N270   @ 1.60GHz
07-21 21:02 DEBUG  WindowsBackend: bootloader=xp
07-21 21:02 DEBUG  WindowsBackend: system_drive=Drive(C: hd 39909.8242188 mb free )
07-21 21:02 DEBUG  WindowsBackend: drive=Drive(C: hd 39909.8242188 mb free )
07-21 21:02 DEBUG  WindowsBackend: uninstaller_path=None
07-21 21:02 DEBUG  WindowsBackend: previous_target_dir=None
07-21 21:02 DEBUG  WindowsBackend: previous_distro_name=None
07-21 21:02 DEBUG  WindowsBackend: keyboard_id=134886410
07-21 21:02 DEBUG  WindowsBackend: keyboard_layout=cl
07-21 21:02 DEBUG  WindowsBackend: keyboard_variant=
07-21 21:02 DEBUG  CommonBackend: locale=es_CL.UTF-8
07-21 21:02 DEBUG  WindowsBackend: total_memory_mb=1015.23046875
07-21 21:02 DEBUG  CommonBackend: Searching ISOs on USB devices
07-21 21:02 DEBUG  CommonBackend: Searching for local CDs
07-21 21:02 DEBUG  Distro:   checking whether C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7E.tmp is a valid Ubuntu CD
07-21 21:02 DEBUG  Distro:     does not contain C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7E.tmp\casper\filesystem.squashfs
07-21 21:02 DEBUG  Distro:   checking whether C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7E.tmp is a valid Ubuntu CD
07-21 21:02 DEBUG  Distro:     does not contain C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7E.tmp\casper\filesystem.squashfs
07-21 21:02 DEBUG  Distro:   checking whether C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7E.tmp is a valid Kubuntu CD
07-21 21:02 DEBUG  Distro:     does not contain C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7E.tmp\casper\filesystem.squashfs
07-21 21:02 DEBUG  Distro:   checking whether C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7E.tmp is a valid Kubuntu CD
07-21 21:02 DEBUG  Distro:     does not contain C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7E.tmp\casper\filesystem.squashfs
07-21 21:02 DEBUG  Distro:   checking whether C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7E.tmp is a valid Xubuntu CD
07-21 21:02 DEBUG  Distro:     does not contain C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7E.tmp\casper\filesystem.squashfs
07-21 21:02 DEBUG  Distro:   checking whether C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7E.tmp is a valid Xubuntu CD
07-21 21:02 DEBUG  Distro:     does not contain C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7E.tmp\casper\filesystem.squashfs
07-21 21:02 DEBUG  Distro:   checking whether C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7E.tmp is a valid Mythbuntu CD
07-21 21:02 DEBUG  Distro:     does not contain C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7E.tmp\casper\filesystem.squashfs
07-21 21:02 DEBUG  Distro:   checking whether C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7E.tmp is a valid Mythbuntu CD
07-21 21:02 DEBUG  Distro:     does not contain C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7E.tmp\casper\filesystem.squashfs
07-21 21:02 INFO   root: Running the installer...
07-21 21:02 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=Spanish, username=felipe
07-21 21:02 INFO   root: Received settings
07-21 21:02 DEBUG  TaskList: # Running tasklist...
07-21 21:02 DEBUG  TaskList: ## Running select_target_dir...
07-21 21:02 INFO   WindowsBackend: Installing into C:\ubuntu
07-21 21:02 DEBUG  TaskList: ## Finished select_target_dir
07-21 21:02 DEBUG  TaskList: ## Running create_dir_structure...
07-21 21:02 DEBUG  CommonBackend: Creating dir C:\ubuntu
07-21 21:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
07-21 21:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
07-21 21:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
07-21 21:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
07-21 21:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
07-21 21:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
07-21 21:02 DEBUG  TaskList: ## Finished create_dir_structure
07-21 21:02 DEBUG  TaskList: ## Running uncompress_target_dir...
07-21 21:02 DEBUG  TaskList: ## Finished uncompress_target_dir
07-21 21:02 DEBUG  TaskList: ## Running create_uninstaller...
07-21 21:02 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\Felipe\Escritorio\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
07-21 21:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
07-21 21:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
07-21 21:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-21 21:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
07-21 21:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev129
07-21 21:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-21 21:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
07-21 21:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
07-21 21:02 DEBUG  TaskList: ## Finished create_uninstaller
07-21 21:02 DEBUG  TaskList: ## Running copy_installation_files...
07-21 21:02 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7E.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
07-21 21:02 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl7E.tmp\winboot -> C:\ubuntu\winboot
07-21 21:02 ERROR  TaskList: [('C:\\DOCUME~1\\Felipe\\CONFIG~1\\Temp\\pyl7E.tmp\\winboot\\wubildr.exe', 'C:\\ubuntu\\winboot\\wubildr.exe', <exceptions.OSError instance at 0x00F080F8>)]
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\win32\backend.py", line 146, in copy_installation_files
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\shutil.py", line 119, in copytree
Error: [('C:\\DOCUME~1\\Felipe\\CONFIG~1\\Temp\\pyl7E.tmp\\winboot\\wubildr.exe', 'C:\\ubuntu\\winboot\\wubildr.exe', <exceptions.OSError instance at 0x00F080F8>)]
07-21 21:02 DEBUG  TaskList: # Cancelling tasklist
07-21 21:02 DEBUG  TaskList: # Finished tasklist
07-21 21:02 ERROR  root: [('C:\\DOCUME~1\\Felipe\\CONFIG~1\\Temp\\pyl7E.tmp\\winboot\\wubildr.exe', 'C:\\ubuntu\\winboot\\wubildr.exe', <exceptions.OSError instance at 0x00F080F8>)]
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 129, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
Error: [('C:\\DOCUME~1\\Felipe\\CONFIG~1\\Temp\\pyl7E.tmp\\winboot\\wubildr.exe', 'C:\\ubuntu\\winboot\\wubildr.exe', <exceptions.OSError instance at 0x00F080F8>)]
07-21 21:11 INFO   root: === wubi 9.04 rev129 ===
07-21 21:11 DEBUG  root: Logfile is c:\docume~1\felipe\config~1\temp\wubi-9.04-rev129.log
07-21 21:11 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Felipe\\Escritorio\\wubi.exe"']
07-21 21:11 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl83.tmp\data
07-21 21:11 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl83.tmp\bin\7z.exe
07-21 21:11 DEBUG  CommonBackend: Fetching basic info...
07-21 21:11 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Felipe\Escritorio\wubi.exe
07-21 21:11 DEBUG  CommonBackend: platform=win32
07-21 21:11 DEBUG  CommonBackend: osname=nt
07-21 21:11 DEBUG  CommonBackend: language=es_CL
07-21 21:11 DEBUG  CommonBackend: encoding=cp1252
07-21 21:11 DEBUG  WindowsBackend: arch=i386
07-21 21:11 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl83.tmp\data\isolist.ini
07-21 21:11 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-21 21:11 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-21 21:11 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-21 21:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-21 21:11 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-21 21:11 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-21 21:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-21 21:11 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-21 21:11 DEBUG  WindowsBackend: Fetching host info...
07-21 21:11 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-21 21:11 DEBUG  WindowsBackend: windows version=xp
07-21 21:11 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
07-21 21:11 DEBUG  WindowsBackend: windows_sp=Service Pack 3
07-21 21:11 DEBUG  WindowsBackend: windows_build=2600
07-21 21:11 DEBUG  WindowsBackend: gmt=-4
07-21 21:11 DEBUG  WindowsBackend: country=CL
07-21 21:11 DEBUG  WindowsBackend: timezone=America/Santiago
07-21 21:11 DEBUG  WindowsBackend: windows_username=Felipe
07-21 21:11 DEBUG  WindowsBackend: user_full_name=Felipe
07-21 21:11 DEBUG  WindowsBackend: user_directory=Felipe
07-21 21:11 DEBUG  WindowsBackend: windows_language_code=1034
07-21 21:11 DEBUG  WindowsBackend: windows_language=Spanish
07-21 21:11 DEBUG  WindowsBackend: processor_name=         Intel(R) Atom(TM) CPU N270   @ 1.60GHz
07-21 21:11 DEBUG  WindowsBackend: bootloader=xp
07-21 21:11 DEBUG  WindowsBackend: system_drive=Drive(C: hd 39907.6796875 mb free )
07-21 21:11 DEBUG  WindowsBackend: drive=Drive(C: hd 39907.6796875 mb free )
07-21 21:11 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
07-21 21:11 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
07-21 21:11 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
07-21 21:11 DEBUG  WindowsBackend: keyboard_id=134886410
07-21 21:11 DEBUG  WindowsBackend: keyboard_layout=cl
07-21 21:11 DEBUG  WindowsBackend: keyboard_variant=
07-21 21:11 DEBUG  CommonBackend: locale=es_CL.UTF-8
07-21 21:11 DEBUG  WindowsBackend: total_memory_mb=1015.23046875
07-21 21:11 DEBUG  CommonBackend: Searching ISOs on USB devices
07-21 21:11 DEBUG  CommonBackend: Searching for local CDs
07-21 21:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl83.tmp is a valid Ubuntu CD
07-21 21:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl83.tmp\casper\filesystem.squashfs
07-21 21:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl83.tmp is a valid Ubuntu CD
07-21 21:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl83.tmp\casper\filesystem.squashfs
07-21 21:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl83.tmp is a valid Kubuntu CD
07-21 21:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl83.tmp\casper\filesystem.squashfs
07-21 21:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl83.tmp is a valid Kubuntu CD
07-21 21:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl83.tmp\casper\filesystem.squashfs
07-21 21:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl83.tmp is a valid Xubuntu CD
07-21 21:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl83.tmp\casper\filesystem.squashfs
07-21 21:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl83.tmp is a valid Xubuntu CD
07-21 21:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl83.tmp\casper\filesystem.squashfs
07-21 21:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl83.tmp is a valid Mythbuntu CD
07-21 21:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl83.tmp\casper\filesystem.squashfs
07-21 21:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl83.tmp is a valid Mythbuntu CD
07-21 21:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl83.tmp\casper\filesystem.squashfs
07-21 21:11 INFO   root: Already installed, running the uninstaller...
07-21 21:11 INFO   root: Running the uninstaller...
07-21 21:11 INFO   CommonBackend: This is the uninstaller running
07-21 21:11 DEBUG  WindowsFrontend: __init__...
07-21 21:11 DEBUG  WindowsFrontend: on_init...
07-21 21:11 INFO   root: Received settings
07-21 21:11 DEBUG  TaskList: # Running tasklist...
07-21 21:11 DEBUG  TaskList: ## Running Backup ISO...
07-21 21:11 DEBUG  TaskList: ## Finished Backup ISO
07-21 21:11 DEBUG  TaskList: ## Running Remove bootloader entry...
07-21 21:11 ERROR  WindowsBackend: Cannot find bcdedit
07-21 21:11 DEBUG  WindowsBackend: undo_bootini C:
07-21 21:11 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 39907.6796875 mb free )
07-21 21:11 DEBUG  TaskList: ## Finished Remove bootloader entry
07-21 21:11 DEBUG  TaskList: ## Running Remove target dir...
07-21 21:11 DEBUG  CommonBackend: Deleting C:\ubuntu
07-21 21:11 DEBUG  TaskList: ## Finished Remove target dir
07-21 21:11 DEBUG  TaskList: ## Running Remove registry key...
07-21 21:11 DEBUG  TaskList: ## Finished Remove registry key
07-21 21:11 DEBUG  TaskList: # Finished tasklist
07-21 21:11 INFO   root: Almost finished uninstalling
07-21 21:11 INFO   root: Finished uninstallation
07-21 21:11 DEBUG  CommonBackend: Fetching basic info...
07-21 21:11 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Felipe\Escritorio\wubi.exe
07-21 21:11 DEBUG  CommonBackend: platform=win32
07-21 21:11 DEBUG  CommonBackend: osname=nt
07-21 21:11 DEBUG  CommonBackend: language=es_CL
07-21 21:11 DEBUG  CommonBackend: encoding=cp1252
07-21 21:11 DEBUG  WindowsBackend: arch=i386
07-21 21:11 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl83.tmp\data\isolist.ini
07-21 21:11 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-21 21:11 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-21 21:11 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-21 21:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-21 21:11 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-21 21:11 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-21 21:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-21 21:11 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-21 21:11 DEBUG  WindowsBackend: Fetching host info...
07-21 21:11 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-21 21:11 DEBUG  WindowsBackend: windows version=xp
07-21 21:11 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
07-21 21:11 DEBUG  WindowsBackend: windows_sp=Service Pack 3
07-21 21:11 DEBUG  WindowsBackend: windows_build=2600
07-21 21:11 DEBUG  WindowsBackend: gmt=-4
07-21 21:11 DEBUG  WindowsBackend: country=CL
07-21 21:11 DEBUG  WindowsBackend: timezone=America/Santiago
07-21 21:11 DEBUG  WindowsBackend: windows_username=Felipe
07-21 21:11 DEBUG  WindowsBackend: user_full_name=Felipe
07-21 21:11 DEBUG  WindowsBackend: user_directory=Felipe
07-21 21:11 DEBUG  WindowsBackend: windows_language_code=1034
07-21 21:11 DEBUG  WindowsBackend: windows_language=Spanish
07-21 21:11 DEBUG  WindowsBackend: processor_name=         Intel(R) Atom(TM) CPU N270   @ 1.60GHz
07-21 21:11 DEBUG  WindowsBackend: bootloader=xp
07-21 21:11 DEBUG  WindowsBackend: system_drive=Drive(C: hd 39909.5546875 mb free )
07-21 21:11 DEBUG  WindowsBackend: drive=Drive(C: hd 39909.5546875 mb free )
07-21 21:11 DEBUG  WindowsBackend: uninstaller_path=None
07-21 21:11 DEBUG  WindowsBackend: previous_target_dir=None
07-21 21:11 DEBUG  WindowsBackend: previous_distro_name=None
07-21 21:11 DEBUG  WindowsBackend: keyboard_id=134886410
07-21 21:11 DEBUG  WindowsBackend: keyboard_layout=cl
07-21 21:11 DEBUG  WindowsBackend: keyboard_variant=
07-21 21:11 DEBUG  CommonBackend: locale=es_CL.UTF-8
07-21 21:11 DEBUG  WindowsBackend: total_memory_mb=1015.23046875
07-21 21:11 DEBUG  CommonBackend: Searching ISOs on USB devices
07-21 21:11 DEBUG  CommonBackend: Searching for local CDs
07-21 21:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl83.tmp is a valid Ubuntu CD
07-21 21:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl83.tmp\casper\filesystem.squashfs
07-21 21:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl83.tmp is a valid Ubuntu CD
07-21 21:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl83.tmp\casper\filesystem.squashfs
07-21 21:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl83.tmp is a valid Kubuntu CD
07-21 21:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl83.tmp\casper\filesystem.squashfs
07-21 21:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl83.tmp is a valid Kubuntu CD
07-21 21:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl83.tmp\casper\filesystem.squashfs
07-21 21:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl83.tmp is a valid Xubuntu CD
07-21 21:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl83.tmp\casper\filesystem.squashfs
07-21 21:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl83.tmp is a valid Xubuntu CD
07-21 21:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl83.tmp\casper\filesystem.squashfs
07-21 21:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl83.tmp is a valid Mythbuntu CD
07-21 21:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl83.tmp\casper\filesystem.squashfs
07-21 21:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl83.tmp is a valid Mythbuntu CD
07-21 21:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Felipe\CONFIG~1\Temp\pyl83.tmp\casper\filesystem.squashfs
07-21 21:11 INFO   root: Running the installer...

```What can I do?

---

