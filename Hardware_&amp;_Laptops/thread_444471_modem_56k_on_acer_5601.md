---
title: "modem 56k on acer 5601"
date: 2007-05-15
forum: Hardware &amp; Laptops
---

### Post by corninos on 2007-05-15
hi, i have a problem my modem doesn't work who i can lets work it??
i have a laptop acer aspire 5601AWLMi

this is lspci
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0a:09.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

```
lsusb
```
Bus 005 Device 004: ID 046d:0892 Logitech, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 062a:0000 Creative Labs Optical Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

tanks for help

---

### Post by corninos on 2007-05-15
pleaseeee.....:confused:

---

### Post by scunc_dvl on 2007-05-21
Sorry I've done hours of googling and this is all I have, no real solution :P

From using scanModem, I got this from SoftModem.txt (Scanmodem seems to spit out a lot of extra junk I don't need to read through). It does not look so good...



[INDENT]-----------------------------------------------------
8086:2668   Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) HDA Controller
****8086:27d8   Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller****
1002:437b   Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
10de:026c   nVidia Corporation MCP51 High Definition Audio
----------------------------------------------------
are the members of this family encountered as of September 2006.
From the file  /proc/asound/card0/codec#1/, there are the following Subsystem chips:

  Vendor IDs  Chip maker     Support type
  ----------  ----------    -------------
  0x14f12bfa  Conexant      hsfmodem , not slmodemd compatible
  0x11c13026  AgereSystems  snd-hda-intel, slmodemd
  0x163c3055  Smartlink         "             "
  0x163c3155    "               "             "
  0x10573055  Motorola          "             "
  0x10573155     "              "             "
[/INDENT]

When I looked at the Vendor ID in that file for my modem (in a new HP dv9000), mine was 0x14f15045, which is (I'm 80% certain) is another Conexant chipset and I'll probably have to pay linuxant.com for a nice modem driver. (Bad news :( )

Apparantly, slmodemd may work for some of the intel chipsets (here -> [https://help.ubuntu.com/community/DialupModemHowto/AlsaModem](https://help.ubuntu.com/community/DialupModemHowto/AlsaModem) ) and that would be nice to have working, but I'm using 64-bit so I can't find any appropriate slmodem packates.

---

### Post by fleiterr on 2007-08-15
howto

[http://ubuntuforums.org/showthread.php?p=2756636](http://ubuntuforums.org/showthread.php?p=2756636)

---

