---
title: "Ubuntu Dual Boot System Issues"
date: 2009-06-08
forum: Installation &amp; Upgrades
---

### Post by vengefulnight on 2009-06-08
I have recently formatted my test pc with Windows 7 and Ubuntu dual boot. During the installation process, I did not add more HDD space to the Ubuntu section of the OS partition. Unfortunately, now, I am not able to sudo apt-get install kubuntu-desktop due to its 700+ MB space requirement. Also, when the screen saver kicks over while logged into Ubuntu, the computer will black screen and be non-responsive; thus, a reboot is needed to restore operationalization. Could the partitioning size of the OS be the reason why it appears to "crash?"

---

### Post by L.J on 2009-06-08
Hey, im new to linux so don't take any notice of my idea if its wrong :lol: but why not get a whole new hard drive just for linux ? Its not that much hassle and might be an easier and quicker solution to your problem. You are able to get some really cheap nowadays, try amazon.com/.co.uk.

just a thought...

---

### Post by vengefulnight on 2009-06-08
Getting a new HDD would be the smartest option but right now I have to deal with the one I have. Is there a way to add more partition space after the OS is already installed? I know this would alleviate one out of two of the problems in which I am having. Right now, Windows 7 is only in the RC phase. When Windows 7 actually releases, I think I will be running a straight Ubuntu box instead of the dual boot.

---

### Post by torgrot on 2009-06-08
> **L.J said:**
> Hey, im new to linux so don't take any notice of my idea if its wrong :lol: but why not get a whole new hard drive just for linux ? Its not that much hassle and might be an easier and quicker solution to your problem. You are able to get some really cheap nowadays, try amazon.com/.co.uk.
 
just a thought...
 
 
):P a big +1 on that idea, I did it when I first installed Ubuntu 6.04 and it has been a god send many times since. Install Ubuntu to the first hard drive and let GRUB boot Windows off the second hard drive. If UBUNTU goes south, I can just connect the Windows disk as the first drive and boot off of it with no problems.
 
torgrot

---

### Post by Mark Phelps on 2009-06-09
> **vengefulnight said:**
> Is there a way to add more partition space after the OS is already installed?

Boot from an Ubuntu LiveCD, or better yet, download and burn a GParted LiveCD from distrowatch.com, and run the Partition Editor.  It will allow you to resize partitions.  The GParted LiveCD is generally better because it's the latest version and it doesn't mount the partitions automatically.

Just understand that GParted can be really S...L...O...W.  It's not unusual for it to take HOURS to resize a partition.  So, let it run to completion or the partitions will be trashed.

---

### Post by vengefulnight on 2009-06-10
Thank you for the input on that program. I will have to try it out when I'm around the box. Thanks again!

---

