---
title: "External Monitor with Radeon Mobility U1 - Karmic"
date: 2010-02-03
forum: Hardware
---

### Post by gazer22 on 2010-02-03
Getting my external monitor connected to my Fujitsu Lifebook S2010 to work is intermittent at best.

I can only rarely get the image from my laptop to get out to the attached external monitor.

Output from lshw -c video:
```

  *-display UNCLAIMED     
       description: VGA compatible controller
       product: Radeon Mobility U1
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-2.0 pm bus_master cap_list
       configuration: latency=66 mingnt=8
       resources: memory:e0000000-e7ffffff(prefetchable) ioport:2000(size=256) memory:d8100000-d810ffff memory:d8120000-d813ffff(prefetchable)

```

Output from xrandr:
```

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 2048 x 768
VGA-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 470mm x 300mm
   1024x768       75.0*    70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     59.9  
   720x400        70.1  
LVDS connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0*+   60.0  
   800x600        60.3     59.9  
   640x480        59.9     59.4  
S-video disconnected (normal left inverted right x axis y axis)

```

I currently have the external monitor configured to "mirror" in display preferences - see attached screen shot (I'd like to not have it mirror later, but it has to work first):
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=145862&d=1265220036[/IMG]

*Sometimes*, I can get an image to appear on the external monitor through a series of Fn-F10 (the monitor key on this computer), but it's maybe a 10% chance that it will work.

Any thoughts?  Thanks.

---

### Post by gazer22 on 2010-02-03
Further information after some troubleshooting:

*If I have the external monitor plugged at boot-time, things work a little better.*  This was the case for my following trouble shooting:

It looks like Fn+F10 (my display hot-key on this laptop) is cycling through 5 settings.  Only one of them really makes any sense.

I did make some modifications to /etc/X11/xorg.conf to increase the virtual screen size and add some specifications of the attached monitor.  (See below).

Here are the different modes I've seen, and thoughts on why most of them are goofy (for reference, the laptop is 1024x768 and the external screen is set to be 1280x1024):
[LIST=1]
[*]LCD on / EXT off : virtual desktop is 2304x1024, so cursor can go off into neverland from the top and right of the laptop's screen
[*]LCD on / EXT off : virtual desktop is 1024x1024, so cursor can go off into neverland from the top of the laptop's screen
[*]LCD off / EXT on : virtual desktop is 2304x1024, so cursor can go off into neverland from the left of the external screen.  Most windows don't show on the external screen until they are moved there (but some do show up).
[*]LCD on / EXT sometimes on : virtual desktop is 2304x1024.  When EXT is on, it's still just a mirror of the LCD, but the cursor can go off into neverland to the right and top of the LCD screen.
[*]LCD on / EXT on : virtual desktop is 1024x768.  This is a true mirror of the LCD screen on the external monitor.
[/LIST]

Only #5 is really doing what I would expect.
#4 would be great if the external screen really were to the right of the laptop's screen.

**Anyone have any ideas?**  I'd particularly like to get the external screen to be to the right of the laptop's screen.


xorg.conf:
```

Section "Monitor"
	Identifier "vx2255wmb - test"
	Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
	Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
	Modeline "1024x768_70.00"   75.25  1024 1080 1184 1344  768 771 775 802 -hsync +vsync
	Modeline "800x600_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync
	Option "PreferredMode" "1280x1024_60.00"
	HorizSync	30-82
	VertRefresh	50-85
	DisplaySize	474 296
EndSection


Section "Screen"
	Identifier	"Configured Screen Device"
	Device	"Configured Video Device"
	SubSection "Display"
		Virtual	2304 1024
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection



```

---

