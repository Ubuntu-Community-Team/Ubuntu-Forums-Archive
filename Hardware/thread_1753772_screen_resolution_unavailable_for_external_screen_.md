---
title: "screen resolution unavailable for external screen on natty"
date: 2011-05-09
forum: Hardware
---

### Post by gidonmiller on 2011-05-09
Hi,
I have an MSI PR601 laptop with an external toshiba TV connected via VGA cable. I upgraded from 10.10 to 11.04 about a week ago and everything is fine except that the screen resolution I had before the upgrade is unavailable. I used to work in 1360x768 and now I can only select 1024x768. this is very annoying since the TV is my main display. 
xrandr does not display the required resolution. here is the output:

```
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
LVDS1 connected (normal left inverted right x axis y axis)
   1280x800       60.0 +
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  

```

I tried to increase the resolution with xrandr using the following commands:
```
sudo cvt 1360 768  60
sudo xrandr --newmode  "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync
sudo xrandr --addmode VGA1 1360x768_60.00
sudo xrandr --output VGA1 --mode 1360x768_60.00
```

but the screen output was cut off so the mouse could move over the whole tv but there was an image only for about 3/4 of it and the rest was black.

I then tried to boot from a live cd to see if a fresh install would fix this but the same resolution appeared.

my graphics card info:
```
[~]# lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03)

```

I have no idea what to do and am very close to going back to 10.10 but I'd like to stay with natty and unity if possible.
any help would be very much appreciated,
Gidon

---

### Post by gidonmiller on 2011-05-10
struggled with this a bit more today. I ran ddcprobe and got:

```
vbe: VESA 3.0 detected.
oem: Intel(r)GM965/PM965/GL960 Graphics Chip Accelerated VGA BIOS
vendor: Intel Corporation
product: Intel(r)GM965/PM965/GL960 Graphics Controller Hardware Version 0.0
memory: 7616kb
mode: 1280x1024x256
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 1024x768x256
mode: 1024x768x64k
mode: 1024x768x16m
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 640x480x256
mode: 800x600x256
mode: 640x480x64k
edid: 
edidfail

```

I also thought I'd create an xorg.conf file (according to [http://www.grenage.com/xorg.html](http://www.grenage.com/xorg.html)) but was unsure how to do this for more than one display (its a laptop connected to a TV). I've started downloading the live cd for 10.10 to see if the ddcprobe will also fail reading the edid. 

can someone help with the xorg.conf or with anything else. please, this is driving me crazy.

---

### Post by r2ramos on 2011-05-10
I have the same problem. I have a Toshiba notebook connected to a LG LCD TV. It was working just fine before the natty upgrade. Someone please help.

---

### Post by raghavendrab on 2011-05-10
i am getting a max resolution of 1024x768. I am using natty distribution

[I]DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
[/I]

when i run ddcprobe, i get the following o/p

[I]vbe: VESA 3.0 detected.
oem: Intel(r)Q965/Q963/G965 Graphics Chip Accelerated VGA BIOS
vendor: Intel Corporation
product: Intel(r)Q965/Q963/G965 Graphics Controller Hardware Version 0.0
memory: 7616kb
mode: 1280x1024x256
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 1024x768x256
mode: 1024x768x64k
mode: 1024x768x16m
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 640x480x256
mode: 800x600x256
mode: 640x480x64k
edid: &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;"&#65533;&#65533;U&#65533;YH&#65533;$PT&#65533;&#65533;
edid: 1 3
id: ffff
eisa: ___ffff
serial: ffffffff
manufacture: 24 2005
input: sync on green, analog signal.
screensize: 34 27
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
dtiming: 1280x1024@70
monitorserial: 52301321PY01
monitorname: AL1716
[/I]

Looks like it is a valid EDID (v1.3). However, I get other EDID related errors.

[I][  254.908270] i915 0000:00:02.0: VGA-1: EDID block 0 invalid.
[  288.215359] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 158
[  288.215365] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[  288.264978] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 158
[  288.264981] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[  288.314574] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 158
[  288.314577] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[  288.364163] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 158
[  288.364166] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[  288.364191] i915 0000:00:02.0: VGA-1: EDID block 0 invalid.
[/I]

