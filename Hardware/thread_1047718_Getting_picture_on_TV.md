---
title: "Getting picture on TV"
date: 2009-01-22
forum: Hardware
---

### Post by 9acro on 2009-01-22
I have problems getting S-video output to work, I can not get any output on it
xrandr --verbose detects TV, but I can not get picture on it (it showed briefly just once on login screen, but disappeared afterwards)
[SIZE="1"]
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1280
VGA disconnected (normal left inverted right x axis y axis)
	Identifier: 0x4b
	Timestamp:  34208
	Subpixel:   unknown
	Clones:    
	CRTCs:      0 1
LVDS connected 1280x800+0+0 (0x4e) normal (normal left inverted right x axis y axis) 331mm x 207mm
	Identifier: 0x4c
	Timestamp:  34208
	Subpixel:   horizontal rgb
	Clones:    
	CRTC:       1
	CRTCs:      1
	EDID_DATA:
		00ffffffffffff00320c00e300000000
		00100103802115780ab3409959538d27
		25505400000001010101010101010101
		010101010101bc1b00a0502017303020
		36004bcf100000190000000000000000
		00000000000000000000000000fe004c
		475068696c6970734c43440a000000fe
		004c503135345758342d544c4333003c
	BACKLIGHT_CONTROL: kernel
		supported: native       legacy       combination  kernel      
	BACKLIGHT: 15 (0x0000000f) range:  (0,15)
  1280x800 (0x4e)   71.0MHz -HSync -VSync
        h: width  1280 start 1328 end 1360 total 1440 skew    0 clock   49.3KHz
        v: height  800 start  803 end  809 total  823           clock   59.9Hz
  1280x800 (0x4f)   83.5MHz
        h: width  1280 start 1344 end 1480 total 1680 skew    0 clock   49.7KHz
        v: height  800 start  801 end  804 total  828           clock   60.0Hz
  1280x768 (0x50)   80.1MHz
        h: width  1280 start 1344 end 1480 total 1680 skew    0 clock   47.7KHz
        v: height  768 start  769 end  772 total  795           clock   60.0Hz
  1024x768 (0x51)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0x52)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  640x480 (0x53)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
[B]TV connected 640x480+0+0 (0x75) normal (normal left inverted right x axis y axis) 0mm x 0mm
	Identifier: 0x4d
	Timestamp:  34208
	Subpixel:   unknown
	Clones:    
	CRTC:       0
	CRTCs:      0 1
	BOTTOM: 37 (0x00000025) range:  (0,100)
	RIGHT: 46 (0x0000002e) range:  (0,100)
	TOP: 36 (0x00000024) range:  (0,100)
	LEFT: 54 (0x00000036) range:  (0,100)
	TV_FORMAT: PAL[/B]
		supported: NTSC-M       NTSC-443     NTSC-J       PAL-M       
		           PAL-N        PAL         
  1024x768 (0x72)   22.4MHz
        h: width  1024 start 1025 end 1088 total 1120 skew    0 clock   20.0KHz
        v: height  768 start  769 end  800 total  801           clock   25.0Hz
  800x600 (0x73)   14.2MHz
        h: width   800 start  801 end  864 total  896 skew    0 clock   15.8KHz
        v: height  600 start  601 end  632 total  633           clock   25.0Hz
  848x480 (0x74)   12.1MHz
        h: width   848 start  849 end  912 total  944 skew    0 clock   12.8KHz
        v: height  480 start  481 end  512 total  513           clock   25.0Hz
  640x480 (0x75)    9.4MHz
        h: width   640 start  641 end  704 total  736 skew    0 clock   12.8KHz
        v: height  480 start  481 end  512 total  513           clock   25.0Hz

[/SIZE]



i tried starting output with
xrandr --output TV --auto --pos 0x0 --mode 640x480

but nothing happens, no picture on TV



lspci -v returns this:


00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
	Subsystem: Fujitsu Siemens Computers Unknown device 1123
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fc000000 (64-bit, non-prefetchable) [size=1M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 1800 [size=8]
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [d0] Power Management version 3

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
	Subsystem: Fujitsu Siemens Computers Unknown device 1123
	Flags: bus master, fast devsel, latency 0
	Memory at fc100000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: [d0] Power Management version 3

---

