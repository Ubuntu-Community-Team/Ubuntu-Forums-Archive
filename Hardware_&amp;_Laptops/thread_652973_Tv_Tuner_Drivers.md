---
title: "Tv Tuner Drivers"
date: 2007-12-29
forum: Hardware &amp; Laptops
---

### Post by kyrhash on 2007-12-29
i got a Pinnacle PCTV HD PCI card (WORST BUY brand) for christmas. I installed it into the pc. Does anyone know a  way to check if it is supported/properly installed. It is semi-new and may need drivers but i have no idea where to find them. hoping to install mythtv. I am running ubuntu 7.10 64 bit version if that makes a difference. Thanks in advance for the help.

---

### Post by w4ett on 2007-12-29
The first thing to do is check if it being recognized.  The terminal command:
```

lspci
```

will let you know in a jiffy.  Then install the mythtv package and give it a go!

Let us know how you get on.  Good Luck!

---

### Post by kyrhash on 2007-12-29
lspci output:
#00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 7100 GS (rev a1)
02:00.0 SATA controller: JMicron Technologies, Inc. JMB361 AHCI/IDE (rev 02)
02:00.1 IDE interface: JMicron Technologies, Inc. JMB361 AHCI/IDE (rev 02)
03:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)#

---

### Post by kyrhash on 2007-12-29
doesnt seem to be recognizing the card does it?

---

### Post by nick_h on 2007-12-30
I posted in your [other thread](http://ubuntuforums.org/showthread.php?t=652509).  Was your card listed on the linuxtv.org site?

---

### Post by kyrhash on 2007-12-30
<http://linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_Card_%28800i%29> that seems to be my card and it says that it is unsupported. :(.  Thanks for the Definitive link though.  anybody know if there is hope for support of the card?

---

### Post by nick_h on 2007-12-30
It may be worth asking on the #linuxtv IRC channel.  They can be very helpful, but you have to be patient in waiting for a reply.

---

