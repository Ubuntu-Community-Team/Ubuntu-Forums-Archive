---
title: "wubi shows &quot;no disks&quot;"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by yangyangzhzh on 2009-10-31
Can anyone help me?
I have downloaded the ubuntu-desktop-9.10 iso file and the wubi.exe file.And I have checked the md5sum.
But when i want to install wubi-ubuntu,after clicking the wubi icon I just get the error "no disk",and three bottoms showing"cancel","try again","continue".
 I am using vista,and run the program as administrator.
Thanks for help.

Here is the file C:\Users\lenovo\AppData\Local\Temp\wubi-9.10ubuntu1-rev160.log
```

10-31 13:39 INFO   root: === wubi 9.10ubuntu1 rev160 ===
10-31 13:39 DEBUG  root: Logfile is c:\users\lenovo\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
10-31 13:39 DEBUG  root: sys.argv = ['main.pyo', '--exefile="J:\\wubi.exe"']
10-31 13:39 DEBUG  CommonBackend: data_dir=C:\Users\lenovo\AppData\Local\Temp\pyl8593.tmp\data
10-31 13:39 DEBUG  WindowsBackend: 7z=C:\Users\lenovo\AppData\Local\Temp\pyl8593.tmp\bin\7z.exe
10-31 13:39 DEBUG  CommonBackend: Fetching basic info...
10-31 13:39 DEBUG  CommonBackend: original_exe=J:\wubi.exe
10-31 13:39 DEBUG  CommonBackend: platform=win32
10-31 13:39 DEBUG  CommonBackend: osname=nt
10-31 13:39 DEBUG  CommonBackend: language=zh_CN
10-31 13:39 DEBUG  CommonBackend: encoding=cp936
10-31 13:39 DEBUG  WindowsBackend: arch=amd64
10-31 13:39 DEBUG  CommonBackend: Parsing isolist=C:\Users\lenovo\AppData\Local\Temp\pyl8593.tmp\data\isolist.ini
10-31 13:39 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-31 13:39 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-31 13:39 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-31 13:39 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-31 13:39 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-31 13:39 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-31 13:39 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-31 13:39 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-31 13:39 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
10-31 13:39 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
10-31 13:39 DEBUG  WindowsBackend: Fetching host info...
10-31 13:39 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-31 13:39 DEBUG  WindowsBackend: windows version=vista
10-31 13:39 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Premium
10-31 13:39 DEBUG  WindowsBackend: windows_sp=Service Pack 1
10-31 13:39 DEBUG  WindowsBackend: windows_build=6001
10-31 13:39 DEBUG  WindowsBackend: gmt=8
10-31 13:39 DEBUG  WindowsBackend: country=CN
10-31 13:39 DEBUG  WindowsBackend: timezone=Asia/Shanghai
10-31 13:39 DEBUG  WindowsBackend: windows_username=lenovo
10-31 13:39 DEBUG  WindowsBackend: user_full_name=lenovo
10-31 13:39 DEBUG  WindowsBackend: user_directory=C:\Users\lenovo
10-31 13:39 DEBUG  WindowsBackend: windows_language_code=1028
10-31 13:39 DEBUG  WindowsBackend: windows_language=Chinese (Traditional)
10-31 13:39 DEBUG  WindowsBackend: processor_name=Genuine Intel(R) CPU            2140  @ 1.60GHz
10-31 13:39 DEBUG  WindowsBackend: bootloader=vista
10-31 13:39 DEBUG  WindowsBackend: system_drive=Drive(C: hd 18707.2695313 mb free ntfs)
10-31 13:39 DEBUG  WindowsBackend: drive=Drive(C: hd 18707.2695313 mb free ntfs)
10-31 13:39 DEBUG  WindowsBackend: drive=Drive(D: hd 59875.1914063 mb free ntfs)
10-31 13:39 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
10-31 13:39 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
10-31 13:39 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
10-31 13:39 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
10-31 13:39 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
10-31 13:39 DEBUG  WindowsBackend: drive=Drive(J: hd 56083.7695313 mb free ntfs)
10-31 13:39 DEBUG  WindowsBackend: drive=Drive(K: hd 57494.140625 mb free ntfs)
10-31 13:39 DEBUG  WindowsBackend: drive=Drive(L: cd 0.0 mb free )
10-31 13:39 DEBUG  WindowsBackend: uninstaller_path=None
10-31 13:39 DEBUG  WindowsBackend: previous_target_dir=None
10-31 13:39 DEBUG  WindowsBackend: previous_distro_name=None
10-31 13:39 DEBUG  WindowsBackend: keyboard_id=134481924
10-31 13:39 DEBUG  WindowsBackend: keyboard_layout=cn
10-31 13:39 DEBUG  WindowsBackend: keyboard_variant=
10-31 13:39 DEBUG  CommonBackend: python locale=('zh_CN', 'cp936')
10-31 13:39 DEBUG  CommonBackend: locale=zh_CN.UTF-8
10-31 13:39 DEBUG  WindowsBackend: total_memory_mb=1021.38671875
10-31 13:39 DEBUG  CommonBackend: Searching ISOs on USB devices
10-31 13:39 DEBUG  Distro:   checking Ubuntu ISO J:\ubuntu-9.10-desktop-i386.iso
10-31 13:39 DEBUG  WindowsBackend:   extracting .disk\info from J:\ubuntu-9.10-desktop-i386.iso
10-31 13:39 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
10-31 13:39 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
10-31 13:39 INFO   Distro: Found a valid iso for Ubuntu: J:\ubuntu-9.10-desktop-i386.iso
10-31 13:39 DEBUG  CommonBackend: Searching for local CDs
10-31 13:39 DEBUG  Distro:   checking whether C:\Users\lenovo\AppData\Local\Temp\pyl8593.tmp is a valid Ubuntu CD
10-31 13:39 DEBUG  Distro:     does not contain C:\Users\lenovo\AppData\Local\Temp\pyl8593.tmp\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether C:\Users\lenovo\AppData\Local\Temp\pyl8593.tmp is a valid Ubuntu CD
10-31 13:39 DEBUG  Distro:     does not contain C:\Users\lenovo\AppData\Local\Temp\pyl8593.tmp\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether C:\Users\lenovo\AppData\Local\Temp\pyl8593.tmp is a valid Ubuntu Netbook Remix CD
10-31 13:39 DEBUG  Distro:     does not contain C:\Users\lenovo\AppData\Local\Temp\pyl8593.tmp\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether C:\Users\lenovo\AppData\Local\Temp\pyl8593.tmp is a valid Kubuntu CD
10-31 13:39 DEBUG  Distro:     does not contain C:\Users\lenovo\AppData\Local\Temp\pyl8593.tmp\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether C:\Users\lenovo\AppData\Local\Temp\pyl8593.tmp is a valid Kubuntu CD
10-31 13:39 DEBUG  Distro:     does not contain C:\Users\lenovo\AppData\Local\Temp\pyl8593.tmp\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether C:\Users\lenovo\AppData\Local\Temp\pyl8593.tmp is a valid Kubuntu Netbook CD
10-31 13:39 DEBUG  Distro:     does not contain C:\Users\lenovo\AppData\Local\Temp\pyl8593.tmp\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether C:\Users\lenovo\AppData\Local\Temp\pyl8593.tmp is a valid Xubuntu CD
10-31 13:39 DEBUG  Distro:     does not contain C:\Users\lenovo\AppData\Local\Temp\pyl8593.tmp\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether C:\Users\lenovo\AppData\Local\Temp\pyl8593.tmp is a valid Xubuntu CD
10-31 13:39 DEBUG  Distro:     does not contain C:\Users\lenovo\AppData\Local\Temp\pyl8593.tmp\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether C:\Users\lenovo\AppData\Local\Temp\pyl8593.tmp is a valid Mythbuntu CD
10-31 13:39 DEBUG  Distro:     does not contain C:\Users\lenovo\AppData\Local\Temp\pyl8593.tmp\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether C:\Users\lenovo\AppData\Local\Temp\pyl8593.tmp is a valid Mythbuntu CD
10-31 13:39 DEBUG  Distro:     does not contain C:\Users\lenovo\AppData\Local\Temp\pyl8593.tmp\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-31 13:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-31 13:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
10-31 13:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-31 13:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-31 13:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
10-31 13:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-31 13:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-31 13:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-31 13:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-31 13:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-31 13:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-31 13:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
10-31 13:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-31 13:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-31 13:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
10-31 13:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-31 13:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-31 13:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-31 13:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-31 13:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-31 13:39 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-31 13:39 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
10-31 13:39 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-31 13:39 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-31 13:39 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
10-31 13:39 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-31 13:39 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-31 13:39 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-31 13:39 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-31 13:39 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-31 13:39 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-31 13:39 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook Remix CD
10-31 13:39 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-31 13:39 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-31 13:39 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
10-31 13:39 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-31 13:39 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-31 13:39 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-31 13:39 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-31 13:39 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-31 13:39 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-31 13:39 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-31 13:39 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook Remix CD


```

---

### Post by garvinrick4 on 2009-10-31
Put your disk in and see if it asks you if you want to use WUBI and say yes.
Pick a password, pick how much space allocated for ubuntu.

Will boot from Vista's grubdos4. Have first option of Windows second option ubuntu.

highlight ubuntu. enter at login screen then password. Off you go.

Ubuntu will be in C: drive next to Users in Windows. Let me know if you find a problem.

I have done it quite a bit never had a problem. 

It is like an Application in Windows. Can uninstall if you make a mess of it. Will not effect your machine. Always make sure you pick WUBI. If not it will go into asking you how you
want your partitions.

---

### Post by yangyangzhzh on 2009-10-31
But what's the meaning of"put my disk in"?
i have the hard disk on my computer already......

---

### Post by SwedO on 2009-10-31
Do you have a card-reader? In that case click the symbol in systray and "safely remove hardware".

---

### Post by yangyangzhzh on 2009-11-01
> **SwedO said:**
> Do you have a card-reader? In that case click the symbol in systray and "safely remove hardware".
yes!! It does really work!!
Thank you very much.
I was so execited that i forgot to say thank you yesterday......

---

### Post by SwedO on 2009-11-02
Great! I had that "no disks"-problem myself...

---

