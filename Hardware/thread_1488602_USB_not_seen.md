---
title: "USB not seen"
date: 2010-05-20
forum: Hardware
---

### Post by IainR on 2010-05-20
Trying to get a pre-historic Dell Latitude running on 10.04.  Did have it fully functioning on 7.05 (I think) but now need to set up wireless card again.  Was making progress with locating drivers, but can't see USB stick to get them onto the laptop.

sudo lsusb gives me:
Bus 001 Device 002: ID 0951:1603 Kingston Technology DataTraveler 1GB/2GB Pen Drive
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Any suggestions where I should go next?

---

### Post by dustinmarlowe56 on 2010-05-20
have you tried "sudo mount /dev/'usbLocation' /media/"?

---

### Post by IainR on 2010-05-20
Gives me "command not found"

---

### Post by IainR on 2010-05-20
Ah! 'usb location' is where it is, not the code I should be putting in.

So can any one tell me what I should enter as the location?

---

### Post by IcarusR on 2010-05-20
Output of this should list all drives & you should be able to work out which is your usb stick..

```
sudo fdisk -l
```

This is one of my sticks...

```
Disk /dev/sdb: 1024 MB, 1024966656 bytes
255 heads, 63 sectors/track, 124 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8ef631df

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         124      995998+   b  W95 FAT32

```

---

### Post by IainR on 2010-05-21
From sudo fdisk -l I get:

Disk /dev/sdb: 1006 MB, 1000610872 bytes
245 heads, 23 sectors/track, 3559 cylinders
Units = cylinders of 552 * 512 = 282624 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minim/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04030201

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         3560     982404   6   FAT16

I have now tried

sudo mount/dev/sdb1

through to 

sudo mount/dev/sdb1/media/flash/

Still getting "command not found" at every try

---

### Post by IcarusR on 2010-05-21
You've missed out a few spaces which cause it to fail. Should be...

```
sudo mount -t vfat /dev/sdb1 /media/flash/

```

You will probably also need to pass a file system type option (-t vfat). See mount manpage (most commands have a manual page accessed from terminal)...

```
man mount
```

---

### Post by IainR on 2010-05-22
If I mount this successfully, how do I find it once I'm out of terminal?

Maybe I should have gone to Absolute Beginers Talk......

---

### Post by IainR on 2010-05-22
Found it now!  Still not mounting.  Tried burning the files on to a CD.  Similar story there.  Can see the CD but get pop-up message:

Unable to mount location
Error creating mount point: Input/Output error

---

