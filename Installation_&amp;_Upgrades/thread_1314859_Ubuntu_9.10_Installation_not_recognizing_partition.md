---
title: "Ubuntu 9.10 Installation not recognizing partition, help!"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by pickboy87 on 2009-11-04
So I've never run into this problem and I needed some help. I have 3 internal HDD's on my computer. They are as follows:

SDA is split into a 60 gig partition for Windows 7 (ntfs) [primary partition if I recall correctly]. The rest is an extended partition broken down into a 10 gig partition for all the Linux OS files (ext4), a couple gig (don't remember size) partition for Linux Swap, and a 160 gig partition for /home (ext4).

SDB is just a 250 gig partition in ext3.
SDC is a 500 gig partition in ntfs.

Problem is my SDA partition does not show on the installer, but shows up just fine in Gparted, and even shows up in the Places menu as the size "drive" that I broke it down into. I thought it might have been something goofy with the ext4 formatting, so I just did a quick ext3 format in gparted, but it's still not showing. Anything I can do to get it to show properly so that I can install Ubuntu 9.10?

---

### Post by dhavalbbhatt on 2009-11-04
It seems that this is a common issue going around with using installation CD to install Karmic. Have you tried installing using the alternate CD? I am trying to install using alternate CD and right now, I am on the "resizing partition" screen, with the HDD doing something..hope it works for me! If not, I am totally giving up on Karmic until they fix these basic installation issues. Jaunty seems to running great for me, so I will continue using that.

---

