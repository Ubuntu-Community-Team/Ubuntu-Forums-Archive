---
title: "More than 2 screens on Ubuntu 18.04"
date: 2018-09-19
forum: Hardware
---

### Post by frederik057 on 2018-09-19
I want to connect 3 screens on my ubuntu computer, i normally know how you can do it but the problem is that only 2 screens are recognized. 
I have tried with monitor setup in gnome (at NL 'schermen'), and they are only 2 screens seen. I have also tried with 'arandr' but same problem, only 2 screens.  
Only with Nvidia-settings i see the 3 screens, but nvidia-settings is not working perfectly anymore. When you setup with nvidia-settings and save it to /etc/X11/xorg.conf i have a black screen on start up and no other visual. When i reboot, the same problem, only when i remove the xorg.conf and restart the computer he start perfect but only with 2 screens. It looks that you can't make xorg.conf or configure xorg.conf anymore. Earlier i do it with xorg.conf (with nvidia-settings) and it works perfect, now with the newer ubuntu versions it only works with randr.

The configuration:
AMD Ryzen 2400G
Asus Prime B350 plus mainboard
12 Gb Kingston ram
2x Nvidia geforce N710 grafic cards
2x 22 inch screens (one on the HDMI output and one on the VGA D-Sub output)
and one 27 inch screen (ont the VGA D-Sub output of the other card)

---

### Post by QIII on 2018-09-19
Hello!

Which monitor is not working?

---

### Post by frederik057 on 2018-09-20
This one on the other card
"and one 27 inch screen (ont the VGA D-Sub output of the other card)"

---

### Post by QIII on 2018-09-21
Have you swapped the cables around to eliminate hardware as the fault?

---

### Post by frederik057 on 2018-09-22
Yes.
But when you open "nvidia-settings" it see 3 screens, but you can not configure anymore with nvidia-settings.  'Screens' in ubuntu doesn't recognize 3 screens, only these on the first card.

---

