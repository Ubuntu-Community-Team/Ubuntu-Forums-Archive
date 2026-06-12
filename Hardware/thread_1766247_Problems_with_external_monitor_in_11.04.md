---
title: "Problems with external monitor in 11.04"
date: 2011-05-24
forum: Hardware
---

### Post by jonasp on 2011-05-24
Hi Guys,

Hope someone can help me a bit here. I have an issue with my monitors. I have an HP G62 Laptop with Intel graphics running 64bit Ubuntu.

Recently I was able to break my internal monitor, making it virtually unusable. As a solution I connected an external monitor to the laptop deciding to rebrand it as my desktop computer :)

However, this proved to be easier said than done. When connected the resolution is reduced to 1024*768 in a mirrored mode. When i try to set a bigger resolution and turn off the internal monitor it generates an interesting error. When setting the native screen resolution of the external monitor (1680*1050) the screen flickers constantly and it is impossible to see anything on the screen due to this. if i choose 1280*1024 the flickering is not as high, but it is still flickering, rendering the computer unusable in any other resolutions than 1024*768. 

The internal monitor has a 16:9, while the external has a 16:10 screen. However in mirror mode only 4:3 screensizes are available to pick from. 

lshw -C video output:
```

description: VGA compatible controller
product: Core Processor Integrated Graphics Controller
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:00:02.0
version: 02
width: 64 bits
clock: 33MHz
capabilities: vga_controller bus_master cap_list rom
configuration: driver=i915 latency=0
resources: irq:42 memory:90000000-903fffff memory:80000000-8fffffff ioport:4050(size=8)

```

xrandr --verbose output
```
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
LVDS1 connected 1024x768+0+0 (0x48) normal (normal left inverted right x axis y axis) 344mm x 194mm
	Identifier: 0x41
	Timestamp:  132082
	Subpixel:   horizontal rgb
	Gamma:      1.0:1.0:1.0
	Brightness: 1.0
	Clones:    
	CRTC:       0
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
	EDID:
		00ffffffffffff0030e47c0200000000
		00130103802213780a4e859e5b559526
		18505400000001010101010101010101
		010101010101121b567850000e302020
		240058c2100000190000000000000000
		00000000000000000000000000fe004c
		4720446973706c61790a2020000000fc
		004c503135365748322d544c51320028
	BACKLIGHT: 10 (0x0000000a)	range:  (0,10)
	Backlight: 10 (0x0000000a)	range:  (0,10)
	scaling mode:	Full aspect
		supported: None         Full         Center       Full aspect 
  1366x768 (0x45)   69.3MHz -HSync -VSync +preferred
        h: width  1366 start 1398 end 1430 total 1486 skew    0 clock   46.6KHz
        v: height  768 start  770 end  774 total  782           clock   59.6Hz
  1360x768 (0x46)   84.8MHz -HSync +VSync
        h: width  1360 start 1432 end 1568 total 1776 skew    0 clock   47.7KHz
        v: height  768 start  771 end  781 total  798           clock   59.8Hz
  1360x768 (0x47)   72.0MHz +HSync -VSync
        h: width  1360 start 1408 end 1440 total 1520 skew    0 clock   47.4KHz
        v: height  768 start  771 end  781 total  790           clock   60.0Hz
  1024x768 (0x48)   65.0MHz -HSync -VSync *current
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0x49)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  800x600 (0x4a)   36.0MHz +HSync +VSync
        h: width   800 start  824 end  896 total 1024 skew    0 clock   35.2KHz
        v: height  600 start  601 end  603 total  625           clock   56.2Hz
  640x480 (0x4b)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
VGA1 connected 1024x768+0+0 (0x48) normal (normal left inverted right x axis y axis) 434mm x 270mm
	Identifier: 0x42
	Timestamp:  132082
	Subpixel:   unknown
	Gamma:      1.0:1.0:1.0
	Brightness: 1.0
	Clones:    
	CRTC:       1
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
	EDID:
		00ffffffffffff001e6d474e972b0000
		031101036a2b1b78ead105a655479d25
		155054a76b80010181808140714f0101
		01010101010121399030621a274068b0
		3600b20e1100001c000000fd00384b1c
		530f000a202020202020000000fc004c
		32303457540a202020202020000000fc
		000a2020202020202020202020200070
  1680x1050 (0x4c)  146.2MHz -HSync +VSync +preferred
        h: width  1680 start 1784 end 1960 total 2240 skew    0 clock   65.3KHz
        v: height 1050 start 1053 end 1059 total 1089           clock   60.0Hz
  1280x1024 (0x4d)  135.0MHz +HSync +VSync
        h: width  1280 start 1296 end 1440 total 1688 skew    0 clock   80.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   75.0Hz
  1280x1024 (0x4e)  108.0MHz +HSync +VSync
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock   64.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   60.0Hz
  1280x960 (0x4f)  108.0MHz +HSync +VSync
        h: width  1280 start 1376 end 1488 total 1800 skew    0 clock   60.0KHz
        v: height  960 start  961 end  964 total 1000           clock   60.0Hz
  1152x864 (0x50)  108.0MHz +HSync +VSync
        h: width  1152 start 1216 end 1344 total 1600 skew    0 clock   67.5KHz
        v: height  864 start  865 end  868 total  900           clock   75.0Hz
  1024x768 (0x51)   78.8MHz +HSync +VSync
        h: width  1024 start 1040 end 1136 total 1312 skew    0 clock   60.1KHz
        v: height  768 start  769 end  772 total  800           clock   75.1Hz
  1024x768 (0x48)   65.0MHz -HSync -VSync *current
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  832x624 (0x52)   57.3MHz -HSync -VSync
        h: width   832 start  864 end  928 total 1152 skew    0 clock   49.7KHz
        v: height  624 start  625 end  628 total  667           clock   74.6Hz
  800x600 (0x53)   49.5MHz +HSync +VSync
        h: width   800 start  816 end  896 total 1056 skew    0 clock   46.9KHz
        v: height  600 start  601 end  604 total  625           clock   75.0Hz
  800x600 (0x49)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  800x600 (0x4a)   36.0MHz +HSync +VSync
        h: width   800 start  824 end  896 total 1024 skew    0 clock   35.2KHz
        v: height  600 start  601 end  603 total  625           clock   56.2Hz
  640x480 (0x54)   31.5MHz -HSync -VSync
        h: width   640 start  656 end  720 total  840 skew    0 clock   37.5KHz
        v: height  480 start  481 end  484 total  500           clock   75.0Hz
  640x480 (0x55)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   60.0Hz
  720x400 (0x56)   28.3MHz -HSync +VSync
        h: width   720 start  738 end  846 total  900 skew    0 clock   31.5KHz
        v: height  400 start  412 end  414 total  449           clock   70.1Hz
HDMI1 disconnected (normal left inverted right x axis y axis)
	Identifier: 0x43
	Timestamp:  132082
	Subpixel:   unknown
	Clones:    
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
	force_audio: 0 (0x00000000)	range:  (-1,1)
DP1 disconnected (normal left inverted right x axis y axis)
	Identifier: 0x44
	Timestamp:  132082
	Subpixel:   unknown
	Clones:    
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
	force_audio: 0 (0x00000000)	range:  (-1,1)
```

Is there anybody out there that are able to help me set a decent resolution to my screen?

---

### Post by greencookie on 2011-05-26
Hello.

Have you tried executing ```
unity --replace
```

?

I ran into a [similar problem]("http://ubuntuforums.org/showthread.php?p=10863373#post10863373") and that has been helpful.

---

