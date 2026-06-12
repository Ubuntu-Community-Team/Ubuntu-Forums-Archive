---
title: "Dell C800 Video issues"
date: 2007-10-22
forum: Hardware &amp; Laptops
---

### Post by thevoidreturns on 2007-10-22
Hey, I've just got a new (well old) laptop and I've installed Unbuntu on it, with the lastest version.

The problem which I have is that the monitor isn't detected properly (its a weird resolution) and I cant get correct resolutions, I only have a little sort of window in the centre of the screen.

So to try and solve the problem I went straight for

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

But unfortunately, I get the error:

```

xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.2007102231625

```

I didn't have this problem on my other laptop which I have recently installed Unbuntu onto (I've just become a linux fan!).

I know how to get the laptop into Vesa mode, but it will only display 800x600 which looks really silly on this laptop.

Thanks.
Adam

---

### Post by allanE on 2007-10-22
try Fn + F7. This will force change the resolution (hardware). I run the C800 and have tried many distros and most do not detect the video properly. This fix  is necessary each time the laptop is booted.

---

### Post by spoolboyy on 2008-02-28
I can see I'm resurrecting a dead post... but just in case anyone else runs into this issue...

With my c800 it seems to be a matter of horizontal refresh.  Although its cumbersome, it is possible to get the OS installed (on my unit anyway) by moving the windows side to side in order to read them.

the c800 was released in two models that ran in two different native resolutions, one is 1400x1050 and one is 1600x1200.  nice BIG resolutions!  My machine runs at 1600x1200.  

Once installed, go to System Settings --> Monitor and Display --> Hardware

and select the configure button for your "Monitor #1."

from the generic list, try the LCD Panel that fits one of those two resolutions.  Then go back to the settings and drag the resolution bar to FULL res.  It seems that once its at max res, there arent any problems with the chopped up screen issues we experience on install.  Apply changes and enjoy.  I do NOT have to redo this each time I boot as the above poster seems to.

Now if anyone can get me the refresh rates or tell me what I'm doing wrong that'd be great.  Any apps I run at full screen revert back to being all messed up and awful, preventing me from using them.  so no games on my lappy :(

hope this helps anyone else with a C800.  If you wish, PM me for any more questions or to help me out.  thanks.

-Adam

---

