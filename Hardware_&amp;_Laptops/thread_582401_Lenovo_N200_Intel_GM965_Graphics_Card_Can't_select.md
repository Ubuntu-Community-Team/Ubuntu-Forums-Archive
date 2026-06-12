---
title: "Lenovo N200: Intel GM965 Graphics Card: Can't select its drivers"
date: 2007-10-19
forum: Hardware &amp; Laptops
---

### Post by davidjuckes on 2007-10-19
Hello all, 

Recently (about an hour ago) upgraded the feisty ubuntu that was on my N200 laptop to the new Gutsy. I was looking forward to doing this because my impression from the boards was that Gutsy included the proper drivers for my GM965, and I was pleased to see the Screens and Graphics preferences window where I could select my 965 card. 

However if I ask ubuntu to test the card, it will switch to black briefly then return and kill the window. If I go ahead without testing then on reboot ubuntu states that the screen and graphics card can't be identified and to make it start I can only select the "generic vesa" graphics driver. I can't seem to select the correct intel driver.

Completely in the dark about what's going on here! Any help much appreciated.

David

---

### Post by davidjuckes on 2007-10-20
Ignore above, ran dpkg-reconfigure xserver-xorg which found the intel chipset and sorted everything out.

---

### Post by SadaraX on 2007-10-30
I am interested to know, have you tried playing games with your laptop through wine using Gutsy?

I tried running warcraft 3 with wine, but it eventually failed to load. I also have noticed some laggy redrawing of windows within Firefox, but I am not sure what to make of these.

---

