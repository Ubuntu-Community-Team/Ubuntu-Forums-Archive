---
title: "Problem w/external hard drive"
date: 2012-11-21
forum: Hardware
---

### Post by rpiche on 2012-11-21
Fdisk lists my internal hard drive but the process hangs after that. The external hard drive never gets detected. I've waited and waited and waited but nothing else happens. I have to kill the process by closing the window.

ls /dev/sd* result:
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda5  /dev/sda6  /dev/sdb

lsusb:
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 05e3:0702 Genesys Logic, Inc. USB 2.0 IDE Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I need to access it so I can re-format it and create the MBR. I'm sure it can be done but I don't know how. Please help!

Thank you! :)

---

### Post by varunendra on 2012-11-24
> **rpiche said:**
> Fdisk lists my internal hard drive but the process hangs after that. The external hard drive never gets detected. I've waited and waited and waited but nothing else happens.
Is the physical condition of the drive good? Sounds like a failing drive.
What are the computer specs and version of Ubuntu you are using the drive with ? For Ubuntu version -
```
lsb_release -d; uname -mr
```

Also, have you tried the inbuilt "Disk Utility" or Gparted (included on live cd) ?

---

### Post by rpiche on 2012-11-24
The drive worked fine before my husband used it on his laptop w/windows 7. I suspect he didn't eject the drive properly which resulted in a corrupted MBR.

Disk Utility doesn't see the drive neither does GParted. Storage Device Manager and Partition Manager do. With both of those, I tried various operations and nothing works. I wait and wait and I have to eventually manually unplug the drive.

---

### Post by varunendra on 2012-11-25
If gparted can't even 'see' it, then I guess it's time to look for some specialized disk testing/repairing tool. I think your best bet is HBCD ([http://www.hirensbootcd.org/download/](http://www.hirensbootcd.org/download/)), which has a plethora of such tools, apart from a huge pile of other very useful stuff.

Please download it and burn it to a cd. Then boot with the cd and use the 'Hard-disk testing' tool of the same vendor as the brand of your HDD to see if it is physically ok and recoverable. You may then use disk management tools on it to create a new partition table and partitions on it.

If there is some data on it that you want to save, you may try 'testdisk' (or any other 'recovery' utility you like) which is included on it. But you may need a separate drive to recover files if there is too much damage. If the data is important and the condition of drive looks too bad, I'd recommend to create an image of it on another drive using testdisk. You may then safely use the image to recover files.

Please let me know if you need any help with that.

---

