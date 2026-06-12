---
title: "Problem resolution in ubuntu 10.04.4 LTS with nvidia GT520 in HDMI"
date: 2012-04-14
forum: Hardware
---

### Post by turkosbon on 2012-04-14
i have nvidia GT520 Low Profile and driver version 295.33. I have TV phillips connect with HDMI.  My resolution in ubuntu 1280x768. 
Howto change resolution 1920x1080.

EDID for my FLAT TV
> 
 --- Modes in ModePool for Philips (DFP-1) ---
 "nvidia-auto-select" : 1280 x  768 @  60.0 Hz  (from: EDID)
 "1920x1080"          : 1920 x 1080 @  60.1 Hz Interlace  (from: EDID)
 "1920x1080_60i"      : 1920 x 1080 @  60.1 Hz Interlace  (from: EDID)
 "1920x1080_60i_0"    : 1920 x 1080 @ 59.94/60 Hz (CEA-861B Format 5) (from: EDID)
 "1920x1080_50i"      : 1920 x 1080 @  50.0 Hz Interlace  (from: EDID)
 "1280x768"           : 1280 x  768 @  60.0 Hz  (from: EDID)
 "1280x768_60"        : 1280 x  768 @  60.0 Hz  (from: EDID)
 "1280x720"           : 1280 x  720 @  60.0 Hz  (from: EDID)
 "1280x720_60"        : 1280 x  720 @  60.0 Hz  (from: EDID)
 "1280x720_60_0"      : 1280 x  720 @ 59.94/60 Hz (CEA-861B Format 4) (from: EDID)
 "1280x720_50"        : 1280 x  720 @  50.0 Hz  (from: EDID)
 "1152x648"           : 1152 x  648 @  75.0 Hz  (from: EDID)
 "1152x648_75"        : 1152 x  648 @  75.0 Hz  (from: EDID)
 "1024x768"           : 1024 x  768 @  75.0 Hz  (from: EDID)
 "1024x768_75"        : 1024 x  768 @  75.0 Hz  (from: EDID)
 "1024x768_60"        : 1024 x  768 @  60.0 Hz  (from: EDID)
 "1024x576"           : 1024 x  576 @  85.0 Hz  (from: EDID)
 "1024x576_85"        : 1024 x  576 @  85.0 Hz  (from: EDID)
 "800x600"            :  800 x  600 @  75.0 Hz  (from: EDID)
 "800x600_75"         :  800 x  600 @  75.0 Hz  (from: EDID)
 "800x600_60"         :  800 x  600 @  60.3 Hz  (from: EDID)
 "800x450"            :  800 x  450 @  85.0 Hz  (from: EDID)
 "800x450_85"         :  800 x  450 @  85.0 Hz  (from: EDID)
 "720x576"            :  720 x  576 @  50.0 Hz  (from: EDID)
 "720x576_50"         :  720 x  576 @  50.0 Hz  (from: EDID)
 "720x480"            :  720 x  480 @  59.9 Hz  (from: EDID)
 "720x480_60"         :  720 x  480 @  59.9 Hz  (from: EDID)
 "640x480"            :  640 x  480 @  75.0 Hz  (from: EDID)
 "640x480_75"         :  640 x  480 @  75.0 Hz  (from: EDID)
 "640x480_60"         :  640 x  480 @  60.0 Hz  (from: EDID)
 "640x480_60_0"       :  640 x  480 @ 59.94/60 Hz Interlace (CEA-861B Format 1) (from: EDID)
 "640x360"            :  640 x  360 @  85.0 Hz  (from: EDID)
 "640x360_85"         :  640 x  360 @  85.0 Hz  (from: EDID)
 --- End of ModePool for Philips (DFP-1): ---


---

### Post by papibe on 2012-04-14
Hi turkosbon.

Have you tried using 'Nvidia X Server Settings'?

If so, what problems did you encounter?

Regards.

---

### Post by turkosbon on 2012-04-14
yes and this it's my xorg.conf and attache screen nviadia-settings

> 
Section "Device"
        Identifier "nvidia"
        Driver  "nvidia"
        Option  "NoLogo"              "true"
        Option  "DynamicTwinView"     "false"
        Option  "FlatPanelProperties" "Scaling = Native"
        Option  "ModeValidation"      "NoVesaModes, NoXServerModes, NoVertRefreshCheck, NoHorizSyncCheck"
        Option  "UseDisplayDevice"    "DFP-1"
        Option  "ModeDebug"           "true"
    Option  "HWCursor"            "false"
