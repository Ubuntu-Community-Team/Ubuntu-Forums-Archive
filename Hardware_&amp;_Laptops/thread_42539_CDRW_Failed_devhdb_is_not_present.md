---
title: "CDRW Failed /dev/hdb is not present"
date: 2005-06-18
forum: Hardware &amp; Laptops
---

### Post by deepaksingh on 2005-06-18
Hi I am unable to mount my CDRW (Samsung) and though dmesg detects it but the /dev/hdb device is not created once the system boots the drive is working fine on winxp and knoppix 3.3

deepak@ubuntu:~ $ dmesg |grep ide
BIOS-provided physical RAM map:
Kernel command line: root=/dev/hda13 hdb=ide-scsi
CPU: After generic identify, caps: 00803035 80803035 00000000 00000000
ide_setup: hdb=ide-scsi
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
    ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
    ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:pio, hdd:DMA
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
 /dev/ide/host0/bus0/target0/lun0: p1 p2 p3 p4 < p5 p6 p7 p8 p9 p10 p11 p12 p13 >
ide1 at 0x170-0x177,0x376 on irq 15
 /dev/ide/host0/bus1/target1/lun0: p1 p2


deepak@ubuntu:~ $ ls -alrt /dev/hd
hda    hda10  hda12  hda2   hda4   hda6   hda8   hdd    hdd2
hda1   hda11  hda13  hda3   hda5   hda7   hda9   hdd1


deepak@ubuntu:~ $ cat /etc/fstab |grep cdrom
/dev/hdb        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0


deepak@ubuntu:~ $

Any Help is highly appreciated :[grin]

>> 
Ubuntu is awesome... I dropped everyother distro...

---

