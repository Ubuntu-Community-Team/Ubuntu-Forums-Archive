---
title: "Need installation help!"
date: 2009-09-19
forum: Installation &amp; Upgrades
---

### Post by the.dark.lord on 2009-09-19
I dual boot Windows Vista and Ubuntu on my laptop. I currently have Ubuntu 9.04 32-bit on it, which I'm going to replace with 64-bit Ubuntu 9.04. Can somebody help me with the partitioning? I want to erase the 32-bit version (installed on /dev/sda5) with the 64-bit version, without affecting anything else.

I've downloaded the 64-bit version, and currently have the partitioner screen open on my laptop right now- but I can't get to figure out how to do it.

UPDATE: I deleted the partition containing the 32-bit version, and selected it for the installation; but however when I click forward I'm getting the error:


No root file system is defined.

Please correct this from the partitioning menu.
-- 

Thanks!

---

### Post by dreamingdarkness on 2009-09-19
Hola,

If you're still having issues, try following one of the guides on here:
[http://members.iinet.net.au/~herman546/](http://members.iinet.net.au/~herman546/)

Basically, you have to select one partition as / from the partitioning screen before you continue. That tells Ubuntu where to put all its files. You can change where you keep your /home or others, but that's more advanced. For the basics, just select a partition which doesn't contain ANY data you want to keep as the '/' or root partition.

And, as my safety-conscious side reminds us, back up important data and make a SuperGrub or AutoSuperGrub disk first ([http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)) just to be on the safe side.

64 bit DEFINITELY made a difference for me in boot times and overall speed - 32 bit 9.04 was slower loading than my Vista partition, but 9.04 64bit blows it out of the water!

---

### Post by the.dark.lord on 2009-09-21
I got it running, thanks a bunch! :)

---

