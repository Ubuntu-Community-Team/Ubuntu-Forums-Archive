---
title: "second Ubuntu installation"
date: 2006-02-14
forum: Installation &amp; Upgrades
---

### Post by renzokuken on 2006-02-14
im currently running just Ubuntu i386 BB on my machine and i'd like to have a play with the 64-bit version.

quick question, whats the easiest way to create a partition for another linux installation. i want it on the same harddrive as i386, but i cant remember if the installation process offers to resize (i.e shrink) my current partition to make room for a new one, or if i have to create the partion first.?

can anyone suggest the easiest most reliable way to do this?

thanks

---

### Post by joey111 on 2006-02-14
well best thing would be, 
get the ubuntu live cd (or knoppix cd)
, use gparted or qtparted and create another ext3 partition. (i think u could use the same swap, and data directories, but would need another / directory).
to avoid getting the grub confused u could install the grub not in the MBR biut in the new partition (when setting up ubuntu 2) and from the old one u could modify grub (how -to -dos around here).

---

