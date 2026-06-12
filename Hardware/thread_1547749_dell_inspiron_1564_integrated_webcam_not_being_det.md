---
title: "dell inspiron 1564 integrated webcam not being detected"
date: 2010-08-07
forum: Hardware
---

### Post by nomi_scorpio on 2010-08-07
hi all. i need help about my integrated webcam drivers. i have spent many time searching for my prob but couldn't solve it. i installed ubuntu 9.10 recently. the problem is that my integrated webcam and microphone are not being detected. i tried cheese, camorama webcam viewer and skype.. its like that webcam drivers are not installed. and i couldn't find any drivers. 
camorama gives the error: could not connect to video device(/dev/video0)
cheese also says No camera found!

reading other threads i found that lsusb comand output might help so here is its output..

Bus 002 Device 003: ID 1c4f:0003 SiGma Micro 
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 003: ID 0c45:641d Microdia 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

hope to hear from someone soon...

id:nauman-laptop
       description: Portable Computer     product: Inspiron 1564     vendor: Dell Inc.     version: A10

---

### Post by nomi_scorpio on 2010-08-07
i desperately need help :S

---

### Post by utilitytrack on 2010-08-07
Post here some diagnostical info:
```
$ uname -r
$ lspci -nn
$ dmesg | egrep -i 'cam|video|0003|641d'
# lsmod | egrep 'cam|video|v4l'
$ dpkg -l *v4l*
$ ls -l /dev/video*
# grep -e video /etc/group
$ ls -l /dev/v4l/by-id/* && ls -l /dev/v4l/by-path/*

```

Please say do you use a auxilary display (connected to VGA port)?

Also try make test record:
```
$ luvcview -l
```

And don't forget configure settings of video capture in [FONT="Courier New"]gstreamer-properties[/FONT] (go to Video tab, change Plugin (v4l or v4l2) and press Test). Give here your impressions.

---

### Post by elzear on 2010-08-15
Hello I have the same issue with dell 1564.

