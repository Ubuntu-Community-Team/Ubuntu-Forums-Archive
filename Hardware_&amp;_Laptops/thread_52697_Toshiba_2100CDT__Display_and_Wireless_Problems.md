---
title: "Toshiba 2100CDT / Display and Wireless Problems"
date: 2005-07-28
forum: Hardware &amp; Laptops
---

### Post by wjp.reg on 2005-07-28
Hi There;

I have a Toshiba laptop 2100CDT ( 400 MHz AMD-K6-2, 192 MB RAM, 2MB S3 (VESA) video card, 12" TFT Display, 4GB HDD ) purchased in 2000 which has been running Win98SE flawlessly for more than 5 years now.

As part of my home network and for roaming I have been using a DWL-650 wireless PC Card, which has been very reliable and compatable with my Linksys wireless router (801.b) which serves as DHCP and DSL connection.  I have two AMD linux / Win desktops as well with ethernet connections.

For some strange reason I can't leave well enough alone, so I have been trying to load various flavours of linux on my laptop (SuSE, Simply Mepis, Damn Small Linux, and  Ubuntu), and have run into a few dark alleys when it comes to hardware recognition and configuration.

Of most interest is my experience with Ubuntu, the reason I am posting here today!

I started with "Warty" and had very favourable results except for freezing during discovery of my PCMCIA ports and configuration of the DWL-650 wireless card, at which point the system would freeze.  As I also have a Linksys 10/100 PC Card, I was experimenting with the installation and setup with that card instead so I would have access to the internet (P.S. couldn't recognize my internal modem either)

As it happens, at one point I forgot to remove the Linksys PC Card and simply inserted the DWL-650 in the second port and all of a sudden the system was able to complete the install, fully recognizing and configuring my wireless card and connecting to the internet (No fiddling, no ndiswrapper-thing-a-ma-jig)!

Was I ever pleased!  So obviously I took it to the next step and shut down, removed the ethernet PC Card and rebooted - NIX!  Same old, same old!!!!

After several more trials I had resigned myself to the fact that if I wanted to use my wireless card I also had to leave my ethernet card. with pigtail attached, in order for Ubuntu to boot properly.

I figured then that I might as well reinstall with "Hoary", 'cause it's newer and most likely even more robust as far as the hardware detection and config is concerned, right?  WRONG!!

Problem was nothing had improved as far as my wireless card being detected "out of the box" and without also having my ethernet card attached, and now I lost my default 800x600 display and no way I could manually reconfigure it even though my xorg.conf listed 640x480 and 800x600 correctly.  It would simply come up at 640x480 with no option to change it (from the screen resolution preferences).

So back I went to reinstall "Warty";then upgrade to "Hoary" which has allowed me to get my 800x600 screen res and all the laptop power features, while I am stuck with having to keep my ethernet card plugged in if I want to have my wireless card functional.  Strange Huh?

Anybody hear of this before?  Any suggestions for how I might fix it so that I can pull the ethernet card and have the system boot and use my wireless card?

I apologize for the length of my post but thought some might find it interesting, if for no other reason than it presents another way to possibly get your wireless card running  ](*,)

Cheers,

P.S. Love Ubuntu and this forum!!

---

