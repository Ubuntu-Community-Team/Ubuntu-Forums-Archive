---
title: "Linux not detecting my Linux partition"
date: 2009-01-30
forum: Installation &amp; Upgrades
---

### Post by troegs on 2009-01-30
Let me start by saying thanks in advance for any help that anyone might be able to offer. Now, let me get started with my problem. It's a long one and the explanation is going to sound very convoluted. I'll try and make it as understandable as possible. 

My problem is the final (I hope) problem in a list of problems. I bought a new laptop, an Asus G50VT-X1. After several botched install attempts 1 because HD wasn't set to compatability mode, another because my disk was corrupted (burned at too high a speed) I now have all the kinks worked out and am ready for a real install. 

Before installing I wanted to get rid of all the Linux partitions I had made during all the installs. (A quick note. My new system came with a 320 gig HD that was already partitioned in half. the C: drive had windows and all its windows stuff on it, the D: drive was completely empty.) I was continually attempting to put linux on the free D: drive but after each botched install, the drive kept getting smaller and smaller as I kept partitioning the partition. I took my laptop into my professor this morning, (a Linux Master) and he helped me figure out what went wrong with all my previous installs, and through fdisk deleted the all the partitions that had been created on the D: drive. 

My problem now is that when I go to install Ubuntu, instead of it seeing that 160 GB D: drive, it doesn't allow me to partition it at all and instead attempts to partition the 160 GB C: drive. I don't want to touch the C: drive and all my attempts, (granted they are limited as I have no real working knowledge of Linux but am resolute in my decision to switch) to make the install use the D: drive for my install have failed. 

It sees that the HD is 320 gb as when I select the "use all" option it says the result will be 320 GBs. It will NOT however, in the guided partition option, allow me to access any of the D: drive. 

Can any of you Linux masters/gurus help me out? 

Again, thank you in advance for any help you might be able to offer me.

T.

---

### Post by lemming465 on 2009-02-01
In this situation you need to use the *manual* partitioning option.  It's not as scary as it sounds.  You only need two partitions, one big one one (20-150GB or so) for root and one small one (4GB) for swap.  Format the root partition (/) as *ext3*.

---

### Post by caljohnsmith on 2009-02-01
Please post the output of:
```
sudo fdisk -lu
sudo sfdisk -d
```
So we can see what your current partitions are.

---

