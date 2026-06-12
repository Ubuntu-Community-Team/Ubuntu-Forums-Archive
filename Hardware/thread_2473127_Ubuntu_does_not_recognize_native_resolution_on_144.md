---
title: "Ubuntu does not recognize native resolution on 1440p monitor via HDMI"
date: 2022-03-24
forum: Hardware
---

### Post by whochismo on 2022-03-24
A few months ago I bought a Sceptre IPS 24-Inch QHD 2560x1440 75Hz monitor (model E248W-QPT). However, when plugging that monitor to the HDMI port of my laptop, Ubuntu 20.04 did not detect the native resolution, it was not listed on the resolution list, and the maximum available resolution was 2048x1152, which made everything look blurry. If I connect the monitor via usb-c using a dongle, the native resolution is picked up automatically, but probably due to a bad cable or something, the monitor blinks from time to time (I saw it happen in other computers, so it's a common issue with usb-c displays).

I ended up messing with xrandr to add a new mode and make the 1440 resolution available in the list. For anyone who's interested, I made a simple bash script to run at the startup so the new resolution is added every time.

```
#! /bin/bash
xrandr --newmode "2560x1440R"  241.50  2560 2608 2640 2720  1440 1443 1448 1481 +hsync -vsync
xrandr --addmode HDMI-2 "2560x1440R"
xrandr --addmode HDMI-1 "2560x1440R"
xrandr --output HDMI-2 --mode "2560x1440R"
xrandr --output HDMI-1 --mode "2560x1440R"
```

It only supports 65Hz, instead of 75Hz, though.

The thing is that yesterday I tried the latest betas from Ubuntu 24.04 and Kubuntu 24.04 and the issue was still there.

Is this something that needs to be reported, so the bug is fixed? What would be the best way?

EDIT: I forgot to add, the native resolution and 75Hz is detected automatically in Windows 10 via HDMI.

---

### Post by TheFu on 2022-03-26
24.04?  Impressive.

You could just modify the xorg.conf file with the new mode. If one doesn't exist, not hard to create it.  Also, I doubt that will work with Wayland, so with the default of Wayland on the next LTS, you'll be among the many (including me) who forces X11.

Pro-Tip: commands that start with 'x' are likely tied to the X/Server and won't likely work with Wayland if they do hardware stuff or take advantage of security failings in X/Windows that Wayland closes.

The modes should be provided by the monitor through the connection, seen by the GPU driver, then made available.  With nvidia proprietary drivers, it is possible to force the EDID information into the xorg.conf if it isn't being provided correctly.  get-edid, parse-edid are the commands.  Sometimes a KVM switch or HDMI switch will prevent non-standard resolutions.  Or there could be an adapter doing conversions.  I've seen the adapter, HDMI switch and KVM switch issues myself.

---

### Post by whochismo on 2022-03-26
Haha, I meant 22.04.

So, the resolution list must be provided by the hardware. But how is it possible that windows detects the native resolution automatically but not Ubuntu?

My laptop has two hours, a integrated Intel and a dedicated Nvidia. By default I use the former because it uses less battery. I think I read that Wayland will only be default when using the Nvidia drivers, right?

---

### Post by TheFu on 2022-03-27
> **whochismo said:**
>  So, the resolution list must be provided by the hardware. But how is it possible that windows detects the native resolution automatically but not Ubuntu?

Different OSes.
Different drivers.
Different driver teams.

a) Sometimes, MSFT doesn't follow standards.  Standards are what Linux uses.  So we get vendors who only test with Windows and Windows drivers, that don't follow standards, so things that shouldn't work, but do.  Cutting corners is how to save $100 off each device sold. Add another $10/per device if no standards testing lab is engaged.

b) Or perhaps the 2-person Linux driver team didn't catch all the intricate details in the standards and since nobody at the vendor tested with Linux and Linux drivers, it doesn't work? 

Take your pick.  IMHO, 90% of the time, it is the "a" scenario.  I've written standards compliant code and found that MSFT choked on it.  Just sayin'.  Had a friend who worked at an RF testing company.  To get a US FCC sticker, nearly all electronics has to be tested by a certified lab. He had stories about all sorts of companies failing. I suppose the passed devices aren't nearly as entertaining for testing.

---

### Post by DuckHook on 2022-03-27
> **whochismo said:**
> …how is it possible that windows detects the native resolution automatically but not Ubuntu?

> **TheFu said:**
> …MSFT doesn't follow standards.  Standards are what Linux uses.  So we get vendors who only test with Windows and Windows drivers, that don't follow standards, so things that shouldn't work, but do.  Cutting corners is how to save $100 off each device sold. Add another $10/per device if no standards testing lab is engaged.
It is a known dynamic that OEMs will actually _*break*_ standards in order to accommodate Windows bugs. Because Windows is such an 800 pound gorilla, the bug then becomes the de facto "standard". Can't really blame the OEMs when 95% of their revenue comes out of Windows, but this leaves guys like Linux (who adhere to standards) out in the cold.

