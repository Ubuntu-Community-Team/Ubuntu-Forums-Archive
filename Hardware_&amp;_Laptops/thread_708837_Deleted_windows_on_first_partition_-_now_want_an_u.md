---
title: "Deleted windows on first partition - now want an use for said partition"
date: 2008-02-26
forum: Hardware &amp; Laptops
---

### Post by c0ldfusi0n on 2008-02-26
Hey everyone, thanks for taking the time to have a look.

I'll get straight to the point. I have a Dell Inspiron 1501 and I must say I was impressed how well Ubuntu (x64 Gutsy) is working on it. It's been on it since edgy, and I have no complaints whatsoever. Up until now, I dual-booted with Windows XP - here's the setup:
/dev/sda1 = Windows [ntfs]
/dev/sda2 = Ubuntu [ext3]
(Note that they're both sda - so same hard drive just different partitions)

The veterans among you should recognize my problem right there, or so I'd like to think.
Here's the thing. I converted /dev/sda1 to reiserfs so I could store some data on it since /dev/sda1 is running out of space (15gb left). The main problem is, it's the same hard drive, and Ubuntu is located on the second partition. I do realize it's silly to be booting on a second partition and storing data on the first, but since I had Windows on it before, as far as I know, that's all I can do right now, unless I merge both partitions and reinstall Ubuntu.
Now, the thing with having done that is that I now have a shiny new partition of 40gb to store stuff on. But my user can't write to it. 

So bottom line is, I either want a way to merge sda1 and sda2 without losing data (which I highly doubt is possible) or learn how to be able to write to the new reiserfs partition I have created on /dev/sda1 - maybe have something like /home/pluc/audio link to /media/sda1/audio or neat stuff like that.

Oh, and I haven't rebooted yet - I'm relatively nervous that what I just did might screw up GRUB (though I removed (hd0,0) entries in menu.lst).

Thanks, appreciate any help.

---

### Post by brandon_r87 on 2008-02-26
If I understand what you're saying here, you want to either (a) make the old partition part of your Linux partition or (b) use space as a new partition for storing other files on.  Both are pretty easy, though (a) will be more time-consuming and risky than (b).

To make your new free space part of your linux partition, just use a live CD like gparted, or GNOME Partition Editor, to erase sda1.   Then you can just resize/move your Linux partition  to fill your free space.  Before you do this, back up /home and anything else you couldn't simply reinstall.  The reason is that the move/resize can sometimes mess up, but I've done it multiple times and never had a problem.  It takes a long time, but once you start it, you can leave and come back to check on it.

To use the space for other files, you just use gparted to make and format a partition, then do some editing in /etc/fstab.  There are tons of resources for doing this, but I've always found [this one]("http://www.tuxfiles.org/linuxhelp/fstab.html") to be handy.  It's not the most detailed, but it's easy enough to get most things done.   I like using this for something like having all my music or MythTV recordings on a partition of its own.  Linux is not like Windows in that you can't install programs onto other partitions or directories, at least I don't think it's possible, so sometimes you just need more space on your Linux partition.

Brandon

Edit: I don't think you'll have to modify GRUB's menu.lst, no matter which method you take, but I could be wrong.  If it doesn't boot, it's easy enough to fix using any live CD.

---

### Post by c0ldfusi0n on 2008-02-26
> To make your new free space part of your linux partition, just use a live CD like gparted, or GNOME Partition Editor, to erase sda1. Then you can just resize/move your Linux partition to fill your free space. Before you do this, back up /home and anything else you couldn't simply reinstall. The reason is that the move/resize can sometimes mess up, but I've done it multiple times and never had a problem. It takes a long time, but once you start it, you can leave and come back to check on it.

Are you sure doing that with a partition that's BEFORE the actual partition that's being booted won't mess up anything?
/dev/sda2 (which is where Ubuntu is) would become /dev/sda - and so would /dev/sda1

I not only *move* the actual files, but I change the drive label and location (or however it's called) from /dev/sda1 and /dev/sda2 to /dev/sda.... if you tell me you're sure and you've done it in the past, I'll give it a shot. I've got around 20gb of music, and I'm currently reformatting my desktop so no backup possible...

---

