---
title: "low graphics mode"
date: 2008-01-11
forum: Hardware &amp; Laptops
---

### Post by nitinrao on 2008-01-11
sorry guys,
 but after bootin up the gutsy gibbon frm live cd, it says low graphics mode... n when i try 2 select the appropriate grap card n monitor, after applying, it goes 2 the background, after which i cant go further 2 the desktop..
any ideas on how i can install ubuntu frm here...
my config are: athlon x2 4400+ dual core, m2n-vm dvi motherboard wit nvidia geforce 7050pv/630....
monitor is viewsonic va1912wb.

---

### Post by gazj on 2008-01-11
go to system > administration > and restricted drivers (i think its called that)

then there should be an option to select nvidia drivers, tick it and apply.

Press ctrl+alt+backspace to restart the graphical desktop

---

### Post by Waldo2020 on 2008-01-11
yeah, good luck with that. "nv" works fine but without acceleration. 
"nvidia" is a stinking pile of dung. It won't read the EDID from your VGA or DVI
scrren, so you have to pull the EDID out some other way and force "nvidia" to take it with option lines in the device section. Otherwise you're stuck with a lovely 640x480 - but it's accelerated!

---

