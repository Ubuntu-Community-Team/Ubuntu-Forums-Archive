---
title: "Probelm in installing ubuntu"
date: 2011-11-05
forum: Hardware
---

### Post by memaieln on 2011-11-05
when i download Ubuntu on my windows using windows installer wubi
when the download finish it pops up an error message that an error occurred we cannot find the file specified for more information see the log file and give a path of text document when i open it there a lot of thing that i could not understand can anyone help me.

here is the log file




```
11-05 01:30 INFO   root: === wubi 11.10 rev245 ===
11-05 01:30 DEBUG  root: Logfile is c:\users\mohmed\appdata\local\temp\wubi-11.10-rev245.log
11-05 01:30 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\mohmed\\Downloads\\Programs\\wubi.exe"']
11-05 01:30 DEBUG  CommonBackend: data_dir=C:\Users\mohmed\AppData\Local\Temp\pyl8D60.tmp\data
11-05 01:30 DEBUG  WindowsBackend: 7z=C:\Users\mohmed\AppData\Local\Temp\pyl8D60.tmp\bin\7z.exe
11-05 01:30 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
11-05 01:30 DEBUG  CommonBackend: Fetching basic info...
11-05 01:30 DEBUG  CommonBackend: original_exe=C:\Users\mohmed\Downloads\Programs\wubi.exe
11-05 01:30 DEBUG  CommonBackend: platform=win32
11-05 01:30 DEBUG  CommonBackend: osname=nt
11-05 01:30 DEBUG  CommonBackend: language=ar_EG
11-05 01:30 DEBUG  CommonBackend: encoding=cp1256
11-05 01:30 DEBUG  WindowsBackend: arch=amd64
11-05 01:30 DEBUG  CommonBackend: Parsing isolist=C:\Users\mohmed\AppData\Local\Temp\pyl8D60.tmp\data\isolist.ini
11-05 01:30 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-05 01:30 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-05 01:30 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-05 01:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-05 01:30 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-05 01:30 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-05 01:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-05 01:30 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-05 01:30 DEBUG  WindowsBackend: Fetching host info...
11-05 01:30 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-05 01:30 DEBUG  WindowsBackend: windows version=vista
11-05 01:30 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
11-05 01:30 DEBUG  WindowsBackend: windows_sp=None
11-05 01:30 DEBUG  WindowsBackend: windows_build=7601
11-05 01:30 DEBUG  WindowsBackend: gmt=2
11-05 01:30 DEBUG  WindowsBackend: country=EG
11-05 01:30 DEBUG  WindowsBackend: timezone=Africa/Cairo
11-05 01:30 DEBUG  WindowsBackend: windows_username=mohmed
11-05 01:30 DEBUG  WindowsBackend: user_full_name=mohmed
11-05 01:30 DEBUG  WindowsBackend: user_directory=C:\Users\mohmed
11-05 01:30 DEBUG  WindowsBackend: windows_language_code=1025
11-05 01:30 DEBUG  WindowsBackend: windows_language=Arabic
11-05 01:30 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 480  @ 2.67GHz
11-05 01:30 DEBUG  WindowsBackend: bootloader=vista
11-05 01:30 DEBUG  WindowsBackend: system_drive=Drive(C: hd 101751.414063 mb free ntfs)
11-05 01:30 DEBUG  WindowsBackend: drive=Drive(C: hd 101751.414063 mb free ntfs)
11-05 01:30 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
11-05 01:30 DEBUG  WindowsBackend: drive=Drive(M: hd 436277.0 mb free ntfs)
11-05 01:30 DEBUG  WindowsBackend: uninstaller_path=None
11-05 01:30 DEBUG  WindowsBackend: previous_target_dir=None
11-05 01:30 DEBUG  WindowsBackend: previous_distro_name=None
11-05 01:30 DEBUG  WindowsBackend: keyboard_id=67699721
11-05 01:30 DEBUG  WindowsBackend: keyboard_layout=us
11-05 01:30 DEBUG  WindowsBackend: keyboard_variant=
11-05 01:30 DEBUG  CommonBackend: python locale=('ar_EG', 'cp1256')
11-05 01:30 DEBUG  CommonBackend: locale=ar_EG.UTF-8
11-05 01:30 DEBUG  WindowsBackend: total_memory_mb=3766.70703125
11-05 01:30 DEBUG  CommonBackend: Searching ISOs on USB devices
11-05 01:30 DEBUG  CommonBackend: Searching for local CDs
11-05 01:30 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pyl8D60.tmp is a valid Ubuntu CD
11-05 01:30 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pyl8D60.tmp\casper\filesystem.squashfs
11-05 01:30 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pyl8D60.tmp is a valid Ubuntu CD
11-05 01:30 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pyl8D60.tmp\casper\filesystem.squashfs
11-05 01:30 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pyl8D60.tmp is a valid Kubuntu CD
11-05 01:30 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pyl8D60.tmp\casper\filesystem.squashfs
11-05 01:30 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pyl8D60.tmp is a valid Kubuntu CD
11-05 01:30 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pyl8D60.tmp\casper\filesystem.squashfs
11-05 01:30 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pyl8D60.tmp is a valid Xubuntu CD
11-05 01:30 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pyl8D60.tmp\casper\filesystem.squashfs
11-05 01:30 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pyl8D60.tmp is a valid Xubuntu CD
11-05 01:30 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pyl8D60.tmp\casper\filesystem.squashfs
11-05 01:30 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pyl8D60.tmp is a valid Mythbuntu CD
11-05 01:30 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pyl8D60.tmp\casper\filesystem.squashfs
11-05 01:30 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pyl8D60.tmp is a valid Mythbuntu CD
11-05 01:30 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pyl8D60.tmp\casper\filesystem.squashfs
11-05 01:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-05 01:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 01:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-05 01:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 01:30 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-05 01:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 01:30 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-05 01:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 01:30 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-05 01:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 01:30 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-05 01:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 01:30 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-05 01:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 01:30 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-05 01:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 01:30 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
11-05 01:30 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 01:30 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
11-05 01:30 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 01:30 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
11-05 01:30 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 01:30 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
11-05 01:30 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 01:30 DEBUG  Distro:   checking whether M:\ is a valid Xubuntu CD
11-05 01:30 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 01:30 DEBUG  Distro:   checking whether M:\ is a valid Xubuntu CD
11-05 01:30 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 01:30 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
11-05 01:30 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 01:30 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
11-05 01:30 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 01:30 INFO   root: Running the installer...
11-05 01:30 DEBUG  WindowsFrontend: __init__...
11-05 01:30 DEBUG  WindowsFrontend: on_init...
11-05 01:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\mohmed\AppData\Local\Temp\pyl8D60.tmp\translations, languages=['ar_EG', 'ar']
11-05 01:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\mohmed\AppData\Local\Temp\pyl8D60.tmp\translations, languages=['ar_EG', 'ar']
11-05 01:31 DEBUG  WinuiInstallationPage: target_drive=M:, installation_size=20000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=mohamed
11-05 01:31 INFO   root: Received settings
11-05 01:31 DEBUG  CommonBackend: Searching for local CD
11-05 01:31 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pyl8D60.tmp is a valid Ubuntu CD
11-05 01:31 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pyl8D60.tmp\casper\filesystem.squashfs
11-05 01:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-05 01:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 01:31 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
11-05 01:31 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 01:31 DEBUG  CommonBackend: Searching for local ISO
11-05 01:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\mohmed\AppData\Local\Temp\pyl8D60.tmp\translations, languages=['en_US', 'en']
11-05 01:31 DEBUG  TaskList: # Running tasklist...
11-05 01:31 DEBUG  TaskList: ## Running select_target_dir...
11-05 01:31 INFO   WindowsBackend: Installing into M:\ubuntu
11-05 01:31 DEBUG  TaskList: ## Finished select_target_dir
11-05 01:31 DEBUG  TaskList: ## Running create_dir_structure...
11-05 01:31 DEBUG  CommonBackend: Creating dir M:\ubuntu
11-05 01:31 DEBUG  CommonBackend: Creating dir M:\ubuntu\disks
11-05 01:31 DEBUG  CommonBackend: Creating dir M:\ubuntu\install
11-05 01:31 DEBUG  CommonBackend: Creating dir M:\ubuntu\install\boot
11-05 01:31 DEBUG  CommonBackend: Creating dir M:\ubuntu\disks\boot
11-05 01:31 DEBUG  CommonBackend: Creating dir M:\ubuntu\disks\boot\grub
11-05 01:31 DEBUG  CommonBackend: Creating dir M:\ubuntu\install\boot\grub
11-05 01:31 DEBUG  TaskList: ## Finished create_dir_structure
11-05 01:31 DEBUG  TaskList: ## Running create_uninstaller...
11-05 01:31 DEBUG  WindowsBackend: Copying uninstaller C:\Users\mohmed\Downloads\Programs\wubi.exe -> M:\ubuntu\uninstall-wubi.exe
11-05 01:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString M:\ubuntu\uninstall-wubi.exe
11-05 01:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir M:\ubuntu
11-05 01:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
11-05 01:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon M:\ubuntu\Ubuntu.ico
11-05 01:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
11-05 01:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
11-05 01:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com]("http://www.ubuntu.com/")
11-05 01:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
11-05 01:31 DEBUG  TaskList: ## Finished create_uninstaller
11-05 01:31 DEBUG  TaskList: ## Running create_preseed_diskimage...
11-05 01:31 DEBUG  TaskList: ## Finished create_preseed_diskimage
11-05 01:31 DEBUG  TaskList: ## Running get_diskimage...
11-05 01:31 DEBUG  TaskList: New task download
11-05 01:31 DEBUG  TaskList: ### Running download...
11-05 01:31 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > M:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
11-05 01:31 DEBUG  downloader: Download start filename=M:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
11-05 02:47 INFO   WindowsFrontend: Operation cancelled
11-05 02:47 INFO   WindowsFrontend: Cancelled cancellation, resuming
11-05 05:51 INFO   root: === wubi 11.10 rev245 ===
11-05 05:51 DEBUG  root: Logfile is c:\users\mohmed\appdata\local\temp\wubi-11.10-rev245.log
11-05 05:51 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\mohmed\\Downloads\\Programs\\wubi.exe"']
11-05 05:51 DEBUG  CommonBackend: data_dir=C:\Users\mohmed\AppData\Local\Temp\pylBB91.tmp\data
11-05 05:51 DEBUG  WindowsBackend: 7z=C:\Users\mohmed\AppData\Local\Temp\pylBB91.tmp\bin\7z.exe
11-05 05:51 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
11-05 05:51 DEBUG  CommonBackend: Fetching basic info...
11-05 05:51 DEBUG  CommonBackend: original_exe=C:\Users\mohmed\Downloads\Programs\wubi.exe
11-05 05:51 DEBUG  CommonBackend: platform=win32
11-05 05:51 DEBUG  CommonBackend: osname=nt
11-05 05:51 DEBUG  CommonBackend: language=ar_EG
11-05 05:51 DEBUG  CommonBackend: encoding=cp1256
11-05 05:51 DEBUG  WindowsBackend: arch=amd64
11-05 05:51 DEBUG  CommonBackend: Parsing isolist=C:\Users\mohmed\AppData\Local\Temp\pylBB91.tmp\data\isolist.ini
11-05 05:51 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-05 05:51 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-05 05:51 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-05 05:51 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-05 05:51 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-05 05:51 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-05 05:51 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-05 05:51 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-05 05:51 DEBUG  WindowsBackend: Fetching host info...
11-05 05:51 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-05 05:51 DEBUG  WindowsBackend: windows version=vista
11-05 05:51 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
11-05 05:51 DEBUG  WindowsBackend: windows_sp=None
11-05 05:51 DEBUG  WindowsBackend: windows_build=7601
11-05 05:51 DEBUG  WindowsBackend: gmt=2
11-05 05:51 DEBUG  WindowsBackend: country=EG
11-05 05:51 DEBUG  WindowsBackend: timezone=Africa/Cairo
11-05 05:51 DEBUG  WindowsBackend: windows_username=mohmed
11-05 05:51 DEBUG  WindowsBackend: user_full_name=mohmed
11-05 05:51 DEBUG  WindowsBackend: user_directory=C:\Users\mohmed
11-05 05:51 DEBUG  WindowsBackend: windows_language_code=1025
11-05 05:51 DEBUG  WindowsBackend: windows_language=Arabic
11-05 05:51 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 480  @ 2.67GHz
11-05 05:51 DEBUG  WindowsBackend: bootloader=vista
11-05 05:51 DEBUG  WindowsBackend: system_drive=Drive(C: hd 101653.949219 mb free ntfs)
11-05 05:51 DEBUG  WindowsBackend: drive=Drive(C: hd 101653.949219 mb free ntfs)
11-05 05:51 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
11-05 05:51 DEBUG  WindowsBackend: drive=Drive(M: hd 436277.5 mb free ntfs)
11-05 05:51 DEBUG  WindowsBackend: uninstaller_path=M:\ubuntu\uninstall-wubi.exe
11-05 05:51 DEBUG  WindowsBackend: previous_target_dir=M:\ubuntu
11-05 05:51 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
11-05 05:51 DEBUG  WindowsBackend: keyboard_id=67699721
11-05 05:51 DEBUG  WindowsBackend: keyboard_layout=us
11-05 05:51 DEBUG  WindowsBackend: keyboard_variant=
11-05 05:51 DEBUG  CommonBackend: python locale=('ar_EG', 'cp1256')
11-05 05:51 DEBUG  CommonBackend: locale=ar_EG.UTF-8
11-05 05:51 DEBUG  WindowsBackend: total_memory_mb=3766.70703125
11-05 05:51 DEBUG  CommonBackend: Searching ISOs on USB devices
11-05 05:51 DEBUG  CommonBackend: Searching for local CDs
11-05 05:51 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pylBB91.tmp is a valid Ubuntu CD
11-05 05:51 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pylBB91.tmp\casper\filesystem.squashfs
11-05 05:51 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pylBB91.tmp is a valid Ubuntu CD
11-05 05:51 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pylBB91.tmp\casper\filesystem.squashfs
11-05 05:51 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pylBB91.tmp is a valid Kubuntu CD
11-05 05:51 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pylBB91.tmp\casper\filesystem.squashfs
11-05 05:51 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pylBB91.tmp is a valid Kubuntu CD
11-05 05:51 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pylBB91.tmp\casper\filesystem.squashfs
11-05 05:51 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pylBB91.tmp is a valid Xubuntu CD
11-05 05:51 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pylBB91.tmp\casper\filesystem.squashfs
11-05 05:51 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pylBB91.tmp is a valid Xubuntu CD
11-05 05:51 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pylBB91.tmp\casper\filesystem.squashfs
11-05 05:51 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pylBB91.tmp is a valid Mythbuntu CD
11-05 05:51 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pylBB91.tmp\casper\filesystem.squashfs
11-05 05:51 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pylBB91.tmp is a valid Mythbuntu CD
11-05 05:51 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pylBB91.tmp\casper\filesystem.squashfs
11-05 05:51 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-05 05:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 05:51 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-05 05:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 05:51 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-05 05:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 05:51 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-05 05:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 05:51 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-05 05:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 05:51 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-05 05:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 05:51 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-05 05:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 05:51 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-05 05:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 05:51 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
11-05 05:51 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 05:51 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
11-05 05:51 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 05:51 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
11-05 05:51 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 05:51 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
11-05 05:51 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 05:51 DEBUG  Distro:   checking whether M:\ is a valid Xubuntu CD
11-05 05:51 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 05:51 DEBUG  Distro:   checking whether M:\ is a valid Xubuntu CD
11-05 05:51 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 05:51 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
11-05 05:51 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 05:51 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
11-05 05:51 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 05:51 INFO   root: Running the installer...
11-05 05:51 DEBUG  WindowsFrontend: __init__...
11-05 05:51 DEBUG  WindowsFrontend: on_init...
11-05 05:51 INFO   WinuiPage: appname=wubi, localedir=C:\Users\mohmed\AppData\Local\Temp\pylBB91.tmp\translations, languages=['ar_EG', 'ar']
11-05 05:51 INFO   WinuiPage: appname=wubi, localedir=C:\Users\mohmed\AppData\Local\Temp\pylBB91.tmp\translations, languages=['ar_EG', 'ar']
11-05 05:51 DEBUG  WindowsFrontend: frontend.on_quit
11-05 05:51 DEBUG  root: application.on_quit
11-05 05:51 INFO   root: sys.exit
11-05 05:51 INFO   root: === wubi 11.10 rev245 ===
11-05 05:51 DEBUG  root: Logfile is c:\users\mohmed\appdata\local\temp\wubi-11.10-rev245.log
11-05 05:51 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\mohmed\\Downloads\\Programs\\wubi.exe"']
11-05 05:51 DEBUG  CommonBackend: data_dir=C:\Users\mohmed\AppData\Local\Temp\pylD93F.tmp\data
11-05 05:51 DEBUG  WindowsBackend: 7z=C:\Users\mohmed\AppData\Local\Temp\pylD93F.tmp\bin\7z.exe
11-05 05:51 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
11-05 05:51 DEBUG  CommonBackend: Fetching basic info...
11-05 05:51 DEBUG  CommonBackend: original_exe=C:\Users\mohmed\Downloads\Programs\wubi.exe
11-05 05:51 DEBUG  CommonBackend: platform=win32
11-05 05:51 DEBUG  CommonBackend: osname=nt
11-05 05:51 DEBUG  CommonBackend: language=ar_EG
11-05 05:51 DEBUG  CommonBackend: encoding=cp1256
11-05 05:51 DEBUG  WindowsBackend: arch=amd64
11-05 05:51 DEBUG  CommonBackend: Parsing isolist=C:\Users\mohmed\AppData\Local\Temp\pylD93F.tmp\data\isolist.ini
11-05 05:51 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-05 05:51 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-05 05:51 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-05 05:51 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-05 05:51 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-05 05:51 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-05 05:51 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-05 05:51 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-05 05:51 DEBUG  WindowsBackend: Fetching host info...
11-05 05:51 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-05 05:51 DEBUG  WindowsBackend: windows version=vista
11-05 05:51 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
11-05 05:51 DEBUG  WindowsBackend: windows_sp=None
11-05 05:51 DEBUG  WindowsBackend: windows_build=7601
11-05 05:51 DEBUG  WindowsBackend: gmt=2
11-05 05:51 DEBUG  WindowsBackend: country=EG
11-05 05:51 DEBUG  WindowsBackend: timezone=Africa/Cairo
11-05 05:51 DEBUG  WindowsBackend: windows_username=mohmed
11-05 05:51 DEBUG  WindowsBackend: user_full_name=mohmed
11-05 05:51 DEBUG  WindowsBackend: user_directory=C:\Users\mohmed
11-05 05:51 DEBUG  WindowsBackend: windows_language_code=1025
11-05 05:51 DEBUG  WindowsBackend: windows_language=Arabic
11-05 05:51 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 480  @ 2.67GHz
11-05 05:51 DEBUG  WindowsBackend: bootloader=vista
11-05 05:51 DEBUG  WindowsBackend: system_drive=Drive(C: hd 101653.378906 mb free ntfs)
11-05 05:51 DEBUG  WindowsBackend: drive=Drive(C: hd 101653.378906 mb free ntfs)
11-05 05:51 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
11-05 05:51 DEBUG  WindowsBackend: drive=Drive(M: hd 436277.5 mb free ntfs)
11-05 05:51 DEBUG  WindowsBackend: uninstaller_path=M:\ubuntu\uninstall-wubi.exe
11-05 05:51 DEBUG  WindowsBackend: previous_target_dir=M:\ubuntu
11-05 05:51 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
11-05 05:51 DEBUG  WindowsBackend: keyboard_id=67699721
11-05 05:51 DEBUG  WindowsBackend: keyboard_layout=us
11-05 05:51 DEBUG  WindowsBackend: keyboard_variant=
11-05 05:51 DEBUG  CommonBackend: python locale=('ar_EG', 'cp1256')
11-05 05:51 DEBUG  CommonBackend: locale=ar_EG.UTF-8
11-05 05:51 DEBUG  WindowsBackend: total_memory_mb=3766.70703125
11-05 05:51 DEBUG  CommonBackend: Searching ISOs on USB devices
11-05 05:51 DEBUG  CommonBackend: Searching for local CDs
11-05 05:51 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pylD93F.tmp is a valid Ubuntu CD
11-05 05:51 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pylD93F.tmp\casper\filesystem.squashfs
11-05 05:51 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pylD93F.tmp is a valid Ubuntu CD
11-05 05:51 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pylD93F.tmp\casper\filesystem.squashfs
11-05 05:51 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pylD93F.tmp is a valid Kubuntu CD
11-05 05:51 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pylD93F.tmp\casper\filesystem.squashfs
11-05 05:51 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pylD93F.tmp is a valid Kubuntu CD
11-05 05:51 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pylD93F.tmp\casper\filesystem.squashfs
11-05 05:51 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pylD93F.tmp is a valid Xubuntu CD
11-05 05:51 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pylD93F.tmp\casper\filesystem.squashfs
11-05 05:51 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pylD93F.tmp is a valid Xubuntu CD
11-05 05:51 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pylD93F.tmp\casper\filesystem.squashfs
11-05 05:51 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pylD93F.tmp is a valid Mythbuntu CD
11-05 05:51 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pylD93F.tmp\casper\filesystem.squashfs
11-05 05:51 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pylD93F.tmp is a valid Mythbuntu CD
11-05 05:51 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pylD93F.tmp\casper\filesystem.squashfs
11-05 05:51 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-05 05:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 05:51 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-05 05:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 05:51 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-05 05:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 05:51 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-05 05:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 05:51 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-05 05:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 05:51 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-05 05:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 05:51 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-05 05:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 05:51 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-05 05:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 05:51 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
11-05 05:51 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 05:51 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
11-05 05:51 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 05:51 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
11-05 05:51 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 05:51 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
11-05 05:51 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 05:51 DEBUG  Distro:   checking whether M:\ is a valid Xubuntu CD
11-05 05:51 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 05:51 DEBUG  Distro:   checking whether M:\ is a valid Xubuntu CD
11-05 05:51 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 05:51 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
11-05 05:51 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 05:51 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
11-05 05:51 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 05:51 INFO   root: Running the installer...
11-05 05:51 DEBUG  WindowsFrontend: __init__...
11-05 05:51 DEBUG  WindowsFrontend: on_init...
11-05 05:51 INFO   WinuiPage: appname=wubi, localedir=C:\Users\mohmed\AppData\Local\Temp\pylD93F.tmp\translations, languages=['ar_EG', 'ar']
11-05 05:51 INFO   WinuiPage: appname=wubi, localedir=C:\Users\mohmed\AppData\Local\Temp\pylD93F.tmp\translations, languages=['ar_EG', 'ar']
11-05 05:51 DEBUG  WinuiInstallationPage: target_drive=M:, installation_size=20000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=mohamed
11-05 05:51 INFO   root: Received settings
11-05 05:51 DEBUG  CommonBackend: Searching for local CD
11-05 05:51 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pylD93F.tmp is a valid Ubuntu CD
11-05 05:51 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pylD93F.tmp\casper\filesystem.squashfs
11-05 05:51 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-05 05:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 05:51 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
11-05 05:51 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 05:51 DEBUG  CommonBackend: Searching for local ISO
11-05 05:51 INFO   WinuiPage: appname=wubi, localedir=C:\Users\mohmed\AppData\Local\Temp\pylD93F.tmp\translations, languages=['en_US', 'en']
11-05 05:51 DEBUG  TaskList: # Running tasklist...
11-05 05:51 DEBUG  TaskList: ## Running select_target_dir...
11-05 05:51 INFO   WindowsBackend: Installing into M:\ubuntu
11-05 05:51 DEBUG  TaskList: ## Finished select_target_dir
11-05 05:51 DEBUG  TaskList: ## Running create_dir_structure...
11-05 05:51 DEBUG  CommonBackend: Creating dir M:\ubuntu
11-05 05:51 DEBUG  CommonBackend: Creating dir M:\ubuntu\disks
11-05 05:51 DEBUG  CommonBackend: Creating dir M:\ubuntu\install
11-05 05:51 DEBUG  CommonBackend: Creating dir M:\ubuntu\install\boot
11-05 05:51 DEBUG  CommonBackend: Creating dir M:\ubuntu\disks\boot
11-05 05:51 DEBUG  CommonBackend: Creating dir M:\ubuntu\disks\boot\grub
11-05 05:51 DEBUG  CommonBackend: Creating dir M:\ubuntu\install\boot\grub
11-05 05:51 DEBUG  TaskList: ## Finished create_dir_structure
11-05 05:51 DEBUG  TaskList: ## Running create_uninstaller...
11-05 05:51 DEBUG  WindowsBackend: Copying uninstaller C:\Users\mohmed\Downloads\Programs\wubi.exe -> M:\ubuntu\uninstall-wubi.exe
11-05 05:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString M:\ubuntu\uninstall-wubi.exe
11-05 05:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir M:\ubuntu
11-05 05:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
11-05 05:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon M:\ubuntu\Ubuntu.ico
11-05 05:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
11-05 05:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
11-05 05:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com]("http://www.ubuntu.com/")
11-05 05:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
11-05 05:51 DEBUG  TaskList: ## Finished create_uninstaller
11-05 05:51 DEBUG  TaskList: ## Running create_preseed_diskimage...
11-05 05:51 DEBUG  TaskList: ## Finished create_preseed_diskimage
11-05 05:51 DEBUG  TaskList: ## Running get_diskimage...
11-05 05:51 DEBUG  TaskList: New task download
11-05 05:51 DEBUG  TaskList: ### Running download...
11-05 05:51 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > M:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
11-05 05:52 DEBUG  downloader: Download start filename=M:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
11-05 08:53 INFO   WindowsFrontend: Operation cancelled
11-05 08:53 DEBUG  WindowsFrontend: frontend.quit
11-05 08:53 DEBUG  WindowsFrontend: frontend.on_quit
11-05 08:53 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
11-05 08:53 DEBUG  TaskList: # Cancelling tasklist
11-05 08:54 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
11-05 08:54 DEBUG  root: application.on_quit
11-05 08:54 DEBUG  root: Forceful exit
11-05 08:54 INFO   root: sys.exit
11-05 08:54 INFO   root: === wubi 11.10 rev245 ===
11-05 08:54 DEBUG  root: Logfile is c:\users\mohmed\appdata\local\temp\wubi-11.10-rev245.log
11-05 08:54 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\mohmed\\Downloads\\Programs\\wubi.exe"']
11-05 08:54 DEBUG  CommonBackend: data_dir=C:\Users\mohmed\AppData\Local\Temp\pyl406D.tmp\data
11-05 08:54 DEBUG  WindowsBackend: 7z=C:\Users\mohmed\AppData\Local\Temp\pyl406D.tmp\bin\7z.exe
11-05 08:54 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
11-05 08:54 DEBUG  CommonBackend: Fetching basic info...
11-05 08:54 DEBUG  CommonBackend: original_exe=C:\Users\mohmed\Downloads\Programs\wubi.exe
11-05 08:54 DEBUG  CommonBackend: platform=win32
11-05 08:54 DEBUG  CommonBackend: osname=nt
11-05 08:54 DEBUG  CommonBackend: language=ar_EG
11-05 08:54 DEBUG  CommonBackend: encoding=cp1256
11-05 08:54 DEBUG  WindowsBackend: arch=amd64
11-05 08:54 DEBUG  CommonBackend: Parsing isolist=C:\Users\mohmed\AppData\Local\Temp\pyl406D.tmp\data\isolist.ini
11-05 08:54 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-05 08:54 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-05 08:54 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-05 08:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-05 08:54 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-05 08:54 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-05 08:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-05 08:54 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-05 08:54 DEBUG  WindowsBackend: Fetching host info...
11-05 08:54 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-05 08:54 DEBUG  WindowsBackend: windows version=vista
11-05 08:54 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
11-05 08:54 DEBUG  WindowsBackend: windows_sp=None
11-05 08:54 DEBUG  WindowsBackend: windows_build=7601
11-05 08:54 DEBUG  WindowsBackend: gmt=2
11-05 08:54 DEBUG  WindowsBackend: country=EG
11-05 08:54 DEBUG  WindowsBackend: timezone=Africa/Cairo
11-05 08:54 DEBUG  WindowsBackend: windows_username=mohmed
11-05 08:54 DEBUG  WindowsBackend: user_full_name=mohmed
11-05 08:54 DEBUG  WindowsBackend: user_directory=C:\Users\mohmed
11-05 08:54 DEBUG  WindowsBackend: windows_language_code=1025
11-05 08:54 DEBUG  WindowsBackend: windows_language=Arabic
11-05 08:54 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 480  @ 2.67GHz
11-05 08:54 DEBUG  WindowsBackend: bootloader=vista
11-05 08:54 DEBUG  WindowsBackend: system_drive=Drive(C: hd 101653.402344 mb free ntfs)
11-05 08:54 DEBUG  WindowsBackend: drive=Drive(C: hd 101653.402344 mb free ntfs)
11-05 08:54 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
11-05 08:54 DEBUG  WindowsBackend: drive=Drive(M: hd 436172.847656 mb free ntfs)
11-05 08:54 DEBUG  WindowsBackend: uninstaller_path=M:\ubuntu\uninstall-wubi.exe
11-05 08:54 DEBUG  WindowsBackend: previous_target_dir=M:\ubuntu
11-05 08:54 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
11-05 08:54 DEBUG  WindowsBackend: keyboard_id=67699721
11-05 08:54 DEBUG  WindowsBackend: keyboard_layout=us
11-05 08:54 DEBUG  WindowsBackend: keyboard_variant=
11-05 08:54 DEBUG  CommonBackend: python locale=('ar_EG', 'cp1256')
11-05 08:54 DEBUG  CommonBackend: locale=ar_EG.UTF-8
11-05 08:54 DEBUG  WindowsBackend: total_memory_mb=3766.70703125
11-05 08:54 DEBUG  CommonBackend: Searching ISOs on USB devices
11-05 08:54 DEBUG  CommonBackend: Searching for local CDs
11-05 08:54 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pyl406D.tmp is a valid Ubuntu CD
11-05 08:54 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pyl406D.tmp\casper\filesystem.squashfs
11-05 08:54 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pyl406D.tmp is a valid Ubuntu CD
11-05 08:54 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pyl406D.tmp\casper\filesystem.squashfs
11-05 08:54 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pyl406D.tmp is a valid Kubuntu CD
11-05 08:54 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pyl406D.tmp\casper\filesystem.squashfs
11-05 08:54 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pyl406D.tmp is a valid Kubuntu CD
11-05 08:54 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pyl406D.tmp\casper\filesystem.squashfs
11-05 08:54 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pyl406D.tmp is a valid Xubuntu CD
11-05 08:54 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pyl406D.tmp\casper\filesystem.squashfs
11-05 08:54 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pyl406D.tmp is a valid Xubuntu CD
11-05 08:54 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pyl406D.tmp\casper\filesystem.squashfs
11-05 08:54 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pyl406D.tmp is a valid Mythbuntu CD
11-05 08:54 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pyl406D.tmp\casper\filesystem.squashfs
11-05 08:54 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pyl406D.tmp is a valid Mythbuntu CD
11-05 08:54 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pyl406D.tmp\casper\filesystem.squashfs
11-05 08:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-05 08:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 08:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-05 08:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 08:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-05 08:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 08:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-05 08:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 08:54 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-05 08:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 08:54 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-05 08:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 08:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-05 08:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 08:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-05 08:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 08:54 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
11-05 08:54 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 08:54 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
11-05 08:54 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 08:54 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
11-05 08:54 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 08:54 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
11-05 08:54 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 08:54 DEBUG  Distro:   checking whether M:\ is a valid Xubuntu CD
11-05 08:54 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 08:54 DEBUG  Distro:   checking whether M:\ is a valid Xubuntu CD
11-05 08:54 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 08:54 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
11-05 08:54 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 08:54 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
11-05 08:54 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 08:54 INFO   root: Already installed, running the uninstaller...
11-05 08:54 INFO   root: Running the uninstaller...
11-05 08:54 INFO   CommonBackend: This is the uninstaller running
11-05 08:54 DEBUG  WindowsFrontend: __init__...
11-05 08:54 DEBUG  WindowsFrontend: on_init...
11-05 08:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\mohmed\AppData\Local\Temp\pyl406D.tmp\translations, languages=['ar_EG', 'ar']
11-05 08:54 INFO   root: Received settings
11-05 08:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\mohmed\AppData\Local\Temp\pyl406D.tmp\translations, languages=['ar_EG', 'ar']
11-05 08:54 DEBUG  TaskList: # Running tasklist...
11-05 08:54 DEBUG  TaskList: ## Running &#1571;&#1586;&#1604; &#1605;&#1583;&#1582;&#1604;&#1577; &#1605;&#1581;&#1605;&#1604; &#1575;&#1604;&#1573;&#1602;&#1604;&#1575;&#1593;...
11-05 08:54 DEBUG  WindowsBackend: Could not find bcd id
11-05 08:54 DEBUG  WindowsBackend: undo_bootini C:
11-05 08:54 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 101653.402344 mb free ntfs)
11-05 08:54 DEBUG  WindowsBackend: undo_bootini M:
11-05 08:54 DEBUG  WindowsBackend: undo_configsys Drive(M: hd 436172.847656 mb free ntfs)
11-05 08:54 DEBUG  TaskList: ## Finished &#1571;&#1586;&#1604; &#1605;&#1583;&#1582;&#1604;&#1577; &#1605;&#1581;&#1605;&#1604; &#1575;&#1604;&#1573;&#1602;&#1604;&#1575;&#1593;
11-05 08:54 DEBUG  TaskList: ## Running &#1571;&#1586;&#1604; &#1575;&#1604;&#1583;&#1604;&#1610;&#1604; &#1575;&#1604;&#1607;&#1583;&#1601;...
11-05 08:54 DEBUG  CommonBackend: Deleting M:\ubuntu
11-05 08:54 DEBUG  TaskList: ## Finished &#1571;&#1586;&#1604; &#1575;&#1604;&#1583;&#1604;&#1610;&#1604; &#1575;&#1604;&#1607;&#1583;&#1601;
11-05 08:54 DEBUG  TaskList: ## Running &#1571;&#1586;&#1604; &#1605;&#1601;&#1578;&#1575;&#1581; &#1575;&#1604;&#1605;&#1590;&#1576;&#1591;&#1577;...
11-05 08:54 DEBUG  TaskList: ## Finished &#1571;&#1586;&#1604; &#1605;&#1601;&#1578;&#1575;&#1581; &#1575;&#1604;&#1605;&#1590;&#1576;&#1591;&#1577;
11-05 08:54 DEBUG  TaskList: # Finished tasklist
11-05 08:54 INFO   root: Almost finished uninstalling
11-05 08:54 INFO   root: Finished uninstallation
11-05 08:54 DEBUG  CommonBackend: Fetching basic info...
11-05 08:54 DEBUG  CommonBackend: original_exe=C:\Users\mohmed\Downloads\Programs\wubi.exe
11-05 08:54 DEBUG  CommonBackend: platform=win32
11-05 08:54 DEBUG  CommonBackend: osname=nt
11-05 08:54 DEBUG  WindowsBackend: arch=amd64
11-05 08:54 DEBUG  CommonBackend: Parsing isolist=C:\Users\mohmed\AppData\Local\Temp\pyl406D.tmp\data\isolist.ini
11-05 08:54 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-05 08:54 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-05 08:54 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-05 08:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-05 08:54 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-05 08:54 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-05 08:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-05 08:54 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-05 08:54 DEBUG  WindowsBackend: Fetching host info...
11-05 08:54 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-05 08:54 DEBUG  WindowsBackend: windows version=vista
11-05 08:54 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
11-05 08:54 DEBUG  WindowsBackend: windows_sp=None
11-05 08:54 DEBUG  WindowsBackend: windows_build=7601
11-05 08:54 DEBUG  WindowsBackend: gmt=2
11-05 08:54 DEBUG  WindowsBackend: country=EG
11-05 08:54 DEBUG  WindowsBackend: timezone=Africa/Cairo
11-05 08:54 DEBUG  WindowsBackend: windows_username=mohmed
11-05 08:54 DEBUG  WindowsBackend: user_full_name=mohmed
11-05 08:54 DEBUG  WindowsBackend: user_directory=C:\Users\mohmed
11-05 08:54 DEBUG  WindowsBackend: windows_language_code=1025
11-05 08:54 DEBUG  WindowsBackend: windows_language=Arabic
11-05 08:54 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 480  @ 2.67GHz
11-05 08:54 DEBUG  WindowsBackend: bootloader=vista
11-05 08:54 DEBUG  WindowsBackend: system_drive=Drive(C: hd 101653.390625 mb free ntfs)
11-05 08:54 DEBUG  WindowsBackend: drive=Drive(C: hd 101653.390625 mb free ntfs)
11-05 08:54 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
11-05 08:54 DEBUG  WindowsBackend: drive=Drive(M: hd 436277.5 mb free ntfs)
11-05 08:54 DEBUG  WindowsBackend: uninstaller_path=None
11-05 08:54 DEBUG  WindowsBackend: previous_target_dir=None
11-05 08:54 DEBUG  WindowsBackend: previous_distro_name=None
11-05 08:54 DEBUG  WindowsBackend: keyboard_id=67699721
11-05 08:54 DEBUG  WindowsBackend: keyboard_layout=us
11-05 08:54 DEBUG  WindowsBackend: keyboard_variant=
11-05 08:54 DEBUG  WindowsBackend: total_memory_mb=3766.70703125
11-05 08:54 DEBUG  CommonBackend: Searching ISOs on USB devices
11-05 08:54 DEBUG  CommonBackend: Searching for local CDs
11-05 08:54 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pyl406D.tmp is a valid Ubuntu CD
11-05 08:54 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pyl406D.tmp\casper\filesystem.squashfs
11-05 08:54 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pyl406D.tmp is a valid Ubuntu CD
11-05 08:54 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pyl406D.tmp\casper\filesystem.squashfs
11-05 08:54 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pyl406D.tmp is a valid Kubuntu CD
11-05 08:54 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pyl406D.tmp\casper\filesystem.squashfs
11-05 08:54 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pyl406D.tmp is a valid Kubuntu CD
11-05 08:54 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pyl406D.tmp\casper\filesystem.squashfs
11-05 08:54 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pyl406D.tmp is a valid Xubuntu CD
11-05 08:54 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pyl406D.tmp\casper\filesystem.squashfs
11-05 08:54 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pyl406D.tmp is a valid Xubuntu CD
11-05 08:54 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pyl406D.tmp\casper\filesystem.squashfs
11-05 08:54 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pyl406D.tmp is a valid Mythbuntu CD
11-05 08:54 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pyl406D.tmp\casper\filesystem.squashfs
11-05 08:54 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pyl406D.tmp is a valid Mythbuntu CD
11-05 08:54 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pyl406D.tmp\casper\filesystem.squashfs
11-05 08:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-05 08:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 08:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-05 08:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 08:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-05 08:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 08:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-05 08:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 08:54 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-05 08:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 08:54 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-05 08:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 08:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-05 08:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 08:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-05 08:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 08:54 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
11-05 08:54 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 08:54 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
11-05 08:54 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 08:54 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
11-05 08:54 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 08:54 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
11-05 08:54 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 08:54 DEBUG  Distro:   checking whether M:\ is a valid Xubuntu CD
11-05 08:54 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 08:54 DEBUG  Distro:   checking whether M:\ is a valid Xubuntu CD
11-05 08:54 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 08:54 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
11-05 08:54 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 08:54 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
11-05 08:54 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 08:54 INFO   root: Running the installer...
11-05 08:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\mohmed\AppData\Local\Temp\pyl406D.tmp\translations, languages=['ar_EG', 'ar']
11-05 08:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\mohmed\AppData\Local\Temp\pyl406D.tmp\translations, languages=['ar_EG', 'ar']
11-05 08:55 DEBUG  WinuiInstallationPage: target_drive=M:, installation_size=20000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=mohamed
11-05 08:55 INFO   root: Received settings
11-05 08:55 DEBUG  CommonBackend: Searching for local CD
11-05 08:55 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pyl406D.tmp is a valid Ubuntu CD
11-05 08:55 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pyl406D.tmp\casper\filesystem.squashfs
11-05 08:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-05 08:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 08:55 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
11-05 08:55 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 08:55 DEBUG  CommonBackend: Searching for local ISO
11-05 08:55 INFO   WinuiPage: appname=wubi, localedir=C:\Users\mohmed\AppData\Local\Temp\pyl406D.tmp\translations, languages=['en_US', 'en']
11-05 08:55 DEBUG  TaskList: # Running tasklist...
11-05 08:55 DEBUG  TaskList: ## Running select_target_dir...
11-05 08:55 INFO   WindowsBackend: Installing into M:\ubuntu
11-05 08:55 DEBUG  TaskList: ## Finished select_target_dir
11-05 08:55 DEBUG  TaskList: ## Running create_dir_structure...
11-05 08:55 DEBUG  CommonBackend: Creating dir M:\ubuntu
11-05 08:55 DEBUG  CommonBackend: Creating dir M:\ubuntu\disks
11-05 08:55 DEBUG  CommonBackend: Creating dir M:\ubuntu\install
11-05 08:55 DEBUG  CommonBackend: Creating dir M:\ubuntu\install\boot
11-05 08:55 DEBUG  CommonBackend: Creating dir M:\ubuntu\disks\boot
11-05 08:55 DEBUG  CommonBackend: Creating dir M:\ubuntu\disks\boot\grub
11-05 08:55 DEBUG  CommonBackend: Creating dir M:\ubuntu\install\boot\grub
11-05 08:55 DEBUG  TaskList: ## Finished create_dir_structure
11-05 08:55 DEBUG  TaskList: ## Running create_uninstaller...
11-05 08:55 DEBUG  WindowsBackend: Copying uninstaller C:\Users\mohmed\Downloads\Programs\wubi.exe -> M:\ubuntu\uninstall-wubi.exe
11-05 08:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString M:\ubuntu\uninstall-wubi.exe
11-05 08:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir M:\ubuntu
11-05 08:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
11-05 08:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon M:\ubuntu\Ubuntu.ico
11-05 08:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
11-05 08:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
11-05 08:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com]("http://www.ubuntu.com/")
11-05 08:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
11-05 08:55 DEBUG  TaskList: ## Finished create_uninstaller
11-05 08:55 DEBUG  TaskList: ## Running create_preseed_diskimage...
11-05 08:55 DEBUG  TaskList: ## Finished create_preseed_diskimage
11-05 08:55 DEBUG  TaskList: ## Running get_diskimage...
11-05 08:55 DEBUG  TaskList: New task download
11-05 08:55 DEBUG  TaskList: ### Running download...
11-05 08:55 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > M:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
11-05 08:55 DEBUG  downloader: Download start filename=M:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
11-05 09:32 INFO   root: === wubi 11.10 rev245 ===
11-05 09:32 DEBUG  root: Logfile is c:\users\mohmed\appdata\local\temp\wubi-11.10-rev245.log
11-05 09:32 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\mohmed\\Downloads\\Programs\\wubi.exe"']
11-05 09:32 DEBUG  CommonBackend: data_dir=C:\Users\mohmed\AppData\Local\Temp\pylFB8.tmp\data
11-05 09:32 DEBUG  WindowsBackend: 7z=C:\Users\mohmed\AppData\Local\Temp\pylFB8.tmp\bin\7z.exe
11-05 09:32 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
11-05 09:32 DEBUG  CommonBackend: Fetching basic info...
11-05 09:32 DEBUG  CommonBackend: original_exe=C:\Users\mohmed\Downloads\Programs\wubi.exe
11-05 09:32 DEBUG  CommonBackend: platform=win32
11-05 09:32 DEBUG  CommonBackend: osname=nt
11-05 09:32 DEBUG  CommonBackend: language=ar_EG
11-05 09:32 DEBUG  CommonBackend: encoding=cp1256
11-05 09:32 DEBUG  WindowsBackend: arch=amd64
11-05 09:32 DEBUG  CommonBackend: Parsing isolist=C:\Users\mohmed\AppData\Local\Temp\pylFB8.tmp\data\isolist.ini
11-05 09:32 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-05 09:32 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-05 09:32 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-05 09:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-05 09:32 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-05 09:32 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-05 09:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-05 09:32 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-05 09:32 DEBUG  WindowsBackend: Fetching host info...
11-05 09:32 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-05 09:32 DEBUG  WindowsBackend: windows version=vista
11-05 09:32 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
11-05 09:32 DEBUG  WindowsBackend: windows_sp=None
11-05 09:32 DEBUG  WindowsBackend: windows_build=7601
11-05 09:32 DEBUG  WindowsBackend: gmt=2
11-05 09:32 DEBUG  WindowsBackend: country=EG
11-05 09:32 DEBUG  WindowsBackend: timezone=Africa/Cairo
11-05 09:32 DEBUG  WindowsBackend: windows_username=mohmed
11-05 09:32 DEBUG  WindowsBackend: user_full_name=mohmed
11-05 09:32 DEBUG  WindowsBackend: user_directory=C:\Users\mohmed
11-05 09:32 DEBUG  WindowsBackend: windows_language_code=1025
11-05 09:32 DEBUG  WindowsBackend: windows_language=Arabic
11-05 09:32 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 480  @ 2.67GHz
11-05 09:32 DEBUG  WindowsBackend: bootloader=vista
11-05 09:32 DEBUG  WindowsBackend: system_drive=Drive(C: hd 101617.355469 mb free ntfs)
11-05 09:32 DEBUG  WindowsBackend: drive=Drive(C: hd 101617.355469 mb free ntfs)
11-05 09:32 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
11-05 09:32 DEBUG  WindowsBackend: drive=Drive(M: hd 436187.996094 mb free ntfs)
11-05 09:32 DEBUG  WindowsBackend: uninstaller_path=M:\ubuntu\uninstall-wubi.exe
11-05 09:32 DEBUG  WindowsBackend: previous_target_dir=M:\ubuntu
11-05 09:32 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
11-05 09:32 DEBUG  WindowsBackend: keyboard_id=67699721
11-05 09:32 DEBUG  WindowsBackend: keyboard_layout=us
11-05 09:32 DEBUG  WindowsBackend: keyboard_variant=
11-05 09:32 DEBUG  CommonBackend: python locale=('ar_EG', 'cp1256')
11-05 09:32 DEBUG  CommonBackend: locale=ar_EG.UTF-8
11-05 09:32 DEBUG  WindowsBackend: total_memory_mb=3766.70703125
11-05 09:32 DEBUG  CommonBackend: Searching ISOs on USB devices
11-05 09:32 DEBUG  CommonBackend: Searching for local CDs
11-05 09:32 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pylFB8.tmp is a valid Ubuntu CD
11-05 09:32 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pylFB8.tmp\casper\filesystem.squashfs
11-05 09:32 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pylFB8.tmp is a valid Ubuntu CD
11-05 09:32 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pylFB8.tmp\casper\filesystem.squashfs
11-05 09:32 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pylFB8.tmp is a valid Kubuntu CD
11-05 09:32 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pylFB8.tmp\casper\filesystem.squashfs
11-05 09:32 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pylFB8.tmp is a valid Kubuntu CD
11-05 09:32 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pylFB8.tmp\casper\filesystem.squashfs
11-05 09:32 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pylFB8.tmp is a valid Xubuntu CD
11-05 09:32 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pylFB8.tmp\casper\filesystem.squashfs
11-05 09:32 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pylFB8.tmp is a valid Xubuntu CD
11-05 09:32 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pylFB8.tmp\casper\filesystem.squashfs
11-05 09:32 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pylFB8.tmp is a valid Mythbuntu CD
11-05 09:32 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pylFB8.tmp\casper\filesystem.squashfs
11-05 09:32 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pylFB8.tmp is a valid Mythbuntu CD
11-05 09:32 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pylFB8.tmp\casper\filesystem.squashfs
11-05 09:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-05 09:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 09:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-05 09:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 09:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-05 09:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 09:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-05 09:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 09:32 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-05 09:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 09:32 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-05 09:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 09:32 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-05 09:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 09:32 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-05 09:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 09:32 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
11-05 09:32 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 09:32 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
11-05 09:32 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 09:32 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
11-05 09:32 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 09:32 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
11-05 09:32 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 09:32 DEBUG  Distro:   checking whether M:\ is a valid Xubuntu CD
11-05 09:32 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 09:32 DEBUG  Distro:   checking whether M:\ is a valid Xubuntu CD
11-05 09:32 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 09:32 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
11-05 09:32 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 09:32 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
11-05 09:32 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 09:32 INFO   root: Already installed, running the uninstaller...
11-05 09:32 INFO   root: Running the uninstaller...
11-05 09:32 INFO   CommonBackend: This is the uninstaller running
11-05 09:32 DEBUG  WindowsFrontend: __init__...
11-05 09:32 DEBUG  WindowsFrontend: on_init...
11-05 09:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\mohmed\AppData\Local\Temp\pylFB8.tmp\translations, languages=['ar_EG', 'ar']
11-05 09:32 INFO   root: Received settings
11-05 09:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\mohmed\AppData\Local\Temp\pylFB8.tmp\translations, languages=['ar_EG', 'ar']
11-05 09:32 DEBUG  TaskList: # Running tasklist...
11-05 09:32 DEBUG  TaskList: ## Running &#1571;&#1586;&#1604; &#1605;&#1583;&#1582;&#1604;&#1577; &#1605;&#1581;&#1605;&#1604; &#1575;&#1604;&#1573;&#1602;&#1604;&#1575;&#1593;...
11-05 09:32 DEBUG  WindowsBackend: Could not find bcd id
11-05 09:32 DEBUG  WindowsBackend: undo_bootini C:
11-05 09:32 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 101617.355469 mb free ntfs)
11-05 09:32 DEBUG  WindowsBackend: undo_bootini M:
11-05 09:32 DEBUG  WindowsBackend: undo_configsys Drive(M: hd 436187.996094 mb free ntfs)
11-05 09:32 DEBUG  TaskList: ## Finished &#1571;&#1586;&#1604; &#1605;&#1583;&#1582;&#1604;&#1577; &#1605;&#1581;&#1605;&#1604; &#1575;&#1604;&#1573;&#1602;&#1604;&#1575;&#1593;
11-05 09:32 DEBUG  TaskList: ## Running &#1571;&#1586;&#1604; &#1575;&#1604;&#1583;&#1604;&#1610;&#1604; &#1575;&#1604;&#1607;&#1583;&#1601;...
11-05 09:32 DEBUG  CommonBackend: Deleting M:\ubuntu
11-05 09:32 DEBUG  TaskList: ## Finished &#1571;&#1586;&#1604; &#1575;&#1604;&#1583;&#1604;&#1610;&#1604; &#1575;&#1604;&#1607;&#1583;&#1601;
11-05 09:32 DEBUG  TaskList: ## Running &#1571;&#1586;&#1604; &#1605;&#1601;&#1578;&#1575;&#1581; &#1575;&#1604;&#1605;&#1590;&#1576;&#1591;&#1577;...
11-05 09:32 DEBUG  TaskList: ## Finished &#1571;&#1586;&#1604; &#1605;&#1601;&#1578;&#1575;&#1581; &#1575;&#1604;&#1605;&#1590;&#1576;&#1591;&#1577;
11-05 09:32 DEBUG  TaskList: # Finished tasklist
11-05 09:32 INFO   root: Almost finished uninstalling
11-05 09:32 INFO   root: Finished uninstallation
11-05 09:32 DEBUG  CommonBackend: Fetching basic info...
11-05 09:32 DEBUG  CommonBackend: original_exe=C:\Users\mohmed\Downloads\Programs\wubi.exe
11-05 09:32 DEBUG  CommonBackend: platform=win32
11-05 09:32 DEBUG  CommonBackend: osname=nt
11-05 09:32 DEBUG  WindowsBackend: arch=amd64
11-05 09:32 DEBUG  CommonBackend: Parsing isolist=C:\Users\mohmed\AppData\Local\Temp\pylFB8.tmp\data\isolist.ini
11-05 09:32 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-05 09:32 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-05 09:32 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-05 09:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-05 09:32 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-05 09:32 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-05 09:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-05 09:32 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-05 09:32 DEBUG  WindowsBackend: Fetching host info...
11-05 09:32 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-05 09:32 DEBUG  WindowsBackend: windows version=vista
11-05 09:32 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
11-05 09:32 DEBUG  WindowsBackend: windows_sp=None
11-05 09:32 DEBUG  WindowsBackend: windows_build=7601
11-05 09:32 DEBUG  WindowsBackend: gmt=2
11-05 09:32 DEBUG  WindowsBackend: country=EG
11-05 09:32 DEBUG  WindowsBackend: timezone=Africa/Cairo
11-05 09:32 DEBUG  WindowsBackend: windows_username=mohmed
11-05 09:32 DEBUG  WindowsBackend: user_full_name=mohmed
11-05 09:32 DEBUG  WindowsBackend: user_directory=C:\Users\mohmed
11-05 09:32 DEBUG  WindowsBackend: windows_language_code=1025
11-05 09:32 DEBUG  WindowsBackend: windows_language=Arabic
11-05 09:32 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 480  @ 2.67GHz
11-05 09:32 DEBUG  WindowsBackend: bootloader=vista
11-05 09:32 DEBUG  WindowsBackend: system_drive=Drive(C: hd 101617.394531 mb free ntfs)
11-05 09:32 DEBUG  WindowsBackend: drive=Drive(C: hd 101617.394531 mb free ntfs)
11-05 09:32 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
11-05 09:32 DEBUG  WindowsBackend: drive=Drive(M: hd 436277.5 mb free ntfs)
11-05 09:32 DEBUG  WindowsBackend: uninstaller_path=None
11-05 09:32 DEBUG  WindowsBackend: previous_target_dir=None
11-05 09:32 DEBUG  WindowsBackend: previous_distro_name=None
11-05 09:32 DEBUG  WindowsBackend: keyboard_id=67699721
11-05 09:32 DEBUG  WindowsBackend: keyboard_layout=us
11-05 09:32 DEBUG  WindowsBackend: keyboard_variant=
11-05 09:32 DEBUG  WindowsBackend: total_memory_mb=3766.70703125
11-05 09:32 DEBUG  CommonBackend: Searching ISOs on USB devices
11-05 09:32 DEBUG  CommonBackend: Searching for local CDs
11-05 09:32 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pylFB8.tmp is a valid Ubuntu CD
11-05 09:32 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pylFB8.tmp\casper\filesystem.squashfs
11-05 09:32 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pylFB8.tmp is a valid Ubuntu CD
11-05 09:32 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pylFB8.tmp\casper\filesystem.squashfs
11-05 09:32 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pylFB8.tmp is a valid Kubuntu CD
11-05 09:32 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pylFB8.tmp\casper\filesystem.squashfs
11-05 09:32 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pylFB8.tmp is a valid Kubuntu CD
11-05 09:32 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pylFB8.tmp\casper\filesystem.squashfs
11-05 09:32 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pylFB8.tmp is a valid Xubuntu CD
11-05 09:32 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pylFB8.tmp\casper\filesystem.squashfs
11-05 09:32 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pylFB8.tmp is a valid Xubuntu CD
11-05 09:32 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pylFB8.tmp\casper\filesystem.squashfs
11-05 09:32 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pylFB8.tmp is a valid Mythbuntu CD
11-05 09:32 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pylFB8.tmp\casper\filesystem.squashfs
11-05 09:32 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pylFB8.tmp is a valid Mythbuntu CD
11-05 09:32 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pylFB8.tmp\casper\filesystem.squashfs
11-05 09:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-05 09:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 09:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-05 09:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 09:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-05 09:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 09:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-05 09:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 09:32 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-05 09:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 09:32 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-05 09:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 09:32 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-05 09:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 09:32 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-05 09:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 09:32 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
11-05 09:32 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 09:32 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
11-05 09:32 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 09:32 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
11-05 09:32 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 09:32 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
11-05 09:32 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 09:32 DEBUG  Distro:   checking whether M:\ is a valid Xubuntu CD
11-05 09:32 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 09:32 DEBUG  Distro:   checking whether M:\ is a valid Xubuntu CD
11-05 09:32 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 09:32 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
11-05 09:32 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 09:32 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
11-05 09:32 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 09:32 INFO   root: Running the installer...
11-05 09:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\mohmed\AppData\Local\Temp\pylFB8.tmp\translations, languages=['ar_EG', 'ar']
11-05 09:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\mohmed\AppData\Local\Temp\pylFB8.tmp\translations, languages=['ar_EG', 'ar']
11-05 09:32 DEBUG  WinuiInstallationPage: target_drive=M:, installation_size=20000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=mohamed
11-05 09:32 INFO   root: Received settings
11-05 09:32 DEBUG  CommonBackend: Searching for local CD
11-05 09:32 DEBUG  Distro:   checking whether C:\Users\mohmed\AppData\Local\Temp\pylFB8.tmp is a valid Ubuntu CD
11-05 09:32 DEBUG  Distro:     does not contain C:\Users\mohmed\AppData\Local\Temp\pylFB8.tmp\casper\filesystem.squashfs
11-05 09:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-05 09:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-05 09:32 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
11-05 09:32 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-05 09:32 DEBUG  CommonBackend: Searching for local ISO
11-05 09:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\mohmed\AppData\Local\Temp\pylFB8.tmp\translations, languages=['en_US', 'en']
11-05 09:32 DEBUG  TaskList: # Running tasklist...
11-05 09:32 DEBUG  TaskList: ## Running select_target_dir...
11-05 09:32 INFO   WindowsBackend: Installing into M:\ubuntu
11-05 09:32 DEBUG  TaskList: ## Finished select_target_dir
11-05 09:32 DEBUG  TaskList: ## Running create_dir_structure...
11-05 09:32 DEBUG  CommonBackend: Creating dir M:\ubuntu
11-05 09:32 DEBUG  CommonBackend: Creating dir M:\ubuntu\disks
11-05 09:32 DEBUG  CommonBackend: Creating dir M:\ubuntu\install
11-05 09:32 DEBUG  CommonBackend: Creating dir M:\ubuntu\install\boot
11-05 09:32 DEBUG  CommonBackend: Creating dir M:\ubuntu\disks\boot
11-05 09:32 DEBUG  CommonBackend: Creating dir M:\ubuntu\disks\boot\grub
11-05 09:32 DEBUG  CommonBackend: Creating dir M:\ubuntu\install\boot\grub
11-05 09:32 DEBUG  TaskList: ## Finished create_dir_structure
11-05 09:32 DEBUG  TaskList: ## Running create_uninstaller...
11-05 09:32 DEBUG  WindowsBackend: Copying uninstaller C:\Users\mohmed\Downloads\Programs\wubi.exe -> M:\ubuntu\uninstall-wubi.exe
11-05 09:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString M:\ubuntu\uninstall-wubi.exe
11-05 09:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir M:\ubuntu
11-05 09:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
11-05 09:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon M:\ubuntu\Ubuntu.ico
11-05 09:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
11-05 09:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
11-05 09:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com]("http://www.ubuntu.com/")
11-05 09:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
11-05 09:32 DEBUG  TaskList: ## Finished create_uninstaller
11-05 09:32 DEBUG  TaskList: ## Running create_preseed_diskimage...
11-05 09:32 DEBUG  TaskList: ## Finished create_preseed_diskimage
11-05 09:32 DEBUG  TaskList: ## Running get_diskimage...
11-05 09:32 DEBUG  TaskList: New task download
11-05 09:32 DEBUG  TaskList: ### Running download...
11-05 09:32 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > M:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
11-05 09:32 DEBUG  downloader: Download start filename=M:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
11-05 12:09 DEBUG  TaskList: ### Finished download
11-05 12:09 DEBUG  downloader: download finished (read 507143012 bytes)
11-05 12:09 DEBUG  TaskList: ## Finished get_diskimage
11-05 12:09 DEBUG  TaskList: ## Running extract_diskimage...
11-05 12:09 ERROR  TaskList: [Errno 2] The system cannot find the file specified
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 443, in extract_diskimage
  File "\lib\wubi\backends\common\utils.py", line 52, in spawn_command
  File "\lib\subprocess.py", line 547, in __init__
  File "\lib\subprocess.py", line 701, in _execute_child
WindowsError: [Errno 2] The system cannot find the file specified
11-05 12:09 DEBUG  TaskList: # Cancelling tasklist
11-05 12:09 DEBUG  TaskList: # Finished tasklist
11-05 12:09 ERROR  root: [Errno 2] The system cannot find the file specified
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 443, in extract_diskimage
  File "\lib\wubi\backends\common\utils.py", line 52, in spawn_command
  File "\lib\subprocess.py", line 547, in __init__
  File "\lib\subprocess.py", line 701, in _execute_child
WindowsError: [Errno 2] The system cannot find the file specified
```

---

### Post by diasf on 2011-11-05
Nothing to do with the problem, but maybe an easier solution... can't you burn a install cd?

---

