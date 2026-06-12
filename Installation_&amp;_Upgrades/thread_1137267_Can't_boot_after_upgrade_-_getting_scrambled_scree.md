---
title: "Can't boot after upgrade - getting scrambled screen"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by galori on 2009-04-25
I upgraded from 8.10 to 9.04 via the upgrade manager. 

Now after it boots I just get a scrambled screen and its not responsive - I don't even get the login screen.  alt-ctrl-f1 or f2 or f3 don't do anything either.

I do have the Ubuntu 8.10 CD and the 9.04 CD which I can boot from if necessary

attached is a lovely screenshot, thanks for your help!

(Maybe a first step would be to try to reset the graphics settings via recover mode? going to try to search for how to do that)

**edit**: I tried "dpkg-reconfigure xserver-xorg" from recover mode, and then "gdm" and it still gave me that same scrambled screen. Then tried rebooting into normal mode with same result.  One thing I did notice is that the ubuntu progress bar while its loading is showing up perfectly, it only becomes scrambled once thats finished.
[B]
edit2: SOLVED[/B] thanks to this thread:
[http://ubuntuforums.org/showthread.php?p=7141975](http://ubuntuforums.org/showthread.php?p=7141975)
This is what I did:
```
apt-get remove --purge xorg-driver-fglrx
dpkg-reconfigure xserver-xorg -phigh
reboot
```

---

