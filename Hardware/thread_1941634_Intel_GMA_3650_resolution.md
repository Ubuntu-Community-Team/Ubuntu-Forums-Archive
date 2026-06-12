---
title: "Intel GMA 3650 resolution"
date: 2012-03-16
forum: Hardware
---

### Post by pderocco on 2012-03-16
OS: Ubuntu 11.10, all updates
Mobo: Intel D2700MUD (Atom) with GMA3650 graphics
Monitor: Eizo CE240W 1920x1200 via DVI
 
Although the mobo supports this resolution, the monitor is not recognized, and the system gives me a 1600x1200 display stretched to fill the monitor. The System Settings -> Displays shows the screen as Unknown, Detect Displays does nothing, and 1600x1200 is the max resolution.
 
I used xrandr to create a 1920x1200 mode, and add it to the display called "default", and aside from a bunch of "Failed to get size of gamma for output default" errors, it does indeed add that mode to the choices in Displays. However, when I select that new mode, it complains "required virtual size does not fit available size", since the max is still 1600x1200. It doesn't say what exactly is enforcing that limit.
 
After a lot of Googling, I found a couple of recommendations that I create an xorg.conf file (there was none), and put something like this into it:
 
```
 
Section "Screen"
    Identifier "Default Screen"
    Device "Default Video Device"
    DefaultDepth 24
    SubSection "Display"
        Virtual 1920 1200
    EndSubSection
EndSection
 

```
 
When I do this, the system won't boot into the GUI, and I have to go into a TTY to delete the file and reboot. The docs I've found on xorg.conf say imply that that if you use an xorg.conf, you need a whole lot more in it than just that, and that Device must refer to another section in the xorg.conf file. I find no mention of the legality of saying "Default Video Device".
 
Oh, and Intel doesn't provide any Linux drivers for this video, so I don't know what the system is using. FYI, lspci identifies the controller as "Intel Corporation Cedarview Integrated Graphics Controller (rev 09)".
 
Any ideas? Anyone? Bueller?

---

### Post by shuggy01 on 2012-05-02
OS: Ubuntu 12.04, all updates
Mobo: Intel D2700DC (Atom) with GMA3650 graphics
Monitor: Acer A231H (1920x1080)

I'm experiencing the same problem.  Ubuntu recognizes my monitor as "Laptop" with max resolution of 1280x1024.

I'd really rather use Ubuntu on this computer and am willing to try some experimental things.  I'm not afraid to reformat if things get bad.  any suggestions?

---

### Post by ahallubuntu on 2012-05-03
You can try this as a last resort:

[http://ubuntuforums.org/showpost.php?p=11888245&postcount=13](http://ubuntuforums.org/showpost.php?p=11888245&postcount=13)

and try swapping in your resolution.

---

