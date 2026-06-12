---
title: "Firewire disk not being seen."
date: 2017-03-02
forum: Hardware
---

### Post by lgbowden on 2017-03-02
This is for Lubuntu on a system that is very old and I use as a server so basically comprises. 2 x 866MHz P3 processors with 1GB RAMBUS memory. Also has a DVD/IDE burner and a AIT/IDE tape drive. AGP graphics card. Boot disk is a 16GB Compact Flash card. 

There's a PCI SATA card with two 1TB disks attached which are RAIDed with madam and served using Samba.

The system really predates USB so one PCI slot has a four port USB card and another has a USB/Firewire combi card with two of each ports on the outside and one of each internally.

I have an external disk caddy that is both USB and Firewire (but can't be both at the same time) and would prefer to use the firewire side of things and keep the USB free.

When this caddy is connected to any of the USB ports in either card all is fine. When I do the same but use the Firewire side nothing. I believe the caddy/disk/cable are OK as they do connect to a second system running Trisquel Lite linux and a four port PCI Firewire card - it's blistering.

What steps do I need to do to ensure Firewire is actually ok. This is what I have done so far.

 cat /proc/version
Linux version 4.8.0-39-generic (buildd@lgw01-52) (gcc version 6.2.0 20161005 (Ubuntu 6.2.0-5ubuntu12) ) #42-Ubuntu SMP Mon Feb 20 11:46:49 UTC 2017

 lspci | grep -E -i "(1394|firewire)"
02:08.4 FireWire (IEEE 1394): ULi Electronics Inc. M5253 P1394 OHCI 1.1 Controller

So there is basic visibility of the card.

 lsmod | grep -E -i "(1394|firewire)"
firewire_ohci          36864  0
firewire_core          65536  1 firewire_ohci
crc_itu_t              16384  1 firewire_core

 dmesg | grep -E -i "(1394|firewire)"
[   10.116126] firewire_ohci 0000:02:08.4: added OHCI v1.10 device as card 0, 4 IR + 8 IT contexts, quirks 0x1, physUB
[   10.624400] firewire_core 0000:02:08.4: created device fw0: GUID 0030bd0518001b30, S400

There's a device called /dev/fw0 but I don't see any devices like /dev/sdd1 which is what I see on the TriSquel Lite system. I tried to mount fw0 with out much optimisim and it failed as not a block device. 

 grep firewire /var/log/kern.log
Mar  1 13:31:56 MINT-Server kernel: [    9.856105] firewire_ohci 0000:02:08.4: added OHCI v1.10 device as card 0, 4 IR + 8 IT contexts, quirks 0x1, physUB
Mar  1 13:31:56 MINT-Server kernel: [   10.368398] firewire_core 0000:02:08.4: created device fw0: GUID 0030bd0518001b30, S400
Mar  1 14:03:55 MINT-Server kernel: [    9.768110] firewire_ohci 0000:02:08.4: added OHCI v1.10 device as card 0, 4 IR + 8 IT contexts, quirks 0x1, physUB
Mar  1 14:03:55 MINT-Server kernel: [   10.272395] firewire_core 0000:02:08.4: created device fw0: GUID 0030bd0518001b30, S400
Mar  1 14:16:47 MINT-Server kernel: [    4.828329] firewire_ohci 0000:02:08.4: added OHCI v1.10 device as card 0, 4 IR + 8 IT contexts, quirks 0x1, physUB
Mar  1 14:16:47 MINT-Server kernel: [    5.344410] firewire_core 0000:02:08.4: created device fw0: GUID 0030bd0518001b30, S400
Mar  1 14:29:35 MINT-Server kernel: [    4.568720] firewire_ohci 0000:02:08.4: added OHCI v1.10 device as card 0, 4 IR + 8 IT contexts, quirks 0x1, physUB
Mar  1 14:29:35 MINT-Server kernel: [    5.088525] firewire_core 0000:02:08.4: created device fw0: GUID 0030bd0518001b30, S400
Mar  1 14:44:25 MINT-Server kernel: [   10.116126] firewire_ohci 0000:02:08.4: added OHCI v1.10 device as card 0, 4 IR + 8 IT contexts, quirks 0x1, physUB
Mar  1 14:44:25 MINT-Server kernel: [   10.624400] firewire_core 0000:02:08.4: created device fw0: GUID 0030bd0518001b30, S400

Are there any other things I can do to check? I installed this Lubuntu with the cards in place rather than add them afterwards.

---

