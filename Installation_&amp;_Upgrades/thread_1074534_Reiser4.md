---
title: "Reiser4"
date: 2009-02-19
forum: Installation &amp; Upgrades
---

### Post by sokolovss on 2009-02-19
I've read a lot of articles about File Systems and realised, that Reiser4 suites me. I decided to install Ubuntu on Reiser4. Also I found some packages, those add support of Reiser4 to GRUB.

Now I use ext4, but it is too slow, so as ext3.

What I've done:
1) boot from live-cd
2) in Synaptic I mark for installation:
libaal-dev          - as I understood it's for GRUB
libncurses5-dev
libreadline5-dev
uuid-dev
libreiser4-dev      - as I understood it's for GRUB
reiser4progs
3) in GParted I made all partitions, exept SWAP in Reiser4
4) start ubiquity installer, disk partitioning. I can't mark my partitions to be Reiser4 (So, that's the problem)

I've read many threads, but nowhere the problem was solved.

I've tried debian-installer on alternate CD, but it has the same problem.

My system now: Ubuntu 9.04 Alpha4 amd64, but I tried all versions from 7.04

---

### Post by sokolovss on 2009-12-25
I hope, that you are still waiting for Reiser4, so I have some good news:
 [Reiser4 may go for mainline inclusion in 2010]("http://www.phoronix.com/scan.php?page=news_item&px=NzY4OQ")

---

