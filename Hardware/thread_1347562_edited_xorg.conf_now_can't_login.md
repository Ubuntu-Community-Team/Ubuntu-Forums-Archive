---
title: "edited xorg.conf now can't login"
date: 2009-12-06
forum: Hardware
---

### Post by benjamonk on 2009-12-06
Hi

I've been trying to get past karmic restricting my screen resolution to 800x600 when my laptop's native resolution is 1024x768. In other words, only half the screen was used and I got a big black border all around the ubuntu desktop.

I had no xorg.conf file in /etx/X11 so had to create one.

I amended it to add the resolution I wanted and rebooted. I thought I had cracked it because the login screen came up full screen and i thought 'Fantastic!!'.

Except I now can't login in - everytime I try I get an error message 'locked out' and then get taken back to the login screen.

The only way I got back in at all was to go the the Shell and rename the xorg.conf file to xorg.fail - Since doing this, I can log back in so this must be something to do with the xorg.conf file !?

I've pasted my xorg.conf file below - can anyone see anything that may be causing this problem?

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "glx"
    Load  "dri2"
    Load  "dbe"
    Load  "record"
    Load  "extmod"
    Load  "dri"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier "Monitor0"
    VendorName "Monitor Vendor"
    ModelName "Monitor Model"
    HorizSync 31.5 - 50
    VertRefresh 50-110
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "CacheLines"             # <i>
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "DRI"                    # [<bool>]
        #Option     "NoDDC"                  # [<bool>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "XvMCSurfaces"           # <i>
        #Option     "PageFlip"               # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    VendorName  "Intel Corporation"
    BoardName   "82815 Chipset Graphics Controller (CGC)"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Depth        1
        Viewport 0 0
        Modes      "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        4
        Viewport 0 0
        Modes      "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        8
        Viewport 0 0
        Modes      "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        16
        Viewport 0 0
        Modes      "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        24
        Viewport 0 0
        Modes      "1024x768"
    EndSubSection
EndSection

---

### Post by jocko on 2009-12-06
Try making your xorg.conf a little bit less complicated.
Try this:
First back up your existing xorg.conf (if you have one):
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
Then make a new, less complicated one:
```
gksudo gedit /etc/X11/xorg.conf
```
Paste this into it:
```
Section "ServerLayout"
    Identifier "X.org Configured"
    Screen 0 "Screen0" 0 0
EndSection


Section "Monitor"
    Identifier "Monitor0"
    VendorName "Monitor Vendor"
    ModelName "Monitor Model"
[COLOR="Blue"]    HorizSync 31.5 - 50
    VertRefresh 50-110[/COLOR]
EndSection

Section "Device"
    Identifier "Card0"
    Driver "intel"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device "Card0"
    Monitor "Monitor0"
EndSection
```
Make sure you double-check that the HorizSync and VertRefresh values really match the ones for your monitor (read your monitor's full specs in the manual, which you can probably find on the manufacturer's webpage).
Save the file and restart xorg:
```
sudo service gdm restart
```

---

### Post by benjamonk on 2009-12-06
Tried that!

Unfortunately the xorg.conf file you suggested caused the system to crash. On there plus side, there were some very pretty colours involved....

I dunno. Must be somethign to do with the .conf file...

Any more ideas?

---

### Post by jocko on 2009-12-06
Apparently something is wrong with your xorg.conf.
Are you sure the intel driver is the correct driver for your card?
Are you sure about the refresh and sync ranges of your monitor?

When xorg crashes, can you get to a terminal (try ctrl+alt+F1)?
In that case, copy the xorg log file to your home directory:
```
cp /var/log/Xorg.0.log $HOME/Xorg.0.log.txt
```
Then remove the xorg.conf, and restart gdm:
```
sudo rm /etc/X11/xorg.conf
sudo service gdm restart
```
Log in and attach the log file to a post. Hopefully it contains some clues to why it crashes.

---

### Post by benjamonk on 2009-12-07
Here is the log file - let me know if you spot anything!

---

### Post by benjamonk on 2009-12-07
What I don't understand is this.

