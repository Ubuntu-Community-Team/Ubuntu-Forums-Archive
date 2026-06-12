---
title: "KERNAL PANIC - Not syncing..."
date: 2005-04-15
forum: Hardware &amp; Laptops
---

### Post by JimmyJazz on 2005-04-15
can anyone help me.  My computer got turned off during a power outage and now when I restart it I get left with "Kernel Panic - not syncing: I/O error reading memory image."
I really don't wanna have to reinstall, I am desprate for a fix.

---

### Post by az on 2005-04-15
WHat happens when you boot into recovery mode?

---

### Post by JimmyJazz on 2005-04-15
I get the same kernel panic  :-?

---

### Post by alastair on 2005-04-16
Could be some fried hardware .... try doing "memtest" from GRUB. Perhaps try a LiveCD (doesn't need to be Ubuntu).

---

### Post by JimmyJazz on 2005-04-17
what would be some test I could run with a live CD say knoppix?

---

### Post by JimmyJazz on 2005-04-17
update I removed the hardrive from the computer and installed it in a second computer.  I was given the same error.  Could this be an error caused by my MBR?

---

### Post by nocturn on 2005-04-20
Try booting the Ubuntu live CD (or Knoppix).

Can you mount your harddrive?

If so, find out the partition that holds / and /boot, umount it and run fsck on it.
What does this say?

---

### Post by ubuntufans on 2005-07-06
i got the same error, i reinstall and it works again, sadly i have to reinstall to get it to work :(

---

### Post by tschaboo on 2005-10-09
I wanted to re-activate this thread again, because exactly the same happened to me today. But I could work out the problem myself, below the protocol of what happened/what I did. Hope it might be helpful for someone else.

**--------------------------------------------------------------------------**

Before all that happened I copied my ubuntu to another disk. Earlier the /boot was on hdb1 (now hda1) and the "/" on hdb3 (now hda7). Swap was hdb2 now hda3.

I worked with this setup for a few days until I threw out hdb and put the old hda (windows) in that place. When I tried to start up the system I got
```
Starting Ubuntu ...
Kernel panic - not syncing: I/O error reading memory image
```

I tried to boot up in recovery mode to get more information and the Kernel panic occured after those lines:
```
Freeing memory ... done (463 pages freed)
attempt to access beyond end of device
hdb2: vw=16, want=8, limit=2
```
I messed around with the cables and master/slave-jumpers on my drives for an hour and the result was that linux came up fine, if the old hdb was in it's place or if there was no hdb at all. If the "new" hdb was there, I got this error. BTW: windows (now on hda1) started up fine and could also acces the FAT32-partitions on the "new" hdb.

Since I didn't find anything useful on google I installed the kernel-sources and did a find/grep on the string, just to get an idea what the kernel wants and the error message is in the file "kernel/power/swsusp.c" which has something todo with "machine suspend".

Now "memory image" makes sense and I guess that this is written into the swap partition and that could be the reason why the kernel (or whoever) tries to acces hdb2 (which was my swap partition earlier?!?!?) :???: 

Then I searched for "hdb2" on my harddisk and found it in /etc/mkinitrd/mkinitrd.conf:
   RESUME=/dev/hdb2
which i changed to /dev/hda5 now. Then i entered
mkinitrd -o /boot/initrd.img-2.6.10-5-k7
(found in some ubuntuforums-thread) and - YES! it's working.

---

### Post by tschaboo on 2005-10-09
You can still boot your system if you pass the parameter "resume=hdxx" to the kernel (hdxx is your swap-partition) which overrides the setting in initrd. That way You don't need a live-cd. It should be even sufficient to put the parameter into grub.conf and not to build a new initrd at all. But I did not test that.

---

