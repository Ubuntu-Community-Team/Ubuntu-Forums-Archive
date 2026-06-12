---
title: "Difference between Intel driver and included driver?"
date: 2004-11-13
forum: Hardware &amp; Laptops
---

### Post by kaput on 2004-11-13
I have an i855 chipset in my laptop. The kernel driver for the video card actually does pretty well, but I was wondering what differences (if any) there were between it and the driver offered by Intel. Anyone have any idea?

[Intel's  Driver](http://downloadfinder.intel.com/scripts-df/filter_results.asp?strOSs=39&strTypes=DRV%2CARC&ProductID=922&OSFullName=Linux*&submit=Go%21). (Not the "extreme" edition. Should be the bottom one.)

---

### Post by mrm on 2005-03-31
I have a Dell Inspiron 700m with the Intel Extreme Graphics 855 GM.

Ubuntu doesn't seem to see my "wide screen" capacity. I'm wondering if the intel drivers will fix this. Or does anyone know a way that I can get Ubuntu to use the correct screen resolution? Thanks.

---

### Post by tyreth on 2005-04-13
You can get it working.  [http://www.linux-on-laptops.com/dell.html](http://www.linux-on-laptops.com/dell.html) and read some of the tips there.

I've got it working in ubuntu with widescreen.

---

### Post by Noccy on 2007-10-07
Sorry for the gravedigging, but I can't seem to find an answer anywhere.

I just installed Ubuntu on my friends laptop (a Dell Latitude D505), and I have been unable to find a properly working driver besides the VESA one. The driver that was default for the Intel i855 chipset (i810 driver) pushes the display contents 1cm down (which hides the bottom centimeter) and adds garbage to the top centimeter of the screen. Furthermore, hardware cursor doesn't work. VESA mode works with what I assume is a software cursor, but no acceleration so it's really slow.

What driver should I use and what should I change to sort this out?

Regards,
Chris

---

### Post by ljonesj on 2007-10-07
i would try 
sudo apt-get install xserver-xorg-video-intel

or something like i810 after intel i had to do this in fiesty to get screen resoulution up towere i like it not for gutsy beta thou

---

### Post by Noccy on 2007-10-09
> **ljonesj said:**
> i would try 
sudo apt-get install xserver-xorg-video-intel

or something like i810 after intel i had to do this in fiesty to get screen resoulution up towere i like it not for gutsy beta thou

Thank you :D Replacing the i810 driver with the xserver-org-video-intel one did the trick. Everything is working as it should now :D

Cheers,
Chris

---

### Post by ljonesj on 2007-10-09
your welcome i have the 950 intel graphics on my acer laptop and to get it working with the resolution1280x800 in fiesty i have to do that for gutsy i dont

---

