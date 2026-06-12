---
title: "Booting Ubuntu on multiple machines from external USB (graphics issue)"
date: 2007-06-27
forum: Hardware &amp; Laptops
---

### Post by KirbySaysHi on 2007-06-27
Hi all,

I've installed Ubuntu to my external USB hard drive using an office computer, and it seemed to work great. However, once I tried on my home computer, it refused to start x, even after reconfiguring with dpkg-reconfigure. It gives an error of "No screens detected". I'm then dumped to a console prompt.

At work I have a Radeon something, which works fine with the desktop effects as well...
At home I have a Nvidia 7600 GT. I tried installing the GLX drivers and ronconfiguring xorg, but no go. The closest I got to a desktop was a white screen with tiny black checkers, and a mouse. The mouse would move, but did nothing. 

I guess the question is: if I reinstall Ubuntu using the live cd onto the external FROM MY NVIDIA COMPUTER (rather than at work), I assume the driver will get loaded and configured automatically?

I later tried to boot from the external on my laptop, which worked fine, but I still had to reconfigure xorg. Is there a way around this?

---

