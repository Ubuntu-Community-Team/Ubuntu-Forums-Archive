---
title: "Monitor underscan with dual monitors (?) issue with fglrx driver"
date: 2015-01-12
forum: Hardware
---

### Post by mladen.adamovic@gmail.com on 2015-01-12
I'm trying to use AMD fglrx drivers with my R9 280X because standard driver. I have two different monitors attached.

```
DFP9 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 160mm x 90mm
   1360x768       60.0 +
   1920x1080      60.0*    50.0     59.9     60.1     50.0     30.0     25.0     24.0     60.0     30.0     24.0  
   1776x1000      50.0     59.9     50.0     25.0     24.0     60.0     30.0  
   1680x1050      60.0     50.0     59.9     30.0     25.0     24.0     30.0     24.0  
   1400x1050      60.0     50.0     59.9     30.0     25.0     24.0     30.0     24.0  
   1600x900       50.0     59.9     25.0     24.0     30.0  
   1280x1024      60.0     50.0     59.9     30.0     25.0     24.0     30.0     24.0  
   1440x900       50.0     59.9     25.0     24.0     30.0  
   1280x960       50.0     59.9     25.0     24.0     30.0  
   1280x768       60.0  
   1280x720       60.0     50.0     59.9  
   1024x768       60.0  
   1152x648       50.0     59.9  
   800x600        60.3  
   720x480        60.0     59.9  
   640x480        59.9  
DFP10 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 527mm x 297mm
   1920x1080      60.0*+
   1680x1050      60.0  
   1400x1050      60.0  
   1600x900       60.0  
   1280x1024      75.0     60.0  
   1440x900       60.0  
   1280x960       75.0     60.0  
   1152x864       60.0     75.0  
   1280x768       75.0     60.0  
   1280x720       75.0     60.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   640x480        75.0     59.9  
CRT1 disconnected (normal left inverted right x axis y axis)

```

I have two problems if I do mirror image: 
- The problem is that image on DFP9 has black margins about 30 pixels wide each size, but I cannot figure out the cause and fix this.
- Sometimes there is a flickering in the bottom of DFP10

These are monitor properties from xrandr --prop
```

DFP9 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 160mm x 90mm
	EDID: 
		00ffffffffffff004c2dd40300000000
		331101038010098c0ae5b1a355499983
		13505421080001010101010101010101
		010101010101662150b051001b304070
		3600a05a0000001e011d007251d01e20
		6e285500a05a0000001e000000fd0017
		3c1a440f000a202020202020000000fc
		0053414d53554e470a202020202001fd
	SignalFormat: TMDS 
	ConnectorType: HDMI 
   1360x768       60.0 +
   1920x1080      60.0*    50.0     59.9     60.1     50.0     30.0     25.0     24.0     60.0     30.0     24.0  
   1776x1000      50.0     59.9     50.0     25.0     24.0     60.0     30.0  
   1680x1050      60.0     50.0     59.9     30.0     25.0     24.0     30.0     24.0  
   1400x1050      60.0     50.0     59.9     30.0     25.0     24.0     30.0     24.0  
   1600x900       50.0     59.9     25.0     24.0     30.0  
   1280x1024      60.0     50.0     59.9     30.0     25.0     24.0     30.0     24.0  
   1440x900       50.0     59.9     25.0     24.0     30.0  
   1280x960       50.0     59.9     25.0     24.0     30.0  
   1280x768       60.0  
   1280x720       60.0     50.0     59.9  
   1024x768       60.0  
   1152x648       50.0     59.9  
   800x600        60.3  
   720x480        60.0     59.9  
   640x480        59.9  
DFP10 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 527mm x 297mm
	EDID: 
		00ffffffffffff0010ac9ba04c455531
		2617010380351e78eaa0a5a656529d27
		0f5054a54b00714f8180a9c0d1c00101
		010101010101023a801871382d40582c
		45000f292100001e000000ff00333657
		4a583339483155454c0a000000fc0044
		454c4c205032343134480a20000000fd
		00384c1e5311000a20202020202000ce
	SignalFormat: TMDS 
	ConnectorType: DVI-I 
   1920x1080      60.0*+
   1680x1050      60.0  
   1400x1050      60.0  
   1600x900       60.0  
   1280x1024      75.0     60.0  
   1440x900       60.0  
   1280x960       75.0     60.0  
   1152x864       60.0     75.0  
   1280x768       75.0     60.0  
   1280x720       75.0     60.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   640x480        75.0     59.9  
CRT1 disconnected (normal left inverted right x axis y axis)
	SignalFormat: VGA 
	ConnectorType: DVI-I 

```



What I've tried without success (among other things):
```

xrandr --output DFP9 --panning 0x0+0+0
xrandr --output DFP9 --scale 1x1
xrandr --output DFP9 --transform none

```

---

