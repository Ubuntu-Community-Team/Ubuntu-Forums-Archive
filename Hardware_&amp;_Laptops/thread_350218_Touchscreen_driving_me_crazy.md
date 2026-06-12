---
title: "Touchscreen driving me crazy"
date: 2007-01-31
forum: Hardware &amp; Laptops
---

### Post by florizs on 2007-01-31
I have a problem, 
Recently I have acquired an old cash register (epson POS IM-320) with a touchscreen.
[IMG]http://img.shopping.com/cctool/PrdImg/images/pr/177X150/00/01/b6/dc/b4/28761268.JPG[/IMG]
this thing would be perfect to setup in my living room as a jukebox and showcase for opensource software.
everything on it works except the touchscreen which has been driving me mad.

this is what I have so far:
* the touchscreen is a gunze tft touchpanel with serial input
*if I type cat /dev/ttyS3 (com-port 3) and touch the touchpanel I get events in the order of:
```

Txxxx,xxxx on touch of the screen
Rxxxx,xxxx on release of the screen

```

*if I use the program touchcal [http://touchcal.sourceforge.net/](http://touchcal.sourceforge.net/) and set the mode to Microtouch
I get a set of coordinates, however the microtouch drivers do not work for me.

*I have tried the gunze toucscreen driver 
[http://ar.linux.it/software/gunzets/](http://ar.linux.it/software/gunzets/)
*I have copied it the driver (gunze_drv.o) to 
```

/usr/lib/xorg/modules/input/gunze_drv.o  and also to 
/usr/lib/xorg/modules/input/gunze_drv.o

```
but It won't load

var/log/Xorg0.log says:
```

(EE) no input driver matching gunze

```

does anybody have a gunze serial touchscreen working? and how did you do it?
or does anyone have other experience with touchscreens? I could use some pointers.

It would be a shame if i had to install windows on this thing just for a stupid touchscreen driver.

---

### Post by PhillD on 2007-03-20
Hi,

Did you ever get this resolved?  I'm having a similar problem.  Except I got the driver to be recognized (somehow) but I'm connecting via USB and it's still not working at all.

Phill

---

### Post by florizs on 2007-06-21
> **PhillD said:**
> Hi,

Did you ever get this resolved?  I'm having a similar problem.  Except I got the driver to be recognized (somehow) but I'm connecting via USB and it's still not working at all.

Phill
nope I gave up, since I was in my exam week and had been fiddling with the thing for about two months.
I finally got the win driver from epson. (the touchscreen is GUNZE) and installed windows.
It's not working smooth now with the virusses etc but hopefully i'll find time in the vacations to work on it.

---

