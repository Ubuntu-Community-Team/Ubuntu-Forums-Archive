---
title: "Moving to Ubuntu"
date: 2009-03-02
forum: Installation &amp; Upgrades
---

### Post by FraggedLocust on 2009-03-02
I'm looking to move to Ubuntu full time, and I was wondering what i need to know before removing my windows partition. I have XP installed under virtualbox, because I'll need access to Visual Studio 2008 and MS Office.

-- My main question is, will i need to repair GRUB?
-- Does VS 2008 work well on XP? haven't tried it yet.
-- How would I go about making Ubuntu the primary partition (not logical), allowing access to the rest of the unpartitioned space on the drive?

So I've managed to resize the windows partition to a minimum size and get most of the disk space onto ubuntu, that's a start.

---

### Post by ranch hand on 2009-03-02
Grub should work if it is installed on your linux partition.  When I left Vista there was no dual boot involved so i don't know where you would put it.

I need be you can install grub from your live CD anywhere you may want it.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Copy paste that in your browser and it probably has any answer you need.  If not the forums are here to help.

I like one extended partition on a HDD.  It is more flexible.  If you want to chnge your partitions I would save your Home folder and start over with a fresh partition by cfdisk as you will probably have a problem getting gparted to get rid of you primary and thenm you are stuck with that  size or smaller.

I don't have a clue what VS is, therefore I will not comment.  Oh WOW, now I know why I am not in polly ticks.

---

