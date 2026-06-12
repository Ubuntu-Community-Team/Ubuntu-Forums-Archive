---
title: "Need help with 8.10 &amp; Toshiba M1 (trident video)"
date: 2009-02-03
forum: Hardware
---

### Post by cbutle3@netzero.com on 2009-02-03
Greetings!  I just installed the latest Ubuntu 8.10 on my Tecra M1 laptop, and only seem to have the option of 800 x 600 resolution.  I was wondering if someone can help, since it seems like the xorg.conf file mentioned as a fix on 8.04 is no longer used.  Below is a small clip of my /var/log/Xorg.0.log file, the "refresh out of range" errors I think have something to do with the problem, but how can I resolve this?


X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux tecra-m1 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686
Build Date: 24 October 2008  08:00:16AM
~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~
 ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~
(II) TRIDENT(0): Not using default mode "640x350" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "320x175" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "640x400" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "320x200" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "720x400" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "360x200" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "640x480" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "320x240" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "640x480" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "320x240" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "640x480" (hsync out of range)
(II) TRIDENT(0): Not using default mode "320x240" (hsync out of range)
(II) TRIDENT(0): Not using default mode "800x600" (hsync out of range)
(II) TRIDENT(0): Not using default mode "400x300" (hsync out of range)
(II) TRIDENT(0): Not using default mode "800x600" (hsync out of range)
(II) TRIDENT(0): Not using default mode "400x300" (hsync out of range)
(II) TRIDENT(0): Not using default mode "800x600" (hsync out of range)
(II) TRIDENT(0): Not using default mode "400x300" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1024x768" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "512x384" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "1024x768" (hsync out of range)
(II) TRIDENT(0): Not using default mode "512x384" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1024x768" (hsync out of range)
(II) TRIDENT(0): Not using default mode "512x384" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1024x768" (hsync out of range)
(II) TRIDENT(0): Not using default mode "512x384" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1024x768" (hsync out of range)
(II) TRIDENT(0): Not using default mode "512x384" (hsync out of range)
~ ~ ~ ~ ~ ~ ~ ~ ~
 ~ ~ ~ ~ ~ ~ ~ ~ ~
(--) TRIDENT(0): Virtual size is 800x600 (pitch 800)

Any help is greatly appreciated, I do love this laptop!

-Chris

---

### Post by kimberlite on 2009-02-04
Hello,
You may try to reconfigure xserver:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by cbutle3@netzero.com on 2009-02-04
Hi Kimberlite!

   I had actually tried that command from another post, but in 8.10 it only seems to ask one question regarding video, whether or not to use framebuffer, unless I am not using the command correctly?  Answering yes or no doesn't seem to give me the 1024x768 resolution option...

-Chris

---

### Post by overdrank on 2009-02-04
> **cbutle3@netzero.com said:**
> Hi Kimberlite!

   I had actually tried that command from another post, but in 8.10 it only seems to ask one question regarding video, whether or not to use framebuffer, unless I am not using the command correctly?  Answering yes or no doesn't seem to give me the 1024x768 resolution option...

-Chris

Hi and you may try the xfix option when booting into recovery mode. Recovery mode is usually the second choice from the grub. Then you can choose the xfix option to correct graphical issues. You then should be given the choice to boot normally. 
If xfix does not work you may look here
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by cbutle3@netzero.com on 2009-02-06
Overdrank, you are the man! Thanks for your help!  I finally got it up to 1024x768 using your instructions.  I did a "sudo gedit /etc/X11/xorg.conf" and changed the file to include the modelines provided with the gtf command.  If anyone is interested, here is the pertinent info I put in my xorg.conf file that makes *my* Toshiba Tecra M1 work:


Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1024x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
	Modeline "640x480@60"  23.86  640 656 720 800  480 481 484 497  -HSync +Vsync
	Modeline "800x600@56"  35.55  800 832 912 1024  600 601 604 620  -HSync +Vsync
	Modeline "800x600@60"  38.22  800 832 912 1024  600 601 604 622  -HSync +Vsync
	Modeline "1024x768@60"  64.11  1024 1080 1184 1344 768 769 772 795  -HSync +Vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
	Modes	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

---

### Post by paulexander on 2009-02-08
Thanks, this totally works for me too.

---

### Post by DDA92 on 2009-02-15
That worked great for me too, thanks for your help!

DDA92.

---

### Post by Altimac on 2009-02-17
I believe the issue is with the sync rate detection - and all you should need to do is add the following lines to the default xorg.conf, inside Section "Monitor":

(using cbutle3's numbers)
Horizsync 31.5-48.0
Vertrefresh 56.0-65.0

(OR the numbers from my install)
HorizSync 28-50
VertRefresh 43-75

Then CTRL+ALT+Backspace to restart X.

---

