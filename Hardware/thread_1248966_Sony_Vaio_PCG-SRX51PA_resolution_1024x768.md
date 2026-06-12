---
title: "Sony Vaio PCG-SRX51P/A resolution 1024x768"
date: 2009-08-24
forum: Hardware
---

### Post by papu40000 on 2009-08-24
Hi!

This is a little note about how I did work resolution 1024x768 60Hz in this laptop using Xubuntu 9.04. 

I post it because there are some people with problems with resolution in laptops and perhaps I could help someone a little bit.

With
```
sudo dpkg-reconfigure xserver-xorg
```
I get two resolutions 800x600 and 640x480 so I had to configure resolutions with xorg.conf. But the problem is with HorizSync and VertRefresh, that couldn't solve with ddcprobe

[http://www.cyberciti.biz/faq/howto-use-linux-ddcprobe-command/](http://www.cyberciti.biz/faq/howto-use-linux-ddcprobe-command/)

So I was surfing the internet and I found a xorg.conf with correct HorizSync and VertRefresh that works
(font [http://freenet-homepage.de/obauer/index.html](http://freenet-homepage.de/obauer/index.html))
```

Section "Monitor"
	Identifier   "Monitor0"
**	HorizSync    31.5 - 48.5**
**	VertRefresh  50.0 - 70.0**
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	DefaultDepth 16
	SubSection "Display"
		Viewport   0 0
		Depth    16 
		Modes	"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

```

[LIST]
[*]copy and paste this code on sections MONITOR and SCREEN to the file /etc/X11/xorg.conf with a editor:
```
sudo mousepad /etc/X11/xorg.conf
```

[*]reset x server
[/LIST]


That's all.
Sorry for my basic english.

Good luck,
papu :P

---

### Post by Aguamiga on 2009-08-26
Had the same sort of problem, and solved it by having Xubuntu 7 generate a correct Xorg.conf file! (You don't need to install version 7, just boot from the cd)
 
For more info, read this post: [http://ubuntuforums.org/showthread.php?p=7850803#post7850803](http://ubuntuforums.org/showthread.php?p=7850803#post7850803)

---

### Post by BiiPiiGii on 2009-08-27
I've been having good resolution with my GF's vaio.  However, we cannot find any additional drivers for her graphics card.  Basically she can't do that neat thing where the windows warp.  Can't figure out why.  I had to get into the xorg file however to change the resolution when I installed Ubuntu in VB.  That was a bit of a pain.

---

