---
title: "how to uninstall?"
date: 2009-10-21
forum: Installation &amp; Upgrades
---

### Post by baffle-boy on 2009-10-21
i want to (temporarily) uninstall ubuntu, but i couldn't find any good guides. is it as simple as deleting the partition? (i dont want to do that because im dual booting xp and ubuntu... and i wouldn't know how to format it back to ntfs). so please just link me to some guide!

---

### Post by jessiebrownjr on 2009-10-22
> **baffle-boy said:**
> i want to (temporarily) uninstall ubuntu, but i couldn't find any good guides. is it as simple as deleting the partition? (i dont want to do that because im dual booting xp and ubuntu... and i wouldn't know how to format it back to ntfs). so please just link me to some guide!

If you want it gone off your HDD completely you would first delete the partition, and then restore Windows MBR.. Google how to restore Windows MBR for that issue, and then you would either want to reformat the old linux partition to a FAT system windows can read, or use a program to combine it with the partition your windows install is on...

---

### Post by baffle-boy on 2009-10-22
ok, thanks a lot, any good programs for that you can recommend?

---

### Post by MelDJ on 2009-10-22
in windows, control panel-administrative tasks-computer management-storage ( or something around those lines)

---

### Post by PrePenguin on 2009-10-22
> **baffle-boy said:**
> ok, thanks a lot, any good programs for that you can recommend?
 
 
 
Download easyBCD and repair your MBR with it then go into control panell/ administrative tool/ Computer management/ Disk management and just delete the partition then right click on your windows partition and choose expand to recover the deleted partition. Remember fix the MBR with easyBCD first.

---

### Post by ottosykora on 2009-10-22
>Download easyBCD and repair your MBR with it <

careful! AFAIK this works reoairs vista bootloader and mbr only , not xp

---

### Post by baffle-boy on 2009-10-23
ok... so that method wont work for me because im using xp, not vista. how about the method explained in this thread: [http://ubuntuforums.org/showthread.php?t=113630](http://ubuntuforums.org/showthread.php?t=113630) i guess that would work right? (i have both ubuntu and xp on the same hard drive)

---

### Post by Mark Phelps on 2009-10-23
> **baffle-boy said:**
> ok... so that method wont work for me because im using xp, not vista. how about the method explained in this thread: [http://ubuntuforums.org/showthread.php?t=113630](http://ubuntuforums.org/showthread.php?t=113630) i guess that would work right? (i have both ubuntu and xp on the same hard drive)

The caution I would add is to delete ONLY the Ubuntu partition(s). The guide says ALL partitions except Windows, which with folks with recovery partitions, wipes out their ability to restore their machines.

---

### Post by baffle-boy on 2009-10-23
ok, i just noticed that according to the windows disk manager, i have two "unknown" partitions. i suppose they are both related to ubuntu?

---

