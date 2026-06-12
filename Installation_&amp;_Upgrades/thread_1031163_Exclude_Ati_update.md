---
title: "Exclude Ati update"
date: 2009-01-05
forum: Installation &amp; Upgrades
---

### Post by Fir3chi3f on 2009-01-05
Hope this is in the right section...anyway.

My desktop has a Nvidia card and update manager wants to update the Ati video display driver.

Would it be ok to remove the Ati package in Synaptic and stop this update?

---

### Post by Tim Sharitt on 2009-01-05
There should be no problem with uninstalling the ATI driver. There are probably other drivers installed that are part of the default installation.

---

### Post by Fir3chi3f on 2009-01-06
Thanks Tim Sharitt, I'm having graphics card problems right now, and had to fall back on an old ati card. (good thing I didn't remove ati drivers just yet!) 

I'll post back when I get my Nvidia back and see what happens when removing the ati drivers. My thinking is the same as yours, but in synaptic if I try to remove the xserver-xorg-video-ati it also wants to remove xserver-xorg-video-all which worried me a bit to remove.

Hopefully RMA doesn't take too long!

---

### Post by Tim Sharitt on 2009-01-06
I wouldn't worry about xserver-xorg-video-all. It's just a meta package that depends on the actual driver packages. It doesnt install any packages itself. Removing its should have no effect on the actual drivers.

---