If we Linux types think we are getting short shafted, it is rewarding to spend some time hanging out on the BSD forums. If OEMs don't much care about Linux, they haven't even heard of BSD. BSD aficionados consider our equipment "problems" little short of a small piece of paradise.

---

### Post by whochismo on 2022-03-30
So, in my specific case, how should I contact the appropriate developers so I can submit a bug report for my case, so other people won't have this problem in the future?

---

### Post by TheFu on 2022-03-30
> **whochismo said:**
> So, in my specific case, how should I contact the appropriate developers so I can submit a bug report for my case, so other people won't have this problem in the future?

Sceptre or the cable is likely the problem here.  That's my best guess, lacking any information (or skill). 

I suppose they got their system to work with Windows and stopped going any further. If you open a bug and the code is known to be standards compliant, it will likely be closed. 

Did you pull the EDID information and see the modes you see in Windows?  That's really the first step.  The EDID commands are:
```
$ man -k edid
**get-edid** (1)         - read-edid tools to retrieve and interpret monitor specification...
**parse-edid** (1)       - read-edid tools to retrieve and interpret monitor specification...
```
Well, I'm here now ....
```
$ sudo get-edid | parse-edid 
This is read-edid version 3.0.2. Prepare for some fun.
Attempting to use i2c interface
No EDID on bus 1
No EDID on bus 2
No EDID on bus 4
2 potential busses found: 0 3
Will scan through until the first EDID is found.
Pass a bus number as an option to this program to go only for that one.
Bus 0 doesn't really have an EDID...
256-byte EDID successfully retrieved from i2c bus 3
Looks like i2c was successful. Have a good day.
Checksum Correct

Section "Monitor"
        Identifier "&#65533;"
        ModelName "&#65533;"
        VendorName "AGO"
        # Monitor Manufactured week 45 of 2013
        # EDID version 1.3
        # Digital Display
        DisplaySize 300 230
        Gamma 1.97
        Option "DPMS" "true"
        #Not giving standard mode: 1280x1024, 60Hz
        #Not giving standard mode: 1280x960, 60Hz
        #Not giving standard mode: 1280x800, 60Hz
        #Not giving standard mode: 1440x900, 60Hz

        #Extension block found. Parsing...
extb[4]: 0x23 (0x20)
Hmm, you have data blocks, but not video ones... weird
Something strange happened. Please contact the author,
**[COLOR="#B22222"]Matthew Kern at <pyrophobicman@gmail.com>[/COLOR]**
```
That's what the HDMI-VGA(Adapter) - KVM-Switch(VGA in/out) - Monitor(VGA in) shows.  But the EDID file I created years ago says this:
```
$ cat /etc/X11/xorg-monitor.dell-2412m.edid.raw | parse-edid
Checksum Correct

Section "Monitor"
        Identifier "DELL U2412M"
        ModelName "DELL U2412M"
        VendorName "DEL"
        # Monitor Manufactured week 10 of 2013
        # EDID version 1.3
        # Analog Display
        Option "SyncOnGreen" "true"
        DisplaySize 520 320
        Gamma 2.20
        Option "DPMS" "true"
        Horizsync 30-83
        VertRefresh 50-61
        # Maximum pixel clock is 170MHz
        #Not giving standard mode: 1280x960, 60Hz
        #Not giving standard mode: 1280x1024, 60Hz
        #Not giving standard mode: 1600x1200, 60Hz
        #Not giving standard mode: 1680x1050, 60Hz
        #Not giving standard mode: **[COLOR="#008000"]1920x1080, 60Hz[/COLOR]**
        Modeline        "Mode 0" 154.00 1920 1968 2000 2080 1200 1203 1209 1235 +hsync -vsync 
EndSection
```

After pulling the EDID information, you can try a bug with the EDID team, if you like. The email is above for the version of code I have. Newer versions could have a different address.  The team might develop on github and probably would prefer to be notified that way.  I didn't look.

The workaround has been possible for decades - that is to create a local xorg.conf file with the desired modeline and updated monitor section.

A new KVM-switch should arrive here any day now, so my setup will massively change in the next week. The HDMI-to-VGA converter won't be needed anymore, hopefully.

---

### Post by him610 on 2022-03-30
whochismo

From the User Manual for Sceptre Model E248W-QPT IPS 24-Inch QHD 2560x1440, Troubleshooting, pages 26-28....

There are several problems listed with possible solutions - no guarantees though, just suggestions. No mention of Operating Systems as culprit. There is reference to Native Resolution being 1920 x 1080 which means that is what it was optimally designed for.

