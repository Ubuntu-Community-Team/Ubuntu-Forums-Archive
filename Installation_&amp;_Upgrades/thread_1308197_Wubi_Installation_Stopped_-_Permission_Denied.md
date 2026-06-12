---
title: "Wubi Installation Stopped - Permission Denied"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by mschraier on 2009-10-31
:pMy Vista drive will not allow me to partition for 9.10.  I read all the possible workarounds and decided to use Wubi.  However, at about 80% or so, I received and error stating permission to access denied.  Here is what was in the log.  How can I get this to install.

10-31 14:18 INFO   root: === wubi 9.10ubuntu1 rev160 ===
10-31 14:18 DEBUG  root: Logfile is c:\users\marty\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
10-31 14:18 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
10-31 14:18 DEBUG  CommonBackend: data_dir=C:\Users\Marty\AppData\Local\Temp\pylF325.tmp\data
10-31 14:18 DEBUG  WindowsBackend: 7z=C:\Users\Marty\AppData\Local\Temp\pylF325.tmp\bin\7z.exe
10-31 14:18 DEBUG  CommonBackend: Fetching basic info...
10-31 14:18 DEBUG  CommonBackend: original_exe=E:\wubi.exe
10-31 14:18 DEBUG  CommonBackend: platform=win32
10-31 14:18 DEBUG  CommonBackend: osname=nt
10-31 14:18 DEBUG  CommonBackend: language=en_US
10-31 14:18 DEBUG  CommonBackend: encoding=cp1252
10-31 14:18 DEBUG  WindowsBackend: arch=amd64
10-31 14:18 DEBUG  CommonBackend: Parsing isolist=C:\Users\Marty\AppData\Local\Temp\pylF325.tmp\data\isolist.ini
10-31 14:18 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-31 14:18 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-31 14:18 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-31 14:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-31 14:18 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-31 14:18 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-31 14:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-31 14:18 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-31 14:18 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
10-31 14:18 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
10-31 14:18 DEBUG  WindowsBackend: Fetching host info...
10-31 14:18 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-31 14:18 DEBUG  WindowsBackend: windows version=vista
10-31 14:18 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Premium
10-31 14:18 DEBUG  WindowsBackend: windows_sp=Service Pack 2
10-31 14:18 DEBUG  WindowsBackend: windows_build=6002
10-31 14:18 DEBUG  WindowsBackend: gmt=-5
10-31 14:18 DEBUG  WindowsBackend: country=US
10-31 14:18 DEBUG  WindowsBackend: timezone=America/New_York
10-31 14:18 DEBUG  WindowsBackend: windows_username=Marty
10-31 14:18 DEBUG  WindowsBackend: user_full_name=Marty
10-31 14:18 DEBUG  WindowsBackend: user_directory=C:\Users\Marty
10-31 14:18 DEBUG  WindowsBackend: windows_language_code=1033
10-31 14:18 DEBUG  WindowsBackend: windows_language=English
10-31 14:18 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 CPU         T5200  @ 1.60GHz
10-31 14:18 DEBUG  WindowsBackend: bootloader=vista
10-31 14:18 DEBUG  WindowsBackend: system_drive=Drive(C: hd 33759.234375 mb free ntfs)
10-31 14:18 DEBUG  WindowsBackend: drive=Drive(C: hd 33759.234375 mb free ntfs)
10-31 14:18 DEBUG  WindowsBackend: drive=Drive(D: hd 4566.7734375 mb free ntfs)
10-31 14:18 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
10-31 14:18 DEBUG  WindowsBackend: uninstaller_path=None
10-31 14:18 DEBUG  WindowsBackend: previous_target_dir=None
10-31 14:18 DEBUG  WindowsBackend: previous_distro_name=None
10-31 14:18 DEBUG  WindowsBackend: keyboard_id=67699721
10-31 14:18 DEBUG  WindowsBackend: keyboard_layout=us
10-31 14:18 DEBUG  WindowsBackend: keyboard_variant=
10-31 14:18 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-31 14:18 DEBUG  CommonBackend: locale=en_US.UTF-8
10-31 14:18 DEBUG  WindowsBackend: total_memory_mb=2037.4453125
10-31 14:18 DEBUG  CommonBackend: Searching ISOs on USB devices
10-31 14:18 DEBUG  CommonBackend: Searching for local CDs
10-31 14:18 DEBUG  Distro:   checking whether C:\Users\Marty\AppData\Local\Temp\pylF325.tmp is a valid Ubuntu CD
10-31 14:18 DEBUG  Distro:     does not contain C:\Users\Marty\AppData\Local\Temp\pylF325.tmp\casper\filesystem.squashfs
10-31 14:18 DEBUG  Distro:   checking whether C:\Users\Marty\AppData\Local\Temp\pylF325.tmp is a valid Ubuntu CD
10-31 14:18 DEBUG  Distro:     does not contain C:\Users\Marty\AppData\Local\Temp\pylF325.tmp\casper\filesystem.squashfs
10-31 14:18 DEBUG  Distro:   checking whether C:\Users\Marty\AppData\Local\Temp\pylF325.tmp is a valid Ubuntu Netbook Remix CD
10-31 14:18 DEBUG  Distro:     does not contain C:\Users\Marty\AppData\Local\Temp\pylF325.tmp\casper\filesystem.squashfs
10-31 14:18 DEBUG  Distro:   checking whether C:\Users\Marty\AppData\Local\Temp\pylF325.tmp is a valid Kubuntu CD
10-31 14:18 DEBUG  Distro:     does not contain C:\Users\Marty\AppData\Local\Temp\pylF325.tmp\casper\filesystem.squashfs
10-31 14:18 DEBUG  Distro:   checking whether C:\Users\Marty\AppData\Local\Temp\pylF325.tmp is a valid Kubuntu CD
10-31 14:18 DEBUG  Distro:     does not contain C:\Users\Marty\AppData\Local\Temp\pylF325.tmp\casper\filesystem.squashfs
10-31 14:18 DEBUG  Distro:   checking whether C:\Users\Marty\AppData\Local\Temp\pylF325.tmp is a valid Kubuntu Netbook CD
10-31 14:18 DEBUG  Distro:     does not contain C:\Users\Marty\AppData\Local\Temp\pylF325.tmp\casper\filesystem.squashfs
10-31 14:18 DEBUG  Distro:   checking whether C:\Users\Marty\AppData\Local\Temp\pylF325.tmp is a valid Xubuntu CD
10-31 14:18 DEBUG  Distro:     does not contain C:\Users\Marty\AppData\Local\Temp\pylF325.tmp\casper\filesystem.squashfs
10-31 14:18 DEBUG  Distro:   checking whether C:\Users\Marty\AppData\Local\Temp\pylF325.tmp is a valid Xubuntu CD
10-31 14:18 DEBUG  Distro:     does not contain C:\Users\Marty\AppData\Local\Temp\pylF325.tmp\casper\filesystem.squashfs
10-31 14:18 DEBUG  Distro:   checking whether C:\Users\Marty\AppData\Local\Temp\pylF325.tmp is a valid Mythbuntu CD
10-31 14:18 DEBUG  Distro:     does not contain C:\Users\Marty\AppData\Local\Temp\pylF325.tmp\casper\filesystem.squashfs
10-31 14:18 DEBUG  Distro:   checking whether C:\Users\Marty\AppData\Local\Temp\pylF325.tmp is a valid Mythbuntu CD
10-31 14:18 DEBUG  Distro:     does not contain C:\Users\Marty\AppData\Local\Temp\pylF325.tmp\casper\filesystem.squashfs
10-31 14:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-31 14:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-31 14:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-31 14:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-31 14:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
10-31 14:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-31 14:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-31 14:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-31 14:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-31 14:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-31 14:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
10-31 14:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-31 14:18 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-31 14:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-31 14:18 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-31 14:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-31 14:18 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-31 14:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-31 14:18 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-31 14:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-31 14:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-31 14:18 DEBUG  Distro:   parsing info from str=Kubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
10-31 14:18 DEBUG  Distro:   parsed info={'name': 'Kubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
10-31 14:18 DEBUG  Distro: wrong name: Kubuntu != Ubuntu
10-31 14:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-31 14:18 DEBUG  Distro: wrong name: Kubuntu != Ubuntu
10-31 14:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
10-31 14:18 DEBUG  Distro: wrong name: Kubuntu != Ubuntu Netbook Remix
10-31 14:18 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-31 14:18 INFO   Distro: Found a valid CD for Kubuntu: E:\
10-31 14:18 INFO   root: Running the CD menu...
10-31 14:18 DEBUG  WindowsFrontend: __init__...
10-31 14:18 DEBUG  WindowsFrontend: on_init...
10-31 14:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marty\AppData\Local\Temp\pylF325.tmp\translations, languages=['en_US', 'en']
10-31 14:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marty\AppData\Local\Temp\pylF325.tmp\translations, languages=['en_US', 'en']
10-31 14:19 INFO   root: CD menu finished
10-31 14:19 INFO   root: Running the installer...
10-31 14:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marty\AppData\Local\Temp\pylF325.tmp\translations, languages=['en_US', 'en']
10-31 14:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marty\AppData\Local\Temp\pylF325.tmp\translations, languages=['en_US', 'en']
10-31 14:20 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Kubuntu, language=en_US, locale=en_US.UTF-8, username=marty
10-31 14:20 INFO   root: Received settings
10-31 14:20 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Marty\AppData\Local\Temp\pylF325.tmp\translations, languages=['en_US', 'en']
10-31 14:20 DEBUG  TaskList: # Running tasklist...
10-31 14:20 DEBUG  TaskList: ## Running select_target_dir...
10-31 14:20 INFO   WindowsBackend: Installing into C:\ubuntu
10-31 14:20 DEBUG  TaskList: ## Finished select_target_dir
10-31 14:20 DEBUG  TaskList: ## Running create_dir_structure...
10-31 14:20 DEBUG  CommonBackend: Creating dir C:\ubuntu
10-31 14:20 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
10-31 14:20 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
10-31 14:20 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
10-31 14:20 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
10-31 14:20 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
10-31 14:20 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
10-31 14:20 DEBUG  TaskList: ## Finished create_dir_structure
10-31 14:20 DEBUG  TaskList: ## Running uncompress_target_dir...
10-31 14:20 DEBUG  TaskList: ## Finished uncompress_target_dir
10-31 14:20 DEBUG  TaskList: ## Running create_uninstaller...
10-31 14:20 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
10-31 14:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
10-31 14:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
10-31 14:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Kubuntu
10-31 14:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Kubuntu.ico
10-31 14:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
10-31 14:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Kubuntu
10-31 14:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.kubuntu.org](http://www.kubuntu.org)
10-31 14:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
10-31 14:20 DEBUG  TaskList: ## Finished create_uninstaller
10-31 14:20 DEBUG  TaskList: ## Running copy_installation_files...
10-31 14:20 DEBUG  WindowsBackend: Copying C:\Users\Marty\AppData\Local\Temp\pylF325.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
10-31 14:20 DEBUG  WindowsBackend: Copying C:\Users\Marty\AppData\Local\Temp\pylF325.tmp\winboot -> C:\ubuntu\winboot
10-31 14:20 DEBUG  WindowsBackend: Copying C:\Users\Marty\AppData\Local\Temp\pylF325.tmp\data\images\Kubuntu.ico -> C:\ubuntu\Kubuntu.ico
10-31 14:20 DEBUG  TaskList: ## Finished copy_installation_files
10-31 14:20 DEBUG  TaskList: ## Running get_iso...
10-31 14:20 DEBUG  TaskList: New task copy_file
10-31 14:20 DEBUG  TaskList: ### Running copy_file...
10-31 14:24 DEBUG  TaskList: ### Finished copy_file
10-31 14:24 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
10-31 14:24 DEBUG  TaskList: # Cancelling tasklist
10-31 14:24 DEBUG  TaskList: New task check_iso
10-31 14:24 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 126, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
10-31 14:24 DEBUG  CommonBackend: Searching for local ISO
10-31 14:24 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
10-31 14:24 DEBUG  TaskList: New task get_metalink
10-31 14:24 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
10-31 14:24 DEBUG  TaskList: # Cancelling tasklist
10-31 14:24 DEBUG  TaskList: # Finished tasklist


thanks

---

### Post by duncanmaybury on 2010-02-07
Did you sort this out? I had 9.10 running in WUBI in vista, then I reinstalled Vista and tried to get 9.10 on using WUBI but it is now coming up with the same message you have. I have had a look around the forum and can't find any solid answers. Anyone know whats going on?

---

### Post by Mark Phelps on 2010-02-08
Sorry for the obvious question, but have you tried selecting the .exe file and then right-clicking and choosing Run as Administrator? This should force Vista to use the trusted installer to load the app -- which should then avoid any permissions problems.

---

### Post by duncanmaybury on 2010-02-09
Hi Mark

Thanks for your reply. No I hadn't tried that, I had assumed that as I was the only user on my laptop I would have all rights. If I run into such problems again I will remember this option! For now I managed to get it to install using the download wubi here: [http://www.ubuntu.com/getubuntu/download-wubi](http://www.ubuntu.com/getubuntu/download-wubi)

as oppose to wubi on a disc,it installed with no problems.

Cheers
Dunc

---

### Post by edisoncm on 2010-10-16
Hello there,
I did all that and still get the message when trying to install the new version 10.10.
I am runing vista 32 .

---

### Post by Preston Durbin on 2010-10-18
I'm running Windows 7 and trying to install 10.04 and I get the same error. I have tried running as an administrator but it hasn't worked. Any other ideas?

---

### Post by anuragchauhan00 on 2010-10-23
i too have same issues.
Windows 7, WUBI installer, ubuntu 10.10.
i have already tried many things as setting folders as public.
ubuntu seems to be under developed as far as installation goes.

A very sad state of affairs.

---

### Post by intel 4004 on 2011-11-04
I also having the same problem
Lenovo laptop
have 4 partition. 2 for windows 7, 1 OEM another unallocated.
Windows 7 32bit
Trying to install 11.10 using Wubi-r245

---

### Post by oldos2er on 2011-11-04
Closed. Please start a new thread for your question.

---