Here is my original xorg.conf file which I created by using the comand ```
sudo  xorg -configure
``````
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "glx"
    Load  "dri2"
    Load  "dbe"
    Load  "record"
    Load  "extmod"
    Load  "dri"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "CacheLines"             # <i>
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "DRI"                    # [<bool>]
        #Option     "NoDDC"                  # [<bool>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "XvMCSurfaces"           # <i>
        #Option     "PageFlip"               # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    VendorName  "Intel Corporation"
    BoardName   "82815 Chipset Graphics Controller (CGC)"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```Now that file there, (above) this original one boots fine, but doesn't give me the 1024x768 resolution I need. 

So, I tried to amend it (below) to force the 1024x768 resolution - Now it sort of does because the login screen comes up in glorious full screen 1024x768 - But I can't get past the login screen!!!! There most be something in this amended .conf file that is upsetting things.....

```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "glx"
    Load  "dri2"
    Load  "dbe"
    Load  "record"
    Load  "extmod"
    Load  "dri"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier "Monitor0"
    VendorName "Monitor Vendor"
    ModelName "Monitor Model"
    HorizSync 31.5 - 50
    VertRefresh 50-110
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "CacheLines"             # <i>
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "DRI"                    # [<bool>]
        #Option     "NoDDC"                  # [<bool>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "XvMCSurfaces"           # <i>
        #Option     "PageFlip"               # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    VendorName  "Intel Corporation"
    BoardName   "82815 Chipset Graphics Controller (CGC)"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Depth        1
        Viewport 0 0
        Modes      "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        4
        Viewport 0 0
        Modes      "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        8
        Viewport 0 0
        Modes      "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        16
        Viewport 0 0
        Modes      "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        24
        Viewport 0 0
        Modes      "1024x768"
    EndSubSection
EndSection
```

---

### Post by realzippy on 2009-12-07
Try using that running xorg.conf an adding desired 1024x768 by xrandr...

[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)

..or post output from:

**xrandr**

 and

**cvt 1024 768 60**

---

### Post by benjamonk on 2009-12-07
> **jocko said:**
> Apparently something is wrong with your xorg.conf.
Are you sure the intel driver is the correct driver for your card?
Are you sure about the refresh and sync ranges of your monitor?


I have a Sony VAIO PCG-QR20 - this machine has the following chipset: 
'Intel 815EM chipset integrated graphic'
LCD Screen is 13.3" XGA ( 1024x768 ) TFT

