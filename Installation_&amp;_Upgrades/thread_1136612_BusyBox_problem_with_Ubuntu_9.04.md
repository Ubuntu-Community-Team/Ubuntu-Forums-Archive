---
title: "BusyBox problem with Ubuntu 9.04"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by velja27 on 2009-04-25
I have a problem with BusyBox,it starts every single time i boot Ubuntu 9.04,i tried 3 other disks with 2 different downloads of Ubuntu 9.04.
Does anyone have this kind of problem or if anyone knows how to solve it please i beg you post it here.

---

### Post by velja27 on 2009-04-25
Bump,i really need this problem solved.

---

### Post by sloppyc on 2009-04-25
I get the same issue on one of my machines.  Had the problem with 8.10 as well, but 8.04 is fine.  It's an older MSI MS-6390 (km266) motherboard.  I have a feeling it's something to do with the IDE controller that Ubuntu doesn't like.

---

### Post by reisrocks on 2009-04-25
Same issue on my machine.

Sony Vaio VGN-AW11M

---

### Post by velja27 on 2009-04-25
Same here i have IDE controller for CD/DVD-ROM drive,btw its NEC.

---

### Post by DaveAU on 2009-04-25
There's a huge thread on busybox problems here:
  [http://ubuntuforums.org/showthread.php?t=765195](http://ubuntuforums.org/showthread.php?t=765195)

It's been a known problem since dapper, and it bit me pretty hard during the gutsy and hardy upgrades.  If I remember correctly it was the most common problem by a long margin in the "How did your upgrade/install go?" poll for hardy or intrepid.

There seems to be several problems with the same symptoms.

The first thing to try is to look at your BIOS and change the SATA mode from IDE to RAID (or to anything other than IDE, I think)

You can try altering your grub options as well - different things work for different people, but the following combinations seemed to have helped people in other threads: 

all_generic_ide 
all_generic_ide irqpoll
all_generic_ide pci=nomsi
pci=nomsi
irqpoll
all_generic_ide floppy=off irqpoll pci=nomsi

Almost all of the above have helped someone and failed for someone else.
I can imagine the post I linked to might become fairly active again soon with all the upgrades, so probably a good idea to check it as well from time to time.

If you're in the mood to give details of your problems to the ubuntu team, this seems like the bug that you're after:
  [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/47768](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/47768)

---

### Post by velja27 on 2009-04-26
I managed to fix my busybox problem by installing an CD/DVD-ROM from LiteOn and its very noisy but gets the job done.Its plugged in same place as my other CD/DVD-ROM but does the magic i want it to do.
Just so you know.

And how do i mark this thread as solved?

---

### Post by reisrocks on 2009-04-28
Got this working by using the Alternate CD

---

### Post by Slyder0244 on 2009-05-09
when trying to load the live version of 9.04 i get the busybox screen as well i tried checking the disc for defects and it runs and then brings me back to busybox i tried doing apic=off and got this

```
[0.318297] pci 0000:01:08.0: BAR 1: error updating (0xe8810004 != 0x000004)
[2.003971] IO APIC resources could be not be allocated.
```

is there anyway i can get this to boot into the live cd

my computer stats are an amd xp 2000+ cpu, 512mb of ram, asus a7n266-vm motherboard, and an ati 9000 all in wonder pro video card

---

### Post by Alex Carroll on 2009-05-09
When I boot the Live CD (9.04), I also get this BusyBox command line. Is this a problem that only affects the Live CD, or would it happen if I managed to install Ubuntu?

I'm attempting to install the 64-Bit version.

---

### Post by Slyder0244 on 2009-05-09
from reading on the forum i've seen people who have upgraded or installed ubuntu have this problem alex so yea you could have that problem if you happened to install it but who knows you might get lucky and not have that problem

---

### Post by raymondh on 2009-05-09
> **velja27 said:**
> 

And how do i mark this thread as solved?

Go to your first post > edit > advanced > click on the start of your title and type SOLVED > save

---

