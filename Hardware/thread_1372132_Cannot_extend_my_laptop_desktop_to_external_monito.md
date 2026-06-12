---
title: "Cannot extend my laptop desktop to external monitor"
date: 2010-01-04
forum: Hardware
---

### Post by venturax on 2010-01-04
My setup is this:
Lenovo T500 + docking station (with DVI output)
Samsung Syncmaster 2443 BW external monitor

The problem is that i can only get a desktop on my laptop. The 2443 is in sleep mode and i cannot get it "turned on", since there's no output from the laptop. Fn+F7 doesnt work.

Detect monitors doesnt find the monitor (its connected via DVI).

This is the output from xrandr:
```
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
```

I assume that DP1 is the DVI connection

---

### Post by venturax on 2010-01-05
This is the verbose output:
```

Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
	Identifier: 0x3b
	Timestamp:  130075
	Subpixel:   unknown
	Clones:    
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
LVDS1 connected 1680x1050+0+0 (0x3e) normal (normal left inverted right x axis y axis) 331mm x 207mm
	Identifier: 0x3c
	Timestamp:  130075
	Subpixel:   horizontal rgb
	Clones:    
	CRTC:       1
	CRTCs:      1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
	EDID_DATA:
		00ffffffffffff0030ae534000000000
		0011010380211578eacd7591554f8b26
		21505400000001010101010101010101
		010101010101a82f90e0601a10402040
		13004bcf10000019b72790e0601a1040
		204013004bcf100000190000000f00b3
		0a32b30a281401004ca35033000000fe
		004c544e31353450332d4c30320a007e
	BACKLIGHT: 15 (0x0000000f)	range:  (0,15)
	Backlight: 15 (0x0000000f)	range:  (0,15)
	scaling mode:	Fullscreen
		supported: Non-GPU      Fullscreen   No scale     Aspect      
  1680x1050 (0x3e)  122.0MHz -HSync -VSync *current +preferred
        h: width  1680 start 1712 end 1776 total 1904 skew    0 clock   64.1KHz
        v: height 1050 start 1051 end 1054 total 1066           clock   60.1Hz
  1680x1050 (0x3f)  214.8MHz -HSync +VSync
        h: width  1680 start 1808 end 1984 total 2288 skew    0 clock   93.9KHz
        v: height 1050 start 1053 end 1059 total 1105           clock   84.9Hz
  1680x1050 (0x40)  187.0MHz -HSync +VSync
        h: width  1680 start 1800 end 1976 total 2272 skew    0 clock   82.3KHz
        v: height 1050 start 1053 end 1059 total 1099           clock   74.9Hz
  1680x1050 (0x41)  174.0MHz -HSync +VSync
        h: width  1680 start 1800 end 1976 total 2272 skew    0 clock   76.6KHz
        v: height 1050 start 1053 end 1059 total 1096           clock   69.9Hz
  1680x1050 (0x42)  146.2MHz -HSync +VSync
        h: width  1680 start 1784 end 1960 total 2240 skew    0 clock   65.3KHz
        v: height 1050 start 1053 end 1059 total 1089           clock   60.0Hz
  1680x1050 (0x43)  101.7MHz -HSync -VSync
        h: width  1680 start 1712 end 1776 total 1904 skew    0 clock   53.4KHz
        v: height 1050 start 1051 end 1054 total 1066           clock   50.1Hz
  1600x1024 (0x44)  103.1MHz +HSync +VSync
        h: width  1600 start 1600 end 1656 total 1664 skew    0 clock   62.0KHz
        v: height 1024 start 1024 end 1029 total 1030           clock   60.2Hz
  1400x1050 (0x45)  179.3MHz -HSync +VSync
        h: width  1400 start 1504 end 1656 total 1912 skew    0 clock   93.8KHz
        v: height 1050 start 1051 end 1054 total 1103           clock   85.0Hz
  1400x1050 (0x46)  155.8MHz +HSync +VSync
        h: width  1400 start 1464 end 1784 total 1912 skew    0 clock   81.5KHz
        v: height 1050 start 1052 end 1064 total 1090           clock   74.8Hz
  1400x1050 (0x47)  145.1MHz -HSync +VSync
        h: width  1400 start 1496 end 1648 total 1896 skew    0 clock   76.5KHz
        v: height 1050 start 1051 end 1054 total 1093           clock   70.0Hz
  1400x1050 (0x48)  122.0MHz +HSync +VSync
        h: width  1400 start 1488 end 1640 total 1880 skew    0 clock   64.9KHz
        v: height 1050 start 1052 end 1064 total 1082           clock   60.0Hz
  1280x1024 (0x49)  157.5MHz +HSync +VSync
        h: width  1280 start 1344 end 1504 total 1728 skew    0 clock   91.1KHz
        v: height 1024 start 1025 end 1028 total 1072           clock   85.0Hz
  1280x1024 (0x4a)  135.0MHz +HSync +VSync
        h: width  1280 start 1296 end 1440 total 1688 skew    0 clock   80.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   75.0Hz
  1280x1024 (0x4b)  108.0MHz +HSync +VSync
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock   64.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   60.0Hz
  1440x900 (0x4c)  106.5MHz -HSync +VSync
        h: width  1440 start 1520 end 1672 total 1904 skew    0 clock   55.9KHz
        v: height  900 start  903 end  909 total  934           clock   59.9Hz
  1280x960 (0x4d)  148.5MHz +HSync +VSync
        h: width  1280 start 1344 end 1504 total 1728 skew    0 clock   85.9KHz
        v: height  960 start  961 end  964 total 1011           clock   85.0Hz
  1280x960 (0x4e)  108.0MHz +HSync +VSync
        h: width  1280 start 1376 end 1488 total 1800 skew    0 clock   60.0KHz
        v: height  960 start  961 end  964 total 1000           clock   60.0Hz
  1360x768 (0x4f)   84.8MHz -HSync +VSync
        h: width  1360 start 1432 end 1568 total 1776 skew    0 clock   47.7KHz
        v: height  768 start  771 end  781 total  798           clock   59.8Hz
  1152x864 (0x50)  143.5MHz -HSync +VSync
        h: width  1152 start 1232 end 1360 total 1568 skew    0 clock   91.5KHz
        v: height  864 start  865 end  868 total  915           clock  100.0Hz
  1152x864 (0x51)  121.5MHz +HSync -VSync
        h: width  1152 start 1216 end 1344 total 1568 skew    0 clock   77.5KHz
        v: height  864 start  865 end  868 total  911           clock   85.1Hz
  1152x864 (0x52)  119.7MHz -HSync +VSync
        h: width  1152 start 1224 end 1352 total 1552 skew    0 clock   77.1KHz
        v: height  864 start  865 end  868 total  907           clock   85.0Hz
  1152x864 (0x53)  108.0MHz +HSync +VSync
        h: width  1152 start 1216 end 1344 total 1600 skew    0 clock   67.5KHz
        v: height  864 start  865 end  868 total  900           clock   75.0Hz
  1152x864 (0x54)  105.0MHz -HSync +VSync
        h: width  1152 start 1224 end 1352 total 1552 skew    0 clock   67.6KHz
        v: height  864 start  865 end  868 total  902           clock   75.0Hz
  1152x864 (0x55)   96.8MHz -HSync +VSync
        h: width  1152 start 1224 end 1344 total 1536 skew    0 clock   63.0KHz
        v: height  864 start  865 end  868 total  900           clock   70.0Hz
  1152x864 (0x56)   81.6MHz -HSync +VSync
        h: width  1152 start 1216 end 1336 total 1520 skew    0 clock   53.7KHz
        v: height  864 start  865 end  868 total  895           clock   60.0Hz
  1024x768 (0x57)   94.5MHz +HSync +VSync
        h: width  1024 start 1072 end 1168 total 1376 skew    0 clock   68.7KHz
        v: height  768 start  769 end  772 total  808           clock   85.0Hz
  1024x768 (0x58)   78.8MHz +HSync +VSync
        h: width  1024 start 1040 end 1136 total 1312 skew    0 clock   60.0KHz
        v: height  768 start  769 end  772 total  800           clock   75.0Hz
  1024x768 (0x59)   75.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1328 skew    0 clock   56.5KHz
        v: height  768 start  771 end  777 total  806           clock   70.1Hz
  1024x768 (0x5a)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  832x624 (0x5b)   57.3MHz -HSync -VSync
        h: width   832 start  864 end  928 total 1152 skew    0 clock   49.7KHz
        v: height  624 start  625 end  628 total  667           clock   74.6Hz
  800x600 (0x5c)   56.3MHz +HSync +VSync
        h: width   800 start  832 end  896 total 1048 skew    0 clock   53.7KHz
        v: height  600 start  601 end  604 total  631           clock   85.1Hz
  800x600 (0x5d)   50.0MHz +HSync +VSync
        h: width   800 start  856 end  976 total 1040 skew    0 clock   48.1KHz
        v: height  600 start  637 end  643 total  666           clock   72.2Hz
  800x600 (0x5e)   49.5MHz +HSync +VSync
        h: width   800 start  816 end  896 total 1056 skew    0 clock   46.9KHz
        v: height  600 start  601 end  604 total  625           clock   75.0Hz
  800x600 (0x5f)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  800x600 (0x60)   36.0MHz +HSync +VSync
        h: width   800 start  824 end  896 total 1024 skew    0 clock   35.2KHz
        v: height  600 start  601 end  603 total  625           clock   56.2Hz
  640x480 (0x61)   36.0MHz -HSync -VSync
        h: width   640 start  696 end  752 total  832 skew    0 clock   43.3KHz
        v: height  480 start  481 end  484 total  509           clock   85.0Hz
  640x480 (0x62)   31.5MHz -HSync -VSync
        h: width   640 start  664 end  704 total  832 skew    0 clock   37.9KHz
        v: height  480 start  489 end  492 total  520           clock   72.8Hz
  640x480 (0x63)   31.5MHz -HSync -VSync
        h: width   640 start  656 end  720 total  840 skew    0 clock   37.5KHz
        v: height  480 start  481 end  484 total  500           clock   75.0Hz
  640x480 (0x64)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
  720x400 (0x65)   35.5MHz -HSync +VSync
        h: width   720 start  756 end  828 total  936 skew    0 clock   37.9KHz
        v: height  400 start  401 end  404 total  446           clock   85.0Hz
  640x400 (0x66)   31.5MHz -HSync +VSync
        h: width   640 start  672 end  736 total  832 skew    0 clock   37.9KHz
        v: height  400 start  401 end  404 total  445           clock   85.1Hz
  640x350 (0x67)   31.5MHz +HSync -VSync
        h: width   640 start  672 end  736 total  832 skew    0 clock   37.9KHz
        v: height  350 start  382 end  385 total  445           clock   85.1Hz
DP1 disconnected (normal left inverted right x axis y axis)
	Identifier: 0x3d
	Timestamp:  130075
	Subpixel:   unknown
	Clones:    
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 

```

