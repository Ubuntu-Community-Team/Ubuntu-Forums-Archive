---
title: "Acer X223W LCD Monitor."
date: 2007-12-26
forum: Hardware &amp; Laptops
---

### Post by zxcvbnm on 2007-12-26
I have an Acer X223W LCD Monitor (Wide screen) 22 in.

I have been trying to configure the  display so it would reflect the native resolution of the monitor.
Problem is, my monitor isn't supported in Desktop Screens and Graphics settings.

Now can I configure it in xorg somehow? So it would force the resolution I want?

Thanks.

---

### Post by stephen.phillip.brown on 2007-12-28
I have the same monitor. I got it to work (in Ubuntu 7.10) at a resolution of 1680x1050 by configuring xorg to treat it as a generic LCD display.

Using the graphical "Screens and Graphics" configuration tool (in the menu System->Administration) go to the "Screen" tab and click on the model button. In the dialogue box that opens select  "Generic" for Manufacturer and "LCD panel 1680x1050" for Model; ensure that the widescreen monitor box is checked. You should then be able to select the appropriate resolution. After this, you may have to select 1680x1050 in System->Preferences->Screen Resolution to ensure that your X-session is not using one of the lower resolutions.

---

### Post by gigaferz on 2008-01-06
[http://myy.helia.fi/~karte/acer_al2216w_-_22_inch_monitor_with_linux.html](http://myy.helia.fi/~karte/acer_al2216w_-_22_inch_monitor_with_linux.html)

 You could try a different driver I did it with the intel driver the other one (i810 or something) was giving me a lot of input not supported messages

I know is not the same model but ive seen a lot of problems with acer lcds

---

