---
title: "VIA/S3G UniChrome Pro IGP Jaunty"
date: 2009-04-26
forum: Hardware
---

### Post by kyroha on 2009-04-26
I have a Gateway MX3228 laptop with a VIA/S3G UniChrome Pro IGP video card. The problem I am having is Jaunty automatically sets the resolution to 1600x1200 or something along those lines, meaning I cannot see a good portion of the desktop. In Windows the laptop runs at 1280x768. When I try to set it to that using the GUI I end up with an unreadable screen. I used to be able to get this same laptop working fine in other versions of Ubuntu be editing xorg.conf and changing the modeline, however is appears that xorg.conf is not used anymore. Any suggestions?

---

### Post by dodle on 2009-05-09
xorg.conf is still used.  Here is mine, hopefully it can help you out.
[quote=Dodle's xorg.conf]Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection	"Display"
		Depth 	24
		Virtual	1024 768
		Modes 	"1024x768@75" "1024x768@60" "800x600@60" "640x480@60"
	EndSubSection
EndSection[/quote]

Make sure to remove any modes that aren't supported by your screen.

I also wanted to add to this thread some problems I am having with VIA Unichrome S3.  I understand that the drivers for it aren't very actively developed.  But I was wondering if anybody was able to get full fuctionality out of it.  I just upgraded to Jaunty, which I love, and am using the vesa driver which is the only one that will work for me.  I would like to be able to use compiz and get some eyecandy going.  If someone has figured out how to accomplish this, could you please post your xorg.conf.  I would really appreciate it.

**Edit: **At least I *think* xorg.conf is still used.  I had to edit it to get gdm to display correctly.

[color=blue][b]I just found some instructions here that I am going to try:
[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome).  I will let you know how it turns out.[/b][/color]

**Update:** My openchrome driver seems to be working, but I still can't use compiz.

---

### Post by DonThompson on 2009-05-21
The question becomes who (what program) configures this stuff the old conf file says is configured, how does he do it and how do we get him to do it right?

(I personalize programs because mine seem to take on a life of their own and are soon, like children, disobeying and going their own way.)

---

