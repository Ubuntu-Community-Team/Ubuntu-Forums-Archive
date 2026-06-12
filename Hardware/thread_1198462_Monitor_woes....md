---
title: "Monitor woes..."
date: 2009-06-27
forum: Hardware
---

### Post by jsdieorksw on 2009-06-27
I have a compaq 5017 LCD monitor and I'm running a NVIDIA Geforce 6150SE nForce 430 graphics card and I keep getting an error message that reads "input signal out range" after I boot up.  I've done a lot of searching and tried many things and only to have seemed to have messed things up more.  Does anybody have a way that I can fix this? 

I'm using an old CRT right now to use the forums but would like to get this fixed to use the better LCD monitor.

---

### Post by philcamlin on 2009-06-27
video card is messed up i had tha issue once 

unplug your pc and monitor for 2 min and then replug in and it should all work 

its not ubuntu its your pc :(

---

### Post by jsdieorksw on 2009-06-27
Tried it already

---

### Post by ajgreeny on 2009-06-27
If it has worked with previous versions of Ubuntu it must be the detection of your monitor that is at fault.  You could try manually editing your /etc/X11/xorg.conf file, adding the correct information regarding resolution and refresh rates to attempt to get it working properly.

What does that file contain at the moment, and is the information there correct for your monitor?  If it appears wrong, again it will be worth editing to the correct figures.  My xorg.conf, which I had to edit in this way for intrepid looks like this
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
```

---

