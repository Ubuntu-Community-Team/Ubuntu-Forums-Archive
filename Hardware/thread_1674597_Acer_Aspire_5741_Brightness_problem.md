---
title: "Acer Aspire 5741 Brightness problem"
date: 2011-01-24
forum: Hardware
---

### Post by surfingonmusic on 2011-01-24
i'm running ubuntu 10.10 and the backlight wont turn on at all, i've seen this problem posted before but not on this model of aspire.
 
help please?!?!

---

### Post by loyol2degame on 2011-01-24
yes i have this exact same problem!!! i cant see anything after the ubuntu logo comes up. the backlight is completey off, and the brightness settings and the brightness shortcuts on the keyboard won't work. ugh

---

### Post by simbav on 2011-03-15
sudo gedit /etc/default/grub

GRUB_CMDLINE_LINUX_DEFAULT="**acpi_osi=Linux**"

sudo update-grub

Restart
:popcorn: :D

---

### Post by rafadev on 2011-03-28
The fix worked perfectly on acer aspire timelinex 3820T. Thanks!

---

