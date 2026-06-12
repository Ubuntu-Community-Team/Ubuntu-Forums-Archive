---
title: "Fn+F5 CRT/LCD key not working"
date: 2008-02-23
forum: Hardware &amp; Laptops
---

### Post by xdevnull on 2008-02-23
I am using an averatec 1050.  The other Fn keys (sound/brightness/mute/sleep) work fine, but for some reason the screen one won't (F5 - VGA/LCD).  If I boot the laptop with a vga cable plugged in, it gets detected and mirrors my laptop screen.  If I don't, when I plug in the monitor cable and hit the Fn key, nothing happens.

Anyone have an idea why these keys don't work when the others do?  Is there a fix or a work around?

Thanks

---

### Post by jpeddicord on 2008-02-24
It's a problem with X.Org, the display manager. If you are running 7.10 (Gutsy) or better, you can configure the external monitor from System > Administration > Screens and Graphics. This is fixed even further in the development version, 8.04, to be released in April. 8.04 uses a newer version of X.Org that is able to detect external monitors the moment they are plugged in.

---

### Post by xdevnull on 2008-02-26
Thanks.  Yeah I tried playing around with that - adding an extra monitor with a profile but it invariable hosed my X session with a kinds of weirdness on both displays.  I finally just gave up.  Hopefully it will be fixed in April!

---

