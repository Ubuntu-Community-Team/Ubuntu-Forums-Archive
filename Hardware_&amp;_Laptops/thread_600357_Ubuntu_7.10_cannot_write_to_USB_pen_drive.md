---
title: "Ubuntu 7.10: cannot write to USB pen drive"
date: 2007-11-02
forum: Hardware &amp; Laptops
---

### Post by kojakk00 on 2007-11-02
I have upgraded from 7.04 to 7,10 and seem to have lost the ability to write to my USB pen drive. When I try to change the folder permissions to 'read and write' I get the error "device is read only". But it isn't - the little plastic switch is in the 'write enable' position. I can write to  the pen drive from a Windows machine - no problem, but not on my Ubuntu laptop . I am fairly new to linux so I think I may be missing something fundamental. I would be grateful for any suggestions.

Kojakk00

---

### Post by kojakk00 on 2007-11-02
I gets better. when I typed:

sudo mount -t vfat /dev/sdb /mnt/usb

I got: "/dev/sdb already mounted or /mnt/usb busy"

Then I typed:
 
umount /dev/sdb

and got:  "/dev/sdb is not mounted (according to mtab)":confused::confused::confused:

Please help!

---

