---
title: "CD_ROM IDE is slowing the boot"
date: 2009-06-12
forum: Hardware
---

### Post by jmz2 on 2009-06-12
Hello,

I think I have some problem with my CDROM and is causing the boot of my machine to be very slow.

The PC keeps waitng during the booting proccess and after doing Atl+F1 you can see messages like this (from my /var/log/dmesg file):

> [  105.248025] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  105.248034] ata2.01: cmd a0/01:00:00:80:00/00:00:00:00:00/b0 tag 0 dma 128 in
[  105.248036]          cdb 5a 00 2a 00 00 00 00 00  80 00 00 00 00 00 00 00
[  105.248037]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[  105.248040] ata2.01: status: { DRDY }
[  110.286534] ata2: port is slow to respond, please be patient (Status 0xd0)
[  115.269075] ata2: device not ready (errno=-16), forcing hardreset
[  115.269077] ata2: soft resetting link

I have set up my BIOS in order not to detect the CDROM IDE Slot but the proble persist.

The systems boots without any problem after 5 minutes or so.

Can you help me to solve this please?

Many thanks

---

