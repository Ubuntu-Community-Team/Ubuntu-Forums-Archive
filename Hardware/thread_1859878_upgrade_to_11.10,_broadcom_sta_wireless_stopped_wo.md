---
title: "upgrade to 11.10, broadcom sta wireless stopped working"
date: 2011-10-14
forum: Hardware
---

### Post by imnvs on 2011-10-14
[http://ubuntuforums.org/showthread.php?t=1859554](http://ubuntuforums.org/showthread.php?t=1859554)

I posted the thread I've provided the link to above.  I don't know, now, if I posted it in the right spot.  Either way, I'm kinda screwed.  I need my wireless working and it isn't, and the 11.10 upgrade from 11.04 is what caused it.

---

### Post by Axx83 on 2011-10-14
It might also be that you don't need it anymore, what is the name of your wireless card? on my laptop the open source driver works flawlessly

---

### Post by tornadoes28 on 2011-10-14
My wireless stopped working also after going to 11.10 from 11.04. I have a Dell Inspiron and it does not connect to the wireless after the upgrade.

---

### Post by Axx83 on 2011-10-15
try to remove the sta driver by blacklisting it, I don't know how's it called, but if you find the name of the module you just insert it in one of the files in /etc/modprobe.d/blacklistxxx and it should load the open source driver by itself, but only IF your card is supported by it, you need to check

---

### Post by nutznboltz on 2011-11-24
Real answers:

[http://nfolamp.wordpress.com/2011/10/15/ubuntu-11-10-getting-wireless-bcm4311-working/](http://nfolamp.wordpress.com/2011/10/15/ubuntu-11-10-getting-wireless-bcm4311-working/)

[http://askubuntu.com/questions/68557/how-do-i-get-a-broadcom-bcm-4311-working](http://askubuntu.com/questions/68557/how-do-i-get-a-broadcom-bcm-4311-working)

---

