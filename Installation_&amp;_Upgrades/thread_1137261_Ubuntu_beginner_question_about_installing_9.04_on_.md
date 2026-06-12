---
title: "Ubuntu beginner question about installing 9.04 on a 2nd hard drive"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by fannibal on 2009-04-25
Hi,

I am eager to install ubuntu 9.04 onto a 2nd internal hard drive.  I am currently stuck on the prompt where the current selection is "install them side by side, choosing between them at startup"

I have many important files on this 2nd hard drive, and I am afraid that this action will erase everything like a clean windows xp install.  Can someone give me a pointer or two as to what I need to do next?

Do I need to back everything up and then install onto a clean 2nd hard drive?

---

### Post by autocrosser on 2009-04-25
First I would open up gparted (Partition Editor) in your normal install & resize your second drive--then create a new partition that will house your Jaunty install...if you have problems with this step or don't feel comfortable with resizing a partition--look around the forums on using gparted (install it via Synaptic if you don't have it).

After you have your partition ready to install Jaunty, you can just install to the newly made partition---install the grub loader from Jaunty--it allows booting for ext4 partitions which will most likely be the standard with Karmic (9.10)....

Any real problems---PM me.....

---

