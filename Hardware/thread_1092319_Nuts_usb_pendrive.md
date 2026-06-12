---
title: "Nuts usb pendrive"
date: 2009-03-10
forum: Hardware
---

### Post by pealpizar on 2009-03-10
:( Hey people I have a big problem I buy a new usb pendrive kingston and works fine sometime in ubuntu and it's working in windows, but now in linux only mount the pendrive like a read only unit, I try to mount manually whit mount -w /dev/sdb1 and didn't work
Help me to mount my pendrive like a write and read unit
this are the info of my pendrive when is mounted
Mounting point: /media/PEDRO
type of files: vfat
mounting options: ro nosuid nodev realtime uid=1000 fmask=0077 dmask=0077 codepage=cp437 iocharset=iso8859-1 shortname=mixed utf8
thanks

---

### Post by taurus on 2009-03-10
Try something like

```
sudo umount /dev/sdb1
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
df -h
```

---

### Post by pealpizar on 2009-03-10
That not work, change all of the options but when I try to move something don't let me, show a message that the sistem is read only

---

### Post by ponyexpress on 2009-03-10
> **pealpizar said:**
> That not work, change all of the options but when I try to move something don't let me, show a message that the sistem is read only

Does the drive have a write protect switch?

---

### Post by pealpizar on 2009-03-10
No is a simple kingston pendrive

---

### Post by taurus on 2009-03-10
Maybe you want to connect that drive back into windows and run a scandisk to check for badblocks or errors.  Then, unmount it first before you unplug it from your windows machine.

---

### Post by pealpizar on 2009-03-10
> **taurus said:**
> Maybe you want to connect that drive back into windows and run a scandisk to check for badblocks or errors.  Then, unmount it first before you unplug it from your windows machine.

I do that but still don't work, in properties drive says tha the pendrive have a firmware PMAP.
the pendrive come with a software for protection but I don't used even once

---

### Post by pealpizar on 2009-03-10
Hey I solve my problem, I have to format my pendrive in ubuntu and after that I can write over my pendrive Thaks for all
:D

---

