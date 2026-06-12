---
title: "Toshiba Satellite L20-P430"
date: 2006-04-20
forum: Hardware &amp; Laptops
---

### Post by anurag_gupta on 2006-04-20
hi 2 all,

I'm a complete newbie. i installed breezy on my new laptop (mentioned in the title) there are a lot of problems.......
1.Battery in not recognised(the battery applet says no battery) altough it recognises the battery specs but not it's state.
2.MOdem isn't working.AC97 Softmodem
3.LAN isn't working.REaltek 8139 fast Ethernet
wat the hell ubuntu doin is it full of crap????????
does it has any of the drivers????????
I also has a assembled pc with which i got the motherboard cd which had the linux drivers but for Red hat n Novell. Will installing those drivers on my laptop or pc help?????????

Isn't there any guide built-in the ubuntu about the avrious commands????????
It's been a headache for me to run ubuntu for the past few weeks.
Can ne body help??????/
Any kind of help will be appreciated.
Thanx in advance.

---

### Post by varunus on 2006-04-20
1.  I'm not sure about the battery...open up a terminal, and type "cd /proc/acpi/battery", then type "ls"; do you see anything there?  if you see a folder, can you "cd" into it, and then type "cat state" into a terminal?

2.  I'm not sure about this...do you have more info about your modem?

3.  The ethernet is supported by Ubuntu.
```
filename:       /lib/modules/2.6.15-20-386/kernel/drivers/net/8139too.ko
author:         Jeff Garzik <jgarzik@pobox.com>
description:    RealTek RTL-8139 Fast Ethernet driver

```

The driver should have been loaded by default; does "System->Administration->Networking" not show you your ethernet card?  If not, type "sudo modprobe 8139too" into a terminal, then open the Networking applet; does it show up then?

---

### Post by Tom Tiger on 2006-04-21
I must admit that the L20 series (like the L10) is a bit more of a challenge to get going.  If you are a complete newbie and you are a bit swamped with all the options then there are two options, if you have allready installed Ubuntu then you are allready halfway there.  If not, try Kanotix linux.  

Today I received a L20 in for repairs (easy job just a new battery) so I had the change to try the live Ubuntu 5.10 cd.  It is hard to get that one going on a L20.  Doable but hard.  Knoppix I couldn't get to work at all (not much time to try) and only Kanotix 2005-4 started and detected everything (also a Debian Linux).  Both networkcards were detected (realtek and wifi 2200)  and both worked,  so under Ubuntu it is just a matter of modules.

Varunus, I've tried your solution (swapped out a drive to do a clean install) and it works, both ethernets wifi and rj45 on a 5.10 install. :-)

Couldn't work on the battery applet problem though.... machine had to go back...

---

### Post by anurag_gupta on 2006-04-22
hi

varunus the only thing i can tell u about my modem (in laptop) is that it's a winmodem "AC97 Softmodem" i don't know what company is it??????????

My problem is dat i'm not able to connect both my dektop n laptop together using a crossed lan cable using the ethernet card.
it is really simple in windows u just have to assign sattic ip's to both tha machines then ping the other machine n the machines are ready to share files n internet. Is it possible in ubuntu?????
As i tried to ping the other machine the machine didn't replied. I don't know wat is wrong b'coz it could  be accomplished easily in windows.

---

### Post by Tom Tiger on 2006-04-26
Yes it is possible (heck I'm doing that every day)  but you need to set up your ubuntu box with file sharing,  system, administration, shared folders.

---

### Post by lancest on 2006-04-27
have a new Toshiba Satellite L-20-*. The battery indicater seems not working.  Everthing else ok except can't change 60hz refresh. Using it now!
Anyone know Horiz/Vertical specs for this Toshiba to put in xorg.conf ? fglrx driver working. Tried to change specs but no change in refresh also. 
ATI Radeon Epxress 200m 

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Xpress 200M (RC410)"
	Driver		"fglrx"
	BusID		"PCI:1:5:0"
EndSection

Section "Monitor"
        HorizSync       30-80
	Identifier	"Generic Monitor"
	Option		"DPMS"
        VertRefresh     50-78
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Xpress 200M (RC410)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768/85"
	EndSubSection

---

