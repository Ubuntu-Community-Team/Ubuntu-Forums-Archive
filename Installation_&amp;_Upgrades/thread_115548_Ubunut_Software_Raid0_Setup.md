---
title: "Ubunut Software Raid0 Setup"
date: 2006-01-10
forum: Installation &amp; Upgrades
---

### Post by WoodPost on 2006-01-10
I have tried a few times to install a software Raid0 setup to Ubuntu but the Grub and Lilo loader fail to install both times. Here what i would like to know, how to set up my partitions and the raid setup. I know the physical action of the partitions but i Don't understand what the swap and journaling spaces are.
Heres my setup;
80gb IDE Hard Drive with windows system files on it
2x 250gb SATA hard drives
     -The current partitions on these drives are, 170gb  partition NTFS for windows storage space. The other 80gb unpartitioned 

I'm not sure how to set up swap space but i believe its important, so any help would be extremely helpful.

---

### Post by mntbighker on 2006-01-11
If your trying to get the RAID going as the root partition (or boot), I'm not sure it ever will work right? I don't know anyone who has managed it. I use my RAID for storage only. It would probably work for /home. You need some pretty sophisticated driver support as far as I know to allow the OS to boot in concert with whatever the RAID/BIOS is doing. It's probably easier with a dedicated quality RAID card? But they cost quite a bit.  I could be entirely wrong but this is the sense I get from what I have read. Some people appear to have this working but they are the exception it seems.

--MM

---

