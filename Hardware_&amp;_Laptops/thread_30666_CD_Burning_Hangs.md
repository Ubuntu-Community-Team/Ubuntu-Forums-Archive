---
title: "CD Burning Hangs"
date: 2005-04-29
forum: Hardware &amp; Laptops
---

### Post by muenzer on 2005-04-29
I'm hoping someone can help me with getting CD buring to work under Hoary.  I have an ATAPI CDRW drive that hangs while trying to burn a CD.   ](*,) 

Based on some other post I've seen here are some things I've tried:
1) Turned on DMA using *hdparm* - Nautilus still hung
2) Installed K3B - It sat for about 30 minutes before I gave up an killed it

Thanks in advance for any help.  Let me know if there is more information I need to post so people can understand my problem.

-Chris Muenzer

---

### Post by deathburger on 2005-04-29
[http://ubuntuforums.org/showthread.php?t=6687](http://ubuntuforums.org/showthread.php?t=6687)  might help.

Always [check Google](http://www.google.com/search?query=nautilus%20cd%20burner%20setup&num=10) too.

---

### Post by muenzer on 2005-05-02
[QUOTE=deathburger][http://ubuntuforums.org/showthread.php?t=6687](http://ubuntuforums.org/showthread.php?t=6687)  might help.

Always [check Google](http://www.google.com/search?query=nautilus%20cd%20burner%20setup&num=10) too.[/QUOTE]

Thanks for the links.  I'm working through them now.  I guess what I'm really looking for is some info on how to diagnose my problem.  Right now I'm not even sure what the next  steps are.

---

### Post by deathburger on 2005-05-02
[QUOTE=muenzer]Thanks for the links.  I'm working through them now.  I guess what I'm really looking for is some info on how to diagnose my problem.  Right now I'm not even sure what the next  steps are.[/QUOTE]
 Well, I had trouble at first too. I installed the xcdroast package, as I was pretty familiar with it. Knew it wasn't a hardware issue since the burner worked in Winblows, BeOS, and Debian. For my setup, I wound up having to use /dev/hdd directly as the device. cdrecord complains about it, but it works now.

Not sure if that helps you or not... maybe someone more familiar with Hoary could be of more help. :)

---

