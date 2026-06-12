---
title: "LCD detection problem with Asus V6VA"
date: 2006-06-13
forum: Hardware &amp; Laptops
---

### Post by Enigmatic on 2006-06-13
I can't even boot into the LiveCD on my V6VA.

The GDM does start as I can hear the sounds, but I get a black screen.

Flipping to the terminal and running dpkg-reconfigure xserver-xorg lets me specify the vesa driver and 1400x1050 at 60Hz for the screen. I then kill X, but starting it from /etc/init.d/ fails.

I tried startx, and it fails saying something like:

(EE) VESA(0) no matching modes
(EE) Screen(s) found, but none have a usable configuration.

Any ideas?

---

### Post by c-prompt on 2006-06-14
Could you post what's under your "screen" section of your xorg.conf (/etc/X11/xorg.conf) ?

---

### Post by Enigmatic on 2006-06-14
Sure.

Section "Screen"
Identifier "Default SCreen"
Device "ATI Technologies Inc, Radeon Mobility X700 (RV410)"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1024x768" "800x600" "640x480"
EndSubSection

And then the depth repeats for 4, 8, 15, 16 and 24. I deleted all the other entries, changed the depth of 1 to 24 and erased all modes and added "1400x1050", but it still gives me the same error. This is using the safe graphics bootup option.

---

### Post by Enigmatic on 2006-06-14
Finally got this working! I had to setup a static IP and install the ATI driver as described in the Ubuntu Wiki. Then I edited xorg.conf to point it to the fglrx driver instead of the ati driver. Then I did telinit 1, followed by telinit 2, and to my amazement GDM came up!

---

