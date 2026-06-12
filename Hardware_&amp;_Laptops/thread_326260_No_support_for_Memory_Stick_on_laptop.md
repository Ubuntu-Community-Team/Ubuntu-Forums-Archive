---
title: "No support for Memory Stick on laptop"
date: 2006-12-27
forum: Hardware &amp; Laptops
---

### Post by KenSentMe on 2006-12-27
I have an Asus A6jc laptop which has a built-in card reader. In Windows it supports both SD and Memory Stick cards, but in Ubuntu (Edgy) only the SD cards works. Inserting a Memory Stick Pro doesn't do anything in dmesg.

This is my lspci:

> 
jeroen@lisa2-ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 01d7 (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. Unknown device 8168 (rev 01)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
04:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
04:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
04:01.2 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
04:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)


As you can see in the bottom line, the MS adapter is detected, but it doesn't seem to work properly.

What can i do to solve this or is there a place i can file a bug for the problem?

---

### Post by KenSentMe on 2006-12-28
Bump

Is there nobody who can help me in the right direction?

---

### Post by KenSentMe on 2006-12-29
Bump again

---

### Post by KenSentMe on 2006-12-29
Ok. I reported this bug on the Linux-source-2.6.20. Hope it will be fixed soon.

[https://bugs.launchpad.net/distros/ubuntu/+source/linux-source-2.6.20/+bug/77391](https://bugs.launchpad.net/distros/ubuntu/+source/linux-source-2.6.20/+bug/77391)

---

### Post by senzapadroni on 2007-01-05
I've an Asus A6JC Q008H and I've noticed the same issue: I hope for fixing too.
Thank you for reporting on Launchpad.

Bye bye

---

### Post by straxus on 2007-01-13
Same issue on an Asus A8Js.

---

### Post by VuDu on 2007-02-11
And on ASUS A6Vc :(

> 01:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
01:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
01:01.2 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
01:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)

---

