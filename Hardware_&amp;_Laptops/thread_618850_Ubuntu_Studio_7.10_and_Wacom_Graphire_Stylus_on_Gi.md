---
title: "Ubuntu Studio 7.10 and Wacom Graphire Stylus on Gimp"
date: 2007-11-20
forum: Hardware &amp; Laptops
---

### Post by srblopes on 2007-11-20
I´m having an anoying problem with my wacom graphire, ubuntu Studio 7.10 and the Gimp. My Stylus is inverted in the Gimp. The eraser functions as a stylus and the stylus functions as an eraser Anyone has any idea on how to resolve this problem.
Thank you.

---

### Post by jespdj on 2007-11-21
I have noticed the same thing in GIMP.

I guess you have already enabled the Wacom stuff in your /etc/X11/xorg.conf. If not, look into that file and uncomment the lines marked with "if you have a Wacom tablet, uncomment this".

Then in GIMP, have a look at File / Preferences / Input Devices and click on the button "Configure Extended Input Devices". I haven't looked at the problem myself yet, but maybe you can find a solution by fiddling with the settings there...

---

### Post by jespdj on 2007-11-21
Well, I'm behind my computer at home now and tested this again, and my Wacom stylus now works normally...

---

### Post by srblopes on 2007-11-21
I´ve already done this about the xorg.conf and already taken a look at the preferences in gimp, but as far it´s the same. Stylus like eraser and eraser like stylus. any other idea?

---

