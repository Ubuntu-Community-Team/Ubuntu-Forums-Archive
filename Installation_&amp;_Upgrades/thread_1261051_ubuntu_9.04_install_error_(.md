---
title: "ubuntu 9.04 install error :("
date: 2009-09-08
forum: Installation &amp; Upgrades
---

### Post by liquidmonkey on 2009-09-08
i'm trying to install ubuntu 9.04 (the latest from their website) onto my machine but i keep getting the following error...

writelines() argument must be a sequence of strings

now, i'm TOTALLY NEW to linux / ubuntu so i have no idea what this could mean. i tried google but nothing :(

i have win7 (j:) and VISTA (c:) on my PC and am running win7 when trying to do the install. i'm also trying to install ubuntu on a separate HDD that has 2 partitions.
(i keep all my OS's on separate physical HDD's).



any ideas?
ps, i need ubuntu to run a robotics program (player/stage) for uni and i need it to work TODAY! aaaaaaaaarrrrrrrrrrgggggggggghhhhhhhhhhhhhh :eek:

---

### Post by liquidmonkey on 2009-09-08
here is the log...

```
09-08 16:20 INFO   root: === wubi 9.04 rev129 ===
09-08 16:20 DEBUG  root: Logfile is j:\users\bobby-~1\appdata\local\temp\wubi-9.04-rev129.log
09-08 16:20 DEBUG  root: sys.argv = ['main.pyo', '--exefile="J:\\Users\\bobby-blobby\\Desktop\\wubi.exe"']
09-08 16:20 DEBUG  CommonBackend: data_dir=J:\Users\BOBBY-~1\AppData\Local\Temp\pyl6B32.tmp\data
09-08 16:20 DEBUG  WindowsBackend: 7z=J:\Users\BOBBY-~1\AppData\Local\Temp\pyl6B32.tmp\bin\7z.exe
09-08 16:20 DEBUG  CommonBackend: Fetching basic info...
09-08 16:20 DEBUG  CommonBackend: original_exe=J:\Users\bobby-blobby\Desktop\wubi.exe
09-08 16:20 DEBUG  CommonBackend: platform=win32
09-08 16:20 DEBUG  CommonBackend: osname=nt
09-08 16:20 DEBUG  CommonBackend: language=sv_SE
09-08 16:20 DEBUG  CommonBackend: encoding=cp1252
09-08 16:20 DEBUG  WindowsBackend: arch=amd64
09-08 16:20 DEBUG  CommonBackend: Parsing isolist=J:\Users\BOBBY-~1\AppData\Local\Temp\pyl6B32.tmp\data\isolist.ini
09-08 16:20 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-08 16:20 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-08 16:20 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-08 16:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-08 16:20 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-08 16:20 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-08 16:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-08 16:20 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-08 16:20 DEBUG  WindowsBackend: Fetching host info...
09-08 16:20 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-08 16:20 DEBUG  WindowsBackend: windows version=vista
09-08 16:20 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-08 16:20 DEBUG  WindowsBackend: windows_sp=None
09-08 16:20 DEBUG  WindowsBackend: windows_build=7600
09-08 16:20 DEBUG  WindowsBackend: gmt=1
09-08 16:20 DEBUG  WindowsBackend: country=SE
09-08 16:20 DEBUG  WindowsBackend: timezone=Europe/Stockholm
09-08 16:20 DEBUG  WindowsBackend: windows_username=bobby-blobby
09-08 16:20 DEBUG  WindowsBackend: user_full_name=bobby-blobby
09-08 16:20 DEBUG  WindowsBackend: user_directory=bobby-blobby
09-08 16:20 DEBUG  WindowsBackend: windows_language_code=1053
09-08 16:20 DEBUG  WindowsBackend: windows_language=Swedish
09-08 16:20 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz
09-08 16:20 DEBUG  WindowsBackend: bootloader=vista
09-08 16:20 DEBUG  WindowsBackend: system_drive=Drive(J: hd 130300.710938 mb free )
09-08 16:20 DEBUG  WindowsBackend: drive=Drive(C: hd 178464.707031 mb free ntfs)
09-08 16:20 DEBUG  WindowsBackend: drive=Drive(D: hd 137464.785156 mb free ntfs)
09-08 16:20 DEBUG  WindowsBackend: drive=Drive(E: hd 116073.316406 mb free ntfs)
09-08 16:20 DEBUG  WindowsBackend: drive=Drive(F: hd 174436.316406 mb free ntfs)
09-08 16:20 DEBUG  WindowsBackend: drive=Drive(G: hd 24005.0898438 mb free ntfs)
09-08 16:20 DEBUG  WindowsBackend: drive=Drive(H: hd 45374.7851563 mb free ntfs)
09-08 16:20 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
09-08 16:20 DEBUG  WindowsBackend: drive=Drive(J: hd 130300.710938 mb free )
09-08 16:20 DEBUG  WindowsBackend: drive=Drive(L: hd 51107.703125 mb free ntfs)
09-08 16:20 DEBUG  WindowsBackend: drive=Drive(W: hd 145066.003906 mb free ntfs)
09-08 16:20 DEBUG  WindowsBackend: uninstaller_path=None
09-08 16:20 DEBUG  WindowsBackend: previous_target_dir=None
09-08 16:20 DEBUG  WindowsBackend: previous_distro_name=None
09-08 16:20 DEBUG  WindowsBackend: keyboard_id=69010461
09-08 16:20 DEBUG  WindowsBackend: keyboard_layout=se
09-08 16:20 DEBUG  WindowsBackend: keyboard_variant=
09-08 16:20 DEBUG  CommonBackend: locale=sv_SE.UTF-8
09-08 16:20 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
09-08 16:20 DEBUG  CommonBackend: Searching ISOs on USB devices
09-08 16:20 DEBUG  CommonBackend: Searching for local CDs
09-08 16:20 DEBUG  Distro:   checking whether C:\ is a valid Ubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether C:\ is a valid Ubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether C:\ is a valid Kubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether C:\ is a valid Kubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether C:\ is a valid Xubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether C:\ is a valid Xubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether C:\ is a valid Mythbuntu CD
09-08 16:20 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether C:\ is a valid Mythbuntu CD
09-08 16:20 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-08 16:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-08 16:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-08 16:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-08 16:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-08 16:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-08 16:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-08 16:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-08 16:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-08 16:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-08 16:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
09-08 16:20 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
09-08 16:20 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether J:\Users\BOBBY-~1\AppData\Local\Temp\pyl6B32.tmp is a valid Ubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain J:\Users\BOBBY-~1\AppData\Local\Temp\pyl6B32.tmp\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether J:\Users\BOBBY-~1\AppData\Local\Temp\pyl6B32.tmp is a valid Ubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain J:\Users\BOBBY-~1\AppData\Local\Temp\pyl6B32.tmp\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether J:\Users\BOBBY-~1\AppData\Local\Temp\pyl6B32.tmp is a valid Kubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain J:\Users\BOBBY-~1\AppData\Local\Temp\pyl6B32.tmp\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether J:\Users\BOBBY-~1\AppData\Local\Temp\pyl6B32.tmp is a valid Kubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain J:\Users\BOBBY-~1\AppData\Local\Temp\pyl6B32.tmp\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether J:\Users\BOBBY-~1\AppData\Local\Temp\pyl6B32.tmp is a valid Xubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain J:\Users\BOBBY-~1\AppData\Local\Temp\pyl6B32.tmp\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether J:\Users\BOBBY-~1\AppData\Local\Temp\pyl6B32.tmp is a valid Xubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain J:\Users\BOBBY-~1\AppData\Local\Temp\pyl6B32.tmp\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether J:\Users\BOBBY-~1\AppData\Local\Temp\pyl6B32.tmp is a valid Mythbuntu CD
09-08 16:20 DEBUG  Distro:     does not contain J:\Users\BOBBY-~1\AppData\Local\Temp\pyl6B32.tmp\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether J:\Users\BOBBY-~1\AppData\Local\Temp\pyl6B32.tmp is a valid Mythbuntu CD
09-08 16:20 DEBUG  Distro:     does not contain J:\Users\BOBBY-~1\AppData\Local\Temp\pyl6B32.tmp\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
09-08 16:20 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
09-08 16:20 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether W:\ is a valid Ubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether W:\ is a valid Ubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether W:\ is a valid Kubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether W:\ is a valid Kubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether W:\ is a valid Xubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether W:\ is a valid Xubuntu CD
09-08 16:20 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether W:\ is a valid Mythbuntu CD
09-08 16:20 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
09-08 16:20 DEBUG  Distro:   checking whether W:\ is a valid Mythbuntu CD
09-08 16:20 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
09-08 16:20 INFO   root: Running the installer...
09-08 16:20 DEBUG  WindowsFrontend: __init__...
09-08 16:20 DEBUG  WindowsFrontend: on_init...
09-08 16:21 DEBUG  WinuiInstallationPage: target_drive=L:, installation_size=17000MB, distro_name=Ubuntu, language=English, username=bobby-blobby
09-08 16:21 INFO   root: Received settings
09-08 16:21 DEBUG  TaskList: # Running tasklist...
09-08 16:21 DEBUG  TaskList: ## Running select_target_dir...
09-08 16:21 INFO   WindowsBackend: Installing into L:\ubuntu
09-08 16:21 DEBUG  TaskList: ## Finished select_target_dir
09-08 16:21 DEBUG  TaskList: ## Running create_dir_structure...
09-08 16:21 DEBUG  CommonBackend: Creating dir L:\ubuntu
09-08 16:21 DEBUG  CommonBackend: Creating dir L:\ubuntu\disks
09-08 16:21 DEBUG  CommonBackend: Creating dir L:\ubuntu\install
09-08 16:21 DEBUG  CommonBackend: Creating dir L:\ubuntu\install\boot
09-08 16:21 DEBUG  CommonBackend: Creating dir L:\ubuntu\disks\boot
09-08 16:21 DEBUG  CommonBackend: Creating dir L:\ubuntu\disks\boot\grub
09-08 16:21 DEBUG  CommonBackend: Creating dir L:\ubuntu\install\boot\grub
09-08 16:21 DEBUG  TaskList: ## Finished create_dir_structure
09-08 16:21 DEBUG  TaskList: ## Running uncompress_target_dir...
09-08 16:21 DEBUG  TaskList: ## Finished uncompress_target_dir
09-08 16:21 DEBUG  TaskList: ## Running create_uninstaller...
09-08 16:21 DEBUG  WindowsBackend: Copying uninstaller J:\Users\bobby-blobby\Desktop\wubi.exe -> L:\ubuntu\uninstall-wubi.exe
09-08 16:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString L:\ubuntu\uninstall-wubi.exe
09-08 16:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir L:\ubuntu
09-08 16:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
09-08 16:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon L:\ubuntu\Ubuntu.ico
09-08 16:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev129
09-08 16:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
09-08 16:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
09-08 16:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
09-08 16:21 DEBUG  TaskList: ## Finished create_uninstaller
09-08 16:21 DEBUG  TaskList: ## Running copy_installation_files...
09-08 16:21 DEBUG  WindowsBackend: Copying J:\Users\BOBBY-~1\AppData\Local\Temp\pyl6B32.tmp\data\custom-installation -> L:\ubuntu\install\custom-installation
09-08 16:21 DEBUG  WindowsBackend: Copying J:\Users\BOBBY-~1\AppData\Local\Temp\pyl6B32.tmp\winboot -> L:\ubuntu\winboot
09-08 16:21 ERROR  TaskList: writelines() argument must be a sequence of strings
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\win32\backend.py", line 152, in copy_installation_files
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 257, in replace_line_in_file
TypeError: writelines() argument must be a sequence of strings
09-08 16:21 DEBUG  TaskList: # Cancelling tasklist
09-08 16:21 DEBUG  TaskList: # Finished tasklist
09-08 16:21 ERROR  root: writelines() argument must be a sequence of strings
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 129, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
TypeError: writelines() argument must be a sequence of strings

```

---

### Post by shredder12 on 2009-09-08
have you tried checking the MD5 sum for the ISO you have downloaded..??
it could have got corrupted while downloading..

---

### Post by liquidmonkey on 2009-09-08
i should have mentioned i don't have a cd-drive on my PC.
does that matter?

also, i have extracted the iso file and everything went fine.
not sure how to do a MD5 check you mentioned.

---

### Post by shredder12 on 2009-09-08
No, a cd drive won't matter until you are installing using wubi..
and when you download the ISO from the website.. they must have mentioned an MD5 checksum...
You will find a lot of window softwares which check the MD5 checksums.
If they are equal... then at least the ISO is error free.
Actually, MD5 checksums.. let you compare softwares or files..

---

### Post by liquidmonkey on 2009-09-08
ok, that must be the problem then, the WUBI thing.
that is how i have been trying to install, by clicking on 'wubi.exe'

how else can i install UBUNTU?
man, i'm so new to this its embarrassing.

---

### Post by shredder12 on 2009-09-08
> **liquidmonkey said:**
> ok, that must be the problem then, the WUBI thing.
that is how i have been trying to install, by clicking on 'wubi.exe'

how else can i install UBUNTU?
man, i'm so new to this its embarrassing.

Well, I don't really know about wubi installation methods but it is a good way to install Ubuntu.. You can try reading the ubuntu community documentation
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

and you can even try booting ubuntu from a usb stick..
refer this link for more details..
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

There is nothing to be embarrassed about.... it was new for everyone once.. 

I would still suggest you to go for wubi.. ( until u find urself more comfortable with USB stick boot up)..

---

### Post by liquidmonkey on 2009-09-08
i just found the UNetbootin utility now. am trying it out since the whole WUBI thing is just not working at all no matter what config i put in :(

thanks for the info!!

---

### Post by liquidmonkey on 2009-09-09
ok, have managed to get UBUNTU9.04 to boot from my USB which is great!
however, i get stuck at step 4 of 7, the 'prepare partitions' section.

i'm trying to install onto a HDD that is physically separate from my win7 HDD. the error message i get when trying to choose a partition on that HDD is...

no root file system is defined


i tried going in to the partition options and choosing NTFS but no luck.
do i need to format the HDD in FAT32 or does NTFS work fine?

any other hints?

---

