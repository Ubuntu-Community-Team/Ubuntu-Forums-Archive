---
title: "Problems with AL2216W monitor"
date: 2008-10-06
forum: Hardware
---

### Post by tehlaser on 2008-10-06
I'm trying to get an Acer AL2216W LCD monitor to work under Hardy with my Acer Aspire laptop.  The laptop only has a VGA port (no DVI), so I'm using that.  I'm unable to get to native resolution (1680x1050); I seem to max out at 1440x900.  If I set anything higher, I get a bunch of scrambled flickering diagonal lines on the display.

According to lspci, my video card is "00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)"  This should be capable of the resolution I'm asking for, but I'm not entirely sure about that.

This is what xrandr sees:

```

$ xrandr --verbose
Screen 0: minimum 320 x 200, current 1440 x 900, maximum 1680 x 1680
VGA connected 1440x900+0+0 (0x52) normal (normal left inverted right x axis y axis) 474mm x 296mm
	Identifier: 0x4b
	Timestamp:  89169
	Subpixel:   unknown
	Clones:    
	CRTC:       0
	CRTCs:      0 1
	EDID_DATA:
		00ffffffffffff000472a1ad1e264081
		0e120103082f1e78eade95a3544c9926
		0f5054bfef90a940714f81408bc09500
		950f9040010121399030621a274068b0
		3600da2811000019000000fd00384d1f
		5411000a202020202020000000ff004c
		41313043303431343033310a000000fc
		00414c32323136570a20202020200009
  1680x1050 (0x4e)  146.2MHz -HSync -VSync
        h: width  1680 start 1784 end 1960 total 2240 skew    0 clock   65.3KHz
        v: height 1050 start 1053 end 1059 total 1089           clock   60.0Hz
  1600x1200 (0x4f)  161.0MHz -HSync +VSync
        h: width  1600 start 1712 end 1880 total 2160 skew    0 clock   74.5KHz
        v: height 1200 start 1203 end 1207 total 1245           clock   59.9Hz
  1680x1050 (0x4e)  146.2MHz -HSync -VSync
        h: width  1680 start 1784 end 1960 total 2240 skew    0 clock   65.3KHz
        v: height 1050 start 1053 end 1059 total 1089           clock   60.0Hz
  1400x1050 (0x50)  121.8MHz -HSync +VSync
        h: width  1400 start 1488 end 1632 total 1864 skew    0 clock   65.3KHz
        v: height 1050 start 1053 end 1057 total 1089           clock   60.0Hz
  1440x900 (0x51)  136.8MHz -HSync +VSync
        h: width  1440 start 1536 end 1688 total 1936 skew    0 clock   70.6KHz
        v: height  900 start  903 end  909 total  942           clock   75.0Hz
  1440x900 (0x52)  106.5MHz -HSync +VSync
        h: width  1440 start 1528 end 1672 total 1904 skew    0 clock   55.9KHz
        v: height  900 start  903 end  909 total  934           clock   59.9Hz
  1280x960 (0x53)  101.2MHz -HSync +VSync
        h: width  1280 start 1360 end 1488 total 1696 skew    0 clock   59.7KHz
        v: height  960 start  963 end  967 total  996           clock   59.9Hz
  1360x765 (0x54)   84.5MHz -HSync +VSync
        h: width  1360 start 1432 end 1568 total 1776 skew    0 clock   47.6KHz
        v: height  765 start  768 end  773 total  795           clock   59.8Hz
  1152x864 (0x55)  108.0MHz +HSync +VSync
        h: width  1152 start 1216 end 1344 total 1600 skew    0 clock   67.5KHz
        v: height  864 start  865 end  868 total  900           clock   75.0Hz
  1152x864 (0x56)  104.0MHz -HSync +VSync
        h: width  1152 start 1224 end 1344 total 1536 skew    0 clock   67.7KHz
        v: height  864 start  867 end  871 total  905           clock   74.8Hz
  1024x768 (0x57)   75.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1328 skew    0 clock   56.5KHz
        v: height  768 start  771 end  777 total  806           clock   70.1Hz
  1024x768 (0x58)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  832x624 (0x59)   57.3MHz -HSync -VSync
        h: width   832 start  864 end  928 total 1152 skew    0 clock   49.7KHz
        v: height  624 start  625 end  628 total  667           clock   74.6Hz
  800x600 (0x5a)   50.0MHz +HSync +VSync
        h: width   800 start  856 end  976 total 1040 skew    0 clock   48.1KHz
        v: height  600 start  637 end  643 total  666           clock   72.2Hz
  800x600 (0x5b)   49.5MHz +HSync +VSync
        h: width   800 start  816 end  896 total 1056 skew    0 clock   46.9KHz
        v: height  600 start  601 end  604 total  625           clock   75.0Hz
  800x600 (0x5c)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  800x600 (0x5d)   36.0MHz +HSync +VSync
        h: width   800 start  824 end  896 total 1024 skew    0 clock   35.2KHz
        v: height  600 start  601 end  603 total  625           clock   56.2Hz
  640x480 (0x5e)   31.5MHz -HSync -VSync
        h: width   640 start  656 end  720 total  840 skew    0 clock   37.5KHz
        v: height  480 start  481 end  484 total  500           clock   75.0Hz
  640x480 (0x5f)   31.5MHz -HSync -VSync
        h: width   640 start  664 end  704 total  832 skew    0 clock   37.9KHz
        v: height  480 start  489 end  491 total  520           clock   72.8Hz
  640x480 (0x60)   30.2MHz -HSync -VSync
        h: width   640 start  704 end  768 total  864 skew    0 clock   35.0KHz
        v: height  480 start  483 end  486 total  525           clock   66.7Hz
  640x480 (0x61)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   60.0Hz
LVDS connected (normal left inverted right x axis y axis)
	Identifier: 0x4c
	Timestamp:  89169
	Subpixel:   horizontal rgb
	Clones:    
	CRTCs:      1
	EDID_DATA:
		00ffffffffffff0006af742100000000
		010f0103802115780a1cf59758508e27
		27505400000001010101010101010101
		010101010101c71b00a0502017303020
		36004bcf100000180000000f00000000
		00000000000000000020000000fe0041
		554f0a202020202020202020000000fe
		004231353445573032205631200a00aa
	BACKLIGHT_CONTROL: combination
		supported: native       legacy       combination  kernel      
	BACKLIGHT: 10390 (0x00002896) range:  (0,10390)
  1280x800 (0x62)   71.1MHz -HSync -VSync
        h: width  1280 start 1328 end 1360 total 1440 skew    0 clock   49.4KHz
        v: height  800 start  803 end  809 total  823           clock   60.0Hz
  1280x800 (0x63)   83.5MHz
        h: width  1280 start 1344 end 1480 total 1680 skew    0 clock   49.7KHz
        v: height  800 start  801 end  804 total  828           clock   60.0Hz
  1280x768 (0x64)   80.1MHz
        h: width  1280 start 1344 end 1480 total 1680 skew    0 clock   47.7KHz
        v: height  768 start  769 end  772 total  795           clock   60.0Hz
  1024x768 (0x58)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0x5c)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  640x480 (0x65)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
TV disconnected (normal left inverted right x axis y axis)
	Identifier: 0x4d
	Timestamp:  89169
	Subpixel:   unknown
	Clones:    
	CRTCs:      0 1
	BOTTOM: 37 (0x00000025) range:  (0,100)
	RIGHT: 46 (0x0000002e) range:  (0,100)
	TOP: 36 (0x00000024) range:  (0,100)
	LEFT: 54 (0x00000036) range:  (0,100)
	TV_FORMAT: NTSC-M
		supported: NTSC-M       NTSC-443     NTSC-J       PAL-M       
		           PAL-N        PAL  

```

Mode 0x50 works (but is the wrong aspect ratio), as does 0x52 and 0x53.  0x4e (why are there two of these?) gives the scrambled display, and 0x4f gives an "out of range" message.

---

