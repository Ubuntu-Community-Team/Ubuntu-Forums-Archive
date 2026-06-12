---
title: "Increase laptop resolution on Ubuntu 8.10"
date: 2009-03-15
forum: Hardware
---

### Post by hubb34 on 2009-03-15
Hi,all, I have an old Dell D610 and just installed a Ubuntu 8.10 on it recently. Everything works pretty good except the low resolution really bothers me. It has a ATI x300 card but the highest resolution I can get is 1024*768, which is also the highest resolution under Windows XP. I have been searching about how to increase the resolution to 1280 *1024 on the internet but most ways won't apply to my computer because no matter How I change xorg.conf file or change do the  dpkg-reconfigure xserver-xorg command, it always shows the follows in my xorg.conf file:

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

I am wondering what is going on here because unlike nobody else, there is nothing refered to other people's solutions.

Is there anybody can help me with that? Thanks ahead!

---

### Post by MyR on 2009-03-15
I think it's safe to say that's the hightest resolution that your screen supports.  No matter what settings you change, the monitor cannot physically display at a higher resolution.

peace

---

