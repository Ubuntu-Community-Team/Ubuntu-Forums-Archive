---
title: "on install, partition resizer remains at 0%"
date: 2009-08-15
forum: Installation &amp; Upgrades
---

### Post by potat on 2009-08-15
Hi.
I am currently installing Ubuntu on a hard drive that also contains Vista. I'm setting it up for dual-boot so the partition needs to be resized. However, the resizing progress bar is staying at 0%. Is there a way to safely shut my computer down without affecting the partition table? Thanks.

---

### Post by presence1960 on 2009-08-15
You should shrink Vista's partition to create space for Ubuntu from within Vista using the disk management utility. Defrag Vista at least once or twice prior to ressizing the partition. I would suggest backing up your data first. then use the Ubuntu Live Cd to install Ubuntu to that unallocated space. A lot of people have had problems with Vista when using anything other than Vista's disk management utility to resize vista's partition.

---

### Post by Mark Phelps on 2009-08-16
> **potat said:**
> ... However, the resizing progress bar is staying at 0%...

I've found that GParted, whether used from LiveCD or from inside Ubuntu, can be very S...L...O...W.  It helps to keep clicking the arrows to open lower levels of detail to actually see what it's doing.

If you turn it off while it was in progress, as with any partitioning tool, there's a likelyhood that it will leave a corrupted partition,  But GParted, unlike some other tools, does a practice run first, in which it doesn't actually change anything. And, that practice run takes as least as long as the real changes.  So, if you shut it down early into the process, there's the chance it will still doing its practice run.

As presence has already said, use the Vista Disk Management tool to shrink the Vista OS partition.  Do NOT use GParted LiveCD or the Ubuntu installer.  Either of the latter poses a strong risk of corrupting the Vista OS in the process.

---

### Post by potat on 2009-08-19
Thanks for the help everyone. I was able to safely shut it down. I used the Vista resizer and was able to make the partition I needed and install Ubuntu. I had intended to keep Vista on my hard drive in case of emergency, but now I think I'm going to just delete it altogether. It has caused me endless trouble and not a shred of good.

---

### Post by presence1960 on 2009-08-19
Before deleting Vista, do you have a recovery partition? if so back it up and I would use the software which allows you to make bootable DVD(s) of the recovery partition. This way if need be you can restore your disk to factory image.

Enjoy Ubuntu.

---

### Post by potat on 2009-08-19
Good idea. Thanks.

---