---

### Post by Grenage on 2011-05-11
> **gidonmiller said:**
> I have no idea what to do and am very close to going back to 10.10 but I'd like to stay with natty and unity if possible.
any help would be very much appreciated,
Gidon

Howdy,

My experience of secondary laptop displays in non-existent, but I'll help if I can; are you after a cloned/mirrored output to the external monitor?

---

### Post by gidonmiller on 2011-05-11
hi,
thanks for the help.
I have an old laptop that I connect to my TV and almost never use the laptops screen. in the monitor preferences of ubuntu I disable the laptop monitor and the external VGA screen is enabled. on the rare occasion that I want to use the laptop not through the TV I will enable the laptop screen and disable the TV (since the max resolution is not the same I dont want to mirror the output).
how can this be done?

---

### Post by Grenage on 2011-05-11
> **gidonmiller said:**
> hi,
thanks for the help.
I have an old laptop that I connect to my TV and almost never use the laptops screen. in the monitor preferences of ubuntu I disable the laptop monitor and the external VGA screen is enabled. on the rare occasion that I want to use the laptop not through the TV I will enable the laptop screen and disable the TV (since the max resolution is not the same I dont want to mirror the output).
how can this be done?

xrandr is far my dynamic than a static x config file, but hopefully if we have the basics in one, then xrandr can do the rest:

```
Section "Monitor"
	Identifier "Monitor0"
	Option "DPMS"
EndSection

Section "Monitor"
	Identifier "Monitor1"
	Modeline "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync
	Option "DPMS"
EndSection

Section "Device"
	Identifier "Device0"
	Driver "intel"
	BusID "PCI:00:02.0"
	VendorName "Intel GM965"
EndSection

Section "Device"
	Identifier "Device1"
	Driver "intel"
	BusID "PCI:00:02.0"
	VendorName "Intel GM965"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1024x768"
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device "Device1"
	Monitor "Monitor1"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1360x768"
	EndSubSection
EndSection
```

Obviously I don't know the frequency range for the TV, but with a specific resolution, it shouldn't matter as long as a modeline exists.  The rest of the information is sparse, but hopefully sufficient to help xrandr along; ideally it will give you the option of 1360x768 on the external, and 1024x768 on the internal.

