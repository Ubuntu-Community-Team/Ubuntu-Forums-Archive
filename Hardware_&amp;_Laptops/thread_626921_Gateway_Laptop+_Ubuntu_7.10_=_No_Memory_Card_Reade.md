---
title: "Gateway Laptop+ Ubuntu 7.10 = No Memory Card Reader Support"
date: 2007-11-29
forum: Hardware &amp; Laptops
---

### Post by crowbarn on 2007-11-29
Hello all,

Running Gutsy Gibbon on my Gateway 4640GZ Laptop, and the on-board MiniSD memory card reader doesn't seem to be supported.  

I ran lspci and received this info:
> 00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
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
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:07.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
02:07.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
02:07.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 01)
02:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:09.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

Can anyone help me figure out how to address the problem and solve it?  

Thank you.

---

### Post by crowbarn on 2007-11-29
On another forum, I was advised that this may work to fix the problem.  I'm a newbie to Linux/Ubuntu, so could anyone help spell out the steps that he has outlined here?  I'd hate to FUBAR something.

> Depends on the model of your card reader, but for mine this is what I had to do in order to get mine to work. I had to make an init script for it to see it. This is what my init script is:

Code:
```

#!/bin/sh

setpci -s 0b:00.3 4c.b=0x02

exit 0

```
And then link that to an S startup script in rc#.d where # is whatever init level your system comes up in. (usually 3 for text, 5 for X windows).

You can find what address needs to go after the -s in the setpci command by typing lspci and finding where your card reader is in the list.

Oh yeah, I forgot to add the common sense stuff (if you know Linux pretty well):

The S link is to start it at boot time so your card reader always works at boot time. Those S links are found in /etc/rc3.d for init level 3 and /etc/rc5.d for init level 5. You also need to make sure you do a chmod 755 on the init script itself, to set it executable. You can run the script and it will take effect and give you your card reader immediately so you don't have to reboot for it to start working.



---

