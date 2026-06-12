---
title: "Mysterious 8gb SATA device"
date: 2009-11-11
forum: Hardware
---

### Post by quinn on 2009-11-11
Hi! I've just been playing around with Karmic a little on a new machine, (specs listed below), and in addition to my hard drives (sda and sdb), i see an unpartitioned, unformatted 8gb device (sdc), even when i have no USB or CD drives hooked in. 

It reads as unpartitioned space to gparted and Ubiquity, and when dumped, it seems to be completely zeroed out. I'm almost tempted to try partitioning it and installing an OS on it, but without having some better idea of what the heck it actually *is*, that seems like a very bad idea. It also seems to show up whether my system is set to express SATA devices as AHCI or IDE.

Anyhow, my system's specs are as follows:

Asus P5Q3 Deluxe WiFi/AP@n motherboard
Intel Core 2 Quad Q9550 @ 2.83gHz
4GB Ram, Mushkin brand
Gigabyte GeForce 7600GS, 256mb
Creative Sound Blaster Audigy
Hauppauge WinTV PVR-500 Tuner card
Maxtor 250GB 7200rpm hard drive
Seagate 1000GB 5900rpm hard drive
TSST DVD-RW drive


Any insights into this would be appreciated! Thank you very much

EDIT: Here's some info from dmesg, if it's of any interest

[    5.040413] scsi 7:0:0:0: Direct-Access     ATA      Config   Disk 0  1.25 PQ: 0 ANSI: 5
[    5.040482] sd 7:0:0:0: Attached scsi generic sg3 type 0
[    5.040504] sd 7:0:0:0: [sdc] 16777215 512-byte logical blocks: (8.58 GB/7.99 GiB)
[    5.040533] sd 7:0:0:0: [sdc] Write Protect is off
[    5.040535] sd 7:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    5.040550] sd 7:0:0:0: [sdc] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    5.040622]  sdc: unknown partition table
[    5.041643] sd 7:0:0:0: [sdc] Attached SCSI disk

---

### Post by tnttrx on 2009-12-04
same here with P5Q Premium.

maybe it's related to express gate functionality...

---

### Post by quinn on 2010-01-12
That was my first thought... but the dd image of it was entirely zeroes. (it was 8gb, and bzip compressed it to like 20k). I'd think if it were the expressgate SSD, some of the actual contents would show up.

---

### Post by AbtZ on 2012-06-24
I have this as well. Does anyone know what it might be?

---

### Post by ljonesj on 2012-06-24
recovery partition for windows maybe for xp, vista, 7

---

### Post by sudodus on 2012-06-24
Could it be a flash memory on the Hauppauge WinTV PVR-500 Tuner card?

---

