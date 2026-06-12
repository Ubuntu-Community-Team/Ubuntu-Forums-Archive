---
title: "GRUB on Adaptec 2045(Also 2405)"
date: 2009-06-18
forum: Installation &amp; Upgrades
---

### Post by LeetDonkey on 2009-06-18
Hello
 
I've tried to install Ubuntu on a 4-disk RAID0 array on my Adaptec 2045(It's the same as 2405)
The installation and partitioning went along fine, but after all the files has been copied it fails to install grub.
 
I guess it's because of my Adaptec controller, but I'm a bit stuck as to how to proceed?
It booted the live version afterwards, and I tried to get some drivers for it, it could only find some for my graphics card.
 
I guess it recognizes my card as it sees and creates the partitions fine, it's just grub that refuses to install..
 
I have a windows 7 partition on /dev/sda1, I created a primary partition on /dev/sda2 for Ubuntu and then a 2 GB swap on /dev/sda3
 
Any ideas?
 
Thanks

---

### Post by LeetDonkey on 2009-07-01
I figured it out.
/boot didn't like being placed after my 1.5TB windows partition.

---

