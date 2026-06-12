---
title: "CD skipping problems emerge after Hoary upgrade"
date: 2005-04-01
forum: Hardware &amp; Laptops
---

### Post by synd on 2005-04-01
I just recently upgraded to Hoary from Warty and have an Asus 48x16x48x CDRW drive and just have noticed that while playing CDs, the CDs skip awkwardly. Like, i can hear other bits of the song while the song plays and skips. Really awkward. Funny thing is, I have the same exact problem on my Toshiba laptop that was recently running upped to Hoary from Warty.

this is my hdparm /dev/hdc

/dev/hdc:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

I was advised to do hdparm -u 1 -d 1 /dev/hdc, and that enabled dma and unmaskirq. That didn't work either. Unless I should enable those and reboot to see if it made a difference. But when I reboot it disabled those (i checked upon login) so I'm not even sure if hdparm -u 1 -d 1 /dev/hdc is what I need? So.. how do I set Ubuntu to do hdparm -u 1 -d 1 /dev/hdc automatically during boot? Or is this even the solution to my problem?

Thanks in advance guys!

---

### Post by kagou on 2005-04-01
Look in /etc/hdparm.conf

---

### Post by synd on 2005-04-01
[QUOTE=kagou]Look in /etc/hdparm.conf[/QUOTE]

What do I do from there?

---

### Post by ubuntu_demon on 2005-04-01
[QUOTE=synd]What do I do from there?[/QUOTE]
 here are some relevant links regarding dma :
[http://www.ubuntuforums.org/showthread.php?t=17071](http://www.ubuntuforums.org/showthread.php?t=17071)
[http://www.ubuntuforums.org/showthread.php?t=19519](http://www.ubuntuforums.org/showthread.php?t=19519)
[http://gentoo-wiki.com/HOWTO_Use_hd...ice_performance](http://gentoo-wiki.com/HOWTO_Use_hd...ice_performance)

---

