---
title: "Xorg settings for LCD monitor"
date: 2005-05-19
forum: Hardware &amp; Laptops
---

### Post by reuben on 2005-05-19
I have a 19" sony lcd monitor; the xorg section reads:

Section "Monitor"
        Identifier      "A90f+"
        Option          "DPMS"
        HorizSync 31.5 - 70
        VertRefresh 40-60
EndSection


However, when I log into KDE, it is running at 1280x1024 @ 75hz, which is higher than the above would seem to indicate is possible. It is a little unsharp, so I would like to get it down to the recommended 60hz to see if anything changes.

Also, when I run dpkg-reconfigure xserver-xorg, it drops me into text mode and can't recover when it autochecks for the monitor.

Ideas?

---

### Post by gray-squirrel on 2005-05-20
If you want to use 60 Hz for the refresh rate, and nothing else, you can open a terminal window and type

```
gtf  1280 1024 60

```


You will be presented with one or more modelines.  When I tried to get my resolution settings and refresh rate fixed, I used gtf for a 1024 x 768 screen and got the following:

```

# 1024x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 64.11 MHz
  Modeline "1024x768_60.00"  64.11  1024 1080 1184 1344 768 769 772 795  -HSync +Vsync

```


You will of course have something different.

If you get one response (like I did), just copy and paste it (it's two lines) into the xorg.conf file, in the Monitor section right below the Vertfresh line.  It should look something like this:


```
Section "Monitor"
	Identifier	"565"
	Option		"DPMS"
	HorizSync	30-61
	VertRefresh	59-75
          # 1024x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 64.11 MHz
  Modeline "1024x768_60.00"  64.11  1024 1080 1184 1344 768 769 772 795  -HSync +Vsync
EndSection

```


Then, save the file, close the windows, and use Ctrl-Alt-Backspace to restart.

If gtf gives you more than one response, just test each one separately to see which one works best for you.

I'm surprised that the computer would select a refresh rate which is out of range of what you specified in xorg.conf.  Even when before I had to switch video drivers to force a change in resolution and refresh rates and get a clean screen, my computer never set anything to value outside the range of anything specified in xorg.conf.

Give it a try, let us know how it works.

---

### Post by reuben on 2005-05-23
[QUOTE=gray-squirrel]If you want to use 60 Hz for the refresh rate, and nothing else, you can open a terminal window and type

```
gtf  1280 1024 60

```
[/QUOTE]

Hello, good command to know about but unfortunately didn't work (KDE believes that it is running at 75hz, at least  according to the desktop settings tool...is there another way to check?). My complete xorg.conf is below...is there something incorrect within?



Section "Files"
        FontPath        "unix/:7100"                    # local font server
        # if the local font server has problems, we can fall back on these
        FontPath        "/usr/lib/X11/fonts/misc"
        FontPath        "/usr/lib/X11/fonts/cyrillic"
        FontPath        "/usr/lib/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/Type1"
        FontPath        "/usr/lib/X11/fonts/CID"
        FontPath        "/usr/lib/X11/fonts/100dpi"
        FontPath        "/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "keyboard"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "Device"
        Identifier      "Intel Corporation 82865G Integrated Graphics Device"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        VideoRam        128000
EndSection

Section "Monitor"
        Identifier      "A90f+"
        Option          "DPMS"
        HorizSync 31.5 - 70
        VertRefresh 40-60
        # 1280x1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 108.88 MHz
        Modeline "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync

EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82865G Integrated Graphics Device"
        Monitor         "A90f+"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1200x800" "1152x864" "1024x768" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1200x800" "1152x864" "1024x768" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1200x800" "1152x864" "1024x768" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1200x800" "1152x864" "1024x768" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1200x800" "1152x864" "1024x768" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1200x800" "1152x864" "1024x768" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection

---

### Post by gray-squirrel on 2005-05-24
It could be your driver selection.  I have a VIA S3/UniChrome graphics card on the system board, and the driver which was installed during my upgrade to 5.04 apparently messed the screen resolution and refresh rate up.  I switched to the VESA driver and everything has been fine since.

Just out of curiosity, what does your Xorg.0.log file say?  Sometimes we can find a clue as to why the proper refresh rate isn't being used in that file.

---

### Post by joliver12 on 2005-05-30
Any updates?  I appear to be having the same problem with my LCD monitor.  No problemo using my old CRT.

John

---

