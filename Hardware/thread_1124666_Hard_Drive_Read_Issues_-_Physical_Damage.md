---
title: "Hard Drive Read Issues - Physical Damage?"
date: 2009-04-13
forum: Hardware
---

### Post by PiGeek31415 on 2009-04-13
Hello everyone,

Last night I happened to trip over my 500GB Western Digital hard drive's USB cable, causing it to hit the ground from a height of about 18 inches. Vista can no longer detect the drive.

I took the drive out of the WD casing, only to find an IDE drive (not SATA, as I expected). Assuming that I simply damaged the power connectors in the original enclosure, I moved the drive into another, working enclosure.

I'm no linux expert, so I tried to use gparted to see if the drive was mounted. It never got past the loading stage. dmesg gives a lot of messages about I/O errors:
```

[  546.088544] sd 8:0:0:0: [sde] Sense Key : Medium Error [current] 
[  546.088552] sd 8:0:0:0: [sde] Add. Sense: Unrecovered read error
[  546.088561] end_request: I/O error, dev sde, sector 0
[  546.091488] sd 8:0:0:0: [sde] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  546.091494] sd 8:0:0:0: [sde] Sense Key : Medium Error [current] 
[  546.091500] sd 8:0:0:0: [sde] Add. Sense: Unrecovered read error
[  546.091506] end_request: I/O error, dev sde, sector 0

```

If anyone can at least tell me how to continue troubleshooting (or if it's even worth it), I would really appreciate it.

Thanks,
-PiGeek31415

---

### Post by Anthon on 2009-04-13
I have had good results with reading NTFS partitions that would no longer boot Windows under Ubuntu booted from CD. That was on a laptop where I did not want to take out the drive. On some subdirs it would take hours to read some files (and a few were corrupted, but most got copied over to a network mounted disk).
If you don't get a mount option you might still be able to copy the data to a file and then run some NTFS recovery tool on that file, assuming that NTFS has redundant filesystem information.
Just as a reference: it took me 3 days to copy a 40Gb drive that was filled for about 50%, but I was able to mount the drive (the head errors were on subdirs).

---

### Post by PiGeek31415 on 2009-04-13
That sounds promising. Are there any general commands or tools you suggest using? I don't know how I would go about copying something like "sde" to a file. Would it just be ```
 sudo cp /dev/sde /home/username/Desktop/sde.dump
``` something like that to get it copied? I think I might be able to google the rest of the way if that works.

---

### Post by Anthon on 2009-04-14
I am not sure if you can do that with 'cp'. I normally use dd for such actions:
dd if=/dev/sde of=/home/username/Desktop/sde.dump bs=32M

To see the progress use 
  killall -USR1 dd 
from some other terminal

---

