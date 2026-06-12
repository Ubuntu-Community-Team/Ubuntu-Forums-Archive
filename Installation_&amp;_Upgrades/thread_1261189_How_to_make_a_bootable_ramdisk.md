---
title: "How to make a bootable ramdisk?"
date: 2009-09-08
forum: Installation &amp; Upgrades
---

### Post by richterlevania3 on 2009-09-08
Hi there,

So, I have 24Gb of RAM. I don't use that, even when I play with 4 or more VM's. So, I heard of ramdisk (actually, I saw it as an option when I was compiling my kernel), and I was trying to find some guide on the net on how to setup a ramdisk and make grub load all the system residing on my HDD to it, then proceed with the boot process. If successful, everytime I power-up my machine, it will pause for some moments, copying my whole system from the HDD to the ramdisk and, when it's done, start the real boot from the ramdisk, which I guess will be pretty fast. Then I would setup cron to check every couple minutes to see if anything changed and copy the changes to the HDD, thus making the changes permanent.

Is that possible? If so, how can I do it?

Thanks in advance.

---

### Post by Fafler on 2009-09-08
It's possible, but i'm not exactly sure how. One method that might work is booting a initrd that mounts tmpfs as / and copies contents from a harddrive.  However you would need to implement some mechanism to sync writes to the harddrive.

Another possiblity is to make a RAID 1 array with a partition on the harddrive and a ramdisk of the same size. On every boot the system would rebuild the array from the harddrive. Read performance would be great speed if Linux software RAID is able request all reads from the ramdisk, however i don't know if thats possible. Write performance would the unaltered. And the redundant array wouldn't be very redundant.

---

### Post by richterlevania3 on 2009-09-08
Thx for the reply.

> It's possible, but i'm not exactly sure how. One method that might work is booting a initrd that mounts tmpfs as / and copies contents from a harddrive.

Could you elaborate how to do this?

The resync problem: I believe I could setup cron to make it from time to time, as I don't shutdown my machine often (like one time a week, maybe).

Thx in advance.

---

### Post by Fafler on 2009-09-08
Usually when i do these kind of things, i use Debian. In Ubuntu i just break stuff. But look at your initrd. The file init is a shell script run by the kernel after it unpacks the initrd. Look for the part that mounts root.

---

