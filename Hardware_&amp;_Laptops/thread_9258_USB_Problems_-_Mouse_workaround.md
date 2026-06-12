---
title: "USB Problems - Mouse workaround"
date: 2004-12-26
forum: Hardware &amp; Laptops
---

### Post by Tyche on 2004-12-26
BACKGROUND:
I have had occasion to try various distributions of Linux, due to not being happy with FedoraCore2 not installing on my machine (I have an NVidia GForce4 video card).  The easiest way was to get LiveCD's and try them out.  If they worked and I liked what I saw, I would consider installing the full distribution.  

PROBLEM:
Two of the distros I've tried are Knoppix and Ubuntu (Knoppix is listed because of it's close association to Ubuntu).  In both cases on first booting off the CD the mouse would appear to be frozen.  Some hunting around and playing with various sthings led me to understand that these distros were seeing my "Aiptek HyperPen" tablet, attached to a USB port, as a mouse, and not looking further to find the PS/2 mouse attached to the system.

WORKAROUND:
I disconnected the pen tablet and re-booted off the Ubuntu LiveCD, and the mouse worked.  In fact, it worked well enough that I could find my way around the screen, pull up FireFox and contact this forum (Bravo! Ubuntu).

POSSIBLE CAUSE:
Disclaimer:  I am not a developer or programmer.
It is possible that the hardware search and initialization either:
1.  Assumes that a pen tablet is a mouse, or
2.  Picks up the pen tablet/USB port connection and doesn't bother looking to see if there is anything else in that catagory attached, or
3.  All of the above.

(So, alright, I'm a school teacher's son, and automatically think in "multiple guess" format  :razz: )

Tyche
Craig A. Eddy

---

