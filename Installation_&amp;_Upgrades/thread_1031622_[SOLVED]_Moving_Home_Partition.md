---
title: "[SOLVED] Moving Home Partition"
date: 2009-01-05
forum: Installation &amp; Upgrades
---

### Post by Tom Atkins on 2009-01-05
I am using HH and on my present installation I did not set up home as a separate partition. I am planning to move it to a new computer and would like to format home as a separate partition. Can I just copy the present partition to a memory stick and then just copy it to new HH set up?

---

### Post by logos34 on 2009-01-05
THe easiest way IMO would be make a separate /home on the original harddisk first (see link in my signature), then use Partimage to copy (.gz) image to usb flash and transfer them over that way, after creating the new partitions on the new machine.  Or if you can directly connect the old hard drive to the new machine (internally or vis usb) you could even do a disk-to-disk copy with dd command.

How big is root and /home folder? How big is original and new hard disk?

sudo fdisk -l

---

### Post by Tom Atkins on 2009-01-05
I haven't purchased the new machine yet. My present one has  / as a 71 Gib ext3 partition and then a 2.86 GiB extended partition used for swap. thanks for your ideas. I will refer to them when I get the new machine.

---