The whole config can be done in an x config (I've not done it, but it can), but xrandr is a far more desirable option.

---

### Post by gidonmiller on 2011-05-12
Grenage, thanks for the help. I will try this file when I get home. just to make sure I get the idea - Xorg will take the modeline into account but still try to autodetect other settings so the fact that the info in the file is not definitive should not be a problem. is that right?

---

### Post by Grenage on 2011-05-12
That's right; we could fill in even more information but it shouldn't be required.  The modes 1360x768 and 1024x768 are listed in the screen sections, they could be expanded upon to allow for further resolutions (right down to 640x480).  I never bother putting more than the native resolutions in, since most screens are TFT.

---

### Post by gidonmiller on 2011-05-12
grenage, I tried the xorg.conf you supplied but X wouldnt come up (all I see is the startup services outputs. I erased the xorg.conf. I saw this in xorg.0.log.old:

```
Backtrace:
[    74.622] 0: /usr/bin/X (xorg_backtrace+0x26) [0x4a2626]
[    74.622] 1: /usr/bin/X (0x400000+0x6219a) [0x46219a]
[    74.622] 2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f4449cce000+0xfc60) [0x7f4449cddc60]
[    74.622] 3: /usr/lib/xorg/modules/extensions/librecord.so (0x7f4447683000+0x2920) [0x7f4447685920]
[    74.622] 4: /usr/bin/X (_CallCallbacks+0x34) [0x432af4]
[    74.622] 5: /usr/bin/X (WriteToClient+0x21a) [0x461c9a]
[    74.622] 6: /usr/lib/xorg/modules/extensions/libdri2.so (ProcDRI2WaitMSCReply+0x52) [0x7f444706ad82]
[    74.623] 7: /usr/lib/xorg/modules/extensions/libdri2.so (DRI2WaitMSCComplete+0x59) [0x7f4447069479]
[    74.623] 8: /usr/lib/xorg/modules/drivers/intel_drv.so (0x7f4446e16000+0x25030) [0x7f4446e3b030]
[    74.623] 9: /lib/x86_64-linux-gnu/libdrm.so.2 (drmHandleEvent+0x108) [0x7f4447274478]
[    74.623] 10: /usr/bin/X (WakeupHandler+0x4b) [0x4322fb]
[    74.623] 11: /usr/bin/X (WaitForSomething+0x1b6) [0x45c786]
[    74.623] 12: /usr/bin/X (0x400000+0x2e032) [0x42e032]
[    74.623] 13: /usr/bin/X (0x400000+0x21a7e) [0x421a7e]
[    74.623] 14: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xff) [0x7f4448c17eff]
[    74.623] 15: /usr/bin/X (0x400000+0x21629) [0x421629]
[    74.623] Segmentation fault at address 0x7f4435878010
[    74.623] 
Caught signal 11 (Segmentation fault). Server aborting
[    74.623] 

```

any ideas? any other info I should supply?
thanks

---

### Post by Grenage on 2011-05-12
It's quite possible that I screwed up with the Bus IDs, they look to match fine, but try commenting them out?  It's also possible that the monitor config for two screens isn't as it should be, so I'll try and refer to one of my dual-screen machines.

---

### Post by gidonmiller on 2011-05-12
well, an improvement. I commented out the bus IDs and X comes up but with no 1360x768 option available. I see the following in Xorg.0.log:

```
[    26.679] (==) No Layout section.  Using the first Screen section.
[    26.679] (**) |-->Screen "Screen0" (0)
[    26.679] (**) |   |-->Monitor "Monitor0"
[    26.680] (**) |   |-->Device "Device0"
[    26.680] (==) Automatically adding devices
[    26.680] (==) Automatically enabling devices

```

and this:

```
[    26.742] (II) intel(0): EDID for output VGA1
[    26.742] (II) intel(0): Printing probed modes for output VGA1
[    26.742] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    26.742] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    26.742] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    26.742] (II) intel(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz)
[    26.742] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 489 492 525 -hsync -vsync (31.5 kHz)
[    26.742] (II) intel(0): Output LVDS1 connected
[    26.742] (II) intel(0): Output VGA1 connected
[    26.742] (II) intel(0): Using user preference for initial modes
[    26.742] (II) intel(0): Output LVDS1 using initial mode 1024x768
[    26.742] (II) intel(0): Output VGA1 using initial mode 1024x768
```

does that help?

---

### Post by Grenage on 2011-05-12
Try swapping the two modes (resolutions) in screen0 and screen1, then move the modeline in monitor1 to monitor0.  If that doesn't work, I'll read up and see if there's a way to specif output based on port name - there must be.

---

### Post by gidonmiller on 2011-05-12
tried it. didnt work :(

---

### Post by Grenage on 2011-05-12
Ok dokes, I'll have a read and see if we can specify output by port.

---

### Post by gidonmiller on 2011-05-12
thanks for all the help. its very much appreciated.

---

### Post by Grenage on 2011-05-12
```
Section "Device"
        Identifier      "Intel GM965"
        Driver          "intel"
        BusID           "PCI:0:2:0"
        Option          "monitor-VGA"  "VGA"
        Option          "monitor-TV"   "TV"
        Option          "monitor-LVCD" "LVCD"
EndSection

Section "Monitor"
        Identifier      "VGA"
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "LVCD"
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "TV"
        Option  "Ignore" "true"
EndSection

Section "Screen"
       Identifier	 "Default Screen"
       Device "Intel GM965"
       Monitor "Generic Monitor"
       DefaultDepth 24
   
       SubSection "Display"
           Depth		24
           Modes		"1360x768" "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
           Virtual 2048 2048
       EndSubSection
EndSection
```
Could you try this (ideally with the TV connected and on), then post the results of:

```
xrandr -q
```

I've tried again with the Bus ID, it may or may not work.  This is pretty unfamiliar territory for me, so I'll bumble along until someone more familiar with this comes along.

---

### Post by gidonmiller on 2011-05-13
I tried it but got the same results (X goes up but with the standard resolutions). heres the xrandr output:
```
[~]# sudo xrandr -q
[sudo] password for gidon: 
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
LVDS1 connected (normal left inverted right x axis y axis)
   1280x800       60.0 +
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  

```

---

### Post by Grenage on 2011-05-13
With the xorg.conf (one before last, where you removed Bus IDs), were you then able to specify resolutions using xrandr?  I'm having another look to see if I can find some decent information on port specification in xorg.conf, but there doesn't appear to be much.

---

### Post by Grenage on 2011-05-13
Looking at another thread, this may help:

```
Section "Device"
        Identifier "Intel GM965"
        Driver     "intel"
	Option     "monitor-VGA"  "External VGA"
	Option     "monitor-LVDS" "Builtin LCD"
EndSection

Section "Monitor"
     Identifier "Builtin LCD"
     Option "Below" "External VGA"
EndSection

Section "Monitor"
     Identifier "External VGA"
     HorizSync 47.72
     VertRefresh 89.80
Modeline "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync
     Option "Above" "Builtin LCD"
EndSection

Section "Screen"
        Identifier "Screen Dual"
        Device "Intel GM965"
	SubSection "Display"
                Virtual 2384 2048
	EndSubSection
EndSection
```

I don't know if the lack of horizontal and vertical frequencies is screwing with the modeline, so I've manually added the frequencies that should be used at 1360x768.

I'd try and replicate your setup, but I don't have a VGA TV.

---

### Post by gidonmiller on 2011-05-13
just tried doing:
```
sudo xrandr --newmode  "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync
sudo xrandr --addmode VGA1 1360x768_60.00
sudo xrandr --output VGA1 --mode 1360x768_60.00
```
I did with the xorg.conf you specified but got the same results as before. the panel at the top stretches to the full 1360 and the mouse can move over the whole 1360 but the right quarter of the screen is black and any window moved there is not visible. if this could be made persistent then maybe if it happened from boot or login it would not have this problem?

---

### Post by Grenage on 2011-05-13
> **gidonmiller said:**
> just tried doing:
```
sudo xrandr --newmode  "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync
sudo xrandr --addmode VGA1 1360x768_60.00
sudo xrandr --output VGA1 --mode 1360x768_60.00
```
I did with the xorg.conf you specified but got the same results as before. the panel at the top stretches to the full 1360 and the mouse can move over the whole 1360 but the right quarter of the screen is black and any window moved there is not visible. if this could be made persistent then maybe if it happened from boot or login it would not have this problem?

I've not seen it personally, but the black area could be a problem with the virtual display not encompassing enough of the screen.

Adding the two monitors together would result in a width of 2384; I have a suspicion that the max size is 2048.

Edit:  Yes, it apparently is, for the 945GM card but you can overlap it:
> 
If the Virtual size is only 2048 wide the above command will fail as the combined width of the two displays exceeds the maximum virtual size. However it is possible to have overlap the display viewports. So to fit within the 2048 limit:

$  xrandr --output VGA --mode 1024x768 --pos 0x0 --output VGA  --mode 1600x1200 --pos 448x0


Let's 'try' it with a bigger virtual, I've made the change in the xorg I posted 10 minutes ago.

---

### Post by gidonmiller on 2011-05-14
tried it. same result :(

---

### Post by gidonmiller on 2011-05-14
well, I gave up and went back to 10.10. thanks for all the help in any case.

---

### Post by Grenage on 2011-05-14
I'm sorry we didn't get to the bottom of it; it would have been a lot easier if I could have replicated your setup, and I was hoping that someone in the same situation would have chimed in by now.

---

