---
title: "Screen problems in 7.10"
date: 2007-10-19
forum: Hardware &amp; Laptops
---

### Post by Whateverist on 2007-10-19
I've upgraded from 7.04 to 7.10 this morning and have been having nothing but issues. Specs:

P4 2.66GHz
604MB RAM
Mobility Radeon 7000
1024x768 monitor

The problem:

Startup takes 2-3 minutes. The login screen is garbled (offset to the left, blurry like a TV with bad reception), as is the desktop. Changing the resolution down to 800x600 *sometimes* fixes the problem. I've had some luck with selecting the generic VESA driver, but that's hit-and-miss too. And for some reason, Xubuntu thinks I have an ATI Rage card.

I took a screenshot of the garbled screen but it came out looking fine, maybe that'd help pinpoint the problem. I've tried rconfiguring x.org and manually picking my screen size and resolution but that didn't seem to help. However, as a bonus, I now occasionally have a randomized keyboard layout when I boot.

This didn't happen with previous versions of Xubuntu down to 6.10. The hardware itself is fine, since XP works normally, as did 7.04 until I upgraded.

If anyone can help me with this, it'd be greatly appreciated.

---

### Post by senken12 on 2007-10-19
My screen also offsets completely, it just zooms in on the top corner of the screen and I have to guess if it's doing everything correctly, but the resolution goes perfectly fine once logged in.

---

### Post by Whateverist on 2007-10-19
I've worked around it by running dpkg-reconfigure xserver-xorg again and selecting the generic VESA driver. It seems to bypass the issue.

> but the resolution goes perfectly fine once logged in

This persists after logging in.

---

### Post by DouglasAWh on 2007-11-02
I too have had many problems with Gutsy.  I've never heard of installing a monitor driver, for instance, which is what "Screens and Graphics" wants me to do.

---

