---
title: "sata dvd drive doing soft resets"
date: 2008-07-24
forum: Hardware
---

### Post by dvice_null on 2008-07-24
Using Ubuntu 8.04

I got new (replaced old broken DVD-drive (by LG) with it) Samsung DVD RW drive, sh-s223. I've been able to read DVDs with it, but sometimes it doesn't seem to work at all. I'm getting a lot  (like every second) of errors like this in dmesg (see attached file for full dmesg):

```
[   25.475501] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   25.811158] ata4.00: configured for UDMA/66
[   25.811167] ata4: EH complete
[   25.811740] ata4.00: exception Emask 0x10 SAct 0x0 SErr 0x180001 action 0x2
[   25.811743] ata4: SError: { RecovData 10B8B Dispar }
[   25.811749] ata4.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[   25.811751]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[   25.811752]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x10 (ATA bus error)
[   25.811755] ata4.00: status: { DRDY ERR }
[   26.122492] ata4: soft resetting link
```

It seems to work if I keep a disk on the drive when booting. Not sure if that is because of the line I added to /etc/fstab:
```
/dev/sr1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

But it would be nice if
a) I could get rid of the error logs
b) It would detect the disk, without a reboot and without keeping a disk on the drive when booting up. 

Anyone got an idea how to do that? More information can be provided, if command line commands to generate that information is provided.

Edit (I found a bug report which I think is related to this):
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/231575](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/231575)

---

