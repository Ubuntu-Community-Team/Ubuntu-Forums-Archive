---
title: "How to extend partition?"
date: 2009-09-07
forum: Installation &amp; Upgrades
---

### Post by gunkaragoz on 2009-09-07
I'm using Ubuntu 9.04 and Windows XP. I hava searched the forum but I think my problem is a bit different.

I have to extend my linux partition because its not enough for me anymore. Last time, I couldn't start Ubuntu due to lack of disk space! (Error Message was something like this) I used Live CD and deleted some files then managed to start. I think, I can't install Lubi ([http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)) I don't if it is the solution, but I don't have enough space to try! :)

As you can see in the screenshot, I have 5 gb disk space unallocated. I used Partition Magic in Windows to shrink Windows partition size and succeeded.  I want to extend my linux partition by this partition, but I can't resize or move the "extend" part to that unallocated area. I tried to do in gparted but I couldn't.

What's wrong with that and what should I do?

---

### Post by bogdan.veringioiu on 2009-09-07
Hi.

You cannot resize the system partition with gparted while mounted. You have to do this with a live cd parted ([http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)), or a live cd distro that has gparted installed.

Cheers.

---

### Post by gunkaragoz on 2009-09-07
> **bogdan.veringioiu said:**
> Hi.

You cannot resize the system partition with gparted while mounted. You have to do this with a live cd parted ([http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)), or a live cd distro that has gparted installed.

Cheers.

I've tried to do this, but it didn't work :( I could'nt move it again. Maybe I had mounted in live cd also. I'll try it again thx ;)

---

### Post by ottosykora on 2009-09-07
it could be also that you did not properly 'catch' the extended partition first.
You have kind of click only into the green border line of the extended partition and so it will become selected. Then you increase the extended partition to the left and then as second taks you can modify the logical partitions inside it.

---

### Post by drs305 on 2009-09-07
Check out this guide on expanding / :
[Expanding an Ubuntu System Partition ]("http://ubuntuforums.org/showthread.php?t=1219270")

*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

