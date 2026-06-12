---
title: "Hard drive filled with bad sectors and kernal panic after power outage."
date: 2016-11-26
forum: Hardware
---

### Post by frojin on 2016-11-26
Yesterday morning I was working on the computer and then the power went off,after 4 hours the power came back,but the hard drive showed so many bad sectors and wasn't even able to boot.It was just showing kernel panic.Anyway, I launched ubuntu live from a usb and when I tried to access the drive it gives this error.
```
Error mounting /dev/sdb5 at /media/lorkin: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdb5" "/media/anwar/lorkin"' 
exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdb5,       missing codepage or helper program, or other error


       In some cases useful info is found in syslog - try
       dmesg | tail or so.



```
So is there a way to get my data back?..Or are they gone for good?

---

### Post by mikewhatever on 2016-11-26
What's "the hard drive showed so many bad sectors"? Can you show us what you saw.

---

### Post by frojin on 2016-11-26
ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
ata1.00: BMDMA stat 0x24
ata1.00: failed command: READ DMA
ata1.00: cmd c8/00:08:b0:f7:46/00:00:00:00:00/e0
         res 51/40:08:b0:f7:46/40:02:02:00:00/e0 Emask 0x9 (media error)
ata1.00: status:{DRDY ERR}
ata1.00:error:{UNC}
end_request: I/O error, dev sda, sector 3650928

[   10.733468] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   10.733482] ata1.00: BMDMA stat 0x24
[   10.733494] ata1.00: failed command: READ DMA
[   10.733513] ata1.00: cmd c8/00:01:87:4b:f9/00:00:00:00:00/ed tag 0 dma 152 in
[   10.733523] ata1.00: status: { DRDY ERR }

---

### Post by frojin on 2016-11-26
These aren't all of them ofcourse, these are just the ones I've written on paper so I can google them.The rest of the lines were in a similar manner.

---

### Post by frojin on 2016-11-26
I installed ubuntu on another drive and this is what I get when trying to mount it from terminal:

mount: /dev/sdb2: can't read superblock

also tried fsck disk which returns this immediately:

fsck from util-linux 2.27.1
e2fsck 1.42.13 (17-May-2015)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb2
Could this be a zero-length partition?

---

### Post by frojin on 2016-11-26
It's ext4..so fsck was a bad choice..
I guess it's all gone now...

---

