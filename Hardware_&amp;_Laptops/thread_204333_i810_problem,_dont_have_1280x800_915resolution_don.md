---
title: "i810 problem, dont have 1280x800 915resolution dont work"
date: 2006-06-26
forum: Hardware &amp; Laptops
---

### Post by repolho on 2006-06-26
Hi guys... can someone help-me? :D

im trying to set-up my Acel TravelMate 4101 with a Intel 915GM chipset...

im alredy use 915resolution, 855resolution, and nothing...

here is a part of my /var/log/Xorg.0.log

> 
(II) I810(0): Not using mode "1280x800" (no mode of this name)
(--) I810(0): Virtual size is 1024x768 (pitch 1024)
(**) I810(0):  Built-in mode "1024x768"


---

### Post by coffeecat on 2006-06-27
According to one website, your Acer Travelmate has a screen resolution of 1024x768. What does System > Preferences > Screen Resolution tell you? What problem are you trying to solve?

(Post edited because I posted a load of irrelevant stuff about 1280x800 mode in xorg.conf first time around.)

---

### Post by coffeecat on 2006-06-28
Got a bit confused with my last post. First I noticed the thread title; then I didn't. Let me clarify.

With a native 1024x768 monitor resolution you cannot get 1280x800. Was this what you were trying to do? 1024x768 is 4x3 format. 1280x800 is widescreen - 16x10 format.

---

### Post by repolho on 2006-06-29
no, my monitor resolution is 1280x800 on windows, its a 15.4" and it is widescreen, 
with ubuntu 5.10 when i ran 915resolution, the screen stay in 1280x800, but with 6.06 doesnt work...

tkz
Roberto

---

### Post by xrchris on 2006-06-29
I helped someone the other day with this problem on his Clevo based Rock Pegasus 650 and all that we did was as follows

1 Installed the 915resolution package from the repositories
2 'sudo dpkg-reconfigure xserver-xorg' in terminal
3 Followed the instructions supplied in the Readme file which came with the 915resolution package.
4 rebooted.

It has worked fine since then. 

The wiki for the 915reolution package is at [https://help.ubuntu.com/community/i915Driver](https://help.ubuntu.com/community/i915Driver) but doesnt say much more than i just posted for Dapper.

---

### Post by coffeecat on 2006-06-29
If xrchris's suggestion doesn't work (I'm sure it will :wink:), post back and I'll post the relevant sections of /etc/X11/xorg.conf from my Dapper installation on a Sony Vaio laptop with a 1280x800 WXGA 15.4" display. You could edit them into your xorg.conf.

---

### Post by repolho on 2006-06-29
no, doesnt work :( 

again the same problem
> 
(II) I810(0): Not using mode "1280x800" (no mode of this name)
(--) I810(0): Virtual size is 1024x768 (pitch 1024)



---

### Post by xrchris on 2006-06-29
OK can you run the following code in Terminal

```
sudo gedit /etc/X11/xorg.conf
```

Then copy and paste the contents on here as might be something else missing.

---

### Post by repolho on 2006-06-29
Here is come my xorg.conf


> Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
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
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
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
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        VideoRam        128000
Option "ForceBIOS"      "1920x1440=1280x800"
EndSection
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-72
        VertRefresh     59.0 - 75.0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           1
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           8                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

---

### Post by coffeecat on 2006-06-29
For what it's worth, the relevant sections from my (working) xorg.conf file are below, but I'm not sure it's going to help.. What worries me is that they do not have HorizSync and VertRefresh values. So, if you do edit them into your xorg.conf, you do so at your own risk. One odd thing I notice about your xorg.conf is the default depth in the screen section. Maybe that's a limitation of your lcd screen. That's why I say, use with caution. I'd be interested to read what xrchris says about this.

```
Section "Device"
    Identifier    "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
    Driver        "i810"
    BusID        "PCI:0:2:0"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1280x800"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1280x800"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1280x800"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1280x800"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1280x800"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1280x800"
    EndSubSection
EndSection
```

---

### Post by xrchris on 2006-06-29
OK can you run the following in Terminal and post the info it shows

```
# 915resolution -l
```

---

### Post by xrchris on 2006-06-29
OK forget the above for a moment 

Go to this post [http://ubuntuforums.org/showthread.php?t=205288&page=2](http://ubuntuforums.org/showthread.php?t=205288&page=2) 
and follow EXACTLY the steps listed by maorc and it should resolve your problem. 

Of course make sure that you enter your own personal settings rather than his.

---

### Post by repolho on 2006-07-04
here is i again :( :( i try what did you give xrchris but nothing... here is my 915resolution -l

> Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 915GM
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 36

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel
Mode 60 : 1280x800, 8 bits/pixel
Mode 61 : 1280x800, 16 bits/pixel
Mode 62 : 1280x800, 32 bits/pixel

---

### Post by xrchris on 2006-07-04
If you have followed the instructions posted by maorc and it still wont work then i cannot help you further as thats the limit of my knowledge.

---

### Post by repolho on 2006-07-05
doesnt work... tkz for your time... ill try install ubuntu 5.10 and than do a dist-upgrade... ill post the result here on sunday, tkz a lot for all

---

### Post by xrchris on 2006-07-05
Sometimes its just best to re-install and start from scratch as you can mess a setting up without realising it. 

Good luck.

---

### Post by repolho on 2006-07-05
maybe, but before ubuntu, ive tried kubuntu, and got same problem... with 5.10 de video is ok, but my wireless didnt work... well... ill try... ans post the results here... i just want linux in my laptop :S heheh lol

---

