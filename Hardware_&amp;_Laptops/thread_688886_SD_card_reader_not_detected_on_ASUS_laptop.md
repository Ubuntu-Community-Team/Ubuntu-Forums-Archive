---
title: "SD card reader not detected on ASUS laptop"
date: 2008-02-05
forum: Hardware &amp; Laptops
---

### Post by richardy on 2008-02-05
Hi,
I recently installed Xubuntu 7.10 (Gutsy) on an Asus Z9100L laptop and found that the SD card reader was not being detected correctly. The dump from LSPCI confirms this although it seems like the card reader is being incorectly detected as a second  PCMCIA (cardbus) port (see below). There is also a dump from the DMESG | tail, command when the sd card was removed and replaced a few times (see below).

Is there a work around for this problem. Any help would be much apreciated.

Cheers.

richard@zen:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
01:05.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
01:05.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
01:05.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 04) 

richard@zen:~$ dmesg | tail
[ 4278.416000] pccard: card ejected from slot 0
[ 4323.036000] pccard: PCMCIA card inserted into slot 0
[ 4323.036000] pcmcia: registering new device pcmcia0.0
[ 4848.008000] pccard: card ejected from slot 0
[ 4855.364000] pccard: PCMCIA card inserted into slot 0
[ 4855.364000] pcmcia: registering new device pcmcia0.0
[ 4858.016000] pccard: card ejected from slot 0
[ 4865.220000] pccard: PCMCIA card inserted into slot 0
[ 4865.220000] pcmcia: registering new device pcmcia0.0

---

