---
title: "[SOLVED] Can't mount USB"
date: 2008-03-12
forum: Hardware &amp; Laptops
---

### Post by tbrminsanity on 2008-03-12
I can't seem to get any of my usb flash drives to mount.  I think that the problem is either the fact I'm going through a USB hub, or the port may be USB 1.0, or my USB drives may be FUBAR.  

One of the the drives is a MPIO MP3 player that I can mount on Windows but not on Ubuntu.
One is a 2GB Flash drive that I can't mount with any OS (the drive use to be a liveUSB of RHEL.
I haven't tested my last USB stick on the Ubuntu machine but it loads in both Windows and my work laptop.

Any suggestions, things I might have overlooked?

---

### Post by justleen on 2008-03-12
does ubuntu recognize the event? as in, can you see in your logs that ubuntu picks it up when you insert a drive?

```
tail -f /var/log/messages 
```
then plug in the device.

If you insert them directly, without the hub, can you then see the events?

---

### Post by tbrminsanity on 2008-03-12
It is picked up by the log.

---

### Post by tbrminsanity on 2008-03-14
Ok I fixed on of the problems and have a work around for the other.

Problem #1 (USB Flash Drive not working)
1. sudo umount /dev/sdX           (where X is the drives location from fdisk-l)
2. sudo fdisk /dev/sdX
3. d                                             (go through and delete any existing partitions)
4. n                                             (to create a new partition)
5. p                                             (make it a primary partition)
6. 1                                             (make it the first partition [sdX1])
7. Enter twice                            (make the partition the whole size of the disk)
8. a                                             (activate partition)
9. 1                                            (activate partition 1)
10. t                                           (Change type of partition)
11. 6                                          (to Fat 32 (I use this drive on Win))
12. w                                        (write changes to the drive and make permanent)
13. sudo mkfs.vfat -F 16 -n name /dev/sdX1 (format and name the drive)(note name = name)
14. pull out and reinsert the USB drive to have the computer recongnize it.

Problem #2 (No USB drives are visible through my USB hub)
I have to use a different USB connection on my computer (luckly for me there are two on the front of my machine).

---

