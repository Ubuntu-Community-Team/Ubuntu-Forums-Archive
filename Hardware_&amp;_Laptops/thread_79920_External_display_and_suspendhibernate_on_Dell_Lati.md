---
title: "External display and suspend/hibernate on Dell Latituide D800"
date: 2005-10-21
forum: Hardware &amp; Laptops
---

### Post by ziphnor on 2005-10-21
Hi,

Im trying to get things working properly on my Dell Latitude D800, im having the following problems:

1. Hibernate and suspend doesnt work
If i hibernate(which i do alot normally) it does seem to shut down properly, but when i turn on the computer again, it gives a lot of messages, the final one being some USB error and then it shows a black screen and does nothing.

However, on an almost identical machine, just slightly newer(video is 5200go instead of 4200go, apart from that no immediate difference) hibernate works fine.

2. External display doesnt quite work optimally
In windows, i have two profiles in the nvidia driver settings, one for the external display and one for the laptop display. Switching between them in software switches correctly and also changes resolution and refresh rate.
So far, the only way i seem to be able to do this in ubuntu is to hit the CRT/LCD button on the laptop itself twice(first time it duplicates the display). However now the external display will be at 1680x1050@60Hz(the laptop display settings) and i have to change these manually. Is it possible to set this up more elegantly, so that one can change this in software and with automatic resolution changes? I thought maybe one way to do it was to simply set up a dual display with two desktops, one on each screen, which would be kind of cool.

---

### Post by chanders on 2005-10-22
I suspect you are using the generic "nv" driver in one pc and the proprietory "nvidia" driver in the other.

The proprietory "nvidia" driver does not support hibernate/suspend natively.....
If you dont use 3D acceleration often, use the "nv" driver.....

If you need 3D acceleration, here is a workaround to get hibernate working with the "nvidia" driver....

[http://ubuntuforums.org/showthread.php?t=79295&highlight=suspend2](http://ubuntuforums.org/showthread.php?t=79295&highlight=suspend2)

---

