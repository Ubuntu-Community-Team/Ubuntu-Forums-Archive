---
title: "Hard disk partition is lost after crash, Ubuntu 14.04"
date: 2014-10-11
forum: Hardware
---

### Post by umut3 on 2014-10-11
Ubuntu crashed and when I hardly restarted, I've got the [reboot and select proper boot device] error. From the scandisk on live-usb, I get the following warnings:

Disk /dev/sda - 8013 MB / 7642 MiB - CHS 1022 247 62
Current partition structure:
     Partition                  Start        End    Size in sectors

Warning: number of heads/cylinder mismatches 64 (FAT) != 247 (HD)
Warning: number of sectors per track mismatches 32 (FAT) != 62 (HD)
 1 * FAT32 LBA                0   0 33  1020 211 46   15633376 [UUI]

Bad sector count.


"boot-repair" does not give me any recommended solution. BootInfo summary is at the following link:

[http://paste.ubuntu.com/8542037/](http://paste.ubuntu.com/8542037/)

I've started using Ubuntu alongside Windows 7, than removed Windows 7 (to overcome other problems) and installed only Ubuntu. It has been going down a few times and I was formating, but this one is new and I need to data in harrdisk. Thanks for help.

---

### Post by oldfred on 2014-10-11
Boot-Repair report is only showing flash drive as sda. No hard drive at all.

Does BIOS show hard drive?
If BIOS does not see it, there is no way for an operating system to see it and mount it for repairs.

---

### Post by umut3 on 2014-10-13
I've just removed hard disk and plugged it in again, then bios was able to see it. Thank you oldfred.

---

