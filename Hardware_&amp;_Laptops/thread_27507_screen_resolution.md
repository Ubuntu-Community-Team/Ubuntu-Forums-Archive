---
title: "screen resolution"
date: 2005-04-16
forum: Hardware &amp; Laptops
---

### Post by nothreat33 on 2005-04-16
i just installed 5.04 today and my screen resolution is all messed up and big.
i went to system>preferences>screen resolution to fix the problem but i only have on choice the one im using now. 
my xorg.conf looks like this:
#############################
Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
        Monitor         "MX90"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
##############################
i should have the option of the other modes. but i don't. does anyone know whats going on? or have an idea what i need to change?
i was hoping for 1024x768.

---

### Post by heimo on 2005-04-16
You probably need to set HorizSync and VertRefresh in Monitor section of xorg.conf

Some hints in this thread:
[http://www.ubuntuforums.org/showthread.php?t=21984]("http://www.ubuntuforums.org/showthread.php?t=21984")


EDIT: And if you tell what your monitor is, I probably can tell you what to put in there, if you're uncertain. (should be found in your monitors manual or manufacturers website)

---

### Post by nothreat33 on 2005-04-16
my monitor is a hp pavilion mx90, with the i810 driver.

part of my xorg.conf file looks like this (i changed it all to 1280x1024):

 Monitor         "MX90"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024"
######################
and i rebooted and i still had the 640x480 @ 60mhz

---

### Post by heimo on 2005-04-16
That's the Screen section. What you need to do is edit Monitor section and add or edit lines:
 ```

HorizSync        30-95
VertRefresh     50-150

``` 
You don't need to restart the computer, just the Xorg. Close programs and hit CTRL+ALT+BACKSPACE, if the screen doesn't come up nicely, change the xorg.conf back to what it was (using console).

EDIT: And put back those other resolutions, you won't get 1024x768 if that's not there. You can cycle through different modes with CTRL+ALT+ + (plus sign).

Here's source for those numbers:
[http://h10032.www1.hp.com/ctg/Manual/bph06493.pdf](http://h10032.www1.hp.com/ctg/Manual/bph06493.pdf)

---

### Post by nothreat33 on 2005-04-16
that worked fine. my screen size is normal. thanks alot

---

