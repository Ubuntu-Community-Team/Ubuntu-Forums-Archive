---
title: "Finepoint stylus driver on gateway tablet (ubuntu noob)"
date: 2010-06-10
forum: Hardware
---

### Post by jadi929 on 2010-06-10
Just installed ubuntu on my gateway cx2618 tablet today, which i bought for college. Anyway, I need help getting the stylus to work with the touchscreen. 

Here are the contents of my xorg.conf file located in /etc/X11/

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
    Load  "dri"
    Load  "record"
    Load  "extmod"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier    "Finepoint Tablet"
    Driver        "fpit"
    Option        "Device"        "/dev/ttyS0"
    # "BaudRate" may need tweaking (9600, 19200, or 38400).
#    Option        "BaudRate"        "19200"
    # For a passive pen, e.g. Stylistic 3400 use "true".
    Option        "Passive"        "false"
    # To make the touchscreen respond automatically to
    # resolution changes and screen rotation:
    Option        "TrackRandR"
    # Not sure if "SendCoreEvents" line is necessary.
    Option        "SendCoreEvents"    "true"
#    Option        "Buttons"        "2"
    # not sure which button line works or both together?
#    Option        "Button2"        "3"
    # These may need tweaking.
    Option        "MaximumXPosition"    "12550"
    Option        "MaximumYPosition"    "7650"
    Option        "MinimumXPosition"    "400"
    Option        "MinimumYPosition"    "400"
    Option        "InvertY"
EndSection

Section "ServerLayout"
    Identifier    "X.org Configured"
#    Identifier    "Default Layout"
#    Screen        "Default Screen"
    Inputdevice    "Finepoint Tablet"
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
    BoardName   "Mobile 915GM/GMS/910GML Express Graphics Controller"
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


I also installed the fpit driver from synaptics but its not working. Is there anything else I need to do?

---

### Post by Favux on 2010-06-11
Hi jadi929,

I'm guessing you are in Lucid.  Did you try the updated fpit driver in Xupdates?:  [https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/+packages?field.name_filter=&field.status_filter=published&field.series_filter=lucid](https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/+packages?field.name_filter=&field.status_filter=published&field.series_filter=lucid)

Your xorg.conf could use some clean up.

---

### Post by jadi929 on 2010-06-11
yes i have the latest version of fpit drivers, is there any way of verifying that fpit drivers were installed correctly?

---

### Post by Favux on 2010-06-11
Hi jadi929,

> yes i have the latest version of fpit drivers
The 5-19-10 one?
> is there any way of verifying that fpit drivers were installed correctly? 
If there weren't any errors it should be installed correctly.  Assuming you used the deb in Synaptic Package Manager you could Search fpit and then click on it.  Then in Package on the upper right choose Properties.  You could verify the Installed files are present.

Did the deb package install a fpit.conf file in xorg.conf.d?  It would have some prefix number like 90-fpit.conf and probably be in /usr/lib/X11/xorg.conf.d/.  I suppose it might be in /etc/X11/xorg.conf.d/.  And the file should be listed in the Installed files in Synaptic.

---

### Post by jadi929 on 2010-06-11
I did not originally install it from synaptics manager. When I tried to, it would give a list of items to be removed and then gave me a weird error. 



I went to the link u gave and installed it from there. Now in synaptics manager fpit drivers are showing as installed. I went into properties and in installed files, there was no file ending in .conf


So I'm assuming it did not install correctly.

---

### Post by Favux on 2010-06-11
Alright, if you used the deb (you dbl click on it after you download it) you're probably good.

The lack of a fpit.conf file probably just indicates the packager didn't write one.  Rather than writing one ourselves, since you are a newbie, we could just work with your xorg.conf.  Where did you get all the video stuff that is in it.  What is your video chipset?

To find out enter in a terminal:
```
lspci | grep VGA
```

---

