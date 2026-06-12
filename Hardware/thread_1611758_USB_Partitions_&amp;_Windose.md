---
title: "USB Partitions &amp; Windose"
date: 2010-11-02
forum: Hardware
---

### Post by spegru on 2010-11-02
Hi I'm trying to partition a USB stick into two - one for normal use and one for a fixed set of files. I have done this using GParted but I have a few questions.

1.   Even if I divide into two with FAT16 format, the Windows 7 PC only sees the first one. I could understand it if one was Ext4 or something but this seems daft. 

2.   I noticed that before I started with this stick, that as it came from the manufacturers, there was an empty space of about 4k before the first partition. It seemed like a waste so this is now gone. Why was it there and is this the reason Windows cant see the second partition?

3.   How can I lock the second partition?

All of this is fine in Linux of course!

---

### Post by spegru on 2010-12-11
bump

---

### Post by davec64 on 2010-12-11
Hi,

By default Windows detects a USB stick as media and as such can't see more than one partition.
Have a look here for more detail and ways around it:
[http://itstechsense.blogspot.com/2010/03/multi-partition-usb-flash-drive-in.html]("http://itstechsense.blogspot.com/2010/03/multi-partition-usb-flash-drive-in.html")

All the best :)

---