I've searched the web for details about refresh and sync ranges but not found confirmation - Found this datasheet but cont find sync and refresh rates?
[http://www.datasheetarchive.com/datasheet-pdf/04/DSA0058090.html]("http://www.datasheetarchive.com/datasheet-pdf/04/DSA0058090.html")

---

### Post by benjamonk on 2009-12-07
> **realzippy said:**
> Try using that running xorg.conf an adding desired 1024x768 by xrandr...

[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)

..or post output from:

**xrandr**

 and

**cvt 1024 768 60**

Sorry - I'm very new to all this (I've been a Windows ludite for years i'm afraid).

Do you want me to put the ORIGINAL of those two xorg.conf files back in place, the restart, and then enter the commands xrandr and cvt 1024 768 60 and post the outputs?

Sorry...

---

### Post by realzippy on 2009-12-07
Yes,you have to be logged in ..
(take running one..or rename or delete current xorg.conf)

Edit.:

parallel thread??
[http://ubuntuforums.org/showthread.php?p=8451899](http://ubuntuforums.org/showthread.php?p=8451899)

---

### Post by benjamonk on 2009-12-07
OK - So have put the ORIGINAL xorg.conf file back in place in /etc/X11/xorg.conf

Here are the outputs from xrandr:
```
ben@Ubuntu-Bag:~$ xrandr
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
ben@Ubuntu-Bag:~$ cvt 1024 768 60
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
ben@Ubuntu-Bag:~$ 

```

I then tried:
```
xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync

```
and then
```
xrandr --addmode default 1024x768_60.00
```
and finally
```
xrandr -s 1024x768
```

But I get the error message:'Failed to change the screen configuration!'

---

### Post by benjamonk on 2009-12-07
> **realzippy said:**
> Yes,you have to be logged in ..
(take running one..or rename or delete current xorg.conf)

Edit.:

parallel thread??
[http://ubuntuforums.org/showthread.php?p=8451899](http://ubuntuforums.org/showthread.php?p=8451899)

Yes - sorry got in a bit of a mess - I'll stick to this one!

---

### Post by realzippy on 2009-12-07
**xrandr --output default --mode 1024x768_60.00**

??

might be the same error.
Try this xorg.conf file:
   --
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	HorizSync	31-60
	VertRefresh	60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	16
	SubSection	"Display"
	Depth		16
	Modes		"1024x768"
	EndSubSection
	SubSection	"Display"
	Depth		24
	Modes		"1024x768"
	EndSubSection
EndSection

---

### Post by benjamonk on 2009-12-07
sorry, again, just to be clear.

Should is use just the lines you've included here? or should i just replace the device, monitor & screen sections of my file?

---

### Post by benjamonk on 2009-12-07
> **realzippy said:**
> **xrandr --output default --mode 1024x768_60.00**

??

might be the same error.
Try this xorg.conf file:
   --
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	HorizSync	31-60
	VertRefresh	60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	16
	SubSection	"Display"
	Depth		16
	Modes		"1024x768"
	EndSubSection
	SubSection	"Display"
	Depth		24
	Modes		"1024x768"
	EndSubSection
EndSection

Tried the file you suggested above - just the lines you included,  and nothing else. I got the same result as my amended xorg.conf file listed earlier in this post :-(

That is to say login screen comes up in 1024x768 (full screen) but when I enter my login details, the resolution pops back to 800x600 and then shell pops up for a second before my machine restarts. So the only way I can log on now is to break into shell, and either delete the .conf or rename it to .fail

Bummer.

---

### Post by realzippy on 2009-12-07
this one:?
[http://ubuntuforums.org/showpost.php?p=6489466&postcount=3](http://ubuntuforums.org/showpost.php?p=6489466&postcount=3)

sorry,no more idea....

---

### Post by benjamonk on 2009-12-07
Interesting....

If I change the depths in the file you gave me:

from
depth 16
depth 16
depth 24

to
depth 8
depth 8
depth 16

it does log into Gnome, as you would expect in crap qaulity - It still reverts however back to 800x600 with a big black border all around the screen - This is after the login screen was 'full screen' 1024x768

So could this be a memory issue?

I'm baffled

---

### Post by benjamonk on 2009-12-07
Could this be a memory problem if it's affected by 'depth'

I think I have 256k on board (but can't remember)

is $ free the right command to use to find out?
```

ben@Ubuntu-Bag:~$ free
             total       used       free     shared    buffers     cached
Mem:        249176     244772       4404          0      10464      70444
-/+ buffers/cache:     163864      85312
Swap:       465844      11524     454320
```

---

### Post by jocko on 2009-12-08
> **benjamonk said:**
> Here is the log file - let me know if you spot anything!
Nothing wrong there. Looks like the xorg started just fine, no crash there (not xorg anyway).

It claims it ran at "*Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz"...

Exactly what do you mean when you say it crashed?
Was it just that you lost the display?
That could mean that you are trying to run your monitor at a refresh rate / resolution combination it can't handle, which usually turns off the monitor to prevent damage (or switches to a lower resolution). This is most likely caused by trying horizontal sync or vertical refresh ranges that your monitor doesn't support.
So what happens if you remove the HorizSync and VertRefresh lines completely and let xorg detect your monitor instead? You could try that both with your original xorg.conf and the simplified from my post. If that doesn't work you really need to find the correct values for your monitor.

---

### Post by jocko on 2009-12-08
> **benjamonk said:**
> Could this be a memory problem if it's affected by 'depth'

I think I have 256k on board (but can't remember)

is $ free the right command to use to find out?
```

ben@Ubuntu-Bag:~$ free
             total       used       free     shared    buffers     cached
Mem:        249176     244772       4404          0      10464      70444
-/+ buffers/cache:     163864      85312
Swap:       465844      11524     454320
```
You mean 256mb, not kb. According to your log the video card has 200mb, which should be more than enough to run 1024x768 at 24 bits per pixel.

---

### Post by realzippy on 2009-12-08
Are the desktop effects enabled?If so,disable them...

---

### Post by benjamonk on 2009-12-08
> **realzippy said:**
> Are the desktop effekts enabled?If so,disable them...

NO - first thing I did was disable desktop effects.

---

### Post by realzippy on 2009-12-08
And did you try 2. xorg.conf:

[http://ubuntuforums.org/showpost.php?p=6489466&postcount=3](http://ubuntuforums.org/showpost.php?p=6489466&postcount=3)
?

---

### Post by benjamonk on 2009-12-08
> **realzippy said:**
> And did you try 2. xorg.conf:

[http://ubuntuforums.org/showpost.php?p=6489466&postcount=3](http://ubuntuforums.org/showpost.php?p=6489466&postcount=3)
?

Just tried the suggested xorg.conf same result:

Login screen loads in full screen 1024x768 then when I enter login details, the screen flips back to 800x600 and then after  a few seconds, shell flicks up an error message for a nano seconf before the login screen appears again, in full screen mode.

---

### Post by realzippy on 2009-12-08
Open that xorg and change:

[I]Option "UseEdidFreqs" "1"
[/I]
to

*Option "UseEdidFreqs" "[COLOR="Lime"]0[/COLOR]"*

to ignore Monitor's EDID....any changes?

---

### Post by benjamonk on 2009-12-08
> **jocko said:**
> 
Exactly what do you mean when you say it crashed?
Was it just that you lost the display?


This is what happens.

with no xorg.conf in place, OR the original xorg.conf file I created using 'sudo Xorg -configure' when I boot the machine the login screen comes up in 800x600 with a black border all around it. I login, and ubuntu loads but in 800x600. Everything works fine in the system, but this resolution is unworkable to the user (me). 

However, if I amend the xorg.conf file to get a resolution of 1024x768 and restart, I get the ubuntu login screen in full screen 1024x768 but when I enter my login details, the screen resolution flicks back to 800x600 with a big border all around the screen, then i see the shell prompt with a 'locked out' error message for a second, the the ubutnu login screen is loaded again in 1024x768. The only way to break that cycle is to break into Shell and 'rm' the xorg.conf file.

---

### Post by benjamonk on 2009-12-08
> **realzippy said:**
> Open that xorg and change:

[I]Option "UseEdidFreqs" "1"
[/I]
to

*Option "UseEdidFreqs" "[COLOR="Lime"]0[/COLOR]"*

to ignore Monitor's EDID....any changes?

I tried that - I'm now getting Ubuntu running in low graphics mode

---

### Post by benjamonk on 2009-12-08
> **jocko said:**
> 
So what happens if you remove the HorizSync and VertRefresh lines completely and let xorg detect your monitor instead? You could try that both with your original xorg.conf and the simplified from my post.

On both occasions login screen comes up in 800x600 - I enter my login details and ubuntu comes up in 800x600.....

Also, i read that $ ddcprobe would identify horiz / vert rates? here is that output:
ben@Ubuntu-Bag:~$ sudo ddcprobe
vbe: VESA 3.0 detected.
oem: Intel815M(TM) Graphics Chip Accelerated VGA BIOS
vendor: Intel Corporation
product: i815M Graphics Controller Hardware Version 0.0
memory: 1024kb
mode: 1280x1024x256
mode: 640x480x16m
mode: 800x600x16m
mode: 1024x768x32k
mode: 1024x768x64k
mode: 640x400x256
mode: 640x480x256
mode: 800x600x16
mode: 800x600x256
mode: 1024x768x256
mode: 640x480x32k
mode: 640x480x64k
mode: 640x480x16m
mode: 800x600x32k
mode: 800x600x64k
edid: 
edidfail

edidfail? [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/194760](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/194760)

---

### Post by realzippy on 2009-12-08
[I]this one from german forum,similar problem,...
[/I]
Section "Device"
        Identifier      "Intel"
        Driver          "intel"
EndSection

Section "Monitor"
	Identifier	"Laptop Monitor"
	Option		"DPMS"
	DisplaySize	1024 768
	HorizSync	30.0-82.0
	VertRefresh	50.0-75.0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel"
        Monitor         "Laptop Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
EndSection

*If it should work,try setting depth from "16" to "24"...*

---

### Post by benjamonk on 2009-12-08
> **realzippy said:**
> [I]this one from german forum,similar problem,...
[/I]
Section "Device"
        Identifier      "Intel"
        Driver          "intel"
EndSection

Section "Monitor"
	Identifier	"Laptop Monitor"
	Option		"DPMS"
	DisplaySize	1024 768
	HorizSync	30.0-82.0
	VertRefresh	50.0-75.0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel"
        Monitor         "Laptop Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
EndSection

*If it should work,try setting depth from "16" to "24"...*

No luck I'm afraid - I'f I drop down to a depth of 8, I log into ubuntu instead of crashing / restarting but it's still in 800x600

---

### Post by benjamonk on 2009-12-08
Would there be different results in Kubuntu do you think???????

---

### Post by realzippy on 2009-12-08
> **benjamonk said:**
> Would there be different results in Kubuntu do you think???????

No.Could you please test one last thing?
I merged your original xorg.conf with the "vesa" driver.See if
this runs:


Section "ServerLayout"
Identifier "single head configuration"
Screen 0 "Screen0" 0 0
InputDevice "Mouse0" "CorePointer"
InputDevice "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
ModulePath "/usr/lib/xorg/modules"
FontPath "/usr/share/fonts/X11/misc"
FontPath "/usr/share/fonts/X11/cyrillic"
FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
FontPath "/usr/share/fonts/X11/Type1"
FontPath "/usr/share/fonts/X11/100dpi"
FontPath "/usr/share/fonts/X11/75dpi"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
FontPath "built-ins"
EndSection

Section "Module"
Load "glx"
Load "dri2"
Load "dbe"
Load "record"
Load "extmod"
Load "dri"
EndSection

Section "InputDevice"
Identifier "Keyboard0"
Driver "kbd"
EndSection

Section "InputDevice"
Identifier "Mouse0"
Driver "mouse"
Option "Protocol" "auto"
Option "Device" "/dev/input/mice"
Option "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
Identifier "Monitor0"
VendorName "Monitor Vendor"
ModelName "Monitor Model"
HorizSync 31.5 - 50
VertRefresh 50-110
EndSection

Section "Device"
Identifier "Card0"
    Driver      "vesa"
    VendorName  "Videocard vendor"
    BoardName   "VESA driver (generic)"
    BusID "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Videocard0"
    Monitor    "Monitor0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     16
        Modes    "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Modes    "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "DRI"
	     Mode 0666
EndSection

---

### Post by benjamonk on 2009-12-09
> **realzippy said:**
> No.Could you please test one last thing?
I merged your original xorg.conf with the "vesa" driver.
EndSection
 
Thanks - i'll try that later when I am back at home.

---

### Post by benjamonk on 2009-12-09
> **realzippy said:**
> No.Could you please test one last thing?
I merged your original xorg.conf with the "vesa" driver.
EndSection

Hmmmm. This one didn't go so well. I now can't boot up, or break into shell to remove the xorg.conf file...

Should of sticking the LiveCD and doing a total re-install i think I may be stuck.

Oh well, maybe I'll try Crunch Bang!

Any way, I've really appreciate you trying to help. I'm pretty much out of ideas.

---

### Post by realzippy on 2009-12-09
*I now can't boot up*

...you can always boot in recovery mode and rm the file..or delete it from a LiveCD.Sorry...


...about reinstalling:

You should try 8.04 LTS.Or 8.10.The Intel problem started with 9.04...

---

