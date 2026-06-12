---
title: "Determine driver status"
date: 2006-03-24
forum: Hardware &amp; Laptops
---

### Post by SeaWeedz on 2006-03-24
Ubuntu is installed, the different devices seem to be working properly, but here is my problem.  

I am trying to figure out the easy way of finding out what devices need drivers, or what devices have updated drivers that I would be able to manually install for better performance.  (If someone can point me to a howto or something, I'll RTFM..but so far I havn't found the TFM)

I have been looking through the device manager, and it collects & provides a great deal of information, however, I can't tell by reading it exactly what the status is.  Some examples..

The IDE device is the 82801AA IDE, and the info.linux.driver shows PIIX_IDE.  I've tried to googling PIIX_IDE to find out what hardware this supports or if it is a generic driver, but didn't find much.  When I was going through the "Automatix" install, I saw on there that there is support for DMA - so I'm not even sure if DMA mode is enabled.  

For the 82801AA ISA Bridge, there is no info.linux.driver listed. 

For the video, 82810 GMCH & 82810 CGC (one device that controls the graphics and one that controls/accesses graphics memory I take?) I did go to the intel website, and download the linux install package for the 82810 chipset, converted it to an installable package from the RPM file, and installed it.  Now the info.linux.driver for 82810 GMCH shows agpgart-intel (linux.subsystem is listed as pci, not agp) and the video card is working.  However, the82810 CGC does not show a linux driver installed.  

I'm not specifically looking for help with the devices I mentioned, I will do the research and find and install the drivers needed.  I would just like to know what bits of information I should be looking for to determine what I could be doing to get this box dancing.  Thanks!

---

