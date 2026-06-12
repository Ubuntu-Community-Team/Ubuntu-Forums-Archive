---
title: "ATI (fglrx) sudden flicker to black"
date: 2008-10-20
forum: Hardware
---

### Post by thijsvanhulten on 2008-10-20
Every now and then my system screen blinks to black for about a second. When it start it usually keeps happening and then all of a sudden it stops. It almost looks like my system is doing a spontaneous re-detect of my monitor.

I've check all the the log files I can view with 'Log Viewer' but there's nothing to be found.

Question 1: Does this sound familiar to anyone ?

Question 2: Is there any way to increase the log level of X, so I can findout what happening ?

Any help would be appreciated


BTW I'm running:
Ubuntu 8.04
Ati propriety drivers 8.9 (september)
Asus M2VA-VM HDMI (AMD690G)
Samsung 225 BW (on DVI)

---

### Post by thijsvanhulten on 2008-10-23
I found some my problems is accurately described as 'Annoying black full screen flash with nvidia' except for the nvidia part.

Anyone got any ideas ?

---

### Post by faintscrawl on 2008-10-26
I have something similar. It just started yesterday. I pulled some photos off my camera and watched them in a slide show. Before the show started the screen blinked for about 4 seconds. Today I have a new problem in oo. It goes fullscreen and the only way to close it is to click on File and Exit.

---

### Post by thijsvanhulten on 2008-11-11
bump

It's still happening......anyone, please ?!

---

### Post by dlenmn on 2008-11-18
I've got the same problem... no solution though.

It happens both with the proprietary drivers, and with the radeonhd drivers.

Did this happen to you before the 8.10 upgrade? I got this video card (4850) after the upgrade, so I don't know if this is a regression or not.

---

### Post by keuller on 2008-11-20
Running "older" ATI HD2900XTX with the same issue in 8.10.

Just finally converted over so I've no experience with any of the earlier releases. But I have the EXACT same problem.

---

### Post by kbo on 2009-01-28
Almost Solved

To the /etc/X11/xorg.conf file 

Changed this:
Section "Module"
        Load  "glx"
EndSection

To this:
Section "Module"
        Load  "glx"
        Option "DisplayPriority" "HIGH"
EndSection

Logged out and back in to restart the X server and now the flicker is just about gone. Running kbuntu 8.10 on Dell Inspiron with ATI HD3X00 with two wide screen monitors. I'm running the lastest restricted driver from the apt repositories. 

When I was typing fast sometimes the screens would blink about 5 times in 30 seconds. Each blink about a second long.

Now I've had 2 blinks in about 4 hours of heavy usage.
Before I would have had several 100's of blinks in that time.

See "man radeon" for more options.

---

### Post by rocco61pivello on 2009-01-29
Kbo,
if I add an Option tag unde the "Module" section, X won't start, because it says something like "unexpected tag 'Option' under section 'Module'".
If I put it under the "Device" section and I check the Xorg.0.log, it says that fglrx has ignored the "DisplayPriority" option.
Any hints? Right now I had to switch back to radeonhd because fglrx just became unusable after a while.

---

### Post by Yashiro on 2009-01-29
You shouldn't be manually loading 'glx' with that driver.

---

### Post by thijsvanhulten on 2009-09-24
Just to wrap up.

My ATI chipset Xpress1250/690G has been marked as legacy. Since this legacy driver does not support the latest X, as used in jaunty, I had no other option than to buy an add-on, nVidia card.

---

