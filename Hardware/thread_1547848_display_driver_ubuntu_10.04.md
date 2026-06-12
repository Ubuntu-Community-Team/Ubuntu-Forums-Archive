---
title: "display driver ubuntu 10.04"
date: 2010-08-07
forum: Hardware
---

### Post by leopex on 2010-08-07
Hello, I am using a Acer Aspire 5810TG. And when i am installing ubuntu it works with the right resolution and it seems fine.

But when i am using the "Hardware Drivers" program that installs driver automatic it says that the display driver is not working. And i am pressing the "Activate" button, after the driver is installed I reboot. And when it starts up again, and start the X. nothing happens. Just a dark screen with nothing on. 

So this is not the right driver for the grafic card. How do I change this back? I am not able to access anything. Screen turn dark in the boot. What should I do? The driver it is installing from the hardware driver program is ATI/AMD. 

Thanks for answers. And sorry for bad english.

---

### Post by tadaskr on 2010-08-07
if you know your graphic card then go to it's manufacturer page and download drivers from there

---

### Post by leopex on 2010-08-08
Well lspci says that i have 2 cards?!

[I]00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)[/I]
 
And. 

*01:00.0 VGA compatible controller: ATI Technologies Inc M92 LP [Mobility Radeon HD 4300 Series]*

---

### Post by tadaskr on 2010-08-08
your GPU is Ati radeon HD 4300. so go to [http://www.amd.com/uk/Pages/AMDHomePage.aspx](http://www.amd.com/uk/Pages/AMDHomePage.aspx) and try download them. but I hear that ati drivers for linux is bad[URL="http://www.amd.com/uk/Pages/AMDHomePage.aspx"]
[/URL]

---

### Post by leopex on 2010-08-08
I have downloaded that driver and installed it... Reboot and the same thing. Screen turns black in the boot. 

Can it be that i can switch grafic card? Becouse now i cant boot at all. 

Can i boot in to a terminal whitout any kind of X?

---

### Post by leopex on 2010-08-08
Okei, I kind'a figured it out... In bios GPU was on "hybrid" I turned this into dGPU and now it is working!

---

