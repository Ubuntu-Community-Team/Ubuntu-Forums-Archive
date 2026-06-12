---
title: "Only failsafe login sessions work"
date: 2009-06-24
forum: Installation &amp; Upgrades
---

### Post by tashirosgt on 2009-06-24
I installed Ubuntu 8.04 on a machine and did all the updates.  I can login into the machine using the Gnome failsafe or simpler sessions. The normal Gnome session login doesn't log me in.  

The dmesg command shows the video card is handled by the drm driver.  It says the card is 
radeon 1.28.0 20060524 on monor 0

I see no errors in dmesg, /var/log/gdm/:0.log or /var/log or /var/log/Xorg.0.log after a login failure..

I'd be happy either to fix this problem or to make the Gnome failsafe session the default login session.  I've gotten screens that popped up on login asking me if I wanted to make the Gnome failsafe session the default session and I did, according to the screen.  But it did not really make Gnome failsafe the default.

---

### Post by tashirosgt on 2009-06-28
I did find the following error in /var/log/gdm/:0.log.1

in RADEONProbeOutputModes
X: r300_emit.c:403: r300EmitArrays: Assertion `((inputs_bitset)[((_TNL_ATTRIB_COLOR0) / (sizeof (GLuint) * 8))] & (1 << ((_TNL_ATTRIB_COLOR0) % (sizeof (GLuint) * 8))))' failed.

and then the log ends.


Edit: I don't see the option on this forum to disable simleys.  The smileys result from the actual file containing the digit 8 where the smiley appears.

---

