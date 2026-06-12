---
title: "Linuxant driverloader"
date: 2005-11-15
forum: Hardware &amp; Laptops
---

### Post by MrCheese on 2005-11-15
Does anyone know if it's still possible to obtain an OEM license for driverloader when using a Ti chipset wifi card? 

I originally installed driverloader on my Hoary laptop, which installed a free license due to Ti having an agreement with Linuxant. I reinstalled no I've gone Breezy, but the OEM license seems to have disappeared from their web site.

Paul.

Edit - This is no longer neccessary. Following  the installation of driverloader & a trial license I set up ndiswrapper instead, which is now working fine. My initial ndiswrapper installation didn't work, so went to Linuxant out of desperation. Installing driverloader showed that two firmware files were required - with these in place in /lib/hotplug/firmware all is well with ndiswrapper.

---

