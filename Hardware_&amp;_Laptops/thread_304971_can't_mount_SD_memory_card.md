---
title: "can't mount SD memory card"
date: 2006-11-22
forum: Hardware &amp; Laptops
---

### Post by k84 on 2006-11-22
Hi, I'm having problems trying to mount a memory card in my Inspiron 6000. I can't even read it in windows due to some drivers conflict that I couldn't resolve. The memory card works well in other laptops. My card reader is a Ricoh R5C822 and after inserting the card I get this with dmesg:

```
[17184697.620000] sdhci: Wake-up:  0x00000000 | Clock:    0x00000107
[17184697.620000] sdhci: Timeout:  0x00000006 | Int stat: 0x00000003
[17184697.620000] sdhci: Int enab: 0x00ff00fb | Sig enab: 0x00ff00fb
[17184697.620000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000001
[17184697.620000] sdhci: Caps:     0x01e021a1 | Max curr: 0x00000040
[17184697.620000] sdhci: ===========================================
[17184697.624000] mmcblk0: error 2 transferring data
[17184697.624000] end_request: I/O error, dev mmcblk0, sector 0
[17184697.632000] mmcblk0: error 2 transferring data
[17184697.632000] end_request: I/O error, dev mmcblk0, sector 0

```

and when I try to mount the block device i get this:

```
sudo mount /dev/mmcblk0 /media/flashk/
mount: /dev/mmcblk0: can't read superblock

or 

sudo mount -t auto -osync /dev/mmcblk0 /media/flashk/
mount: you must specify the filesystem type
```


I don't know about the filesystem of the memory card, in Windows shows the filesystem as RAW. Does anyone can help me with this problem? thanx

---

### Post by melman101 on 2007-05-28
I also have problems mounting my R5C822. Works fine in USB reader.

---

