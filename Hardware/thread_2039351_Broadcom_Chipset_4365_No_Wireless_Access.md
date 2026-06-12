---
title: "Broadcom Chipset 4365: No Wireless Access"
date: 2012-08-08
forum: Hardware
---

### Post by Slvtmong00se on 2012-08-08
Hi everybody!

I bought a Dell Inspiron 5220 about 5 days ago and struggled for four days to get the Wireless Network to detect after upgrading to 64bit Ubuntu 12.04 LTS.

To the best of my googling abilities, there's nothing to to be done but wait for support for this broadcom chipset (4365).

So, I decided to google around and get a wireless USB dongle for now, one that runs "straight out of the box" on Ubuntu. I got a TP-Link TL-WN722N dongle. Now in Ubuntu 12.04, that doesn't work either!

lsusb lists the device, but I have no idea how to get it up and running. Network manager does not see it. Please help me out here, I desperately need wi-fi on this machine, and it has cost me a LOT of money.

---

### Post by Slvtmong00se on 2012-08-13
BUMP.


Also, update: after a lot of distro hopping, it turns out PCLinuxOS runs this wifi chip out of the box. It uses kernel 2.6.something. Upgrading the kernel in PCLOS broke driver suport for a lot of other things, so thats not a solution. 

Currently running Xubuntu 12.04 64bit does anyone have any idea how to get started running this with my kernel? Wildman? Chili? anybody?

---

### Post by Slvtmong00se on 2012-08-13
Anybody? Im really desperate so far ive downloaded ath9k_htc.fw and put it in /lib/firmware

and  compat-wireless-2012-07-03 , used driver-select ath9k_htc and successgully run make and sudo make install

in the end of all this, sudo modprobe ath9k_htc gives not output, so i think it executes fine 

But it didnt work, the green light on the Device isnt even on. 

Can anyone please help? :(

---

### Post by lincoln32 on 2012-08-13
I had one with the B43XX and had a terible time finding firmware driver package for it and cannot find it at the moment but I will look again later
I do carry a older linksys so I can upload to fix wifi issues
and have been know to swap wifi cards so that I do not have to deal with broadcom devices

open a terminal and post the results of lspci and lsusb I am not shure what chipset the usb one is and these commands will tell us:)

---

### Post by Slvtmong00se on 2012-08-19
[http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560](http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560)

The .deb package listed here worked perfectly for me, after i removed ndiswrapper and windows driver, and undid any and all solution attempts I had made before (blacklisting some drivers, etc etc)

---

