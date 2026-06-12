---
title: "Frequency Out Of Range (Gateway Monitor)"
date: 2009-08-17
forum: Hardware
---

### Post by TheIdiotThatIsMe on 2009-08-17
Hi guys. I'm getting really frustrated so I'm hoping you can help me. I have a Gateway monitor that is a Gateway FPD1765 17in LCD. I've gotten Ubuntu completely up and running, except I had to use another monitor to get it so because everytime I attach this monitor, I get an error right after the booting screen that simply says Frequency Out Of Range. I looked up a couple of different solutions, and none have seemed to work so far. I edited xorg.conf to try and use the frequency ranges provided by Gateway (they say should use 1280x1024 using 60Hz frequency). The following is my xorg.conf file:

```
Section "Monitor"
	Identifier	"Configured Monitor"
	HorizSync	58-68
	VertRefresh	55-65
	Modeline "1280x1024" 109.62  1280 1336 1472 1720  1024 1024 1026 1062
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
```

---

### Post by Vakman on 2009-08-17
Currently, are you posting from that machine with another monitor or are you in low-graphics mode? Or...? Also can you confirm your drivers are installed correctly? Or is this a fresh install. If you like you can reset to the default by ```
sudo dpkg-reconfigure xserver-xorg
``` and then we can go from there. Lastly, what graphics card do you have? It is nVIDIA but I am wondering what card exactly.

---

### Post by ajgreeny on 2009-08-17
Unfortunately the command suggested by Thisislaw does not do anything with the new xorg versions we are using in ubuntu, so don't bother with that.

Your xorg.conf is similar to one I had to produce to get intrepid to work properly, but just a little different in the placing of the resolution data.  Here's mine which worked very well, when the default produced on install gave me wrong resolutions, and no chance to get the one I needed.
```
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
            HorizSync    30-80
            VertRefresh    50-75
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    SubSection "Display"
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection
```Use your own resolution figures of course and refresh rates, leave your driver info as well, and see if it works better than your manual edit.

---

### Post by Vakman on 2009-08-18
> **ajgreeny said:**
> Unfortunately the command suggested by Thisislaw does not do anything with the new xorg versions we are using in ubuntu, so don't bother with that.
Will debate this after :P

---