EndSection

Section "Screen"
        Identifier      "screen"
        Device          "nvidia"
        SubSection      "Display"
        Modes           "1920x1080_60"
        EndSubSection
EndSection

Section "Extensions"
        Option  "Composite"           "false"
EndSection



---

### Post by efflandt on 2012-04-14
What Ubuntu version are you using. Your (X) Server Vender Version is 1.7.6 and mine in 11.10 is 1.10.4, but versions of everything else are the same.

How did you install nvidia drivers.  Did you do it the easy way using **Additional Drivers** (with or without x-swat repository added), so everything is compatible and coordinated to update properly? Or did you manually download something from nvidia website and do it the hard way (which may require reinstall after kernel updates)?

My xorg.conf could not be much simpler (the default when installed using Additional Drivers):

```
Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
EndSection
```

Something is not right, because in your X Server Display Settings, **Configuration** says **Disabled**, and **Resolution** setting is missing. It should look more like mine.

---

### Post by turkosbon on 2012-04-14
efflandt i have Ubuntu 10.04.4 LTS i386. with xbmc, and try to quit judder efect. i try playback at 23.97 or 59.94 Hz with NVIDIA GPU hardware.

well i try test in another HDD but same pc to install nvidia with  x-swat repository.

---

### Post by papibe on 2012-04-14
I would say let's keep it simple: let's try first to get the resolution fixed, and then take care of of other problems. This is what I do:

Backup your conf file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
Then generate a new one:
```
sudo nvidia-xconfig
```
Then restart the machine, and check 'Nvidia X Server Settings' to see if the 1080i resolution is available.

If that doesn't work, please paste your /var/log/Xorg.0.log file here: [http://paste.ubuntu.com/]("http://paste.ubuntu.com/"), and post back the link so we can take a look.

Regards.

---

### Post by rhss6-2011 on 2012-04-14
Copied from another post of mine...


Hello there,
I made a guide for such issues and you can find it here:

[http://forums.debian.net/viewtopic.php?f=16&t=78330](http://forums.debian.net/viewtopic.php?f=16&t=78330)

Also, at the very bottom of the post is a list of resolutions that computers recognize...

Hope it helps!


-----
Just use the same guidlines for the different resolutions... I hooked one of my laptops up to a flatscreen and it worked fine with the steps I wrote down...

---

### Post by turkosbon on 2012-04-15
hello thank you for alll, but i think the problem it's TV phillips 32" model 32PF5531D, because this model HD LCD WXGA display, with a 1366 x 768p resolution and HD Ready

> 
HD Ready
Enjoy the exceptional picture quality of High Definition pictures and be fully prepared for
HD sources like HDTV settop box or Blu-ray disc. HD Ready is a protected label that offers picture quality beyond that of progressive scan. It conforms to strict standards laid out by EICTA to offer a HD screen that displays the benefits of resolution and picture quality of a High Definition signal. It has a universal connection for both analog YPbPr and uncompressed Digital connection of DVI or HDMI, supporting HDCP. It can display 720p,
and 1080i signals at 50 and 60Hz.


well i remove my xorg.conf and excecute "nvidia-xconfig"

> 
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 295.33  (buildmeister@swio-display-x86-rhel47-06.nvidia.com)  Sat Mar 17 16:01:53 PDT 2012

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


i force 1920x1080 but top bar and down bar i can't see.

---

### Post by papibe on 2012-04-15
That may be another problem: [Overscan]("http://en.wikipedia.org/wiki/Overscan")

If so, you have 2 options to solve it:

First (recommended): Some TV's have the ability to set how the signal is reproduced. In case of my Sony Bravia you can fix it by setting 'Full Pixel' to Screen -> Display Area. In my brother's Samsung you would set the attribute P.size to 'Full Scan' ( in the Picture Options -> Screen Size menu if I remember correctly).

Play with the options available on your TV, may be the option is not easy to see. Check your manual or research about it on the Internet.

Second: the 'Nvidia X Server Settings' has an option to correct overscan manually. Check [this]("http://smartsoftwarefactory.blogspot.com/2011/01/correct-tv-overscan-using-ubuntu-nvidia.html") article.

Tell us how it goes,
Regards.

---

### Post by turkosbon on 2012-04-16
thank you. but i think that overscan manually it's only option.

---

