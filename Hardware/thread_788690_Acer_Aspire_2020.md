---
title: "Acer Aspire 2020"
date: 2008-05-10
forum: Hardware
---

### Post by Pord on 2008-05-10
Ive got an acer aspire 2026WLMI (which is a varient of the acer aspire 2020 model) which has a ati 9700 mobility graphics card in it.
When i use gutsy it picks up the graphics card fine and I can install the restricted driver with no problems. When I try to upgrade to heron it randomly crashes. Ive tried the live cd which I never get to boot as it crashes after trying to start the xserver unless i use safe graphics mod which it then only uses VESA and when i got to use ati again it locks up.
 Ive tried the xfix which doesnt recongnise the graphics card and only loads an xorg file with no infomration in it pertaning to the type of graphics card which leads to it booting in low resolution mode with vesa. I cannot use the open source driver on heron either as it locks/crashes when xserver starts. It refuses to recongnise my graphics card. Ive also tried the ati properietry driver from the web site and using apt-get install xorg-driver-fglrx.
When i do upgrade from gutsy to heron with the fglrx driver already installed it crashes randomly with a black screen or it goes all garbled and locks up making me hard reboot.
When i upgrade from gutsy with the opensource driver it puts it into vesa mode of which I cannot get out of without it crashing everytime the xerver starts.

Does any1 know a fix for heron so i can upgrade? Else I might have to stick with gutsy
I dont have compiz running and dont want it to run so that isnt the problem

P.s. The graphics card is a ati 9700 Mobility 128Mb

---

### Post by antribeiro on 2009-04-18
This may come a little late, but for every version of xorg > 7.3 i've had the same problem (I have an aspire 2023wlmi).

This is a hardware quirk and has been resolved in the xorg package, so from 7.5 up this will be solved. For now, here's how to solve it:

Edit your /etc/X11/xorg.conf file with sudo and make sure the Device section is like this:

Section "Device"
	Identifier	"ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
	Driver		"radeon"
	BusID		"PCI:1:0:0"

#may not be necessary in a future version of xorg (>=7.5)
	Option		"AGPMode"		"1"

#improves 3d performance - check DRI wiki for Radeon 9600/9700
	Option		"EnablePageFlip"	"1"
	Option		"ColorTiling"		"1"
EndSection

Basically, the AGPMode has to be forced to 1x. With that config, all is perfect, and the open source driver is as good as the closed source ati in terms of speed, and much better in stability!

---

