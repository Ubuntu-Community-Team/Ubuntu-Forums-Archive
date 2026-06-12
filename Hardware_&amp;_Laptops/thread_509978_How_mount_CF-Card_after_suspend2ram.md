---
title: "How mount CF-Card after suspend2ram"
date: 2007-07-26
forum: Hardware &amp; Laptops
---

### Post by mbier on 2007-07-26
My configuration:

Ubuntu 6.06
VIA-EPIA MII6000E, no real hard-disks.
root on 1GB CF-Card via IDE-CF Bridge (/dev/hda1).
suspend2disk, suspend2ram works (with just one cf-card).
This board has an CF-Card slot via PCMCIA (but insn't bootable from there).
So I want to use in the 2nd CF-Card slot a 2nd card as /dev/hde1 (type: ext3).
Works more or less. I copied all directories from /usr/share to the 2nd CF-Card and installed links in /usr/share.
The problem is in awaking from "suspend2ram" I get a lot of errors (dmesg), /dev/hde1 is not useable, sometimes it can be repaiered automaticly via journal, sometimes by hand (fsck), and I even had to write a new partition-table.

Please can somebody explain me the right way to disable/enable the cf-card.

I would have thought:
before "suspend2ram"
umount /mnt 
/sbin/pccardctl eject 

after "suspend2ram": 
/sbin/pccardctl insert 
mount /dev/hde1 /mnt 

but this seems not to work.

Thanks in advance

Markus

---

