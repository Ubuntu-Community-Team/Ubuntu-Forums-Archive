---
title: "X-server wont start after ATI driver update(new 8.29.6 drivers)"
date: 2006-09-27
forum: Hardware &amp; Laptops
---

### Post by mmgfish on 2006-09-27
Hey guys, this is my first post ever in a forum, I always read other peoples forums and found answers to my problems but this so far is being very stuborn.

Installed Ubuntu 6.06 and it picked up my ATI Mobility Radeon x300 as a "M300", although everything looked great (got my 1920x1200 resolution I get in XP normally) the FPS count using glxgears was awfully low (800-900 FPS). Checking with fglrxinfo  I would get that the OpenGl vendor string and the other two lines were in fact these mesa3d.org drivers rather than ATI Radeon drivers.  So I went on and used this How-to:

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

and used the manual option to upgrade to the latest ATI drivers (supportive of X300), I went through all the commands and everything went flawlessly. I went to reboot and problems started

1.  I get the Ubuntu welcome screen
2.  I get to log in
3.  Right after logging in all I get is the red background and the mouse pointer and it gets stuck there.

Ive tried everything (checked xorg.conf, flgrx, reconfigured xorg.conf) sometimes I got the blue screen saying that xserver could not start at all, sometimes I get the login screen but once I log in it doesnt go past the red screen with the mouse pointer.

I hope I was very clear,

Thanks for any support

Inspiron 6000:
Pentium M 2 GHZ, 2GB RAM, 100GB 7200RPM HD, ATI Mobility Radeon x300 128 MB

---

