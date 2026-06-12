---
title: "USB Flash Drive Size"
date: 2017-06-13
forum: Hardware
---

### Post by wewantutopia on 2017-06-13
So, embarrassingly, I got scammed and purchased a flash drive from ebay that reports that it's larger than it actually is. :(

Is there anyway I can make the drive report to the OS what its actual size is?

Thanks!

---

### Post by Autodave on 2017-06-13
The program *disks *will probably tell you.  I know that it works on my one terabyte USB and formats it to the 8 gig that it actually is. :-)

---

### Post by ajgreeny on 2017-06-13
Plug it in and show us the output from ```
sudo parted -l
```
You could also try ```
sudo blkid -c /dev/null
```

---

### Post by wewantutopia on 2017-06-13
Thanks for the replies.  Parted shows: ```
Model: General UDisk (scsi)Disk /dev/sdd: 2097GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 



```

Disks also shows 2TB, which it clearly isn't.  It just crashes when trying to format it.

Any ideas on how to see big it actually is?

---

### Post by ajgreeny on 2017-06-13
Using gparted try going to Device -> Create partition table and use GPT instead of msdos.

---

