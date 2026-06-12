---
title: "How to uninstall Ubuntu?"
date: 2009-09-22
forum: Installation &amp; Upgrades
---

### Post by zking on 2009-09-22
I set up a dual-boot between Vista and Ubuntu. Unfortunately, I didn't install Ubuntu the way I wanted it. So now I need to uninstall Ubuntu. I researched ways on how to do it, but many of the methods require using a Vista installation CD. I do not have this CD. Is there still a way to uninstall Ubuntu from my system? 

EDIT: My main objective is to reinstall Ubuntu. I am trying to uninstall it, then install it again. 

Thanks,

---

### Post by raymondh on 2009-09-22
> **zking said:**
> I set up a dual-boot between Vista and Ubuntu. Unfortunately, I didn't install Ubuntu the way I wanted it. So now I need to uninstall Ubuntu. I researched ways on how to do it, but many of the methods require using a Vista installation CD. I do not have this CD. Is there still a way to uninstall Ubuntu from my system? 

EDIT: My main objective is to reinstall Ubuntu. I am trying to uninstall it, then install it again. 

Thanks,

It depends on how you installed it (ubuntu) in the first place.

WUBI

1.  It being "inside windows", you use the add/remove (in control panel) to remove ubuntu.
2.  you then have to edit the boot.ini file (in c:/ drive) to remove the WUBI-related line.  ONLY THE WUBI RELATED LINE or you risk loosing your Vista boot.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

UBUNTU IN ITS' OWN PARTITION

-You can use gparted from the liveCD to delete the partition
-You then use a Vista install disc to fixmbr.  If you don't have a original install disc, you can download and burn this first before removing anything.

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

As for re-installation, it depends now on how you want to configure your dual-boot.  What is the issue with the first install?  Maybe there is a workaround without the need to delete/reinstall.

Back-up your files first.

---

### Post by michaelpanderson on 2009-10-02
I have a similar situation, but I don't understand the previous suggestion.
I had Vista. I bought a new hard drive, created two partitions, followed some instructions to create dual boot capability, installed Ubuntu and restored Vista. (I don't remember which order.) So now I have (at least) two partitions, one with Vista; one with Ubuntu. I apparently have TWO boot managers. The first one defaults to booting Ubuntu, so I have to move down to select a boot of Vista. Then I get a second boot manager, which defaults to Vista. I have to go through this every time I restart my laptop.
Since then, I have successfully installed Ubuntu on my old hard drive. So I would like to remove Ubuntu and the boot managers and the second partition from my new hard drive. 
Is there some way, using the "partition manager",  that I could eliminate the 2nd (Ubuntu) partition and merge it into the first? If so, will I need to get rid of the boot managers? If so, how?
 
I thought I was fairly savvy, but this is way over my head.
 
Thanks a lot

---

### Post by presence1960 on 2009-10-02
> **michaelpanderson said:**
> I have a similar situation, but I don't understand the previous suggestion.
I had Vista. I bought a new hard drive, created two partitions, followed some instructions to create dual boot capability, installed Ubuntu and restored Vista. (I don't remember which order.) So now I have (at least) two partitions, one with Vista; one with Ubuntu. I apparently have TWO boot managers. The first one defaults to booting Ubuntu, so I have to move down to select a boot of Vista. Then I get a second boot manager, which defaults to Vista. I have to go through this every time I restart my laptop.
Since then, I have successfully installed Ubuntu on my old hard drive. So I would like to remove Ubuntu and the boot managers and the second partition from my new hard drive. 
Is there some way, using the "partition manager",  that I could eliminate the 2nd (Ubuntu) partition and merge it into the first? If so, will I need to get rid of the boot managers? If so, how?
 
I thought I was fairly savvy, but this is way over my head.
 
Thanks a lot

Please start your own thread so you and the OP can get the best help possible. It can be very cumbersome for all involved trying to solve 2 issues for 2 different people on the same thread.

---

### Post by michaelpanderson on 2009-10-03
I've opened a new thread: [http://ubuntuforums.org/showthread.php?p=8046156#post8046156](http://ubuntuforums.org/showthread.php?p=8046156#post8046156)

---

### Post by michaelpanderson on 2009-10-03
I think my copy/paste got messed up. The correct link for my new uninstall Q is (I think): [http://ubuntuforums.org/showthread.php?t=1281487](http://ubuntuforums.org/showthread.php?t=1281487)

---