Hope this helps. It's a bit frustrating that my 24" monitor is idle :-)

---

### Post by venturax on 2010-01-05
Ok, so I've tampered a bit more with this. It seems that its only DVI, that's not detected. In frustration I removed the DVI cable and inserted a VGA instead and to my surprise, this was detected.
```
Screen 0: minimum 320 x 200, current 1920 x 1200, maximum 8192 x 8192
VGA1 connected 1920x1200+0+0 (normal left inverted right x axis y axis) 518mm x 324mm
   1920x1200      60.0*+
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        60.0  
LVDS1 connected (normal left inverted right x axis y axis)
   1680x1050      60.1 +   84.9     74.9     69.9     60.0     50.1  
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
```
So now i can use the monitor, but the quality is not comparable to DVI.
My current guess is that something in the kernel is missing to support DVI. I have not much experience with configuring, compiling and switching kernels and would like to avoid it if possible. 

Anyone got a guess, what i should look for in the kernel configuration?

---

### Post by ronni on 2010-01-19
Hi,

I'm using Ubuntu 9.10 on a T500 with an ATI graphic card + the advanced minidock; I think it is.

I have two Samsung monitors connected, one on DVI and one on VGA and both works, sort of, one of the monitors picture is unclear, difficult to explain.
But I do have a picture, and they are both detected, and I have not loaded anything for the kernel.

Have you tried another screen, cable etc.?

---

### Post by venturax on 2010-08-23
Gotta close this thread as I now have figured out the problem. The DVI was due to a bad docking station. 

I re-tried dual monitor after upgrading to 10.04 and it worked as expected, but one small issue was left, namely that the task bar and main menu was on the laptop monitor and not on my 24". The monitor setup does not have sufficient controls to change this, but thanks to [http://ubuntuforums.org/showthread.php?p=9754184](http://ubuntuforums.org/showthread.php?p=9754184) I was able solve it.
```
xrandr --output VGA1 --primary
```

---

