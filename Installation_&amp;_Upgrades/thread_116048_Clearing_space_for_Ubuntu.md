---
title: "Clearing space for Ubuntu"
date: 2006-01-11
forum: Installation &amp; Upgrades
---

### Post by Steve- on 2006-01-11
My PC currently is split into two partitions, one for XP and one for SuSE 10. I want to install Ubuntu, and have space to do so without removing either of the other 2 OSs. My plan is to shrink the SuSE partition by 15 gigs, in order to give room to install Ubuntu, but I am unsure how to do so.

My best attempt has been using the Ubuntu Live version and using attempting to use GParted to resize it. It lets me choose the options and appears to do things, but upon finishing, it tells me that one of the operations was on a busy partition and I should restart the kernel. Allowing GParted to refresh the view shows there has been no change, and restarting shows nothing has happened too.

The SuSE partition is an extended physical partition, split into a linux swap and a reiserfs type main section. I am wanting to shrink the main section, but it seems the swap is active, even when using Live Ubuntu. Do I need to unmount the swap, so that I can resize anything in the extended partition?
Or is there another way?

Thanks for the help
-Steve

---

### Post by plors on 2006-01-12
often it's best to partition a non-busy (no partitions are mounted) disk. Best way is to use a livecd.

gparted has its own [livecd]("http://gparted.sourceforge.net/livecd.php") 

oh, and don't forget to backup important files!

---

