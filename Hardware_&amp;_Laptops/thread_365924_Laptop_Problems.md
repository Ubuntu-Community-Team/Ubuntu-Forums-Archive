---
title: "Laptop Problems"
date: 2007-02-20
forum: Hardware &amp; Laptops
---

### Post by Real Newbie on 2007-02-20
I have an old Gateway Solo 2300 that I have loaded Xbuntu on. Last night I was playing with a Fluxbuntu live CD and the battery died, taking the laptop down in the middle playing with Fluxbuntu. Now that I have it connected back to power, the display won't work. I have tried to boot to Xbuntu and the Fluxbuntu live CD. No display.

Does anybody have any idea what I did?

Thx,
Noob

---

### Post by tgalati4 on 2007-02-20
Dear Noob,

Linux as a general rule does not handle hardware failure gracefully.  RAM, video RAM, BIOS errors can cause fits.  Since you were not using the hard disk, you can reasonably assume that the disk is OK.

When battery voltage declines, current increases linearly to keep the same level of power to the motherboard.  It's possible that the power supply is toasted with the sudden drop in voltage.  The tiny MOSFETs that regulate current can burn up with a surge.  With a normal battery, there are warnings and a shutdown process that starts when the battery gets to 10% of normal capacity.  With an old battery, the voltage drops off so fast that the computer doesn't have time to react and perform a normal shutdown.  This leaves the hardware vulnerable to this power fluctuation.

When running from Live CD, you are taxing the processor, moving lots of memory around (since there is only swap space available and limited RAM).  This results in more power consumption than a normal hard disk installation.  Higher power draw with an old battery is a dangerous combo.

If your laptop has a TV out or external VGA connection, try connecting them and hitting the Projector output function key to get some sort of response.

If you hear boot up noises then you can assume your power supply is OK and the display backlight is probably shot.  These are high voltage flourescents and they are also susceptible to power fluctuations.  Was your display normal brightness before the failure?  Was it dim and reddish from age?

It's fun to revive old hardware with Ubuntu.  It's also a pain to fix hardware problems.  I'm repairing a broken hinge on a year 2000 Dell Inspiron.  I'm using a binder clip to hold the display up while waiting for parts.

I'm not familiar with Gateway's construction quality, but a Google search will turn up problems that others have had.

Let us know what you find out.

Good luck,

Terry

---

