---
title: "New monitor - any problems to watch out for?"
date: 2007-12-25
forum: Hardware &amp; Laptops
---

### Post by Scruffynerf on 2007-12-25
Ubuntu 7.04, likely to upgrade to 8.04. 7.10 no worky for me.

Currently have a 17" CRT (LG Studioworks 710s), @1024x768 and 50hz  looking to upgrade the monitor to a 22" LCD (Acer 223w).

Also, running the nvidia driver 169.04 (beta) btw. Have a nvidia 6600GT 256MB GPU.

I'm not intending to run dual-screens, will be happy at this stage anyway with the one large one.

Looking around the place, it looks like I should just be able to unplug the old monitor, plug in the new one, boot, open up the nvidia manager, set the resolution up a few notches, and then up the resolution on the 'Screen Resolution' options.

Or am I likely to run into problems?

If anyone has any advice or experience with monitor swapovers, I'd like to hear it.

---

### Post by taurus on 2007-12-25
Is that the black Acer or the new white Acer?

You need to boot into recovery mode from GRUB menu and reconfigure X server again with

```
dpkg-reconfigure -phigh xserver-xorg
```
I would pick **vesa** driver until you get your machine up and running again.  Then, go into System -> Administration -> Restricted Drivers Manager and install nvidia driver for your graphic card.

---

### Post by ThomasWii on 2007-12-25
Just to let you know, you cant upgrade from 7.04 to 8.04, you have to do 7.04 to 7.10 then 8.04.

---

### Post by Scruffynerf on 2007-12-26
> **ThomasWii said:**
> Just to let you know, you cant upgrade from 7.04 to 8.04, you have to do 7.04 to 7.10 then 8.04.

Considering that 7.10 doesn't work from either an upgrade or a clean install, it will be 8.04. Clean install. 7.10 is just too buggy.

Taurus: Oh, I still have to worry about doing that do I? Hm. considering everything, I'll most likely go into the recovery and re-install the nvidia driver - it sets up xorg better with the correct drivers rather than that command, which just puts everything back to "nv".

Actually, all in all, the nvidia driver install script works a hellava lot better than the old reconfigure command.

---

