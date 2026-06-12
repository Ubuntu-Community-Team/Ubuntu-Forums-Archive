---
title: "Disable Synaptics Touchpad Solution (Maybe)"
date: 2010-06-08
forum: Hardware
---

### Post by Frihet on 2010-06-08
I have been trying to disable the Synaptics touchpad on my Thinkpad Edge 13 (Intel) with 10.04. The posts in this forum and elsewhere did not help. I did find a solution that seems to work even if it is not pretty, so I thought I would put it here.

First, uncheck Disable Touchpad While Typing in Mouse Preferences. This stops the keyboard from constantly restarting the touchpad after you have turned it off it by some other method (like synclient, Gsynaptics, or GPointingDeviceSettings).

Second, install Gsynaptics (that's what I used) and uncheck Enable Touchpad. That's it. Works for me -- at least now. Time will tell.

Put Gsynaptics on the menu bar where you can access it if you want to turn it back on.

---

### Post by Professor IllDog43 on 2010-06-11
try this [http://crunchbanglinux.org/forums/topic/4282/disabling-touchpad-taptoclick-with-gsynaptics-nb-the-caveat/]("http://crunchbanglinux.org/forums/topic/4282/disabling-touchpad-taptoclick-with-gsynaptics-nb-the-caveat/")

---

