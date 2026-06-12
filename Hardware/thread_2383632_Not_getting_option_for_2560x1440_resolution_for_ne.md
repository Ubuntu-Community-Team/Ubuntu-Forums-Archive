---
title: "Not getting option for 2560x1440 resolution for new monitor"
date: 2018-01-27
forum: Hardware
---

### Post by Eredeath on 2018-01-27
I'm trying to get the full resolution out of my new monitor, a Lenovo L24q_20 which is 2560x1440 connected on HDMI1
However I'm only getting the option for 1920x1200
My computer is capable of the full resolution on the HDMI but I haven't had any luck setting it. I've tried using xrandr and it always ends in an error: "Configure crtc 0 failed" with no other useful information about why it might have failed. 
I'm using 64bit Ubuntu 16.04 LTS on an Intel Core i7-3630QM CPU @ 2.40GHz × 8 with Ivybridge Mobile graphics 

Any help would be appreciated. 

Thank you

---

### Post by olegorov on 2018-01-28
I have the same problem.
Laptop MSI GL62 6QF with Intel Graphics 530 and NVidia GTX960M. New monitor Samsung C27H711QEI with native resolusion 2560x1440 at 60Hz and HDMI cable.
Windows 10 works with this monitor as expected. But Ubuntu 17.10 shows only FullHD resolution at 60Hz.
With cvt and xrandr I can setup 2560x1440@58Hz (hsync: 86.41 kHz; pclk: 300.00 MHz). This configuration works fine.
But I still don't know:
1. Why I cannot use 60Hz and
2. Where and how to save these settings? (gdm3, xorg.conf, [COLOR=#333333][FONT=monospace]~/.xprofile ?)[/FONT][/COLOR]

---

### Post by Autodave on 2018-01-28
olegorov: please start your own thread on this. The solution to your issue could be quite different from Eredeath's issue since you both have different graphics cards, computers, etc.

---

### Post by Yellow Pasque on 2018-01-28
Post the /var/log/Xorg.0.log (use code tags). Maybe it's an issue with EDID.

---

### Post by olegorov on 2018-01-29
done

---

### Post by maventulep on 2018-08-26
I have the same issue on 64-bit Ubuntu 18.04 LTS on an Intel Core i5-4200H and 4400 graphics through HDMI. Did any of you manage to solve it and if so, how?

It may be interesting to mention that the screen resolution got picked up automatically and correctly (2,560x1,440) by Ubuntu 14.04 LTS on exactly the same hardware. What gives?

Thanks!



Tried the steps laid out here: [http://ubuntuhandbook.org/index.php/2017/04/custom-screen-resolution-ubuntu-desktop/](http://ubuntuhandbook.org/index.php/2017/04/custom-screen-resolution-ubuntu-desktop/)

but to no avail, the resolution didn't take :(

---

### Post by wildmanne39 on 2018-08-26
Hello maventulep, please start your own thread instead of posting in an unsolved thread that is old you will be more likely to get the help you need that way.

Thanks

---

### Post by maventulep on 2018-08-26
Will do!

---