### Post by jadi929 on 2010-06-11
> **Favux said:**
> Alright, if you used the deb (you dbl click on it after you download it) you're probably good.

The lack of a fpit.conf file probably just indicates the packager didn't write one.  Rather than writing one ourselves, since you are a newbie, we could just work with your xorg.conf.  Where did you get all the video stuff that is in it.  What is your video chipset?

To find out enter in a terminal:
```
lspci | grep VGA
```
The only thing i put in the xorg was the tablet pc stuff, everything, including the video stuff was in it already.

I have an Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04).

Here is what the xorg looks like right now, I tried to clean it up a bit:

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
        InputDevice    "Tablet"
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
    Load  "dri"
    Load  "record"
    Load  "extmod"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
Identifier "Tablet"
Driver "fpit"
Option "Device" "/dev/ttyS0"
Option "AlwaysCore" "on"
Option "InvertY"
Option "MaximumXPosition" "12550"
Option "MaximumYPosition" "7650"
Option "MinimumXPosition" "400"
Option "MinimumYPosition" "400"
Option "SendCoreEvents"
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
    BoardName   "Mobile 915GM/GMS/910GML Express Graphics Controller"
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

---

### Post by Favux on 2010-06-11
Hi jadi929,

Good, let's see if we can clean it up some more.  Added a couple of Finepoint options too.  I put "ServerLayout" at the end.  Don't want to mess with the video because I think that Intel chipset needs special care and feeding.

As always back up your current working xorg.conf and be prepared to restore it from the command line in case we break X.  If you don't know how ask.

---

### Post by jadi929 on 2010-06-11
got it! well atleast some kind of response, but the cursor goes crazy when i touch it, so it needs some kind of calibration. thanks alot! now where to from here? how do i calibrate it?

---

### Post by Favux on 2010-06-11
Hi jadi929,

Good, some response now is a positive thing.

Don't remember a calibration utility for Finepoint.  Besides are we sure it's calibration you need?

Let's see what Xinput thinks it is seeing:
```
xinput --list
```
and what driver Xorg.0.log says is grabbing the tablet and how well it is doing it.  Xorg.0.log is in /var/log.  You can compress it by right clicking on it and using Create Archive.  Then to post it use Manage Attachments below.

