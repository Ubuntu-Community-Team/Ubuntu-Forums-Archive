---
title: "need terminal command to LONG FORMAT a hard drive"
date: 2007-07-02
forum: Hardware &amp; Laptops
---

### Post by molly_001 on 2007-07-02
Edit:  I initially failed to mention that the reason I want a long format is because this hard drive currently shows errors in a read scan using bootable floppy of SeaTools. 

Hello --

Both Gparted, and, Ubuntu 7.04's native removeable media manager "Disk Manager" ... they only do a "short" format of a hard drive.  

In other words, it takes just a few seconds to format a 20GB hard drive in FAT32.

I am looking for a command (terminal) structure to format a hard drive the long way.  Or maybe installing a package of some sort which would accommodate this.

NOTE: I can't get this motherboard to boot from its CD-ROM devices, or I would just use Knoppix to do this.  (I don't even know if Knoppix performs such a "long" format, but it would be worth a try if I could get a boot from IDE CD-ROM.)

NOTE 2: I've run across the following commands, but I don't know that I am literate enough with the shell to do it right.
dd if=/dev/zero of=/dev/hda
cat /dev/zero > /dev/hda
dev/urandom

THANKS!!

---

### Post by logos34 on 2007-07-02
What about 

**mkdosfs -vF 32 /dev/hda**

or

**mkfs -t vfat /dev/hda**

Or do they just quick format too?

---

