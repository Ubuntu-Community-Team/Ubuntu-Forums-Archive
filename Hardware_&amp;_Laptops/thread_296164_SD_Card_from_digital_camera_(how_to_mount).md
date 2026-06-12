---
title: "SD Card from digital camera (how to mount?)"
date: 2006-11-09
forum: Hardware &amp; Laptops
---

### Post by gray380 on 2006-11-09
Hi Mighty All!

Is there any possibility to mount SD card under Ubuntu 6.06? 
Which device I should use? 

When I insert card in the slot the following messages is appeared:

> 
Nov  2 09:57:30 localhost kernel: [17191533.024000] pccard: PCMCIA card inserted into slot 0
Nov  2 09:57:30 localhost kernel: [17191533.024000] cs: memory probe 0xd0200000-0xd02fffff: excluding 0xd0200000-0xd020ffff
Nov  2 09:57:30 localhost kernel: [17191533.024000] pcmcia: registering new device pcmcia0.0


But automount does not work.

A liitle more information about my system:
> 
~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
0000:00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
0000:00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to AGP Controller (rev 02)
0000:00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
0000:00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
0000:00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
0000:00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
[B]0000:02:07.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
0000:02:07.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)[/B]
0000:02:07.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 01)
0000:02:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:09.0 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)


> 
~$ uname -a
Linux SomeHost 2.6.15-27-686 #1 SMP PREEMPT Sat Sep 16 02:13:27 UTC 2006 i686 GNU/Linux


brg,
Serhiy.

---

### Post by Najand on 2006-11-09
Hmm after plugging it to your computer can you send a copy of your "sudo fdisk -l" output here?

---

### Post by gray380 on 2007-01-24
> **Najand said:**
> Hmm after plugging it to your computer can you send a copy of your "sudo fdisk -l" output here?


&#1044;&#1080;&#1089;&#1082; /dev/hda: 80.0 &#1043;&#1073;, 80060424192 &#1073;&#1072;&#1081;&#1090;
255 &#1075;&#1086;&#1083;&#1086;&#1074;&#1086;&#1082;, 63 &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;&#1110;&#1074;/&#1076;&#1086;&#1088;&#1110;&#1078;&#1082;&#1091;, 9733 &#1094;&#1080;&#1083;&#1110;&#1085;&#1076;&#1088;&#1110;&#1074;
&#1054;&#1076;&#1080;&#1085;&#1080;&#1094;&#1110; &#1074;&#1080;&#1084;&#1110;&#1088;&#1091; = &#1094;&#1080;&#1083;&#1110;&#1085;&#1076;&#1088;&#1080; &#1079; 16065 * 512 = 8225280 &#1073;&#1072;&#1081;&#1090;

&#1055;&#1088;&#1080;&#1089;&#1090;&#1088;&#1110;&#1081; &#1047;&#1072;&#1074;&#1072;&#1085;&#1090;  &#1055;&#1086;&#1095;&#1072;&#1090;&#1086;&#1082;     &#1050;&#1110;&#1085;&#1077;&#1094;&#1100;     &#1041;&#1083;&#1086;&#1082;&#1110;&#1074;  &#1030;&#1076;  &#1057;&#1080;&#1089;&#1090;&#1077;&#1084;&#1072;
/dev/hda1   *           1        4867    39094146    7  HPFS/NTFS
/dev/hda2            4868        5475     4883760   83  Linux
/dev/hda3            5476        5597      979965   82  Linux swap / Solaris
/dev/hda4            5598        9733    33222420    5  Extended
/dev/hda5            5598        9733    33222388+  83  Linux

That's all.

---

### Post by gray380 on 2007-01-25
I have found the [**_answer_**]("http://tuxmobil.org/mmc_sd_card_unix.html") to the issue. Sadly.

---

