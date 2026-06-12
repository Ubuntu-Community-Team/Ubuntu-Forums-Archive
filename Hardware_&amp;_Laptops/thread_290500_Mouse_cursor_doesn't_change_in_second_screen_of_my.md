---
title: "Mouse cursor doesn't change in second screen of my dual-head setup."
date: 2006-11-01
forum: Hardware &amp; Laptops
---

### Post by sgarman on 2006-11-01
Hi there,

I did a clean install of Edgy on my workstation which was previously working fine with Dapper in dual-head mode. My video card is an ATI X300, so it was not detected during the install and I had to grab the fglrx driver and get that installed and working before I could configure X. 

Using the following xorg.conf file, I am back to running in dual-head mode. Everything works fine except for one issue. Only in my Secondary Screen (see xorg.conf file), my mouse cursor will not change when dragging a window. 

For example:

1. If I move a window from the primary screen to the secondary screen, the mouse cursor remains a hand until I move the mouse back into the primary screen.

2. If I start moving a window in the secondary screen, it never changes into a hand, unless I move the window into the primary screen.

3. When trying to resize windows in the secondary screen, the cursor doesn't change and is not correctly aligned with the edge of the window, so resizing windows in the secondary screen is difficult to do.

The mouse cursor changes as expected in the primary screen. 

I've done some searches but can't seem to find anyone else with this problem. Any suggestions?

Thanks,

Scott

My xorg.conf file:

```

Section "Files"

        # path to defoma fonts
        FontPath     "/usr/share/X11/fonts/misc"
        FontPath     "/usr/share/X11/fonts/cyrillic"
        FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/Type1"
        FontPath     "/usr/share/X11/fonts/100dpi"
        FontPath     "/usr/share/X11/fonts/75dpi"
        FontPath     "/usr/share/fonts/X11/misc"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load  "i2c"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "type1"
        Load  "vbe"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us"
        Option      "XkbOptions" "lv3:ralt_switch"
EndSection

       Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
        Option      "ZAxisMapping" "4 5"
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. RV370 5B60 [Radeon X300 (PCIE)] 1"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
        Screen          0
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. RV370 5B60 [Radeon X300 (PCIE)] 2"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
        Screen          1
EndSection

Section "Monitor"
        Identifier      "HP L1902 1"
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "HP L1902 2"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier "Primary Screen"
        Device     "ATI Technologies, Inc. RV370 5B60 [Radeon X300 (PCIE)] 1"
        Monitor    "HP L1902 1"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Secondary Screen"
        Device          "ATI Technologies, Inc. RV370 5B60 [Radeon X300 (PCIE)] 2"
        Monitor         "HP L1902 2"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Dual Head Layout"
        Screen          "Primary Screen"
        Screen          "Secondary Screen" LeftOf "Primary Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        Option          "Xinerama"
EndSection

Section "DRI"
        Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "0"
EndSection

```

---

### Post by blaamann on 2006-11-06
I have the exact problem with my ATI card and dual head system. Dapper was no problem but Edgy is. I was told in another forum to turn of composite in my xorg.conf file (as I see you have done too), but still I have this annoying bug.

This is the second time Ubuntu breaks something in X for me. If this endures I have to switch distro because this is not good enough!!

Please post the solution to your problem if you can find it.

---

### Post by sgarman on 2006-11-06
Thanks for the reply. I do have some good news - I managed to resolve the issue by not using Xinerama. Not sure why Xinerama worked for me in dapper but not edgy, but in any case I'm glad to not have to deal with this anymore. Here is my updated xorg.conf file:

```
Section "Files"

        # path to defoma fonts
        FontPath     "/usr/share/X11/fonts/misc"
        FontPath     "/usr/share/X11/fonts/cyrillic"
        FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/Type1"
        FontPath     "/usr/share/X11/fonts/100dpi"
        FontPath     "/usr/share/X11/fonts/75dpi"
        FontPath     "/usr/share/fonts/X11/misc"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load  "i2c"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "type1"
        Load  "vbe"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us"
        Option      "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
        Option      "ZAxisMapping" "4 5"
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. RV370 5B60 [Radeon X300 (PCIE)] 1"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
        Option          "DesktopSetup" "horizontal"
        Screen          0
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. RV370 5B60 [Radeon X300 (PCIE)] 2"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
        Screen          1
EndSection

Section "Monitor"
        Identifier      "HP L1902 1"
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "HP L1902 2"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier "Primary Screen"
        Device     "ATI Technologies, Inc. RV370 5B60 [Radeon X300 (PCIE)] 1"
        Monitor    "HP L1902 1"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Secondary Screen"
        Device          "ATI Technologies, Inc. RV370 5B60 [Radeon X300 (PCIE)] 2"
        Monitor         "HP L1902 2"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Dual Head Layout"
        Screen          0 "Primary Screen" 0 0
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "0"
EndSection
```

