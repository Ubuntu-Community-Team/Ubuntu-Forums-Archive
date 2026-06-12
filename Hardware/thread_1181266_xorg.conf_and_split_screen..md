---
title: "xorg.conf and split screen."
date: 2009-06-07
forum: Hardware
---

### Post by kinghippy on 2009-06-07
Hi.  I have an old school sony vaio pcg-r505JS.  I was having problems with my screen resolution, as there was a one inch black border around my screen on all sides. I changed the xorg.conf file, and now Kubuntu is filling my screen at the proper resolution.  The problem now is a split screen. What should be the left side of my screen is on the far right side, with a 3/4" black bar running vertically right down the side. I've attached a photograph that resembles it. (The photo attached is a gimp created photo, not a screencapture because my laptop doesn't have internet so I recreated this pic on my desktop real quick using gimp.)  The screen now looks roughly like the picture.  The following is my xorg.conf file as I have edited it.  Does anyone know what might be causing this problem?


Section "Device"
        Identifier      "Configured Video Device"
        Driver  "intel"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync 31.5-48.5
        VertRefresh 40-70
        Option "dpms"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth 16
        Option "Accel"
        SubSection "Display"
                Depth 16
                Modes "1024x768"
        EndSubSection
        SubSection "Display"
                Depth 24
                Modes "1024x768"
        EndSubSection
EndSection

---

### Post by kinghippy on 2009-06-07
Never mind!  I just had an error in my file. When I double checked it, I found my error.  It's working great now!

---

