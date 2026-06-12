---
title: "Mount USB Mass Storage Device?"
date: 2009-01-20
forum: Hardware
---

### Post by fhsm on 2009-01-20
I've got a digital voice recorder that isn't officially supported on linux.  But I'm hoping to get it to mount and see if I can figure out a way to pull files off.

If I attach the recorder to my 8.10 laptop it goes into upload mode (which it doesn't do if i just connect it to a powered hub that isn't connected to a computer).

It doesn't automatically mount that way an external HDD would.  If I run fdisk -l it doesn't show up at all.

If I run lsusb it does show up
```
Bus 001 Device 003: ID 07b4:021b ... 
```

Can anyone suggest steps I might take to encourage the device to mount?

---

