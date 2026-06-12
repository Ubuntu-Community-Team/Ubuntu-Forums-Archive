---
title: "Triple boot? Jaunty, Knoppix, and Debian KDE?"
date: 2009-10-21
forum: Installation &amp; Upgrades
---

### Post by Gogeden on 2009-10-21
How would I triple boot Ubuntu Jaunty, Knoppix, and Debian KDE? I know I have to modify the menu.lst file but what do I type in there? Thank you! :lolflag:

---

### Post by jeremyswalker on 2009-10-21
They should all be setup automatically. I am not 100% certain if Knoppix or Debian will (I can't remember). However, if you install Ubuntu last, it should recognize your other installations and add the entries for you.

---

### Post by oldfred on 2009-10-22
If it does not automatically add the entries you have to manually add the entries as they are in each menu.lst for each distribution. Also each kernal update will require you to go back and manually edit the menu.lst. Grub2 may automatically do all of that if it sees the other distrubutions with a update-grub2.

An alternative is chainbooting. You put grub into the partition of each distribution and from the last install's menu.lst add simple chainboot entries.

chainboot 145 systems
[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)
[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_)

---

