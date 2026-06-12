---
title: "Can I change a hard drive serial number?"
date: 2013-02-18
forum: Hardware
---

### Post by ookooboontoo on 2013-02-18
I work in a disk wiping environment. We have had a set of disks come in which even after a triple write wipe, they still come back with the same serial number but not the one printed on the outside of the disk. These are part of a bunch of the same disks that do have the correct serial number on their outside.
I beleive the serial number is kept in the chips on the outside of a disk. Is there a command that can change the serial number to another? This would then mean I can marry up the right disks with their appropriate S/Ns. BTW I am not talking UUIDs just in case.

Many Thanks
A

---

### Post by ookooboontoo on 2013-02-18
Just to add, These are on SCSI disks but it would be useful to know if the serial number can be chaged on SATA and IDEs too. I am aware that there are some Windows programs out there that suggest this can be done but I do not use Windows at work :) (And not that often at home either :) )
THanks

---

### Post by schragge on 2013-02-18
If what you mean is [this number](http://www.xboxharddrive.com/freeware.html) then I think it's stored in MBR, not on some chips.

---

### Post by haqking on 2013-02-18
Only spoofing it.  You can change it in Windows with many tools, this is one way gamers use for certain instances. But it is only changing the volume label or ID which is the serial number Windows assigns to it when you create a partition or volume.

However the real serial number of the HDD itself seen in the BIOS is hardcoded and as far as I know cannot be changed.

---

### Post by ookooboontoo on 2013-02-18
Thank you both. The number I need to change I am guessing is not in the mbr or spoofed as the drives are completely write/wiped including the partitions that holding the mbr. I am sure this must be able to be done as I have the physical evidence. When talking to colleagues they feel it will be somewhere off the spinning disks themselves. I wondered if I should look at what these guys were working on
[http://forum.archosfans.com/viewtopic.php?f=34&t=26784](http://forum.archosfans.com/viewtopic.php?f=34&t=26784)
Thanks again.

---

