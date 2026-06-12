---
title: "Can't change to 1280 x 800"
date: 2007-07-18
forum: Hardware &amp; Laptops
---

### Post by bogo24dk on 2007-07-18
I have just installed ubuntu latest version on my laptop. I tryed to change the screen resolution to 1280 x 800. But  the screen begins to flicker. What can i do to change it 1280 ?


Laptop : Fujistsu Siemens 1437 g
Graphic Card : ati x 700 + 128 ram

---

### Post by defishguy on 2007-07-18
What is the video card in your computer?

---

### Post by bogo24dk on 2007-07-18
This one :)

> **bogo24dk said:**
>  Graphic Card :ati  x 700 + 128 ram

---

### Post by w4ett on 2007-07-18
From the terminsl type:

cat /etc/X11/xorg.conf

and post the results here.  We need to check what GFX driver you are using.

---

### Post by bogo24dk on 2007-07-18
Section "Device"
        Identifier      "ATI Technologies Inc Radeon Mobility X700 (PCIE)"
        Driver          "ati"
        BusID           "PCI:3:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc Radeon Mobility X700 (PCIE)"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

---

### Post by w4ett on 2007-07-18
I recommend you enable the restricted drivers for your ATI card.....Do this from the System tab, or try using ENVY:

[http://www.albertomilone.com/](http://www.albertomilone.com/)

This is a GUI script to install the proprietary ATI Radeon driver for your card....Run this and it will install the driver and modify your xorg.conf.

---

### Post by bogo24dk on 2007-07-18
> **w4ett said:**
> I recommend you enable the restricted drivers for your ATI card.....Do this from the System tab, or try using ENVY:

[http://www.albertomilone.com/](http://www.albertomilone.com/)

This is a GUI script to install the proprietary ATI Radeon driver for your card....Run this and it will install the driver and modify your xorg.conf.

Thanks for the great advice. It was successful installing a updated driver. But know the max resolution which i can choose is 1024. I need help with the last part with the xconf.

---

### Post by stchman on 2007-07-18
> **bogo24dk said:**
> Section "Device"
        Identifier      "ATI Technologies Inc Radeon Mobility X700 (PCIE)"
        Driver          "ati"
        BusID           "PCI:3:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc Radeon Mobility X700 (PCIE)"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

Enable the restricted driver and if that does not work use this line in your xorg.conf.  Substitute this for every Modes line.

Modes           "1280x800" "1024x768" "800x600" "640x480"

---

### Post by bogo24dk on 2007-07-18
> **stchman said:**
> Enable the restricted driver and if that does not work use this line in your xorg.conf.  Substitute this for every Modes line.

Modes           "1280x800" "1024x768" "800x600" "640x480"


I am totally new to linux could you please explain what i need to do ?

---

### Post by iota on 2007-07-18
[http://www.linuxcompatible.org/Screen_refresh_rate_t33565.html](http://www.linuxcompatible.org/Screen_refresh_rate_t33565.html)

If you follow the second post on that page it gives you a pretty decent walkthrough on altering your xorg for a custom resolution/refresh rate. Hopefully it will help, it worked for me :)

---

### Post by stchman on 2007-07-19
> **bogo24dk said:**
> I am totally new to linux could you please explain what i need to do ?

sudo gedit /etc/X11/xorg.conf

This will bring up a text editor and then simply substitute the line that I specified.  Save and reboot.

---

