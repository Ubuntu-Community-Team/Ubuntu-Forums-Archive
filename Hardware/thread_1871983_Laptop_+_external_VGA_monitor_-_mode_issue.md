---
title: "Laptop + external VGA monitor - mode issue"
date: 2011-10-29
forum: Hardware
---

### Post by roncampbell on 2011-10-29
I am having a problem with external monitors when connected to my laptop through the VGA port.  

The resolution dimensions are correct (1280x1024, etc) for any monitor I connect, however there always seems to be what I will call an interlace effect happening (I'm not sure if interlace is the cause or not).

The VGA port and the monitor work fine in Windows so it must just be a configuration issue.  I suspect it has something to do with the xorg.conf file definition of the monitor, but I need a bit of help going through that process.

The two web pages I have been following to try and figure it out are these, and the last one is the actual specifications of the external monitor (page 13):
```
https://wiki.ubuntu.com/X/Config/Resolution
```
```
http://www.x.org/wiki/FAQVideoModes#head-82230a582646cbf28ac41dec2139732ee868e0d2
http://igor.chudov.com/manuals/NEC-Accusync-LCD72VX-Users-Manual.pdf
```

The laptop is a Dell Vostro 3300.

Here is the current xorg.conf file:
```

Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
EndSection
```

Here is the VGA adapters:
I am using the default Ubuntu drivers, not the proprietary NVidia drivers (the VGA display has the same problem even with the NVidia drivers)
```
ron@ron-Vostro-3300:/etc/X11$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 310M] (rev a2)

```

Here is the xrandr output:
```
ron@ron-Vostro-3300:/etc/X11$ xrandr
Screen 0: minimum 320 x 200, current 2646 x 1024, maximum 8192 x 8192
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 293mm x 164mm
   1366x768       60.2*+   40.0  
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1280x1024+1366+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0*+   75.0  
   1280x960       75.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
   1280x1024_108   60.0  
ron@ron-Vostro-3300:/etc/X11$ 

```

From Windows I got the specifications of the monitor working correctly using Power Strip:
```
PowerStrip timing parameters:
1280x1024=1280,48,112,248,1024,1,3,38,108000,512

Generic timing details for 1280x1024:
HFP=48 HSW=112 HBP=248 kHz=64 VFP=1 VSW=3 VBP=38 Hz=60

VESA detailed timing:
PClk=108.00 H.Active=1280 H.Blank=408 H.Offset=32 HSW=112 V.Active=1024 V.Blank=42 V.Offset=1 VSW=3

Linux modeline parameters:
"1280x1024" 108.000 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
```

If I understand correctly, the monitor display modes must be set in either the monitors.xml file or xorg.conf file.  Only when the monitors modes have been defined can the graphics card mode be set to a matching mode.  If a mode is set by the graphics card and it has not been defined that it is a mode the monitor can support it would not work.  Please correct me if I'm wrong.

So if someone could help with the next steps I would very much appreciate it.

---

### Post by papibe on 2011-10-29
Hi MoizBhukhiya, you have [Optimus]("http://www.nvidia.com/object/optimus_technology.html"). Which is a kind of new graphic architecture and it's just starting to be supported on Linux. Despite that fact, there are a couple of projects in progress that have some success to support it.

I would advice you to start reading a couple of useful threads. [This]("http://ubuntuforums.org/showthread.php?t=1657660") one to understand what it is (but a pessimist). And this [other]("http://ubuntuforums.org/showthread.php?t=1845896&highlight=nvidia") one (from post #7), with a more practical approach.

There are laptops that can either disable it, or simplify things by turning off the Nvidia card. Check your BIOS if you have any of those options.

I hope that helps,
Regards.

---

