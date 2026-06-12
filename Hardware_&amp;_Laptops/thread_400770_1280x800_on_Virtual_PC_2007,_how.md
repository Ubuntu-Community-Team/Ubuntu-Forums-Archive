---
title: "1280x800 on Virtual PC 2007, how?"
date: 2007-04-03
forum: Hardware &amp; Laptops
---

### Post by PQOWIEURYT on 2007-04-03
Hi,

This is my first post and my second install of Ubuntu. But this time it is on my new laptop, via Virtual PC 2007.

My native resolution is 1280x800, but Virtual PC emulates the graphics card as an "S3" graphics card. Obviously, it only works in 16 bit (virtual PC again). It would seem that Ubuntu's understanding of this this graphics driver is that it does not support 1280x800, which is probably correct. I've tried changing the driver in "xorg.conf" to "vesa" but no luck, all this while the mode under "screen" in "xorg.conf" was only set to "1280x800" only. The best I could get was: 1152x768 in full screen, and 1280x1024 windowed. Remember, laptop screen max's out at 1280x800.

Has anyone been able to achieve this wide-screen resolution in Virtual PC?

Attached is my xorg.conf.
My graphics card is an intel 945GM

Many thanks,

Hass

---

