---
title: "ATI 9200 Pro (RV280) + Widescreen 1680x1050 = Everything shifted to the right"
date: 2008-01-24
forum: Hardware &amp; Laptops
---

### Post by eredhuin on 2008-01-24
I am not sure what the problem is here. I see that numerous people have also had the same issue with seeing a 2 inch black band of text on the monitor when trying to drive it at native resolution.

I fiddled with many modelines, with ddcprobe, with other things. No luck. I did the xserver-xorg reconfigure trick. I tried using both "widescreen" checked on and off on the "Screen and Graphics Preferences" menu. I tried using Vesa, ATI and Radeon drivers. I tried using "gtf" to create modelines. 

No luck.

I can only use the monitor in 1280x1024 mode.  Maybe it's X, maybe it's my card.  OpenSolaris 11 looks the same; everything is shifted to the right. The display works fine with my PS3 and my mac.

I am running Gutsy on x86-64. I have an ATI Radeon 9200 Pro (RV280). The driver for it is "ati", btw. I can't use i915 or nv drivers. The generic "vesa" driver doesn't support 1680x1050. This is from my /var/log/Xorg.0.log file

...skipping
(II) RADEON(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #4: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEON(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 146.2 MHz   Image Size:  473 x 296 mm
(II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) RADEON(0): Ranges: V min: 56  V max: 75 Hz, H min: 31  H max: 81 kHz, PixClock max 170 MHz
(II) RADEON(0): Monitor name: VW222
(II) RADEON(0): Serial No: 7ALMQS023962
...skipping
(II) RADEON(0): Modeline "1680x1050"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
(II) RADEON(0): Modeline "1680x1050"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +hsync -vsync
(II) RADEON(0): EDID vendor "ACI", prod id 8866
(II) RADEON(0): Not using mode "1280x1024" (vrefresh out of range)
...
[B](II) RADEON(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
[/B]
...
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +hsync -vsync (65.3 kHz)
(II) RADEON(0): Modeline "1600x1200"x59.9  161.00  1600 1712 1880 2160  1200 1203 1207 1245 -hsync +vsync (74.5 kHz)
(II) RADEON(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)

The bolded line seems important, maybe, perhaps.

My monitor is an ASUS VW222. The following is out of ddcprobe. Can somebody help me understand if my card is the problem, based on this?  I would REALLY hate buying a card and still running it on 1280x1024.

matt@matt-ubuntu:~$ sudo ddcprobe
[sudo] password for matt:
vbe: VESA 2.0 detected.
oem: ATI RADEON 9200
memory: 16384kb
mode: 800x600x16
mode: 1024x768x16
mode: 320x200x32k
mode: 320x200x64k
mode: 320x200x16m
mode: 1600x1200x256
mode: 640x400x256
mode: 640x480x256
mode: 640x480x32k
mode: 640x480x64k
mode: 640x480x16m
mode: 1600x1200x32k
mode: 800x600x256
mode: 800x600x32k
mode: 800x600x64k
mode: 800x600x16m
mode: 1600x1200x64k
mode: 1024x768x256
mode: 1024x768x32k
mode: 1024x768x64k
mode: 1024x768x16m
mode: 1280x1024x256
mode: 1280x1024x32k
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 132x25 (text)
mode: 132x43 (text)
edid: 
edid: 1 3
id: 22a2
eisa: ACI22a2
serial: 01010101
manufacture: 42 2007
input: separate sync, composite sync, sync on green, analog signal.
screensize: 47 30
gamma: 2.200000
dpms: RGB, active off, suspend, standby
timing: 720x400@70 Hz (VGA 640x400, IBM)
timing: 720x400@88 Hz (XGA2)
timing: 640x480@60 Hz (VGA)
timing: 640x480@67 Hz (Mac II, Apple)
timing: 640x480@72 Hz (VESA)
timing: 640x480@75 Hz (VESA)
timing: 800x600@60 Hz (VESA)
timing: 800x600@72 Hz (VESA)
timing: 800x600@75 Hz (VESA)
timing: 832x624@75 Hz (Mac II)
timing: 1024x768@87 Hz Interlaced (8514A)
timing: 1024x768@70 Hz (VESA)
timing: 1024x768@75 Hz (VESA)
timing: 1280x1024@75 (VESA)
ctiming: 1152x864@75
ctiming: 1280x1024@60
ctiming: 1280x960@60
ctiming: 1440x1440@60
ctiming: 1600x1200@60
ctiming: 1680x1680@60
dtiming: 1680x1050@77
monitorrange: 31-81, 56-75
monitorname: VW222
monitorserial: 7ALMQS023962

from my xorg.conf

Section "Device"
	Identifier	"ATI Technologies Inc RV280 [Radeon 9200 PRO]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"VW222"
	Option		"DPMS"
	HorizSync	31-81
	VertRefresh	56-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV280 [Radeon 9200 PRO]"
	Monitor		"VW222"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1680x1050" "1280x1024" "1152x864" "1024x768"
	EndSubSection
EndSection

Any help interpreting this would be greatly appreciated.

---

### Post by eredhuin on 2008-01-28
What I think is happening is that Ubuntu wants to give me 1680x1050@77 but my monitor only supports vert refresh between 56 and 75Hz. 

So it falls back to 1280x1024@75, which works. 

But my read is that my monitor would work at 60Hz.

How do I trick X into doing this?

---

### Post by eredhuin on 2008-01-30
So here's the fix:

Attempt 11. Try video card 2, an ATI 2600HD something or other. My SFF computer's PSU couldn't keep up. Return that card to Best Buy.

Attempt 12. Try video card 3, a $60 PNY branded NVIDIA 6200. Install. Check windows. Windows works, well it bluescreens, but it works. I won't bother with nvidia drivers or games, so I don't care if DirectX9 has some weirdo corner cases.

I boot into Ubuntu. X fails. I run 
   sudo dpkg-reconfigure xserver-xorg
I give it all the information it needs. It boots up X, and it's 1680x1050 - still shifted to the right.

Attempt 13. I download the restricted drivers for Nvidia. Restart.

Magic. It works. 

Woo!

So, I still don't understand what was wrong. I tried a lot of things. If the same card works with a proprietary driver, I can live with that.

---

### Post by oldsoundguy on 2008-01-30
you have just found out what a lot of others have found out.  The generic driver for wide screen and higher intensity utilities  such as rotate do NOT work.  And the drivers from ATI and their site are very shaky at best and do not work at worst.
NVidia, on the other hand, has drivers that WORK.  And if you use Envy (a third party program) to install them, you will get ALL of the bells and whistles.  (I have three boxes of Ubuntu with 6200 cards in them and they work flawlessly!)(Oneihas a nice HP 24" cinema display the others are running LCD panels .. and I ROTATE them for web pages such as this one!)
At one time, the only cards I had were ATI .. those are now all history including two WinDOZW boxes!

---

