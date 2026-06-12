---
title: "Can't use 1920x1080 resolution on acer monitor"
date: 2016-01-28
forum: Hardware
---

### Post by Kilarin on 2016-01-28
My laptop is Lenovo ThinkPad Edge E555 20DH002QUS AMD Dual Core A6-7000, 4GB RAM
Graphics adapter: AMD Radeon R5 (Kaveri), Core: 514 MHz, 14.201.1003.1001
Running Xubuntu 14.04 (32bit)
Just bought a new Acer G257HL bmidx 25-Inch Full HD (1920 x 1080) Widescreen Display
hooked up to the laptop through a vga cable and kvm switch

Problem is, this monitor should be used at 1920x180 resolution, obviously. But I can't get there!

Using driver X.Org X server -- AMD/ATI display driver wrapper from xserver-xorg-video-ati(open source, tested) 
my maximum resolution is 1280x768

Using driver for the AMD graphics accelerators from fglrx-updates (proprietary)
I have options:
1600x1200
1400x1050
1600x900

but no 1920x1080

This seems very odd to me.  1920x1080 has to be one of the most common resolutions out there.  What am I doing wrong?

thanks in advance for any help.

---

### Post by weatherman2 on 2016-01-28
Is there a custom video driver available from AMD?

---

### Post by Kilarin on 2016-01-28
[quote="weatherman2"]Is there a custom video driver available from AMD? [/quote]
Isn't that what *"river for the AMD graphics accelerators from fglrx-updates (proprietary)"* is?

It seems like 1920x1080, being a standard, should probably be in the open source driver, and definitely be in the AMD proprietary driver.  There is nothing wrong with the monitor itself, because I can get 1920x1080 when using it on another windows 7 laptop.

doesn't make any sense that 1920x1080 isn't supported in linux.

---

### Post by weatherman2 on 2016-01-28
Yeah, don't know what to tell you.  I can get 1920x1080 on my 42" Plasma TV (native is only 720p) with Ubuntu 12.04, so it's not a matter of "Linux" not supporting that resolution.  (I have an Intel graphics card.)  Although I usually recommend sticking with an LTS version, you might try booting Ubuntu 15.10 and see if there is any difference.  (Or if you aren't using 14.04.3 try booting that.)

---

### Post by Kilarin on 2016-01-29
Well, I have to apologize to the entire linux community.  I proved this morning that it is actually the graphics card.  Apparently it just does not support 1920x1080.  You have to purchase the fancy dancy (and expensive) one-link dock if you want to use that.  Sheesh.  <sigh>

Good news, but odd.  Switching from vga cable (which works with my kvm switch) to hdmi cable, 1920x1080 is now supported.
I wonder why it would support 1920x1080 through the hdmi cable but NOT through the vga cable?  anyway, I guess it's time to look for a kvm switch that supports hdmi.
thanks again folks.

---

