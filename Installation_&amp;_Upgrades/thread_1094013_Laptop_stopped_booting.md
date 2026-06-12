---
title: "Laptop stopped booting"
date: 2009-03-12
forum: Installation &amp; Upgrades
---

### Post by Toe Knee on 2009-03-12
Hi,
  This morning my laptop was working fine, I turned it off and went for the bus.  Bootin it up this morning it can't find the ubuntu partitions.  

I've booted from a live disk, and it has /dev/sda4* in gparted as unknown.  I'm not sure what is supposed to be there, the ubuntu partitions are encrypted.  Can anyone help me restore them?

* My partition layout it:
[LIST]
[*]/dev/sda1 - EFI
[*]/dev/sda2 - hfs+ (OSX)
[*]/dev/sda3 - /boot (unencrypted)
[*]/dev/sda4 - LVM with / /home and swap space encrypted
[*](and some unallocated space at the end from when I upgraded harddrives...)
[/LIST]

Any ideas how to get it back?

Cheers in advance.

---

### Post by wpshooter on 2009-03-12
I would be more concerned about WHY it is that it would boot in the first place.  I noticed that you said "I turned it OFF and went to the bus".  Does that means that you PROPERLY shutdown the computer's O/S or did you just press the power button and actually just turn the computer off without properly shutting down the O/S ?

If you can not get a Ubuntu fscheck run on the system, then I would suggest that you get the diagnostic software from your hard drive manufacturer and test the integrity of your hard drive.

---

### Post by Toe Knee on 2009-03-12
Yes, I did shut it down properly.  Maybe I didn't explain it well enough, but rEFIt wouldn't see the Ubuntu partition.

It turns out that this happend when I was re-partitioning an external disk last night.  For some reason, grub get's lost on the internal disk.  I had to re setup grub, and now things work.

The following topics detail the issue and resolution.  Although there doesn't seem to be a bug in launchpad about it.  Off to report one now...

[http://ubuntuforums.org/showthread.php?t=871410&highlight=restore+grub](http://ubuntuforums.org/showthread.php?t=871410&highlight=restore+grub)
[http://ubuntuforums.org/showpost.php?p=121355&postcount=5](http://ubuntuforums.org/showpost.php?p=121355&postcount=5)

---

### Post by Toe Knee on 2009-03-12
My bug report [https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/341792](https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/341792)

---

