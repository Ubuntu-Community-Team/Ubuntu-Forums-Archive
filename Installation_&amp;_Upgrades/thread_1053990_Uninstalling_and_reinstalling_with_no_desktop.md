---
title: "Uninstalling and reinstalling with no desktop"
date: 2009-01-29
forum: Installation &amp; Upgrades
---

### Post by gemmala on 2009-01-29
Hi,

I had a problem with my installation of 8.04 ([http://ubuntuforums.org/showthread.php?t=966596](http://ubuntuforums.org/showthread.php?t=966596)) - someone did suggest a fix, however it didn't accept my password when I tried it - I'm the only user on the machine, so I suspect it was down to a problem with my wireless keyboard not working very well with Ubuntu.  So I'm stuck with no desktop, and I want to try the time honoured tradition of 'turning it off and turning it on again'.  With no desktop, is it possible to reinstall Ubuntu?

Thanks

---

### Post by frost151n on 2009-01-29
> the time honoured tradition of 'turning it off and turning it on again'
Only known fix with a 100% success rate, haha!!

If you have a Live CD you can go through the installation process and then when it comes to partitioning tell it to format the previous partitions and then write on it.

Alternatively after booting the Live CD go to System>Administration>Partition Editor (or something similar). You should be able to manage the rest

---

### Post by gemmala on 2009-02-11
Installed from the LiveCD with little trouble, however I couldn't just format the old partition.  I have a Windows installation, and when the options came up about partitioning I could move adjust how much memory my new installation took up, but only within the existing partition for my old Ubuntu installation - I didn't want to format off all my Windows installation!  This leaves me with an old Ubuntu sat on my hard drive, still coming up on Grub, and using up hard drive space.  How can I get rid of it?  I've got the Gnome Partition Editor, and it sees the plethora of ext3 format partitions and swap areas I'm accumulating, though I'm finding it hard to tell which ones I should keep and get rid of - the only important thing for me is to clean up my hard drive!

---