---

### Post by whochismo on 2022-04-01
Running these commands on my computer, I get the following output:

```
(base) user@TM1703:~$ sudo get-edid | parse-edid
This is read-edid version 3.0.2. Prepare for some fun.
Attempting to use i2c interface
No EDID on bus 0
No EDID on bus 1
No EDID on bus 2
No EDID on bus 4
No EDID on bus 5
No EDID on bus 7
2 potential busses found: 3 6
Will scan through until the first EDID is found.
Pass a bus number as an option to this program to go only for that one.
256-byte EDID successfully retrieved from i2c bus 3
Looks like i2c was successful. Have a good day.
Checksum Correct

Section "Monitor"
	Identifier "Sceptre Q24"
	ModelName "Sceptre Q24"
	VendorName "SPT"
	# Monitor Manufactured week 30 of 2020
	# EDID version 1.3
	# Digital Display
	DisplaySize 700 400
	Gamma 2.20
	Option "DPMS" "true"
	Horizsync 23-99
	VertRefresh 48-65
	# Maximum pixel clock is 300MHz
	#Not giving standard mode: 1024x768, 60Hz
	#Not giving standard mode: 1280x720, 60Hz
	#Not giving standard mode: 1280x1024, 60Hz
	#Not giving standard mode: 1600x900, 60Hz
	#Not giving standard mode: 1152x864, 60Hz
	#Not giving standard mode: 1920x1080, 60Hz

	#Extension block found. Parsing...
	Modeline 	"Mode 13" 175.50 1920 2008 2052 2080 1080 1084 1089 1125 +hsync +vsync 
	Modeline 	"Mode 0" 241.70 2560 2608 2640 2720 1440 1443 1448 1481 +hsync +vsync 
	Modeline 	"Mode 1" 74.250 1280 1390 1420 1650 720 725 730 750 +hsync +vsync
	Modeline 	"Mode 2" 74.250 1920 2008 2052 2200 1080 1082 1087 1125 +hsync +vsync interlace
	Modeline 	"Mode 3" 27.027 720 736 798 858 480 489 495 525 -hsync -vsync
	Modeline 	"Mode 4" 74.250 1280 1720 1760 1980 720 725 730 750 +hsync +vsync
	Modeline 	"Mode 5" 74.250 1920 2448 2492 2640 1080 1082 1089 1125 +hsync +vsync interlace
	Modeline 	"Mode 6" 27.000 720 732 796 864 576 581 586 625 -hsync -vsync
	Modeline 	"Mode 7" 25.200 640 656 752 800 480 490 492 525 -hsync -vsync
	Modeline 	"Mode 8" 27.027 720 736 798 858 480 489 495 525 -hsync -vsync
	Modeline 	"Mode 9" 27.000 720 732 796 864 576 581 586 625 -hsync -vsync
	Modeline 	"Mode 10" 148.500 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync
	Modeline 	"Mode 11" 148.500 1920 2448 2492 2640 1080 1084 1089 1125 +hsync +vsync
	Modeline 	"Mode 12" 27.000 1440 1464 1590 1728 576 578 581 625 -hsync -vsync interlace
	Modeline 	"Mode 14" 148.50 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync 
	Modeline 	"Mode 15" 85.75 1366 1436 1579 1792 768 771 774 798 +hsync +vsync interlace
	Modeline 	"Mode 16" 298.56 2560 2592 2640 2690 1440 1443 1448 1480 -hsync -vsync 
	Option "PreferredMode" "Mode 13"
EndSection
```

The "Mode 16" seems to be the native resolution of this monitor. But I don't really know how to interpret these results. If it's there, does it mean that X11 should detect that resolution automatically?


> **him610 said:**
> 

From the User Manual for Sceptre Model E248W-QPT IPS 24-Inch QHD 2560x1440, Troubleshooting, pages 26-28....

There are several problems listed with possible solutions - no guarantees though, just suggestions. No mention of Operating Systems as culprit. There is reference to Native Resolution being 1920 x 1080 which means that is what it was optimally designed for.


The manual, [https://www.sceptre.com/pub/Manuals/LEDMONITOR/SCEPTRE%20E248W-QPT-UM.pdf](https://www.sceptre.com/pub/Manuals/LEDMONITOR/SCEPTRE%20E248W-QPT-UM.pdf), later (pag 30) specifies that the native resolution 2560x1440. The 1920 x 1080 must be a typo, most likely they reused the manual from an older model.

---

### Post by TheFu on 2022-04-01
> Option "PreferredMode" "Mode 13"

That will be the default.
If you want something else, see if **lxrandr** will show the mode you want and pick it.

Regardless, seems the EDID stuff isn't the issue.

---

