---
title: "xf86-video-intel Trouble with External CRT"
date: 2007-07-27
forum: Hardware &amp; Laptops
---

### Post by roots on 2007-07-27
hi,

i'm trying to get an external display to work on my acer notbook with intel 855gm gfx chipset, that is, i ONLY want the exernal display to be active. i'm running ubuntu feisty.

i was using the i810 driver before which worked fine as far as the crt switching is concerned: i did a fresh feisty install with crt connected, then when i booted the machine with crt still attached, then only the crt was active, without any maniplulations of xorg.conf.
now unfortunately i did not get the proper resolutions working, even when using 915resolution.

that's why i switched to the xf86-video-intel driver (2.1.0) but - now when i boot into ubuntu with crt attached, BOTH displays (crt and internal) are activated, showing the same content both at 1024x768 which is what i'm definitely NOT looking for. using the fn-f5 key combination doesn't have any effect

so now the question is: is there any way to deactivate the internal display, so i can use only the external one with the desired, high resolution?


cheers and thanks in advance,
root.

---

