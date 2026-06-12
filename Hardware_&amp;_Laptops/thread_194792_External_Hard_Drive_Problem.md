---
title: "External Hard Drive Problem"
date: 2006-06-11
forum: Hardware &amp; Laptops
---

### Post by feardotcom on 2006-06-11
Hey all, i got a problem with my external hard drive, its a internal with a external kit on it, and when i plugged it upf or the first time in a few months(after i installed ubuntu) ubuntu sees the hard drive fromt he "disks" program, but it says theres nothing on it and i can even get into it to see it, do any of you have any ideas on how to fix this?, its plugged in from a usb 2.0, and goes to a usb hub, it sees my ipod from the hub so it can be the hub. any help would be greatly appreciated.

---

### Post by spyke01 on 2006-06-11
try plugging it into ints own port, since its usb it should be automounted. If you knew what device it was(hda, hdb, etc) you could always see what the following command shows

> 
sudo fdisk -l /dev/hda 


just replace hda with that drive (i dont know what the usb is, otherwise id give you that command)

---

### Post by musther on 2006-06-12
usb disks should show up as sdx (where x is a, b, c etc), you should be able to see what it is from the disks gui in system -> admin.

---

### Post by feardotcom on 2006-06-12
it comes up with sdc, and sdd, and when i try the command you gave, it doesn;t come upw ith anything, it just starts a hole new line, like i just press enter or something.

---

