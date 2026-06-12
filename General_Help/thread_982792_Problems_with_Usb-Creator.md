---
title: "Problems with Usb-Creator"
date: 2008-11-15
forum: General Help
---

### Post by Peter09 on 2008-11-15
Hi,
I'm trying to use Usb-Creator. I am running it on Ubuntu Intrepid 64 bit.

The problem I have us that, although it appears to format and setup my 2Gb thumb drive it does not create a bootable system (from an i386 iso). The target machine complains that there is no bootable partition in the table.

Anyone any thoughts on where to go from here?

---

### Post by Peter09 on 2008-11-17
Further to this-
somewhere along the line my USB stick has been partitioned and now appears as two separate drives. Using gparted I have been unable to merge these two partitions. I have deleted them both, but still see two drives when mounted. 

I believe that this may be the problem I have, as the first partion is very small and I think that systems are trying to use that as the MBR.

I have been totally unsuccessful in using this 2GB drive as a bootable system. Systems recognize that it is bootable, but no system actual starts booting. They just hang.

---

### Post by C.S.Cameron on 2008-11-17
I have had problems booting flash drives after a U-C install.
The thing that seems to work for me every time is to first install using Unetbootin, delete all files and then install using usb-creator.

---

