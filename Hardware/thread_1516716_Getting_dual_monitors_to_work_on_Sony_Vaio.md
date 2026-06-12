---
title: "Getting dual monitors to work on Sony Vaio"
date: 2010-06-24
forum: Hardware
---

### Post by andymantell on 2010-06-24
Hi,

I am having some trouble configuring dual monitors to work on my Sony Vaio Laptop F(V) series. I am connecting an external monitor to the HDMI port which I want to run as well as the main laptop screen. I can get each screen to work independently by reinstalling the nvidia drivers with or without the external monitor plugged in. However, I can't get them both to run at once.

Some basic details about my laptop:

```

Product ID : VPCF11V5E
Description : Laptop VPC-F11V - Configurable
Chipset : Intel PM55
Processor : Intel® Core(TM) i3 Processor
Display : 41.6 cm LCD, 1920x1080+ webcam
Graphics : NVIDIA® GeForce® 310M 512MB
Market : VPCF11C5E
HDMI(TM) output : HDMI(TM) output
```

My xorg.conf for getting the external monitor to work
```

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```

and my xorg.conf for the internal laptop screen (using xorg from here: [http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup](http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup) in order to get the nvidia drivers to recognise the panel)

```

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
        Option          "ConnectedMonitor" "DFP-0"
        Option          "CustomEDID" "DFP-0: /proc/acpi/video/NGFX/LCD/EDID"
        Option          "RegistryDwords" "EnableBrightnessControl=1"
EndSection

```

I've tried hacking it about a bit using various things people were saying about TwinView and Xinerama but I'm fairly new to Linux and I simply end up breaking things! Does anyone know how to fix this?

Thanks very much,

Andy

---

