---
title: "Wubi - fails to install"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by dhs13 on 2009-04-24
I tried to install 9.04. I copied the ISO to directory that holds the wubi.exe file. (1) the installer doesn't see the iso image and makes me put the iso file on the cd rom ; (2) Norton Antivirus 2009 doesn't like the files like pyl275f.tmp.exe for some reason and (3) the installations about 90% done. I have added the installation log file below.

How do I get installation to work?

thanks

04-24 08:21 INFO   root: === wubi 9.04 rev129 ===
04-24 08:21 DEBUG  root: Logfile is c:\users\davids~1\appdata\local\temp\wubi-9.04-rev129.log
04-24 08:21 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\temp\\wubi904.exe"']
04-24 08:21 DEBUG  CommonBackend: data_dir=C:\Users\DAVIDS~1\AppData\Local\Temp\pyl5294.tmp\data
04-24 08:21 DEBUG  WindowsBackend: 7z=C:\Users\DAVIDS~1\AppData\Local\Temp\pyl5294.tmp\bin\7z.exe
04-24 08:21 DEBUG  CommonBackend: Fetching basic info...
04-24 08:21 DEBUG  CommonBackend: original_exe=C:\temp\wubi904.exe
04-24 08:21 DEBUG  CommonBackend: platform=win32
04-24 08:21 DEBUG  CommonBackend: osname=nt
04-24 08:21 DEBUG  CommonBackend: language=en_US
04-24 08:21 DEBUG  CommonBackend: encoding=cp1252
04-24 08:21 DEBUG  WindowsBackend: arch=amd64
04-24 08:21 DEBUG  CommonBackend: Parsing isolist=C:\Users\DAVIDS~1\AppData\Local\Temp\pyl5294.tmp\data\isolist.ini
04-24 08:21 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-24 08:21 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-24 08:21 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-24 08:21 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-24 08:21 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-24 08:21 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-24 08:21 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-24 08:21 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-24 08:21 DEBUG  WindowsBackend: Fetching host info...
04-24 08:21 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-24 08:21 DEBUG  WindowsBackend: windows version=vista
04-24 08:21 DEBUG  WindowsBackend: windows_version2=Windows (TM) Vista Ultimate
04-24 08:21 DEBUG  WindowsBackend: windows_sp=None
04-24 08:21 DEBUG  WindowsBackend: windows_build=6001
04-24 08:21 DEBUG  WindowsBackend: gmt=-5
04-24 08:21 DEBUG  WindowsBackend: country=US
04-24 08:21 DEBUG  WindowsBackend: timezone=America/New_York
04-24 08:21 DEBUG  WindowsBackend: windows_username=David Sherman
04-24 08:21 DEBUG  WindowsBackend: user_full_name=David Sherman
04-24 08:21 DEBUG  WindowsBackend: user_directory=David Sherman
04-24 08:21 DEBUG  WindowsBackend: windows_language_code=1033
04-24 08:21 DEBUG  WindowsBackend: windows_language=English
04-24 08:21 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual-Core Processor TK-55
04-24 08:21 DEBUG  WindowsBackend: bootloader=vista
04-24 08:21 DEBUG  WindowsBackend: system_drive=Drive(C: hd 217614.621094 mb free )
04-24 08:21 DEBUG  WindowsBackend: drive=Drive(C: hd 217614.621094 mb free )
04-24 08:21 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
04-24 08:21 DEBUG  WindowsBackend: drive=Drive(E: removable 17.2905273438 mb free fat)
04-24 08:21 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
04-24 08:21 DEBUG  WindowsBackend: drive=Drive(G: hd 138273.5625 mb free ntfs)
04-24 08:21 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
04-24 08:21 DEBUG  WindowsBackend: drive=Drive(I: removable 13.3125 mb free fat32)
04-24 08:21 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free cdfs)
04-24 08:21 DEBUG  WindowsBackend: uninstaller_path=None
04-24 08:21 DEBUG  WindowsBackend: previous_target_dir=None
04-24 08:21 DEBUG  WindowsBackend: previous_distro_name=None
04-24 08:21 DEBUG  WindowsBackend: keyboard_id=67699721
04-24 08:21 DEBUG  WindowsBackend: keyboard_layout=us
04-24 08:21 DEBUG  WindowsBackend: keyboard_variant=
04-24 08:21 DEBUG  CommonBackend: locale=en_US.UTF-8
04-24 08:21 DEBUG  WindowsBackend: total_memory_mb=1917.80859375
04-24 08:21 DEBUG  CommonBackend: Searching ISOs on USB devices
04-24 08:21 DEBUG  CommonBackend: Searching for local CDs
04-24 08:21 DEBUG  Distro:   checking whether C:\Users\DAVIDS~1\AppData\Local\Temp\pyl5294.tmp is a valid Ubuntu CD
04-24 08:21 DEBUG  Distro:     does not contain C:\Users\DAVIDS~1\AppData\Local\Temp\pyl5294.tmp\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether C:\Users\DAVIDS~1\AppData\Local\Temp\pyl5294.tmp is a valid Ubuntu CD
04-24 08:21 DEBUG  Distro:     does not contain C:\Users\DAVIDS~1\AppData\Local\Temp\pyl5294.tmp\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether C:\Users\DAVIDS~1\AppData\Local\Temp\pyl5294.tmp is a valid Kubuntu CD
04-24 08:21 DEBUG  Distro:     does not contain C:\Users\DAVIDS~1\AppData\Local\Temp\pyl5294.tmp\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether C:\Users\DAVIDS~1\AppData\Local\Temp\pyl5294.tmp is a valid Kubuntu CD
04-24 08:21 DEBUG  Distro:     does not contain C:\Users\DAVIDS~1\AppData\Local\Temp\pyl5294.tmp\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether C:\Users\DAVIDS~1\AppData\Local\Temp\pyl5294.tmp is a valid Xubuntu CD
04-24 08:21 DEBUG  Distro:     does not contain C:\Users\DAVIDS~1\AppData\Local\Temp\pyl5294.tmp\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether C:\Users\DAVIDS~1\AppData\Local\Temp\pyl5294.tmp is a valid Xubuntu CD
04-24 08:21 DEBUG  Distro:     does not contain C:\Users\DAVIDS~1\AppData\Local\Temp\pyl5294.tmp\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether C:\Users\DAVIDS~1\AppData\Local\Temp\pyl5294.tmp is a valid Mythbuntu CD
04-24 08:21 DEBUG  Distro:     does not contain C:\Users\DAVIDS~1\AppData\Local\Temp\pyl5294.tmp\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether C:\Users\DAVIDS~1\AppData\Local\Temp\pyl5294.tmp is a valid Mythbuntu CD
04-24 08:21 DEBUG  Distro:     does not contain C:\Users\DAVIDS~1\AppData\Local\Temp\pyl5294.tmp\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-24 08:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-24 08:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-24 08:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-24 08:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-24 08:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-24 08:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-24 08:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-24 08:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-24 08:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-24 08:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-24 08:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-24 08:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-24 08:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-24 08:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-24 08:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-24 08:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-24 08:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-24 08:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-24 08:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-24 08:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-24 08:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-24 08:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-24 08:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-24 08:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-24 08:21 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-24 08:21 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-24 08:21 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-24 08:21 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-24 08:21 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-24 08:21 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-24 08:21 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-24 08:21 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
04-24 08:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
04-24 08:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
04-24 08:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
04-24 08:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
04-24 08:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
04-24 08:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
04-24 08:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
04-24 08:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-24 08:21 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-24 08:21 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
04-24 08:21 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
04-24 08:21 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
04-24 08:21 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
04-24 08:21 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
04-24 08:21 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
04-24 08:21 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
04-24 08:21 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
04-24 08:21 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
04-24 08:21 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
04-24 08:21 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
04-24 08:21 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
04-24 08:21 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
04-24 08:21 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-24 08:21 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
04-24 08:21 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-24 08:21 INFO   root: Running the installer...
04-24 08:21 DEBUG  WindowsFrontend: __init__...
04-24 08:21 DEBUG  WindowsFrontend: on_init...
04-24 08:22 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=30000MB, distro_name=Ubuntu, language=English, username=davidsherman
04-24 08:22 INFO   root: Received settings
04-24 08:22 DEBUG  TaskList: # Running tasklist...
04-24 08:22 DEBUG  TaskList: ## Running select_target_dir...
04-24 08:22 INFO   WindowsBackend: Installing into C:\ubuntu
04-24 08:22 DEBUG  TaskList: ## Finished select_target_dir
04-24 08:22 DEBUG  TaskList: ## Running create_dir_structure...
04-24 08:22 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-24 08:22 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-24 08:22 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-24 08:22 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-24 08:22 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-24 08:22 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-24 08:22 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-24 08:22 DEBUG  TaskList: ## Finished create_dir_structure
04-24 08:22 DEBUG  TaskList: ## Running uncompress_target_dir...
04-24 08:22 DEBUG  TaskList: ## Finished uncompress_target_dir
04-24 08:22 DEBUG  TaskList: ## Running create_uninstaller...
04-24 08:22 DEBUG  WindowsBackend: Copying uninstaller C:\temp\wubi904.exe -> C:\ubuntu\uninstall-wubi.exe
04-24 08:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-24 08:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-24 08:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-24 08:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-24 08:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev129
04-24 08:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-24 08:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-24 08:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-24 08:22 DEBUG  TaskList: ## Finished create_uninstaller
04-24 08:22 DEBUG  TaskList: ## Running copy_installation_files...
04-24 08:22 DEBUG  WindowsBackend: Copying C:\Users\DAVIDS~1\AppData\Local\Temp\pyl5294.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-24 08:22 DEBUG  WindowsBackend: Copying C:\Users\DAVIDS~1\AppData\Local\Temp\pyl5294.tmp\winboot -> C:\ubuntu\winboot
04-24 08:22 DEBUG  WindowsBackend: Copying C:\Users\DAVIDS~1\AppData\Local\Temp\pyl5294.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-24 08:22 DEBUG  TaskList: ## Finished copy_installation_files
04-24 08:22 DEBUG  TaskList: ## Running get_iso...
04-24 08:22 DEBUG  CommonBackend: Searching for local CD
04-24 08:22 DEBUG  Distro:   checking whether C:\Users\DAVIDS~1\AppData\Local\Temp\pyl5294.tmp is a valid Ubuntu CD
04-24 08:22 DEBUG  Distro:     does not contain C:\Users\DAVIDS~1\AppData\Local\Temp\pyl5294.tmp\casper\filesystem.squashfs
04-24 08:22 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-24 08:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 08:22 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-24 08:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 08:22 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-24 08:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-24 08:22 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-24 08:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-24 08:22 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
04-24 08:22 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-24 08:22 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-24 08:22 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-24 08:22 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
04-24 08:22 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-24 08:22 DEBUG  CommonBackend: Searching for local ISO
04-24 08:22 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
04-24 08:22 DEBUG  TaskList: New task get_metalink
04-24 08:22 DEBUG  TaskList: ### Running get_metalink...
04-24 08:22 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-amd64.metalink](http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-amd64.metalink) > C:\ubuntu\install
04-24 08:22 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-9.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-amd64.metalink, basename=ubuntu-9.04-desktop-amd64.metalink, length=19580, text=None
04-24 08:22 DEBUG  downloader: download finished (read 19580 bytes)
04-24 08:22 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.04/MD5SUMS-metalink](http://releases.ubuntu.com/9.04/MD5SUMS-metalink) > C:\ubuntu\install
04-24 08:22 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/9.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=413, text=None
04-24 08:22 DEBUG  downloader: download finished (read 413 bytes)
04-24 08:22 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/9.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
04-24 08:22 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/9.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
04-24 08:22 DEBUG  downloader: download finished (read 189 bytes)
04-24 08:22 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
04-24 08:22 INFO   saplog: Checking block bindings..
04-24 08:22 INFO   saplog: Key verified successfully.
04-24 08:22 DEBUG  CommonBackend: metalink md5sums:
1ec553ada3a4a18fb977816ccac02dfc  ubuntu-9.04-alternate-amd64.metalink
5daf9cb57325672f0eb768d6c11888e8  ubuntu-9.04-alternate-i386.metalink
3df58e889d3613abc2347a6b0e8f4d04  ubuntu-9.04-desktop-amd64.metalink
542bc6d7988f1d2967d419c089b08f57  ubuntu-9.04-desktop-i386.metalink
ea0b13f00711ef4b2e5c772482033a1f  ubuntu-9.04-server-amd64.metalink
88e47c579eb587c8aae1a7d7737ab3f0  ubuntu-9.04-server-i386.metalink

04-24 08:22 DEBUG  TaskList: ### Finished get_metalink
04-24 08:22 DEBUG  TaskList: New task download
04-24 08:22 DEBUG  TaskList: ### Running download...
04-24 08:22 DEBUG  downloader: downloading [http://de.archive.ubuntu.com/ubuntu-releases/9.04/ubuntu-9.04-desktop-amd64.iso](http://de.archive.ubuntu.com/ubuntu-releases/9.04/ubuntu-9.04-desktop-amd64.iso) > C:\ubuntu\install\ubuntu-9.04-desktop-amd64.iso
04-24 08:22 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-9.04-desktop-amd64.iso, url=http://de.archive.ubuntu.com/ubuntu-releases/9.04/ubuntu-9.04-desktop-amd64.iso, basename=ubuntu-9.04-desktop-amd64.iso, length=730554368, text=None
04-24 08:27 INFO   WindowsFrontend: Operation cancelled
04-24 08:27 DEBUG  WindowsFrontend: frontend.quit
04-24 08:27 DEBUG  WindowsFrontend: frontend.on_quit
04-24 08:27 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
04-24 08:27 DEBUG  TaskList: # Cancelling tasklist
04-24 08:27 DEBUG  downloader: download finished (read 983040 bytes)
04-24 08:27 DEBUG  TaskList: ### Finished download
04-24 08:27 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
04-24 08:27 DEBUG  root: application.on_quit
04-24 08:27 DEBUG  root: Forceful exit
04-24 08:27 INFO   root: sys.exit
04-24 08:48 INFO   root: === wubi 9.04 rev129 ===
04-24 08:48 DEBUG  root: Logfile is c:\users\davids~1\appdata\local\temp\wubi-9.04-rev129.log
04-24 08:48 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\temp\\wubi904.exe"']
04-24 08:48 DEBUG  CommonBackend: data_dir=C:\Users\DAVIDS~1\AppData\Local\Temp\pyl36BB.tmp\data
04-24 08:48 DEBUG  WindowsBackend: 7z=C:\Users\DAVIDS~1\AppData\Local\Temp\pyl36BB.tmp\bin\7z.exe
04-24 08:48 DEBUG  CommonBackend: Fetching basic info...
04-24 08:48 DEBUG  CommonBackend: original_exe=C:\temp\wubi904.exe
04-24 08:48 DEBUG  CommonBackend: platform=win32
04-24 08:48 DEBUG  CommonBackend: osname=nt
04-24 08:48 DEBUG  CommonBackend: language=en_US
04-24 08:48 DEBUG  CommonBackend: encoding=cp1252
04-24 08:48 DEBUG  WindowsBackend: arch=amd64
04-24 08:48 DEBUG  CommonBackend: Parsing isolist=C:\Users\DAVIDS~1\AppData\Local\Temp\pyl36BB.tmp\data\isolist.ini
04-24 08:48 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-24 08:48 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-24 08:48 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-24 08:48 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-24 08:48 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-24 08:48 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-24 08:48 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-24 08:48 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-24 08:48 DEBUG  WindowsBackend: Fetching host info...
04-24 08:48 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-24 08:48 DEBUG  WindowsBackend: windows version=vista
04-24 08:48 DEBUG  WindowsBackend: windows_version2=Windows (TM) Vista Ultimate
04-24 08:48 DEBUG  WindowsBackend: windows_sp=None
04-24 08:48 DEBUG  WindowsBackend: windows_build=6001
04-24 08:48 DEBUG  WindowsBackend: gmt=-5
04-24 08:48 DEBUG  WindowsBackend: country=US
04-24 08:48 DEBUG  WindowsBackend: timezone=America/New_York
04-24 08:48 DEBUG  WindowsBackend: windows_username=David Sherman
04-24 08:48 DEBUG  WindowsBackend: user_full_name=David Sherman
04-24 08:48 DEBUG  WindowsBackend: user_directory=David Sherman
04-24 08:48 DEBUG  WindowsBackend: windows_language_code=1033
04-24 08:48 DEBUG  WindowsBackend: windows_language=English
04-24 08:48 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual-Core Processor TK-55
04-24 08:48 DEBUG  WindowsBackend: bootloader=vista
04-24 08:48 DEBUG  WindowsBackend: system_drive=Drive(C: hd 216872.804688 mb free )
04-24 08:48 DEBUG  WindowsBackend: drive=Drive(C: hd 216872.804688 mb free )
04-24 08:48 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
04-24 08:48 DEBUG  WindowsBackend: drive=Drive(E: removable 17.2905273438 mb free fat)
04-24 08:48 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
04-24 08:48 DEBUG  WindowsBackend: drive=Drive(G: hd 138273.5625 mb free ntfs)
04-24 08:48 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
04-24 08:48 DEBUG  WindowsBackend: drive=Drive(I: removable 13.3125 mb free fat32)
04-24 08:48 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free cdfs)
04-24 08:48 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-24 08:48 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-24 08:48 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-24 08:48 DEBUG  WindowsBackend: keyboard_id=67699721
04-24 08:48 DEBUG  WindowsBackend: keyboard_layout=us
04-24 08:48 DEBUG  WindowsBackend: keyboard_variant=
04-24 08:48 DEBUG  CommonBackend: locale=en_US.UTF-8
04-24 08:48 DEBUG  WindowsBackend: total_memory_mb=1917.80859375
04-24 08:48 DEBUG  CommonBackend: Searching ISOs on USB devices
04-24 08:48 DEBUG  CommonBackend: Searching for local CDs
04-24 08:48 DEBUG  Distro:   checking whether C:\Users\DAVIDS~1\AppData\Local\Temp\pyl36BB.tmp is a valid Ubuntu CD
04-24 08:48 DEBUG  Distro:     does not contain C:\Users\DAVIDS~1\AppData\Local\Temp\pyl36BB.tmp\casper\filesystem.squashfs
04-24 08:48 DEBUG  Distro:   checking whether C:\Users\DAVIDS~1\AppData\Local\Temp\pyl36BB.tmp is a valid Ubuntu CD
04-24 08:48 DEBUG  Distro:     does not contain C:\Users\DAVIDS~1\AppData\Local\Temp\pyl36BB.tmp\casper\filesystem.squashfs
04-24 08:48 DEBUG  Distro:   checking whether C:\Users\DAVIDS~1\AppData\Local\Temp\pyl36BB.tmp is a valid Kubuntu CD
04-24 08:48 DEBUG  Distro:     does not contain C:\Users\DAVIDS~1\AppData\Local\Temp\pyl36BB.tmp\casper\filesystem.squashfs
04-24 08:48 DEBUG  Distro:   checking whether C:\Users\DAVIDS~1\AppData\Local\Temp\pyl36BB.tmp is a valid Kubuntu CD
04-24 08:48 DEBUG  Distro:     does not contain C:\Users\DAVIDS~1\AppData\Local\Temp\pyl36BB.tmp\casper\filesystem.squashfs
04-24 08:48 DEBUG  Distro:   checking whether C:\Users\DAVIDS~1\AppData\Local\Temp\pyl36BB.tmp is a valid Xubuntu CD
04-24 08:48 DEBUG  Distro:     does not contain C:\Users\DAVIDS~1\AppData\Local\Temp\pyl36BB.tmp\casper\filesystem.squashfs
04-24 08:48 DEBUG  Distro:   checking whether C:\Users\DAVIDS~1\AppData\Local\Temp\pyl36BB.tmp is a valid Xubuntu CD
04-24 08:48 DEBUG  Distro:     does not contain C:\Users\DAVIDS~1\AppData\Local\Temp\pyl36BB.tmp\casper\filesystem.squashfs
04-24 08:48 DEBUG  Distro:   checking whether C:\Users\DAVIDS~1\AppData\Local\Temp\pyl36BB.tmp is a valid Mythbuntu CD
04-24 08:48 DEBUG  Distro:     does not contain C:\Users\DAVIDS~1\AppData\Local\Temp\pyl36BB.tmp\casper\filesystem.squashfs
04-24 08:48 DEBUG  Distro:   checking whether C:\Users\DAVIDS~1\AppData\Local\Temp\pyl36BB.tmp is a valid Mythbuntu CD
04-24 08:48 DEBUG  Distro:     does not contain C:\Users\DAVIDS~1\AppData\Local\Temp\pyl36BB.tmp\casper\filesystem.squashfs
04-24 08:48 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-24 08:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 08:48 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-24 08:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 08:48 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-24 08:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 08:48 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-24 08:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-24 08:48 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-24 08:49 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release amd64 (20090420.1)
04-24 08:49 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'amd64'}
04-24 08:49 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
04-24 08:49 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-24 08:49 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
04-24 08:49 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-24 08:49 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
04-24 08:49 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-24 08:49 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
04-24 08:49 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-24 08:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 08:49 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-24 08:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 08:49 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-24 08:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 08:49 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-24 08:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 08:49 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-24 08:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 08:49 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-24 08:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 08:49 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-24 08:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 08:49 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-24 08:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-24 08:49 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-24 08:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-24 08:49 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-24 08:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-24 08:49 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-24 08:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-24 08:49 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-24 08:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-24 08:49 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-24 08:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-24 08:49 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-24 08:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-24 08:49 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-24 08:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-24 08:49 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-24 08:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-24 08:49 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-24 08:49 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-24 08:49 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-24 08:49 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-24 08:49 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-24 08:49 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-24 08:49 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-24 08:49 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-24 08:49 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-24 08:49 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-24 08:49 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-24 08:49 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-24 08:49 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-24 08:49 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-24 08:49 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-24 08:49 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-24 08:49 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
04-24 08:49 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-24 08:49 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
04-24 08:49 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-24 08:49 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
04-24 08:49 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-24 08:49 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
04-24 08:49 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-24 08:49 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
04-24 08:49 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-24 08:49 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
04-24 08:49 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-24 08:49 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
04-24 08:49 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-24 08:49 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
04-24 08:49 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-24 08:49 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-24 08:49 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-24 08:49 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-24 08:49 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-24 08:49 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
04-24 08:49 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-24 08:49 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
04-24 08:49 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-24 08:49 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
04-24 08:49 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-24 08:49 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
04-24 08:49 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-24 08:49 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
04-24 08:49 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-24 08:49 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
04-24 08:49 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-24 08:49 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
04-24 08:49 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-24 08:49 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
04-24 08:49 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-24 08:49 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
04-24 08:49 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-24 08:49 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
04-24 08:49 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-24 08:49 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
04-24 08:49 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-24 08:49 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
04-24 08:49 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-24 08:49 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
04-24 08:49 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-24 08:49 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
04-24 08:49 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-24 08:49 INFO   root: Already installed, running the uninstaller...
04-24 08:49 INFO   root: Running the uninstaller...
04-24 08:49 INFO   CommonBackend: This is the uninstaller running
04-24 08:49 DEBUG  WindowsFrontend: __init__...
04-24 08:49 DEBUG  WindowsFrontend: on_init...
04-24 08:50 INFO   root: Received settings
04-24 08:50 DEBUG  TaskList: # Running tasklist...
04-24 08:50 DEBUG  TaskList: ## Running Backup ISO...
04-24 08:50 DEBUG  TaskList: ## Finished Backup ISO
04-24 08:50 DEBUG  TaskList: ## Running Remove bootloader entry...
04-24 08:50 DEBUG  WindowsBackend: Could not find bcd id
04-24 08:50 DEBUG  WindowsBackend: undo_bootini C:
04-24 08:50 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 216872.804688 mb free )
04-24 08:50 DEBUG  WindowsBackend: undo_bootini E:
04-24 08:50 DEBUG  WindowsBackend: undo_configsys Drive(E: removable 17.2905273438 mb free fat)
04-24 08:50 DEBUG  WindowsBackend: undo_bootini G:
04-24 08:50 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 138273.5625 mb free ntfs)
04-24 08:50 DEBUG  WindowsBackend: undo_bootini I:
04-24 08:50 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 13.3125 mb free fat32)
04-24 08:50 DEBUG  TaskList: ## Finished Remove bootloader entry
04-24 08:50 DEBUG  TaskList: ## Running Remove target dir...
04-24 08:50 DEBUG  CommonBackend: Deleting C:\ubuntu
04-24 08:50 DEBUG  TaskList: ## Finished Remove target dir
04-24 08:50 DEBUG  TaskList: ## Running Remove registry key...
04-24 08:50 DEBUG  TaskList: ## Finished Remove registry key
04-24 08:50 DEBUG  TaskList: # Finished tasklist
04-24 08:50 INFO   root: Almost finished uninstalling
04-24 08:50 INFO   root: Finished uninstallation
04-24 08:50 DEBUG  CommonBackend: Fetching basic info...
04-24 08:50 DEBUG  CommonBackend: original_exe=C:\temp\wubi904.exe
04-24 08:50 DEBUG  CommonBackend: platform=win32
04-24 08:50 DEBUG  CommonBackend: osname=nt
04-24 08:50 DEBUG  CommonBackend: language=en_US
04-24 08:50 DEBUG  CommonBackend: encoding=cp1252
04-24 08:50 DEBUG  WindowsBackend: arch=amd64
04-24 08:50 DEBUG  CommonBackend: Parsing isolist=C:\Users\DAVIDS~1\AppData\Local\Temp\pyl36BB.tmp\data\isolist.ini
04-24 08:50 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-24 08:50 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-24 08:50 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-24 08:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-24 08:50 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-24 08:50 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-24 08:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-24 08:50 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-24 08:50 DEBUG  WindowsBackend: Fetching host info...
04-24 08:50 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-24 08:50 DEBUG  WindowsBackend: windows version=vista
04-24 08:50 DEBUG  WindowsBackend: windows_version2=Windows (TM) Vista Ultimate
04-24 08:50 DEBUG  WindowsBackend: windows_sp=None
04-24 08:50 DEBUG  WindowsBackend: windows_build=6001
04-24 08:50 DEBUG  WindowsBackend: gmt=-5
04-24 08:50 DEBUG  WindowsBackend: country=US
04-24 08:50 DEBUG  WindowsBackend: timezone=America/New_York
04-24 08:50 DEBUG  WindowsBackend: windows_username=David Sherman
04-24 08:50 DEBUG  WindowsBackend: user_full_name=David Sherman
04-24 08:50 DEBUG  WindowsBackend: user_directory=David Sherman
04-24 08:50 DEBUG  WindowsBackend: windows_language_code=1033
04-24 08:50 DEBUG  WindowsBackend: windows_language=English
04-24 08:50 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual-Core Processor TK-55
04-24 08:50 DEBUG  WindowsBackend: bootloader=vista
04-24 08:50 DEBUG  WindowsBackend: system_drive=Drive(C: hd 216874.269531 mb free )
04-24 08:50 DEBUG  WindowsBackend: drive=Drive(C: hd 216874.269531 mb free )
04-24 08:50 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
04-24 08:50 DEBUG  WindowsBackend: drive=Drive(E: removable 17.2905273438 mb free fat)
04-24 08:50 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
04-24 08:50 DEBUG  WindowsBackend: drive=Drive(G: hd 138273.5625 mb free ntfs)
04-24 08:50 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
04-24 08:50 DEBUG  WindowsBackend: drive=Drive(I: removable 13.3125 mb free fat32)
04-24 08:50 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free cdfs)
04-24 08:50 DEBUG  WindowsBackend: uninstaller_path=None
04-24 08:50 DEBUG  WindowsBackend: previous_target_dir=None
04-24 08:50 DEBUG  WindowsBackend: previous_distro_name=None
04-24 08:50 DEBUG  WindowsBackend: keyboard_id=67699721
04-24 08:50 DEBUG  WindowsBackend: keyboard_layout=us
04-24 08:50 DEBUG  WindowsBackend: keyboard_variant=
04-24 08:50 DEBUG  CommonBackend: locale=en_US.UTF-8
04-24 08:50 DEBUG  WindowsBackend: total_memory_mb=1917.80859375
04-24 08:50 DEBUG  CommonBackend: Searching ISOs on USB devices
04-24 08:50 DEBUG  CommonBackend: Searching for local CDs
04-24 08:50 DEBUG  Distro:   checking whether C:\Users\DAVIDS~1\AppData\Local\Temp\pyl36BB.tmp is a valid Ubuntu CD
04-24 08:50 DEBUG  Distro:     does not contain C:\Users\DAVIDS~1\AppData\Local\Temp\pyl36BB.tmp\casper\filesystem.squashfs
04-24 08:50 DEBUG  Distro:   checking whether C:\Users\DAVIDS~1\AppData\Local\Temp\pyl36BB.tmp is a valid Ubuntu CD
04-24 08:50 DEBUG  Distro:     does not contain C:\Users\DAVIDS~1\AppData\Local\Temp\pyl36BB.tmp\casper\filesystem.squashfs
04-24 08:50 DEBUG  Distro:   checking whether C:\Users\DAVIDS~1\AppData\Local\Temp\pyl36BB.tmp is a valid Kubuntu CD
04-24 08:50 DEBUG  Distro:     does not contain C:\Users\DAVIDS~1\AppData\Local\Temp\pyl36BB.tmp\casper\filesystem.squashfs
04-24 08:50 DEBUG  Distro:   checking whether C:\Users\DAVIDS~1\AppData\Local\Temp\pyl36BB.tmp is a valid Kubuntu CD
04-24 08:50 DEBUG  Distro:     does not contain C:\Users\DAVIDS~1\AppData\Local\Temp\pyl36BB.tmp\casper\filesystem.squashfs
04-24 08:50 DEBUG  Distro:   checking whether C:\Users\DAVIDS~1\AppData\Local\Temp\pyl36BB.tmp is a valid Xubuntu CD
04-24 08:50 DEBUG  Distro:     does not contain C:\Users\DAVIDS~1\AppData\Local\Temp\pyl36BB.tmp\casper\filesystem.squashfs
04-24 08:50 DEBUG  Distro:   checking whether C:\Users\DAVIDS~1\AppData\Local\Temp\pyl36BB.tmp is a valid Xubuntu CD
04-24 08:50 DEBUG  Distro:     does not contain C:\Users\DAVIDS~1\AppData\Local\Temp\pyl36BB.tmp\casper\filesystem.squashfs
04-24 08:50 DEBUG  Distro:   checking whether C:\Users\DAVIDS~1\AppData\Local\Temp\pyl36BB.tmp is a valid Mythbuntu CD
04-24 08:50 DEBUG  Distro:     does not contain C:\Users\DAVIDS~1\AppData\Local\Temp\pyl36BB.tmp\casper\filesystem.squashfs
04-24 08:50 DEBUG  Distro:   checking whether C:\Users\DAVIDS~1\AppData\Local\Temp\pyl36BB.tmp is a valid Mythbuntu CD
04-24 08:50 DEBUG  Distro:     does not contain C:\Users\DAVIDS~1\AppData\Local\Temp\pyl36BB.tmp\casper\filesystem.squashfs
04-24 08:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-24 08:50 INFO   Distro: Found a valid CD for Ubuntu: D:\
04-24 08:50 INFO   root: Running the installer...
04-24 08:50 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=30000MB, distro_name=Ubuntu, language=English, username=davidsherman
04-24 08:50 INFO   root: Received settings
04-24 08:50 DEBUG  TaskList: # Running tasklist...
04-24 08:50 DEBUG  TaskList: ## Running select_target_dir...
04-24 08:50 INFO   WindowsBackend: Installing into C:\ubuntu
04-24 08:50 DEBUG  TaskList: ## Finished select_target_dir
04-24 08:50 DEBUG  TaskList: ## Running create_dir_structure...
04-24 08:50 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-24 08:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-24 08:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-24 08:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-24 08:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-24 08:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-24 08:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-24 08:50 DEBUG  TaskList: ## Finished create_dir_structure
04-24 08:50 DEBUG  TaskList: ## Running uncompress_target_dir...
04-24 08:50 DEBUG  TaskList: ## Finished uncompress_target_dir
04-24 08:50 DEBUG  TaskList: ## Running create_uninstaller...
04-24 08:50 DEBUG  WindowsBackend: Copying uninstaller C:\temp\wubi904.exe -> C:\ubuntu\uninstall-wubi.exe
04-24 08:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-24 08:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-24 08:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-24 08:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-24 08:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev129
04-24 08:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-24 08:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-24 08:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-24 08:50 DEBUG  TaskList: ## Finished create_uninstaller
04-24 08:50 DEBUG  TaskList: ## Running copy_installation_files...
04-24 08:50 DEBUG  WindowsBackend: Copying C:\Users\DAVIDS~1\AppData\Local\Temp\pyl36BB.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-24 08:50 DEBUG  WindowsBackend: Copying C:\Users\DAVIDS~1\AppData\Local\Temp\pyl36BB.tmp\winboot -> C:\ubuntu\winboot
04-24 08:50 DEBUG  WindowsBackend: Copying C:\Users\DAVIDS~1\AppData\Local\Temp\pyl36BB.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-24 08:50 DEBUG  TaskList: ## Finished copy_installation_files
04-24 08:50 DEBUG  TaskList: ## Running get_iso...
04-24 08:50 DEBUG  TaskList: New task copy_file
04-24 08:50 DEBUG  TaskList: ### Running copy_file...
04-24 08:55 DEBUG  TaskList: ### Finished copy_file
04-24 08:55 ERROR  TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 22] Invalid argument
04-24 08:55 DEBUG  TaskList: # Cancelling tasklist
04-24 08:55 DEBUG  TaskList: New task check_iso
04-24 08:55 ERROR  root: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 129, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 22] Invalid argument
04-24 08:55 DEBUG  CommonBackend: Searching for local ISO
04-24 08:55 DEBUG  Distro:   checking Ubuntu ISO C:\temp\ubuntu-9.04-desktop-amd64.iso
04-24 08:55 DEBUG  WindowsBackend:   extracting .disk\info from C:\temp\ubuntu-9.04-desktop-amd64.iso
04-24 08:55 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release amd64 (20090420.1)
04-24 08:55 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'amd64'}
04-24 08:55 INFO   Distro: Found a valid iso for Ubuntu: C:\temp\ubuntu-9.04-desktop-amd64.iso
04-24 08:55 DEBUG  CommonBackend: Trying to use ISO C:\temp\ubuntu-9.04-desktop-amd64.iso
04-24 08:55 DEBUG  TaskList: New task check_iso
04-24 08:55 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
04-24 08:55 DEBUG  TaskList: New task get_metalink
04-24 08:55 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
04-24 08:55 DEBUG  TaskList: # Cancelling tasklist
04-24 08:55 DEBUG  TaskList: # Finished tasklist

---

