---
title: "Wireless setting up?"
date: 2009-07-29
forum: Installation &amp; Upgrades
---

### Post by CDSA on 2009-07-29
new to Ubuntu today ....

-  Have just installed Ubuntu on a laptop & have a  Belkin G+ F5D7011uk notebook card ... will this only work with Windows 2000 or XP? 
 
Do I need to get a notecard / usb supported by Linux

---

### Post by philcamlin on 2009-07-29
I solved my problem, the file bcmwl5.inf that came with the installatiobn cd from belkin worked perfectly with ndiswrapper and FC2, but looking at 

[http://home.nc.rr.com/thehinnants/stuff/drivers/](http://home.nc.rr.com/thehinnants/stuff/drivers/)  (the zip-fil)

I found that the file bcmwl5.inf differed from the previos (old/wrong)

md5sum: OLD/WRONG worked for me using FC2
b19da13eeba8333fe7f43761e9f6078d  bcmwl5.inf
52d67c5465c01913b03b7daca0cc4077  bcmwl5.sys

md5sum: The ones that worked for me using kubuntu 6.10
02e93649508d68e60c4919fda92c2273  bcmwl5.inf
ebf36d658d0da5b1ea667fa403919c26  bcmwl5.sys
 
the installation is simple and is described at
[http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)


I hope that someone that understand these issues with the wireless cards for Linux, structures the everything up, and makes it much more transparent and easy to use.

---

