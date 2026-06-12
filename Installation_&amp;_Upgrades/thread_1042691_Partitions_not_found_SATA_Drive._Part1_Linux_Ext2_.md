---
title: "Partitions not found SATA Drive. Part1: Linux Ext2 Part2 /Swap"
date: 2009-01-17
forum: Installation &amp; Upgrades
---

### Post by notj on 2009-01-17
I have used partition magic in windows XP to create 2 partitions, one Ext2 partition, and a SWAP partition. but none of my linux installs will detect the partitions. I've tried Slackware 12.1, and now Ubuntu and neither will detect. 

any idea why?

---

### Post by caljohnsmith on 2009-01-17
How about opening a terminal (Applications > Accessories > Terminal), and please post the output of:
```
sudo fdisk -lu
sudo sfdisk -d
```
And we can work from there if you want.

---

### Post by TonyFordz on 2009-01-17
If you want to do a primary install to a SATA this is what I had to do to get it to work for me.

1 ). Boot into a Windows OS CD
2 ). Whip out any partitions on the HDs you will use for Ubuntu
3 ). Reboot with your Ubuntu CD/DVD

This has worked just fine for me & I have noticed there are a lot of people out there having problems with Ubuntu installing on a SATA drive but this should solve your problems because Ubuntu will not find your SATA drives if you have foreign partitions on them so thus when you whip them out you will have no problems installing.

Hope this helps someone,
Tony Ford

---

