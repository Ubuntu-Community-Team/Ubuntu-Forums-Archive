---
title: "Screen Resolution problems after using projector"
date: 2009-12-12
forum: Hardware
---

### Post by Rookie4Linux on 2009-12-12
I installed Ubuntu 9.10 when it officially came out using the upgrade manager, and everything worked fine until i used a projector the other day.  Since then i have not been able to access the 1280x800 resolution that my monitor is capable of.  i have searched for an answer and found several things, non of which worked.  they included creating and editing the xorg config file, using dpkg-reconfigure, and some others that i don't remember right now.  i am using an integrated ATI Radeon Xpress 200M, with a dell 15.4 inch widescreen.  I have booted with an Ubuntu 9.04 live cd and the resolution was automaticly set at the correct 1280x800.  

This is my xorg.conf file as it stands now
```
Section "Screen"
        Identifier      "Configured Screen Device"
        Device  "Configured Video Device"
        SubSection "Display"
                Modes "1280x800" // I added this line
                Virtual 2048 768
        EndSubSection
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection

```
And the output of xrandr from my 9.10 install.


```
Screen 0: minimum 320 x 200, current 1280 x 720, maximum 2048 x 768
VGA-0 disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x720+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x720       59.9* 
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   640x480        59.4  

```

And the  output of xrandr from the 9.04 live CD
```

Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1200
VGA-0 disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   640x480        59.4 

```

I am willing to try anything short of a fresh install, or retry steps that I have previously done, incase I might have missed something the first time.  Pleas let me know if you need any other information from me.  

Thanks in advance
Thomas

---

### Post by Rookie4Linux on 2009-12-12
Got it fixed... lol it was actually stupidly simple.  When I plugged in the projector apparently it created the xorg.config file and it telling my computer that it had a screen the size of the projector. (the "Virtual 2048 768" line in the xorg file).  all i had to do was delete the xorg.conf file and everything works like it is supposed to.  It figures that i get this figured out as soon as i post a question up:-)

Thanks.

---

