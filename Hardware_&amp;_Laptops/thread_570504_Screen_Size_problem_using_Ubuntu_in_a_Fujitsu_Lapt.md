---
title: "Screen Size problem using Ubuntu in a Fujitsu Laptop"
date: 2007-10-08
forum: Hardware &amp; Laptops
---

### Post by jbeya on 2007-10-08
Hi There,


This is the first time I've installed ubuntu and it worked really well. no problems with drivers or anything except that ubuntu only allows me to use a fraction of my laptop screen.

I tried to look for any options to change the screen resolution but there is only 2 (640x480 and 800x600) and the resolution of my LCD screen is 1024x768.

I also tried looking for drivers but fujitsu only provides support for windows users.

The model of my laptop is a Fujitsu S series Lifebook S4542.

In another forum, someone said that I could use some commands in the xorg.conf but I have no idea how to access to that file.

Thanks in advance

Jose

---

### Post by hmlessalky on 2007-10-20
I have the same problem on an older (e342) Fujitsu laptop. I can't get above 640x480.

---

### Post by rookie_paul on 2007-10-21
Hello folks! I am quite a newbie, but I hope to be of some help. I had a very similar problem when I upgraded from Edgy to Feisty: the Ubuntu dekstop was about 3/4 of the screen size.
I managed to solve this problem by editing the /etc/X11/xorg.conf file (obviously, I suggest to do a backup copy of it before editing). I opened it with a text editor and looked to the lines after "Section Screen". Here I chenged DefaultDepth and the Modes in Subsections Display, then reboot and it was fixed!The Section Screen of my xorg.conf file is like this:

> Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		16
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050"
	EndSubSection
EndSection


I have a different machine and - do not forget it - I am newbie, but, in my case, it worked... ;)

---

