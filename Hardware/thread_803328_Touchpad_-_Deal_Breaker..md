---
title: "Touchpad - Deal Breaker."
date: 2008-05-22
forum: Hardware
---

### Post by troupa on 2008-05-22
Computer:  HP Pavilion dv9617nr

Synaptics touchpad problems.  I personally despise tap-to-click.  The first thing I do is to immediately disable it.  I did this with Hardy as well and with the default apps installed it worked fine.  However, after installing some additional apps it would, seemingly at random, enable tap-to-click and also disable the touchpad scrolling ability. It seems that something about running kde apps is what messes up my touchpad and to get it to stop I have to install the **whole** KDE desktop and manually edit things in xorg.conf to get my touchpad to work using ksynaptics.  Still, at times, the tap-to-click will re-enable and scrolling stops working.  This is very confusing especially since I went to the lengths of adding Option TouchButton0(1,2) 0 to xorg.conf which SHOULD HAVE completely disabled tap-to-click no matter what app/de/wm was running.  There are further complications since one touchpad configuration program said I had to have SHMConfig set to "on" in xorg.conf, another said set SHMConfig to "true" to work.  
:mad:

Very irritating.  Very irritating indeed.  I ended up having to completely reinstall Ubuntu and never use any kde apps to get it to behave properly.  This is a deal breaker.  The only video dvd burning program I can find offered by Ubuntu is k3b.  Sorely disappointed.

This was the first linux distro I have tried with this, my first laptop.  I am unsure if this problem is in all distros and is a general gnu/linux/xorg/kde/etc. issue.  Still, this has lead to a decision to make the laptop a dual-boot Vista/Ubuntu machine with a 3rd vfat partion for shared data, something I was seriously trying to avoid.

I will say, however that Hardy works pretty much flawlessly on my desktop.  I would like to turn that into a headless server but it is not an option for me until I can get this touchpad working correctly under linux.

---

### Post by Zorael on 2008-05-22
Have you tried disabling tap-to-click in xorg.conf and not just via {k,g}synaptics?

```
MaxTapTime (Integer)
    Maximum time (in milliseconds) for detecting a tap.
```
Perhaps setting that to 0 or 1 might do the trick. Unlikely that you'll ever tap it for only 1ms. Unless you are heavily allergic to kryptonite.

[http://linux.die.net/man/5/synaptics](http://linux.die.net/man/5/synaptics)

---

### Post by troupa on 2008-05-22
Yes.  I did 
```
Option        "TapButton0"          "0"
Option           "TapButton1"        "0"
Option           "TapButton2"        "0"
```

which should have effectively disabled it completely.  However it did not stick all the time.

---

