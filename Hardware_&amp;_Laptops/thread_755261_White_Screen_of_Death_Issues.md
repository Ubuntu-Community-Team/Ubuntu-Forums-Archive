---
title: "White Screen of Death Issues"
date: 2008-04-14
forum: Hardware &amp; Laptops
---

### Post by seuzy13 on 2008-04-14
I recently installed Ubuntu 7.10 on an old Sony Vaio laptop. When I first booted into Linux from GRUB, I got the white screen of death. A white fog spreads slowly across the screen starting with the bottom-left corner. Eventually, the whole screen is covered... you can see some air bubbles, etc. At first, I was afraid I had busted my laptop. I'm a total Linux newbie--raised on Windows--have little idea what I'm doing. However, I left it on for a bit, and about fifteen minutes later the Ubuntu login screen was there and ready to go.

Ubuntu runs great. Once it has booted everything is fine. However, when I boot up the computer, shut it off, switch users, or log off, I get the white screen of death to varying degrees. Switching user and logging off it doesn't even have time to spread across the whole screen.

This would not seem to be a big problem, but I don't think I should have to wait fifteen to twenty minutes every time I want to start up Linux. There is also another problem that I think is somehow related and much more irritating. I cannot put my laptop into stand by or hibernate. Most of the time, it will successfully "shut off" at least as much as it does when it goes it stand by or hibernate, but it will not come back on. For standby, I will hear the fan kick back in, and it seems as if it is starting up, but the screens stays black. Similar problem with hibernate. I fiddled with the settings for the two a little, but the obvious-looking things I tried did not help any.

I have read that this can be caused by ATI graphics cards and beryl. I have an ATI graphics card, but am not using and don't necessarily intend to use beryl. [This article]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") had a link to another [driver]("http://xorg.freedesktop.org/releases/X11R6.7.0/doc/radeon.4.html") I could use for my type of graphics card, but my specific model was not listed. I did not try this yet, because I know how finicky drivers can be, and I'm not even sure if it will help my problem.

I need someone to help explain to me in plain English some ways that I could go about fixing this. Thank you!

I am using a Sony VAIO dual-boot laptop (model# PCG-FRV27)-with Windows XP Home and Ubuntu 7.10. My graphics card is a RADEON IGP 345M with an ATI RS200M chip type. I have 512MB of RAM.

---

### Post by tvtech on 2008-04-15
this is a problem with how your hardware is being detected by X.   it may be a simple config problem with your xorg.conf file which can be found in /etc/X11/xorg.conf.  it may also be a driver related issue specific to your hardware.  i use Nvidia and have wonderful black screen issues when I try to use beryl or compiz-fusion.  all very tragic really.   on earlier releases of ubuntu 6.04-6.10  I had white screen issues especially when trying to do things like suspend and hibernate.  never have quite got that sorted ou,t but I'm buying a new computer with that tax rebate from mr. oil himself, so I guess I don't care to sort it.  on the compiz-fusion website there is a good how too on all of this somewhere in their wiki I don't remember quite where. 

[http://www.compiz-fusion.org/]("http://www.compiz-fusion.org/")

I'd suggest try playing with your video card driver and roll it back a version or two see if that clears up your problems.

---

### Post by seuzy13 on 2008-04-15
I guess I will try some different drivers and look at the xorg file. Do you (or anyone else) have some specific suggestions? Should I try the driver that I linked to previously?

I don't know what I'm looking for on the Compiz Fusion Wiki. All of it seems to be about...well...Compiz Fusion, which I'm not interested in installing.

Thank you for your help!

---

### Post by seuzy13 on 2008-04-16
I tried ATI's [provided driver]("http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html") for Linux. When I ran the script I got a syntax error. 

"$ sh ati-driver-installer-8.28.8.run"

"..."

"./ati-installer.sh: 165: Syntax error: Bad substitution"

Am I doing something wrong?

I also looked for x.org drivers. [This page]("http://xorg.freedesktop.org/releases/X11R6.7.0/doc/radeon.4.html") describes a driver I would like to try, but I don't see any links to actually *get* the driver.

As for the Xorg file, all seems to be well.

Section "Device"
	Identifier	"ATI Technologies Inc Radeon IGP 330M/340M/350M"
	Driver		"ati"
	BusID		"PCI:1:5:0"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon IGP 330M/340M/350M"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768"
	EndSubSection
EndSection

Thanks all!

---

