---
title: "Can't install 7.10 on my desktop"
date: 2007-12-05
forum: Hardware &amp; Laptops
---

### Post by chendry on 2007-12-05
Hi 
could someone help me please!!!!

I am trying to install 7.10 on my desktop, 
#Processor: Intel Core 2 Quad Q6600 2.4GX4 2x4Mb Quad Core 1066M LGA775

#Motherboard: Asus P5KR Inter P35 Chipset , Core 2 Quad support
#RAM: 4GB DDR2-800
#Hard Drive: 1TB(2x500GB) Seagate 7200.11 32MB Cache SATA2 Harddrive Raid0
#Video Card: 8800GT 512MB PCI-E Video Card 2x DVI-I HDTV

but the install gets to *Running local boot scripts (/etc/rc.local)
 then repeats 
[603.234435] bcm43xx: Error: microcode "bcm43xx_microcode5.fw" not available or failed to load

the number increases but nothing else happens.... whats going on?

---

### Post by ewr2san on 2007-12-16
Try burning a clean new CD (not dvd). Boot into the test menu's and run through them.  Let the memory test run for at least 2-3 hours.

---

### Post by feenicks on 2007-12-19
See my thread here, just resolved last night.

[http://ubuntuforums.org/showthread.php?t=642702](http://ubuntuforums.org/showthread.php?t=642702)

I think the error message that repeats during boot has to do with the CPU changing voltage, disabling Cool n Quiet in the BIOS on mine stopped it.  It retrospect I might not have needed to do that, since the part you really need is the GRUB which pops up before the Ubuntu load screen.  You might not need to do that.  I think your problem is the video card drivers.  Get to the root prompt, type dpkg-reconfigure xserver-xorg and accept the defaults.  Make sure the driver selected is "vesa."  It should then start into the GUI.

If you can see the load screen then I think your install DVD might be okay.  I burned mine to CD not DVD so that might be something to consider.  On the other hand, I slid in a Lite-On DVD writer Monday and it was picked up right away, no fuss.

---

