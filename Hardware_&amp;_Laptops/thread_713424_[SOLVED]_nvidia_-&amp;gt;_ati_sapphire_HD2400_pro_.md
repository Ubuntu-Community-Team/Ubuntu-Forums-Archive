---
title: "[SOLVED] nvidia -&amp;gt; ati sapphire HD2400 pro = blank screen"
date: 2008-03-02
forum: Hardware &amp; Laptops
---

### Post by stinkinrich88 on 2008-03-02
hi,

I used to have an Nvidia card. Now I have installed my ATI Sapphire HD 2400 video card and now all i get is a black screen when I boot ubuntu.

If I go into ubuntu recovery mode I cannot access the internet and therefore cannot download any drivers with apt-get such as fglrx. 

Oh, I ran dpkg-reconfigure xserver-xorg and haven't had much luck. I can now startx from recovery mode, but once again I cannot access the internet and when I attempt to change the display drivers (with the gui) it messes my display right up (inverted colours etc when i click "test", even if I test the one it was currently using)

Please help!! thank you!

---

### Post by stinkinrich88 on 2008-03-03
Well, in the end I managed to get the internet working with the following command:

```
/etc/init.d/udev restart
/etc/init.d/module-init-tools restart
/etc/init.d/networking start
dhclient
```

Then I started gnome (using GDM in the terminal), installed envy and got its scripts to do all the work for me. Problem solved! 

Just a few problems with my new ati card which can be found here: 

[http://ubuntuforums.org/showthread.php?p=4447822#post4447822](http://ubuntuforums.org/showthread.php?p=4447822#post4447822)

---