> lsusb
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 007: ID 413c:8160 Dell Computer Corp. 
Bus 001 Device 006: ID 413c:8162 Dell Computer Corp. 
Bus 001 Device 005: ID 413c:8161 Dell Computer Corp. 
Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub> $ uname -r
2.6.32-23-generic-pae> $ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 12)
00:01.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express x16 Root Port [8086:0045] (rev 12)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 06)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 06)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 06)
00:1c.5 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 [8086:3b4c] (rev 06)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 06)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a6)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 06)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 06)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 06)
02:00.0 VGA compatible controller [0300]: ATI Technologies Inc M92 LP [Mobility Radeon HD 4300 Series] [1002:9552]
02:00.1 Audio device [0403]: ATI Technologies Inc RV710/730 [1002:aa38]
04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
ff:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 02)
ff:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 02)
ff:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 02)> dmesg | egrep -i 'cam|video|0003|641d'
[    0.000000]   AMD AuthenticAMD
[    0.000000] init_memory_mapping: 0000000000000000-00000000379fe000
[    0.000000] Move RAMDISK from 0000000037862000 - 0000000037fefe54 to 0093c000 - 010c9e54
[    0.000000] ACPI: HPET bf7fecfa 00038 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG bf7fed32 0003C (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: SSDT bf7e3000 009F1 (v01  PmRef    CpuPm 00003000 INTL 20060912)
[    0.000000]   Normal   0x00001000 -> 0x000379fe
[    0.000000]   HighMem  0x000379fe -> 0x00138000
[    0.000000] Initializing HighMem for node 0 (000379fe:00138000)
[    0.000031] AppArmor: AppArmor initialized
[    0.000037] Mount-cache hash table entries: 512
[    0.610132] pci 0000:02:00.0: Boot video device
[    0.626553] ACPI: SSDT bf71ac18 003A0 (v01  PmRef  Cpu0Ist 00003000 INTL 20060912)
[    0.627116] ACPI: SSDT bf718698 005EC (v01  PmRef  Cpu0Cst 00003001 INTL 20060912)
[    0.628275] ACPI: SSDT bf719a98 00303 (v01  PmRef    ApIst 00003000 INTL 20060912)
[    0.628741] ACPI: SSDT bf717d98 00119 (v01  PmRef    ApCst 00003000 INTL 20060912)
[    2.083265] generic-usb 0003:413C:8161.0001: input,hidraw0: USB HID v1.11 Keyboard [HID 413c:8161] on usb-0000:00:1a.0-1.1.1/input0
[    2.086100] generic-usb 0003:413C:8162.0002: input,hidraw1: USB HID v1.11 Mouse [HID 413c:8162] on usb-0000:00:1a.0-1.1.2/input0
[   13.000319] input: Dell WMI hotkeys as /devices/virtual/input/input8
[   13.356455] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/LNXVIDEO:00/input/input9
[   13.356529] ACPI: Video Device [M86] (multi-head: yes  rom: no  post: no)> lsmod | egrep 'cam|video|v4l'
video                  17375  0 
output                  1871  1 video
> dpkg -l *v4l*
Wybór=U=Nieznany/I=Instalacja/R=Usuni&#281;cie/P=Wyczyszczenie/H=Zatrzymanie
| Stan=N=Brak/I=Zainst./C=Skonfig./U=Rozpak./F=Nieskonfig./H=Wpó&#322;-zainst./W=Wyzw-czek/T=Wyzw-zapl
|/ B&#322;&#281;dy?=(brak)/H=Wstrzym./R=Do przeinst. (Stan,B&#322;&#281;dy:wielk.lit.=&#378;le)
||/ Nazwa          Wersja         Opis
+++-==============-==============-============================================
ii  libv4l-0       0.6.4-1ubuntu1 Collection of video4linux support libraries
un  xserver-xorg-d <brak>         (brak dost&#281;pnego opisu)
ii  xserver-xorg-v 1:0.2.0-4      X.Org X server -- Video 4 Linux display driv> ls -l /dev/video*
ls: nie ma dost&#281;pu do /dev/video*: No such file or directory
> # grep -e video /etc/group
video:x:44:
> ls -l /dev/v4l/by-id/* && ls -l /dev/v4l/by-path/*
ls: nie ma dost&#281;pu do /dev/v4l/by-id/*: No such file or directory
> luvcview -l
luvcview 0.2.6

SDL information:
  Video driver: x11
  A window manager is available
Device information:
  Device path:  /dev/video0
ERROR opening V4L interface: No such file or directory
I don't use VGA connector.
I upgrade ubuntu from 9.10 to 10.04 i don't know that drivers works before (don't check).

I check gstreamer-properties and check all thinks there but when I click test i saw only pixels.

Can anybody help me? :)

---

### Post by jimned on 2011-04-03
Has anyone found a solution.  I have the same problem with my Dell 1564 web cam with Ubuntu 10.10

---

### Post by jimned on 2011-04-10
Solved. Web cam working. Included other repositories in update options. Next set of updates included files for Skype.  Camera works fine!

---

### Post by kokonobs on 2011-05-07
> **jimned said:**
> Solved. Web cam working. Included other repositories in update options. Next set of updates included files for Skype.  Camera works fine!

How do you mean you added the other repositories? I'm struggling with this issue.

---

### Post by kokonobs on 2011-07-02
For anyone still having issues with this.. I followed the instructions here

[http://stemp.wordpress.com/2009/11/03/karmic-get-the-latest-drivers-for-gspca-uvc-usbvideo-and-other/](http://stemp.wordpress.com/2009/11/03/karmic-get-the-latest-drivers-for-gspca-uvc-usbvideo-and-other/)

So far everything is working perfectly. I did not understand what it all does but all i know is that it works great. 

It might be necessary to repeat it when there is a kernel update (someone with more knowledge please confirm)

Thanks

UPDATE: This did not provide a lasting solution. It just remained as it was, working randomly every now and then. But alas the root of the problem has been found and its not software related. see dell support link below, post by medic29

[http://en.community.dell.com/support-forums/laptop/f/3518/p/19353884/19891390.aspx?PageIndex=1]("http://en.community.dell.com/support-forums/laptop/f/3518/p/19353884/19891390.aspx?PageIndex=1")

---