---

### Post by blaamann on 2006-11-07
Thanks, it works !! (always nervous when doing big changes to my xorg.conf file :-) ). 

Seems like X starts a little bit slower, but that is ok as long as I got my weird cursor fixed.

---

### Post by brokerjoker on 2006-11-08
yes, I had that problem, too and your idea fixed it. thank you!
but, unfortunately I have two different resolutions, so that X acts a little wierd:

if I set up both screens in their native resolution, both run with the resolution of the smaller one. grrr.

so I have to set up the smaller one with a virtual resolution (the one of the bigger one) to have both run in their native resolution. but this has a price: there is a dead border around my screens (to the right of the bigger one and below the smaller one). Especially the invisible border under the smaller screen is likely to be used by the control bar which tries to hide there. nasty! :evil: 

what can I do else? is there a workaround for this problem?:confused: 



my conclusion so far: dual screen with ati and (k)ubuntu and two different screen sizes is a mess. I am not sure where the bugs live, is it X, in the graphics driver (hm, I tried open and closed source. same problem!) or is it distribution-specific? any experiences with other distros?

next time I'll buy a monitor with the same resolution as my laptop. ](*,)

---

### Post by sgarman on 2006-11-08
> **brokerjoker said:**
> yes, I had that problem, too and your idea fixed it. thank you!
but, unfortunately I have two different resolutions, so that X acts a little wierd:

if I set up both screens in their native resolution, both run with the resolution of the smaller one. grrr.

<snip>

next time I'll buy a monitor with the same resolution as my laptop. ](*,)

I've never had luck running dual-head with two monitors of different resolutions under Linux, either. Good luck.

Scott

---

### Post by holloway on 2006-11-19
I had this problem too on my ATI X600. In my case the second monitor's mouse pointer was rendered as 3 bars of gradient (taken from the current background image) with a bit of transparency between them.

I'll just leave some search terms for people trying to resolve this problem. Compaq NX8220 1650x1050 and 1280x1024 Dual Head.

Edit: Also the 'Option "DesktopSetup" "horizontal"' when changed to vertical works, but not when the external monitor is above, Eg, 'Option "DesktopSetup" "vertical,reverse". When the vertical monitor is above I get no panels in Gnome.

---

### Post by JacobSteelsmith on 2008-04-08
> **sgarman said:**
> Thanks for the reply. I do have some good news - I managed to resolve the issue by not using Xinerama. Not sure why Xinerama worked for me in dapper but not edgy, but in any case I'm glad to not have to deal with this anymore. Here is my updated xorg.conf file:

```
Section "Files"

        # path to defoma fonts
        FontPath     "/usr/share/X11/fonts/misc"
        FontPath     "/usr/share/X11/fonts/cyrillic"
        FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/Type1"
        FontPath     "/usr/share/X11/fonts/100dpi"
        FontPath     "/usr/share/X11/fonts/75dpi"
        FontPath     "/usr/share/fonts/X11/misc"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load  "i2c"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "type1"
        Load  "vbe"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us"
        Option      "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
        Option      "ZAxisMapping" "4 5"
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. RV370 5B60 [Radeon X300 (PCIE)] 1"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
        Option          "DesktopSetup" "horizontal"
        Screen          0
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. RV370 5B60 [Radeon X300 (PCIE)] 2"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
        Screen          1
EndSection

Section "Monitor"
        Identifier      "HP L1902 1"
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "HP L1902 2"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier "Primary Screen"
        Device     "ATI Technologies, Inc. RV370 5B60 [Radeon X300 (PCIE)] 1"
        Monitor    "HP L1902 1"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Secondary Screen"
        Device          "ATI Technologies, Inc. RV370 5B60 [Radeon X300 (PCIE)] 2"
        Monitor         "HP L1902 2"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Dual Head Layout"
        Screen          0 "Primary Screen" 0 0
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "0"
EndSection
```

Thank you very much for this post. This solution works much better in Gutsy versus using xinerama performance-wise. It also solved the problem I was experiencing with the cursor described above.

---

