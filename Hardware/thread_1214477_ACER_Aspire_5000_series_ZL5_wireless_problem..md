---
title: "ACER Aspire 5000 series ZL5 wireless problem."
date: 2009-07-16
forum: Hardware
---

### Post by aireek on 2009-07-16
Hey everyone.  Im generally new to Linux and Im assuming these questions are annoying to most but i've been searching for a solution and havent come across something I can manage.

I have an Acer Aspire 5000 series laptop in which i partitioned a working Ubuntu 8.04 Hardy Heron.  

My laptop has a button to activate the wifi card (Broadcom Corp BCM4318 AirForce One 54g 802.11 Wirless Lan Controller)

The card is recognized in Ubuntu through the hardware testing in /System but i cant get the wireless working.  I have been reading about this issue with Acer laptops but I can not find a solution.

Any help would be appreciated.  Could someone please contact me via email or pm on this board or if necessary, send me to a post that actually has working links (ex. downloading certain software that never seems to be online when i attempt to download)

Thank you so much in advance.

My email is: aireek @ gmail.com

Cheers.

---

### Post by brianmc on 2009-12-27
> **aireek said:**
> 
I have an Acer Aspire 5000 series laptop in which i partitioned a working Ubuntu 8.04 Hardy Heron.  

My laptop has a button to activate the wifi card (Broadcom Corp BCM4318 AirForce One 54g 802.11 Wirless Lan Controller)

The card is recognized in Ubuntu through the hardware testing in /System but i cant get the wireless working.  I have been reading about this issue with Acer laptops but I can not find a solution.


Running from an Ubuntu 9.10 Live CD this hardware will be detected and a driver can be installed. Without digging into the technical details the following items need dealt with for this machine.

Install clean 9.10.
While not connected to the net, enable all desired repositories
The "detected hardware" will come up and offer to install/activate the Broadcomm driver.
Make a network connection either by hard-wiring, or a supported USB WiFi adaptor.
Now click to install/enable the Broadcomm driver.
It downloads, installs, and WiFi may be switched on or off with the machine's WiFi button.

Additional gotcha with this machine is the SiS graphics. You may need to edit /etc/modules and append a line for "sisfb".

$ gksudo gedit /etc/modules

Add a line with "sisfb" (no quotes) to the end of the file. Save, reboot.

This should be done before installing all updates since the live CD. Such an update can break X and a recovery boot would be required to hand-edit /etc/modules.

All other hardware on the machine appears supported; managed to get a 1Gb model happily up and running with Medibuntu additions, Flash, Adobe AIR, and the BBC's Desktop iPlayer. :P

---

