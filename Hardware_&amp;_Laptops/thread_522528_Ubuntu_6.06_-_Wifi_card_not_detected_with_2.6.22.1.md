---
title: "Ubuntu 6.06 - Wifi card not detected with 2.6.22.1 kernel"
date: 2007-08-10
forum: Hardware &amp; Laptops
---

### Post by yaustar on 2007-08-10
I have recently compiled a new kernel with this guide for the tickless feature:
[http://howtoforge.com/kernel_compilation_ubuntu](http://howtoforge.com/kernel_compilation_ubuntu)

The new kernel doesn't show my Wifi card in Network Settings although it is listed in lspci. After a little digging I found that my modules.alias file in /lib/module/2.6.22.1-custom doesn't list any:

alias pci:v00008086d00001043sv00008086sd00002701bc*sc*i* ipw2200

lines. Any ideas?

Cheers

---

### Post by moore.bryan on 2007-08-10
*what kind of wifi card do you have?*

---

### Post by yaustar on 2007-08-10
0000:01:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)

---

### Post by moore.bryan on 2007-08-10
*my lspci has a very similar line, but that's not my card/chipset... is there a line for "ethernet controller?"*

---

### Post by yaustar on 2007-08-10
```
yaustar@yau-ulaptop:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
0000:00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
0000:00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
0000:00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
0000:00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
0000:00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
0000:00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
0000:01:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)
0000:01:05.0 CardBus bridge: O2 Micro, Inc. OZ711M1/MC1 4-in-1 MemoryCardBus Controller (rev 20)
0000:01:05.1 CardBus bridge: O2 Micro, Inc. OZ711M1/MC1 4-in-1 MemoryCardBus Controller (rev 20)
0000:01:05.2 System peripheral: O2 Micro, Inc. OZ711Mx 4-in-1 MemoryCardBus Accelerator
0000:01:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
yaustar@yau-ulaptop:~$

```
The entire lspci output.

---

### Post by moore.bryan on 2007-08-11
> **yaustar said:**
> ```
0000:01:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```The entire lspci output.
*that's the line we're looking for... you have a realtek chipdet.  what kind of laptop is this?  realtek is very common in dell inspiron laptops.  whether or not that's the case, [this thread]("http://ubuntuforums.org/showthread.php?t=297092") might be of help.*

---

### Post by yaustar on 2007-08-11
The wireless works using the default kernel with 6.06. It doesn't using the kernel I compiled and I can't figure out way as it uses the same config as the default kernel. It seems like the module for ipw2200 didn't exist :/

Anyway, I cheated and installed 7.10 Tribe 4 since 7.04 wouldn't boot half the time. Now wireless works out of the box as expected :)

---

### Post by moore.bryan on 2007-08-11
*not sure why your compiled kernel isn't working, but i'm glad to hear you were able to work it out!*

---

