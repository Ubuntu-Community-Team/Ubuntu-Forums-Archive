---
title: "Hi - I need help writing my xorg.conf file"
date: 2009-11-20
forum: Hardware
---

### Post by youbuntu on 2009-11-20
Hello. I have an IBM pc which has a Matrox Millenium G450 dual head card in it, and a SINGLE crt attached - an LG Studioworks 221U.

I need to know how I setup my (currently missing) xorg.conf please - here are my refresh rates for the CRT:

Horizontal: 30-115Khz
Vertical: 50-200Hz

The maximum resolution (the ONLY one I need) on this card is 1280x1024

Many thanks

---

### Post by SuperSonic4 on 2009-11-20
Can you not get the driver from [http://www.matrox.com/graphics/en/support/drivers/](http://www.matrox.com/graphics/en/support/drivers/)

This is just mine with a few tweaks- almost certainly won't work since I'm not use to messing with xorg

```
Section "ServerLayout"                                                                                                                                                           
    Identifier     "Layout0"                                                                                                                                                     
    Screen      0  "Screen0" 0 0                                                                                                                                                 
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
    ModelName      "LG Studioworks 221U"
    HorizSync       30.0 - 115.0
    VertRefresh     50.0 - 200.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "matrox" #**I would recommend using the driver from the link at the top**
    VendorName     "Matrox" #**I would suggest you get this from above too**
    BoardName      "G450"
EndSection
```

---

### Post by youbuntu on 2009-11-20
Nope, both those ideas failed.

---

### Post by doas777 on 2009-11-20
It looks like that xorg.conf could use a screen section. this might work for you.
it's configured for dual-head as though you had two of the same monitor. should be enough to show you where you need to tweak it for whatever monitor.
usually an xorg screen consists of three parts: a device, a monitor, and a screen.
when you have two x screens, you have two of each, as below. if your doing single head, then jsut comment out the lines indicated below (device1, Monitor1, and screen1).

also, run the command ```
lspci
``` and note the PCI bus id for your vid card. be sure to configure the "BusID" option under each device where indicated below.

this is a smerging of Supersonic's xorg, and an older one i had from back before twinview worked right, so it is almost gaurenteed to need some tweaking and expirementation. back up often to new filenames. 


good luck

```

                                                                                                                                                                                 
Section "ServerLayout"                                                                                                                                                           
    Identifier     "Layout0"                                                                                                                                                     
    Screen      0  "Screen0" 0 0     #change if you switch to LeftOf
    Screen    1  "Screen1" RightOf "Screen0"                                                                                                                                           
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
    ModelName      "LG Studioworks 221U"
    HorizSync       30.0 - 115.0
    VertRefresh     50.0 - 200.0
    Option         "DPMS"
EndSection

#comment this block for single head rig
Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "LG Studioworks 221U"
    HorizSync       30.0 - 115.0
    VertRefresh     50.0 - 200.0
    Option         "DPMS"
EndSection


Section "Device"
    Identifier     "Device0"
    Driver         "matrox" #I would recommend using the driver from the link at the top
    VendorName     "Matrox" #I would suggest you get this from above too
    BoardName      "G450"
     #run lspci, and find the busid. it will be somthing like PCI:1:0:1
    BusID       "fill this with pci bus id from lspci"
    Screen       0 
EndSection

#comment this block for single head rig
Section "Device"
    Identifier     "Device1"
    Driver         "matrox" #I would recommend using the driver from the link at the top
    VendorName     "Matrox" #I would suggest you get this from above too
    BoardName      "G450"
    #run lspci, and find the busid. it will be somthing like PCI:1:0:1
    BusID       "fill this with pci bus id from lspci"
    Screen       1 
EndSection

Section "Screen"
    Identifier    "Screen0"
    Device        "Device0"
    Monitor        "Monitor0"   
    DefaultDepth    24
  SubSection "Display"
    Depth        16
    Modes        "1024x768" "800x600" "640x480" "1280x1024"
  EndSubSection
  SubSection "Display"
    Depth        24
    Modes        "1024x768" "800x600" "640x480" "1280x1024"
  EndSubSection
EndSection

#comment this block for single head rig
Section "Screen"
    Identifier    "Screen1"
    Device        "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
   SubSection "Display"
    Depth        16
    Modes        "1024x768" "800x600" "640x480" "1280x1024"
  EndSubSection
  SubSection "Display"
    Depth        24
    Modes        "1024x768" "800x600" "640x480" "1280x1024"
  EndSubSection


EndSection



```SuperSonic4, i love the sig!

---

### Post by youbuntu on 2009-11-20
Nope, fail.

---

### Post by doas777 on 2009-11-20
post it back with your tweaks.

---

### Post by youbuntu on 2009-11-20
This is ridiculous - how hard can it be JUST to get a crt working?!

---

### Post by Melcar on 2009-11-20
If you boot into safe mode (or kill X and drop to command prompt mode) you can generate a fresh xorg.conf file with this command:

```
Xorg -configure
```

This will drop a file named xorg.conf.new into your root directory.  This file will have everything from input devices to graphics driver settings.  Since Ubuntu 9.10 does not need the xorg.conf file anymore to function, you can safely remove everything from that file and just leave in the options you want to configure/add (leaving the **Device** section is a good idea, as well as the **Screen** section if you want to add extra resolutions). 

In order to configure the file, open it with:

```
sudo nano /root/xorg.conf.new
```

Make your changes and save the file as **xorg.conf** so Ubuntu can recognize it.  Lastly, you need to move this file to /etc/X11:

```
sudo mv /root/xorg.conf /etcX11/
```

Now just reboot

```
sudo reboot
```

If for some reason you can't boot after the changes to xorg.conf, you can simply remove the file:

```
sudo rm /etc/X11/xorg.conf
```

Ubuntu will simply load the default values for your system next time you boot.

---

### Post by youbuntu on 2009-11-20
This seems to work:

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
    Load  "dri2"
    Load  "dri"
    Load  "record"
    Load  "extmod"
    Load  "dbe"
    Load  "glx"
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
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LG Studioworks 221U"
    HorizSync       30.0 - 115.0
    VertRefresh     50.0 - 200.0
    Option         "DPMS"
EndSection


Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "SWcursor"               # [<bool>]
        #Option     "HWcursor"               # [<bool>]
        #Option     "PciRetry"               # [<bool>]
        #Option     "SyncOnGreen"            # [<bool>]
        #Option     "NoAccel"                # [<bool>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "MGASDRAM"               # [<bool>]
        #Option     "ShadowFB"               # [<bool>]
        #Option     "UseFBDev"               # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "SetMclk"                # <freq>
        #Option     "OverclockMem"           # [<bool>]
        #Option     "VideoKey"               # <i>
        #Option     "Rotate"                 # [<str>]
        #Option     "TexturedVideo"          # [<bool>]
        #Option     "Crtc2Half"              # [<bool>]
        #Option     "Crtc2Ram"               # <i>
        #Option     "Int10"                  # [<bool>]
        #Option     "AGPMode"                # <i>
        #Option     "AGPSize"                # <i>
        #Option     "DigitalScreen1"         # [<bool>]
        #Option     "DigitalScreen2"         # [<bool>]
        #Option     "TV"                     # [<bool>]
        #Option     "TVStandard"             # [<str>]
        #Option     "CableType"              # [<str>]
        #Option     "NoHal"                  # [<bool>]
        #Option     "SwappedHead"            # [<bool>]
        #Option     "DRI"                    # [<bool>]
        #Option     "MergedFB"               # [<bool>]
        #Option     "Monitor2HSync"          # [<str>]
        #Option     "Monitor2VRefresh"       # [<str>]
        #Option     "Monitor2Position"       # [<str>]
        #Option     "MetaModes"              # [<str>]
        #Option     "OldDmaInit"             # [<bool>]
        #Option     "ForcePciDma"            # [<bool>]
        #Option     "AccelMethod"            # [<str>]
        #Option     "KVM"                    # [<bool>]
    Identifier  "Card0"
    Driver      "mga"
    VendorName  "Matrox Graphics, Inc."    BoardName   "MGA G400/G450"
    BusID       "PCI:2:0:0"
EndSection

Section "Screen"
    Identifier    "Screen0"
    Device        "Device0"
    Monitor        "Monitor0"   
    DefaultDepth    24
  SubSection "Display"
    Depth        16
    Modes        "1024x768" "800x600" "640x480" "1280x1024" "1280x1024@96"
  EndSubSection
  SubSection "Display"
    Depth        24
    Modes        "1024x768" "800x600" "640x480" "1280x1024" "1280x1024@96"
  EndSubSection
EndSection

```

EXCEPT it forgets my res upon logout :(

---

### Post by Melcar on 2009-11-20
What if you remove all he resolutions and just leave the one you want?

---

### Post by youbuntu on 2009-11-20
> **Melcar said:**
> What if you remove all he resolutions and just leave the one you want?

Genius!. Wish I'd thought of that - haha!. It works, thankyou.

---

### Post by doas777 on 2009-11-20
glad to hear it! getting an xorg configured for TV out was my second major experience in linux. 

have fun and good luck

---

### Post by youbuntu on 2009-11-21
Thanks for your support - I think I'll continue to tweak it and build on it; this is only an old 800Mhz box and I can just fiddle to my hearts content :)

---

