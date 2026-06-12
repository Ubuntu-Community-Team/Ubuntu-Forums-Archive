---
title: "Zoom Q8 Handy Video Recorder"
date: 2017-06-09
forum: Hardware
---

### Post by drsaamah on 2017-06-09
So I jut bought a Zoom Q8, and since it recorded to SD card I got all lazy and did zero "does-it-work-with-linux" research and now I'm kicking myself in the ass.

So when I connect the damn thing to my laptop, put it in "Card Reader" mode and try to mount it I get X throwing some weird error at me that's like "blah blah blah can't mount something something blah blah."  I figure whatever, and just pop in the SD card to my computer and the icon shows on my desktop but unmounted.  When I try to mount it, it gives me the same error.

I popped the SD card into a windows box and at first it had the same issue.  But after downloading Zoom's Q8 driver from their website, I can mount and open the files on the SD card just fine.

I am baffled that in 2017, a hardware manufacturer would make it so the formatting on a SD card isn't something that can just plug and play without a god damn driver.

Any suggestions?  Anyone have experience with this unit (or the Q4 or the Q2)??  Any help is much appreciated, as always.

---

### Post by cariboo on 2017-06-09
> **drsaamah said:**
>  "blah blah blah can't mount something something blah blah." 

isn't much of an error message. In order for us to help you please post the exact error message you are getting.

---

### Post by drsaamah on 2017-06-09
Exact error message in XFCE is:
> Error mounting /dev/mmcblk0p1 at /media/saam/Q8_SD: Command-line `mount -t "exfat" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,iocharset=utf8,namecase=0,errors=remount-ro" "/dev/mmcblk0p1" "/media/saam/Q8_SD"' exited with non-zero exit status 32: mount: unknown filesystem type 'exfat'
 I can't identify where which device in /dev/ is the SD card reader so I can't get you a terminal output.

---

### Post by drsaamah on 2017-06-09
Okay never mind, I've been awake for too long and I've gotten stupid.  For some reason I thought Ubuntu could read exfat filesystems by default.

For anyone else that picks up one of these units... make sure you can mount exfat filesystems by running:

> sudo apt-get install exfat-fuse exfat-utils

AFTER that... plug and play baby :popcorn:

---

