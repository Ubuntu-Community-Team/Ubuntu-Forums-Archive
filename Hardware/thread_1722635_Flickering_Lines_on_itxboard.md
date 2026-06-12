---
title: "Flickering Lines on itxboard"
date: 2011-04-06
forum: Hardware
---

### Post by prunk on 2011-04-06
Hello,

I have a mini-itx intel board with what i believe is onboard sis video.

I just installed ubuntu 10.10. Once running ubuntu the screen had flickering lines running in vertical bands on the screen. I made a new xorg.conf files and since it was previously empty i added this:

Section "Device"
       Identifier "Configured Video Device"
       Driver "sis"
EndSection

Section "Monitor"
         Identifier "Configured Monitor"
         HorizSync 31.5 - 70.0
         VertRefresh 50-160
EndSection

Section "Screen"
        Identifier "Default Screen"
        Monitor "Configured Monitor"
        Device "Configured Video Device"
        DefaultDepth 24
        Subsection "Display"
             Depth 24
             Modes "1280x1024"
        EndSubsection
EndSection

that didn't seem to fix it and after more searching i changed:
        .... 
        DefaultDepth 16
        Subsection "Display"
             Depth 16
             Modes "1280x1024"
        ...

This made it better but not completely gone. 

Any suggestions? Fairly new at this.

---

