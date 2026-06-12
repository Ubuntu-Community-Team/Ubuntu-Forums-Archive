---
title: "Unallocated disk space"
date: 2008-10-26
forum: General Help
---

### Post by lionheartxxi on 2008-10-26
Hi i was wondering if any one knows how to use unallocated disk space.  So right now im using a 70GB ubuntu server, i have 70 GB of unallocated space also.  What i want is to take 50GB of that unallocated space and give it to the ubuntu server os, so that will mean i will have a 130GB main os.  The other 20GB is for another os.  Does anyone know how i can do this.

Thank you.

---

### Post by Pro-reason on 2008-10-26
Use GParted to resize or create partitions.

---

### Post by lionheartxxi on 2008-10-26
Hi pro reason.  I have went to gparted and created the 50GB ext3 and 20GB fat32.  How do i transfer the 50GB to the ubunu server im using.

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9556    76758538+  83  Linux
/dev/sda2            9557       19929    83321122+   5  Extended
/dev/sda5           19174       19929     6072538+  82  Linux swap / Solaris
/dev/sda6            9557       18776    74059587   83  Linux
/dev/sda7           18777       19173     3188871   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x469d60df

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    c  W95 FAT32 (LBA)


Thank you

---

### Post by lionheartxxi on 2008-10-26
I have attached a screenshot, maybe it will help

---

### Post by lionheartxxi on 2008-10-26
for some reason the fat32 partition has gone :s

---

### Post by lionheartxxi on 2008-10-26
do i have to unmount the dev/sda6 (the partition im using for my os atm) in order to get the 50GB on to it.

---

### Post by vanadium on 2008-10-26
Clarify your question: I have the impression that nobody has a clue of what you really want to achieve (I don't).

---

### Post by lionheartxxi on 2008-10-26
This is what i done at the start,  I accidentally installed ubuntu server twice, (i meant to get the desktop version), so i worked on one to be more user friendly.  So obviously i have another partition which is useless to me been the second ubuntu os, so i deleted it in gparted and it became unallocated space.  I want 50GB of that space brought over to the os im currently typing this up on now.  The other 20 GB that will be left i will be installing wins xp on it for games.  The question i have is "how do i switch unallocated space to another partition".  I was thinking that i might have to unmount this partition and bring it to the left of gparted to add the space in that way, but im new to this and i dont want to mess my main partition up, i have been operating wins xp for two years since i got a computer.

Im thinking of buying some material to read about linux.  The ppl who seem to operate on command base only in the terminal seem to know their stuff.

---

### Post by vanadium on 2008-10-27
That makes things more clear on what you want to do. The tool gparted indeed is the answer. We do not know, however, which partition you are wanting to keep and which one to discard. How to proceed depends on the specifics of your system. It might or might not render your system unbootable, which can be solved by reinstalling grub. If you install Windows XP after having installed Ubuntu, you will need to do that anyway.

In other words, it is, though not that difficult, not trivial also for an unexperienced user to rearrange the partitions without reinstalling the OS.

For an unexperienced user, there are two options

1) Just use the unused partitions as extra data storage (i.e. mount the partitions in your existing installation

2) Reinstall, instructing the installer to use the entire disk.

Anyway, if you want dual boot, the easy way is 1) install XP, have it use 20 GB space, 2) install Ubuntu, which will automatically setup a dual boot configuration.

---

