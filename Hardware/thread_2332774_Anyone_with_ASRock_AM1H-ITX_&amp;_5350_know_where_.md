---
title: "Anyone with ASRock AM1H-ITX &amp; 5350 know where to find the chipset drivers?"
date: 2016-08-03
forum: Hardware
---

### Post by giga+bytes on 2016-08-03
According to reviews on Newegg and Amazon, I should download the AMD chipset driver/drivers directly from AMD, because of many owners having trouble with these drivers obtained from anywhere else. One review said it can be found on the AMD drivers page under a "option downloads" link, but I do not see any such thing. The manual driver search (where I can select OS as Ubuntu) only seems to give proprietary graphics drivers, and down at the bottom-right of the main drivers page is a link to the "AMD chipset, AHCI, USB 3.0 and RAID drivers", but it only shows for Windows.

Anyone know which I need?

---

### Post by him610 on 2016-08-03
You don't need to download drivers from AMD. Ubuntu will take care of your system on either 14.04 or 16.04 
I own a similar mainboard, an Asus AM1I-A with an AMD Athlon 5350 Kabini and have experienced no problems whatsoever. I have no experience with raid though.

---

### Post by giga+bytes on 2016-08-03
Okay, that reviewer probably installed Windows then. I don't use RAID either, I was just typing exactly what the link showed.

---

### Post by him610 on 2016-08-04
There is some proprietary micro code available for your AMD processor. 
After you install your chosen _buntu distro, click on System_Settings>Software&Updates>tab_Additional_Drivers, give the system a little time to complete its search, you will be given the option to install Processor microcode firmware.

---

