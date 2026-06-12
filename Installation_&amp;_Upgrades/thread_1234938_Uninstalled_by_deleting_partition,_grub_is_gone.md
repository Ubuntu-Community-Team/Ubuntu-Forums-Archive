---
title: "Uninstalled by deleting partition, grub is gone"
date: 2009-08-08
forum: Installation &amp; Upgrades
---

### Post by Dave2081 on 2009-08-08
I had a laptop with both ubuntu and vista for awhile. I have a job now which sadly uses SQL server, visual studio etc... and decided to just make it a vista machine. Possibly install ubuntu inside vista later via vmware or something. 

ANYWAY ------> Begin real question

I deleted the swap partition, than a linux partition, than another or the main linux partition. Not sure why I did it three times. It was actually a linux partition that when opened had the swap and linux partition as sub menus.
I did this in gparted on the liveCD. I don't have the windows recovery disk, but am downloading it right now. I'm trying to fix this inside the ubuntu live cd using gparted. But am thinking it might be easier with the windows recovery disk. 
I'm just looking for any advice on which direction to take I've looked at other posts and they're all slightly different and I wanna make sure I don't f this up further. 
also, I currently have 

Partition File S  Label      Size             Flags
/dev/sda1 fat16 DellUtility 31.31(total) MiB
/dev/sda2 ntfs  RECOVERY    9.77         GiB
/dev/sda3 ntfs  d           1993.64      GiB  Boot
unallocated unallocated      23.44       GiB

Thanks,
Dave

---

### Post by raymondh on 2009-08-08
After deleting Ubuntu, which GRUB is likewise deleted, you'll have to recover the windows bootlader (in the MBR).

You are downloading a Vista recovery disk you mentioned.  Boot into it, select repair >access a command prompt > and type

bootrec.exe/FixMbr

Good luck.

---

