---
title: "External monitor doesn't work"
date: 2010-04-14
forum: Hardware
---

### Post by borish on 2010-04-14
Hello,

I just installed Ubuntu 9.10 on a thinkpad T500. I have an external monitor connected to the digital output of the docking station, which I haven't got working with Ubuntu yet.

This is the output of xrandr:

iti27% xrandr -q
Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1680x1050      60.1 +   84.9*    74.9     69.9     60.0     50.1  
   1600x1024      60.2  
   1400x1050      85.0     74.8     70.0     60.0  
   1280x1024      85.0     75.0     60.0  
   1440x900       59.9  
   1280x960       85.0     60.0  
   1360x768       59.8  
   1152x864      100.0     85.1     85.0     75.0     75.0     70.0     60.0  
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
DP1 disconnected (normal left inverted right x axis y axis)
iti27% 

Also, if I click on "detect monitors" in system/preferences/display, only my internal laptop LCD is shown. I tried to examine the xorg.conf, but there's none in /etc/X11.

What to do?

Cheers,
Boris

---

### Post by borish on 2010-04-16
I am now able to use the external monitor after I changed some settings in the BIOS. However, I can't use the monitor's native resolution. 

The internal LCD has a resolution of 1680 x 1050, the external moitor 1920 x 1200. In System/Preferences/Display, I can select "mirror screens" and a monitor for output. If I unselect "mirror screens" and select the 1920 x 1200 resolution for my external monitor, I can't seen the gnome panels any more.

---

### Post by fsando on 2010-05-15
I don't know if you have solved your problem but here's my input. I have a t500 with ati-graphics and an external 1920x1200 as well. I've bee fighting quite a lot with this and solved it. I don't know if you have the integrated intel+ati version or only the intgrated intel.

My info may not be completely accurate because I don't dare to change things to check.
You may only need to change you xorg.conf (see below) in any case do that first.

I believe you need to set up the display in the catalyst control center. It may not be installed by default (don't recall anymore). Then the dance begins. You need to set it to "multi-display" or "big-desktop" (Not sure what will be called) then set up screens the way you like there.

Caveat:
My impression is that catalyst makes various mistakes when saving your choices depending on the sequence of choices and the current settings relative to new settings. In my case I had to change settings back and forth many times before it actually saved what I intended - restarting x each time (logout-login). As if it can only change one thing at a time and only in a specific sequence (as if one setting must be already set before the next one can be set). I was never able to make any sense of it.

After that you need to set your desktop size in xorg.conf.
You must create one big desktop, the size is the the size of the largest screen in one direction and the combined sizes in the other.

My screens are above each others which means 1920 wide and 1200+1050 high. This means that there will be an invisible area somewhere (in my case to the right of my laptop screen).

My xorg.conf
```

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
	SubSection "Display"
		Virtual	1920 2250
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"fglrx"
EndSection

```

---

