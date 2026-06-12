---
title: "ITE IT8212 IDE controller"
date: 2005-04-15
forum: Hardware &amp; Laptops
---

### Post by soulcoughy on 2005-04-15
I just installed Ubuntu about a week ago.  I have two pieces of hardware that refuse to work.

The major one is the onboard IDE/Raid controller (ITE IT8212 on a Gigabyte GA-7400N Pro2 mainboard).  I'm using it in vanilla IDE mode.  From what I gather, I need alan cox's kernel patches to get this up and working in 2.6.10.  Aparently the ITE drivers don't compile under 2.6.10.  However, the patch doesn't seem to apply cleanly to the ubuntu sources and compilation fails with an error in ide_generic.  Anyone have any useful tips?


Secondary is getting my broadcom wireless card to work with ndiswrapper.  It seems that ndiswrapper installs the drivers just fine and detects the hardware, but a survey of the wireless neighborhood reveals nothing.  I get the feeling this one is going to take me a while.

thanks!

-Brian

EDIT:  For anyone interested, i got the broadcom PCI wireless card working.  It was actually very easy.  (Model BCM4306).  For one reason or another the ndiswrapper package in the ubuntu repositories didn't work, i just downloaded and compiled the latest from the ndiswrapper webpage.  It works great now.

---

