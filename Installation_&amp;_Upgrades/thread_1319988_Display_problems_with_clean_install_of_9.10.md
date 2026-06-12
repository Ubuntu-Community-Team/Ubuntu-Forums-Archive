---
title: "Display problems with clean install of 9.10"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by apetty on 2009-11-08
Hi folks,

I have done a clean install to Ubuntu 9.10 on an IBM thinkpad A31 (Pentium 4 processor, ATI's Mobility Radeon 7500).  The display didn't work at all (i.e. wouldn't refresh and most applications won't display other than the menu bar) after install.  I tried resetting the display size to what it should be (1400 by 1050)- just using the GUI, I am a newbie! I couldn't get that option, but when I resized it smaller (800 by 600 I think) it would work okay, at least to get me out of strife.

I'm guessing this is a driver issue with the ATI Radeon?  Please share your thoughts.

---

### Post by ximhot on 2009-11-28
I have the same problem. I upgraded from 9.04 and the display doesn't work. I tried GNOME safe mode and it works fine, just no internet connection under safe mode. So it won't help me.

---

### Post by apetty on 2009-11-29
Yes, likewise - safe mode works, but not particularly useful.  Also, the display looks good in the startup window, it's just after I log in that it craps itself.  What's going on?

---

### Post by ximhot on 2009-12-04
Same problem with T30! Very annoying. I had to reinstall 9.04. A few hours of fooling with computer and lots of complaint from wife. No fun. 

I guess Radeon 7500 is having problem with 9.10. I will wait for the next LTS to try again and will stay with 9.04 for now.

---

### Post by kristofv2002 on 2009-12-22
I had the same with A31P, setting the color depth to 16 (create xorg.conf file) solved the issue

---

### Post by henrikb on 2009-12-24
Got a clean Ubuntu 9.10 (kernel 2.6.31-14-generic) on a Thinkpad A31 (1GB RAM, 1.80GHz) with an ATI Radeon Mobility 7500 card (as reported by lspci).

I had problems with odd stripes on the display and that the system would completely freeze where not even the CapsLook led would respond. Only solution was a hard reboot.

Things like starting Firefox and the Update Manager would cause a freeze. When running System -> Administration -> System Testing, it would freeze early on in the "cycle through the detected video modes" (xrandr_cycle) test.

I did do:

```
apt-get update
apt-get upgrade
```

hoping that this would solve something but it didn't.

However, following kristofv2002 advice to the set X11 color depth to 16 works for me.  At least it does not freeze in the cycle test and when starting Firefox.  However, the gst_pipeline_tst show some artifacts in the colored bars.

Here is how you set the X11 color depth:

1. In Ubuntu 9.10 there is no longer a /etc/X11/xorg.conf file.
2. Instead, do: sudo gedit /etc/X11/xorg.conf to create a new and add:

```
Section "Screen"
 Identifier "Screen0"
 Device "Card0"
 Monitor "Monitor0"
 DefaultDepth 16
EndSection
```

3. Restart your system.

That worked for me :)

---

### Post by dugaldtaylor on 2010-04-07
Quickest fix was regress to 9.04 while I wait for Radeon or Canonical to fix for 10.X.
 
D. Taylor
Thinkpad A31

---

