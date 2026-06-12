---
title: "MSI VX600 xorg issue with 9.10 (informational)"
date: 2009-12-02
forum: Hardware
---

### Post by chrisubuntu on 2009-12-02
This might prove interesting.. perhaps not. 
Apologies for the lack of detail... it's supposed to provide basic info.

Laptop: MSI VX600
Intel Core2Duo T6500 2.1Ghz Processor 
ATi Mobility Radeon HD3410 512MB
SIS 672 DX+SIS968 Chipset 

Issue:

I booted with the latest 9.10 live cd... no problems noted.
So, i chose to 'install' and expected everything to run like the live cd.

After successfull completion of the install, I rebooted and found the X wouldn't start!  I got a shaky login prompt for about 30 seconds (as it desperately tried to startx) and then the login prompt. Xorg.log complained of 'No Screens Found'


Anyway, I plugged in my ethernet, logged in, ran a 

`sudo apt-get dist-upgrade`  

and after rebooting my X started. 

And, for what it's worth, the VX600 is working great! no problems encountered at all.




so, yeah, not a particularly interesting thread... but perhaps someone might encounter the same problem with their vx600 and wonder why the X component failed. Might save a few minute/hours of xorg.conf troubleshooting.

---