By the way to box code, like xorg.conf, just use the code tags (# above right) and copy and paste your code between them.

---

### Post by jadi929 on 2010-06-12
> **Favux said:**
> Hi jadi929,

Good, some response now is a positive thing.

Don't remember a calibration utility for Finepoint.  Besides are we sure it's calibration you need?

Let's see what Xinput thinks it is seeing:
```
xinput --list
```and what driver Xorg.0.log says is grabbing the tablet and how well it is doing it.  Xorg.0.log is in /var/log.  You can compress it by right clicking on it and using Create Archive.  Then to post it use Manage Attachments below.

By the way to box code, like xorg.conf, just use the code tags (# above right) and copy and paste your code between them.

Here is the input list:

```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; TOUCHSCREEN                                 id=6    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=11    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]
```
Attached is the log you requested.

---

### Post by Favux on 2010-06-12
OK, that's looking good.

At first:
```
   &#8627; TOUCHSCREEN                                 id=6    [slave  pointer  (2)]

```
concerned me because I thought it would say Finepoint Tablet, like we labeled it in xorg.conf.

But the Finepoint driver seems to be loading correctly in Xorg.0.log:
```
(II) LoadModule: "fpit"
(II) Loading /usr/lib/xorg/modules/input/fpit_drv.so
(II) Module fpit: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.3.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
```
and it seems to be grabbing your tablet:
```
(**) TOUCHSCREEN: always reports core events
(**) FPIT device name: TOUCHSCREEN
(**) Fpit associated screen: 0
(**) Option "MaximumXPosition" "12550"
(**) FPIT maximum x position: 12550
(**) Option "MinimumXPosition" "400"
(**) FPIT minimum x position: 400
(**) Option "MaximumYPosition" "7650"
(**) FPIT maximum y position: 7650
(**) Option "MinimumYPosition" "400"
(**) FPIT minimum y position: 400
(**) Option "InvertY"
(**) Option "Passive" "false"
(**) Option "TrackRandR"
(**) FPIT invert X axis: No
(**) FPIT invert Y axis: Yes
(**) FPIT swap X and Y axis: No
(**) FPIT Passive button mode: No
(**) FPIT RandR tracking: Yes
(II) XINPUT: Adding extended input device "TOUCHSCREEN" (type: Fujitsu Stylistic)
(**) Option "Device" "/dev/ttyS0"
(**) Option "BaudRate" "19200"
(**) Option "StopBits" "0"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "10"
(**) Option "Vtime" "1"
(**) Option "FlowControl" "None"
```
Could you describe how the cursor "goes crazy" in a little more detail?  Does the pointer track your stylus?  Does it go to the edges and corners of the screen?  How old is the battery in the stylus?

Maybe it's the baudrate?  From my generic Gateway-CX2724 xorg.conf:
```
	# "BaudRate" may need tweaking (9600, 19200, or 38400).
#	Option		"BaudRate"		"19200"
```
Since Xorg.0.log shows:
```
(**) Option "BaudRate" "19200"
```
you could add the option and try the other two baudrates.

---

### Post by jadi929 on 2010-06-12
well the pointer randomly moves up and down the screen really fast, and also seems to click by itself. Where do u want me to add the baudrate option? in xorg.conf?

---

### Post by Favux on 2010-06-12
Hi jadi929,

> Where do u want me to add the baudrate option? in xorg.conf? 
Correct.  Immediately below the:
```
	Option		"Device"		"/dev/ttyS0"
```
line.  Still curious about the battery.

---

### Post by jadi929 on 2010-06-12
i changed the baudrate to 9600 and now it seems to go to the top right corner of the screen most of the time. as for the battery, i think its pretty old because the actual battery of the laptop is so old it can hardly take a charge. Do u think its related to the battery in the stylus?

---

### Post by Favux on 2010-06-12
Did you try 38400 too?
> Do u think its related to the battery in the stylus? 
I think it's possible (likely?).   Does the stylus work OK in Windows?

My guess is the line that got it responding was:
```
	Option		"Passive"		"false"
```
If it is not a passive stylus, but an active stylus, it is battery powered.

You could also try removing the comment (#) out from in front of these two lines, maybe one at a time?
```
#Option "AlwaysCore" "on"

#Option "SendCoreEvents"
```
But I don't think they are needed anymore with the Xserver 1.7 in Lucid.  And the Xorg.0.log seems to bear that out.  Oh, and you removed the comment out from in front of the baudrate line I'm sure.

---

### Post by jadi929 on 2010-06-12
i bought this used and hd was blank, so directly put ubuntu, but i was told everything works when i bought it. i'll try change the passive to "true" and see what happens.


otherwise, i'll try to install windows xp tablet edition

---

### Post by Favux on 2010-06-12
OK, good luck!

---

### Post by jadi929 on 2010-06-12
no luck :( i'm not trying to go through slip streaming again and install xp, but there has to be a way to configure this stylus

---

### Post by jadi929 on 2010-06-13
update: was able to get xp tablet running and the stylus tracks fine, but clicking does not work. This is strange, clicking worked in ubuntu but no tracking, tracking works in xp but no clicking


Guess its in issue with the stylus

---

### Post by Favux on 2010-06-14
Weird.  I don't know where to go with this other than suggest a new stylus battery and hope that fixes things.

---

### Post by jadi929 on 2010-06-14
yea i'v heard its really difficult, almost impossible to replace the battery, but thanks for all the help

---

### Post by Favux on 2010-06-14
I know that there a places that specialize in that.  I remember another Finepoint user saying he used a place that gave him a good price.  He apparently went through a lot of styli.  I guess you'll need to google.

---

