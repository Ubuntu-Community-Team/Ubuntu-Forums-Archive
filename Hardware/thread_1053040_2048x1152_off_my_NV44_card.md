---
title: "2048x1152 off my NV44 card?"
date: 2009-01-28
forum: Hardware
---

### Post by bazzer on 2009-01-28
Having major issues getting my monitor working in it's native resolution of 2048x1152. It's an nvidia card, can anyone help?

The maximum I can get it working at is 1680x1050...

---

### Post by number nine on 2009-03-11
Have you tried manually adding a modeline to your xorg.conf? I calculated it would be:

```
# 2048x1152 @ 60.00 Hz Reduced Blank (CVT)
#   field rate 59.91 Hz; hsync: 70.99 kHz; pclk: 156.75 MHz
Modeline "2048x1152_60.00_rb"  156.75  2048 2096 2128 2208  1152 1155 1160 1185  +HSync -Vsync

```

I'm looking to purchase a Samsung SyncMaster 2343BW that has the same resolution and the above modeline is within the specs of that monitor.

According to all specs I've seen, 2048x1152 should work with my GMA 950, so it should certainly work for your NV44.

---

### Post by bazzer on 2009-03-12
Well, I have it working off the vga out, but the dvi out wouldn't play ball. I was waiting until the next version of the nvidia driver came out to try it again.

---

