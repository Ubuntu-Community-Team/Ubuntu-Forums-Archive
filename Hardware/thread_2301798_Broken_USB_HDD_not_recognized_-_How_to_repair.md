---
title: "Broken USB HDD not recognized - How to repair?"
date: 2015-11-05
forum: Hardware
---

### Post by tigerjack89 on 2015-11-05
I know, there are a lot of question in regard to this argument, but I'm still stuck at the begininng phase.
I have a broken external USB drive (say HDD1): it fell on the ground and now it makes the typical sounds of a physical damage.
It is formatted as NTFS and has 2GiB of memory.

So, I've bought another external USB drive (say HDD2) to recover the files on the old one.

The problem is that when I connect HDD1 to Ubuntu it doesn't show off anywhere. It isn't listed in GParted, fdisk, blkid, df nor using lsusb or any other kind of tool. Also, there is no track of it on dmesg.

So, how could I repair HDD1?

---

### Post by weatherman2 on 2015-11-05
You probably will not be able to "repair" the old drive.  At best, you will be able to recover some of the files form it.  The drive may have completely failed, so that you may have to pay a data recovery service to extract your data with special equipment, at great expense.  I have a few bad drives sitting around that have failed in this category - not with important data on them (not worth any expense for data recovery) but still sitting around in case "some day" there is some more practical way to get the data off, just because.

There are a few things you can try to try to get data off yourself.  One is to remove the internal drive from inside the external USB case, then plug the internal drive directly into a computer.  However, this will probably destroy the external drive completely, and it may not help anything anyway.  It could be that the USB controller is damaged and that if you plug the internal drive directly into a computer it will work,  but if it is making "sounds of a physical damage," it is likely to be the drive itself.  But it's something I would myself try.  There is some chance the drive has a strange connector that will not allow it to be plugged into a conventional SATA port on a desktop computer, but it might just be SATA and plug right in to any modern desktop computer, so you could try it.

---

### Post by TheFu on 2015-11-05
When a drive makes noises, it isn't good. That generally means platters and heads are rubbing - destroying the physical surface and the data. This is the worst type of issue.

You can try getting as close to the platters as possible - work your way in. This is what a commercial data recovery company would do. 
* Remove the drive from the USB controller. See if the data can be accessed. Doubtful.
* Replace the drive electronics with an exact version of the same. That means you need the exact same model HDD (not USB parts).
* if you are crazy-good, perhaps replacing the heads is possible. [http://www.harddrive-repair.com/head-swap.html](http://www.harddrive-repair.com/head-swap.html) "replace HD heads" found a few youtube videos.

The scraping sounds probably mean this won't work. Every attempted read probably does more damage and loses more data.

Backups are handy at times like this and much cheaper.

---

