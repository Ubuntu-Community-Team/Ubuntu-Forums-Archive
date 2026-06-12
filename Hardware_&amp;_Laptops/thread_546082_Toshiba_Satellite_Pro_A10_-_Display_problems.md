---
title: "Toshiba Satellite Pro A10 - Display problems"
date: 2007-09-08
forum: Hardware &amp; Laptops
---

### Post by Top Gear on 2007-09-08
Hi Geeks,

I am a new ubuntu user. After installing ubuntu 7.04, I found that the display resolution is very bad. Also the video resolution is terrible, I play the same video clips in MS Windows with the media player with a much better resolution, especially in full screen.

When I read all the threads related to the display issues and followed most of the solutions mentioned, nothing worked for me.

I have a Toshiba Satellite Pro A10. I have an integrated 855GM Intel card.

Here is my xorg.conf file reading; the display section.

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Could anyone give me a SIMPLE solution that I can use, or at least a detailed one, so a newbie like me could understand?

Thanks in advance.

---

### Post by El Rogueo on 2007-09-08
> **Top Gear said:**
> 

Could anyone give me a SIMPLE solution that I can use, or at least a detailed one, so a newbie like me could understand?

Thanks in advance.

I'm not sure if I read it correctly, but it looks like you're still using the default video drivers. Have you tried updating them, or looking to see if there's a Restricted Driver you can use to match your hardware?

Those are the two quick-fixes that usually work for me. And what kind of resolution quality are you expecting exactly?

Also, which solutions have you already tried?

---

### Post by Top Gear on 2007-09-09
Thanks for your reply.

I believe I am using the wrong drivers as you said.

I don't have any restricted devices, I once had the WLAN card, but now it's working fine.

I have downloaded the Intel drivers. Also the 915resolution, and activated it.
I have tried the sudo dpkg-reconfigure -phigh xserver-xorg and used the i810 & Intel & vesa, nothing seems to work.

The only thing happened that now I have a new resolution in the xerver-xorg (1280x1280), but when I choose it, the system restarts automatically (as if I use CTRL + ALT + Bk Sp), but when I check the settings again, it reads 1024x768.

The video still plays with a terrible resolution.

Thanks in advance.

---

### Post by El Rogueo on 2007-09-09
> **Top Gear said:**
> 
I have downloaded the Intel drivers. Also the 915resolution, and activated it.
I have tried the sudo dpkg-reconfigure -phigh xserver-xorg and used the i810 & Intel & vesa, nothing seems to work.


Which drivers from Intel did you install? (assuming there's more than one package, I haven't tried myself...) Just by guessing from the numbers I see (915, i810) I would guess that you've still got the wrong drivers, especially when juxtaposed with your xorg.conf, which says i810. Are you sure there's not a specific driver for your graphics card?

[http://intellinuxgraphics.org/documentation.html](http://intellinuxgraphics.org/documentation.html)

According to that, there should just be a driver called "855GM" specific to your integrated device. I'll keep looking and see if there's a download, in case you haven't tried it yet.

Also, if you're willing to get your hands dirty, there's a mildly more complex alternative that appears to work

[http://absolutebeginner.wordpress.com/2006/07/26/installing-intel-815852855-graphics-controller-drivers-on-ubuntu-debian/](http://absolutebeginner.wordpress.com/2006/07/26/installing-intel-815852855-graphics-controller-drivers-on-ubuntu-debian/)

The link to the driver package you want is there in the guide, but you'll need to follow the instructions to use it.

If you know how to open the terminal and how navigate the linux file system, then the guide is newbie-enough for your needs ;)

Hope that helps.

---

