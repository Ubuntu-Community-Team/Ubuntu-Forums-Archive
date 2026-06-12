---
title: "grub timeout=0"
date: 2005-05-16
forum: Hardware &amp; Laptops
---

### Post by analyser on 2005-05-16
HI ; 

I've changed my menu.lst in /BOOT/GRUB  and set  timeout=0  by mistake.  :mad: 

default=0 
timeout=0 
splashimage=(hd0,1)/grub/splash.xpm.gz 

I've TWO partitions XP and UBUNTU; now it starts automatically on XP.

PLZ How can i turn back to the initial settings  ??


THANKS FOR YOUR HELP ;

---

### Post by NTolerance on 2005-05-16
Boot with the Ubuntu live CD and mount your HDD.  Then fix your menu.lst file.

---

### Post by wvslkr on 2005-05-16
Just change timout to what you want, I believe the default is 30.

---

### Post by the_clown on 2005-05-16
[QUOTE=analyser]HI ; 

I've changed my menu.lst in /BOOT/GRUB  and set  timeout=0  by mistake.  :mad: 

default=0 
timeout=0 
splashimage=(hd0,1)/grub/splash.xpm.gz 

I've TWO partitions XP and UBUNTU; now it starts automatically on XP.

PLZ How can i turn back to the initial settings  ??


THANKS FOR YOUR HELP ;[/QUOTE]
 Boot into windows and install this program:
Explore2fs
[http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)
and modify menu.lst

---

### Post by spd106 on 2005-05-16
Hi,  You could make a grub boot floppy. Not sure how to do this from windows... You might be able to use rawrite, check out the grub website for details.

Have you tried pressing esc very quickly as it boots?

Good luck

---