### Post by bazzer on 2009-03-13
Actually, just found this, which suggests that DVI resolutions this larde require dual-link dvi, which my cheapo card will not do.
[http://www.nvnews.net/vbulletin/showthread.php?t=125495 ]("http://www.nvnews.net/vbulletin/showthread.php?t=125495")

---

### Post by gunnar123 on 2009-06-16
I was able to set up dual display with my quite old HP zt3110EA laptop (1200x800 LCD of the HP zt3000 series, similar to a Compaq X1000) and a new Samsung Syncmaster 2343BW (2048x1152) side by side.
I run Jaunty Ubuntu 9.04. This laptop uses ATI Radeon video hardware and the 'radeon' driver in Ubuntu.

By default the video driver does not offer the 2048x1152 resolution but I found by using the xrandr command it is possible to define a new mode and have it take effect so that the ordinary Display control panel can use it !  

I verified the modeline value I used corresponds exactly to Samsung recommended values.

No need for complex xorg.conf settings.

Here we go!  Using 'xrandr' we define the new 2048x1152 resolution setting for the 2343BW. It is set up using manufacturer recommended timings. I verified this is exactly the same timings as I get using "powerstrip" on Windows XP (which queries the monitor and generates a custom .inf for it) :

xrandr --newmode "2048x1152"  156.80 2048 2096 2128 2208 1152 1155 1160 1185 -hsync +vsync

The values above follow 'modeline' conventions, e.g same as used in xorg.conf settings.

156.8 means the video clock frequency in MHz
Horizontal:
2048 is the Active Width
2096 sets the Front Porch as 48 pixels ( 2096-2048 )
2128 sets the Sync Width as 32 pixels ( 2128-2096 )
2208 (total pixels) sets the Back Porch as 80 pixels ( 2208-2128 )
Vertical:
1152 is the Active Height
1155 sets the Front Porch as 3 lines ( 1155-1152 )
1160 sets the Sync Width as 5 lines ( 1160-1155 )
1185 (total lines) sets the Back Porch as 25 lines ( 1185-1160 )

Once you have set this it becomes available in the system as a valid setting for the zt3000 video driver
and setting up dual head can then be accomplished via the ordinary "System->Settings->Display" panel.

You can now test your new mode by using an xrandr command:
xrandr --output VGA-0 --mode 2048x1152

(VGA-0 is the VGA port on the zt3000).

You should now have a 2048x1152 resolution set on your external monitor !
I spent a whole night in fruitless xorg.conf attempts until I found this out.

You get a list of all the xrandr options by the command
xrandr --help

xrandr without arguments lists your monitor setup.


For reference; between the lines below is my /etc/X11/xorg.conf file.   As you see nothing fancy, the major setup occurs without consulting this file. I don't think the 2343BW entry I have in there becomes used at all, so it can be removed.

The important line is the "Virtual" screen setting:
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	3328 1152
	EndSubSection
EndSection

where 3328 is the sum of the widths of the two screens in a side by side setup, in my case 1200+2048 = 2228
and 1152 is the height of the highest screen = (that of the 2343BW in my case):

#--------------------------------------------------------
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Monitor"
	Identifier	"Samsung SyncMaster 2343BW"
	Modeline "2048x1152_60.00_rb" 156.75 2048 2096 2128 2208 1152 1155 1160 1185 +HSync -Vsync
	# 2048x1152 @ 60.00 Hz Reduced Blank (CVT)
	# field rate 59.91 Hz; hsync: 70.99 kHz; pclk: 156.75 MHz
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	3328 1152
	EndSubSection
EndSection

Section "Screen"
	Identifier	"External Monitor"
	Monitor		"Samsung SyncMaster 2343BW"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	3328 1152
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection
#-----------------------------------------------------------

Samsung recommended timing for Samsung SyncMaster 2343BW  (from the user manual):

Resolutuion   Horiz freq (kHz)  Vert freq (Hz) Pixel Clock (MHz)  Sync polarity (H/V)

 IBM, 640 x 480		31,469			59,940			25,175			-/-
VESA, 800 x 600		35,156			56,250			36,000			+/+
VESA, 800 x 600		37,879			60,317			40,000			+/+
VESA, 1024 x 768	48,363			60,004			65,000			-/-
VESA, 1280 x 800	49,702		 	59,810 			83,500			-/+
VESA, 1280 x 960	60,000 			60,000			108,000			+/+
VESA, 1280 x 1024	63,981			60,020			108,000			+/+
VESA, 1440 x 900	55,935 			59,887			106,500			-/+
VESA, 1680 x 1050	65,290 			59,954			146,250			-/+
VESA, 2048 x 1152	70,992			59,909			156,750			+/-

Here's a photo showing the dual display (laptop + 2343BW) :
[IMG]http://swedapps.com/pics/dual-display-3.22am.jpg[/IMG]

---

### Post by jorgemarmo on 2009-09-18
Hi, I need some help and I really beleive you can help me. If you could check [http://ubuntuforums.org/showthread.php?t=1269838](http://ubuntuforums.org/showthread.php?t=1269838) I will appreciate it a lot!

Thanks you.-

---

### Post by _nikola on 2009-12-05
> **gunnar123 said:**
> I was able to set up dual display with my quite old HP zt3110EA laptop (1200x800 LCD of the HP zt3000 series, similar to a Compaq X1000) and a new Samsung Syncmaster 2343BW (2048x1152) side by side.
I run Jaunty Ubuntu 9.04. This laptop uses ATI Radeon video hardware and the 'radeon' driver in Ubuntu.

By default the video driver does not offer the 2048x1152 resolution but I found by using the xrandr command it is possible to define a new mode and have it take effect so that the ordinary Display control panel can use it !  

I verified the modeline value I used corresponds exactly to Samsung recommended values.

No need for complex xorg.conf settings.

Here we go!  Using 'xrandr' we define the new 2048x1152 resolution setting for the 2343BW. It is set up using manufacturer recommended timings. I verified this is exactly the same timings as I get using "powerstrip" on Windows XP (which queries the monitor and generates a custom .inf for it) :

xrandr --newmode "2048x1152"  156.80 2048 2096 2128 2208 1152 1155 1160 1185 -hsync +vsync

The values above follow 'modeline' conventions, e.g same as used in xorg.conf settings.

156.8 means the video clock frequency in MHz
Horizontal:
2048 is the Active Width
2096 sets the Front Porch as 48 pixels ( 2096-2048 )
2128 sets the Sync Width as 32 pixels ( 2128-2096 )
2208 (total pixels) sets the Back Porch as 80 pixels ( 2208-2128 )
Vertical:
1152 is the Active Height
1155 sets the Front Porch as 3 lines ( 1155-1152 )
1160 sets the Sync Width as 5 lines ( 1160-1155 )
1185 (total lines) sets the Back Porch as 25 lines ( 1185-1160 )

Once you have set this it becomes available in the system as a valid setting for the zt3000 video driver
and setting up dual head can then be accomplished via the ordinary "System->Settings->Display" panel.

You can now test your new mode by using an xrandr command:
xrandr --output VGA-0 --mode 2048x1152

(VGA-0 is the VGA port on the zt3000).

You should now have a 2048x1152 resolution set on your external monitor !
I spent a whole night in fruitless xorg.conf attempts until I found this out.

You get a list of all the xrandr options by the command
xrandr --help

xrandr without arguments lists your monitor setup.


i have a samsung 2343NW (no dvi input) , added a new mode(as u directed 2048x1152) in xrandr and it shows up in the xrandr list of resolutions:

[COLOR=DimGray][I][SIZE=1]Screen 0: minimum 320 x 200, current 1360 x 768, maximum 1360 x 1360
DVI-0 disconnected (normal left inverted right x axis y axis)
VGA-0 connected 1360x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8* 
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
  2048x1152 (0x119)  156.8MHz
        h: width  2048 start 2096 end 2128 total 2208 skew    0 clock   71.0KHz
        v: height 1152 start 1155 end 1160 total 1185           clock   59.9Hz[/SIZE][/I][/COLOR]

 but i cant select the new mode:

"[COLOR=DimGray]*xrandr: cannot find mode 2048x1152*[/COLOR]     "

:confused:

im using Ubuntu 9.10 with ATI Radeon 4650HD Graphic card. btw ati catalyst console also doesn't show me the 2048x1152 resolution...

**[SIZE=3]please help[/SIZE]**

---

### Post by barakani on 2010-06-15
Gunnar123 ,
 just to say thanks for this excellent tutorial - it fixed problem with my Geforce 6600 le nvidia card, nvidia drivers on Lucid 10.04 and monitor 2343nw!
Now 2048x1152 resolution is working excellent!\

:guitar:

After 30 mins I just discovered that now Visual effects doesn't work - Any ide what is causing this problem?

---

