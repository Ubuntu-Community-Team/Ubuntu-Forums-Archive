---
title: "ubuntu dapper lts on toshiba tecra 550cdt"
date: 2009-03-03
forum: Installation &amp; Upgrades
---

### Post by petebarchetta on 2009-03-03
hello all,
currently a happy camper :)
i'm writing on my ageing laptop via ubuntu.....yay... not a hint of xp in sight. 
here's the problem :(
the machine is running a 266mhz MMX Cpu, 160mb ram, 40gb HD, Teac DV-28-b DvD-Rom. OS is Ubuntu Dapper LTS.
It used to run Hoary, then that got upgraded to Breezy, then dapper.
wifi and nic PCMCIA cards work great, hence me posting from it :)
my issue is the Xorg.conf file will not make full use of the screen, the tosh specs say a res of 1024x768 is possible, the xorg file has this in, with the lowest res now being 800x600, but it still displays at 640x480, where is the system picking up the info if not from the xorg file?
attached is my xorg
i would love to use all the  screen as ubuntu and debian all seem to put the buttons just off screen.
i know its possible as knoppix once installed on another drive used all screen
apologies for the cut and paste
any ideas

Section "Monitor"
        Identifier      "L367"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "S3 Inc. ViRGE/MX"
        Monitor         "L367"
        DefaultDepth    24
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "832x624" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "832x624" "800x600"
               EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "832x624" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "832x624" "800x600"
        EndSubSection
EndSection


i know its gotta be something simple, i'd just love to have ubuntu running in crystal clear full res

---

### Post by petebarchetta on 2009-03-19
> **petebarchetta said:**
> hello all,
currently a happy camper :)
i'm writing on my ageing laptop via ubuntu.....yay... not a hint of xp in sight. 
here's the problem :(
the machine is running a 266mhz MMX Cpu, 160mb ram, 40gb HD, Teac DV-28-b DvD-Rom. OS is Ubuntu Dapper LTS.
It used to run Hoary, then that got upgraded to Breezy, then dapper.
wifi and nic PCMCIA cards work great, hence me posting from it :)
my issue is the Xorg.conf file will not make full use of the screen, the tosh specs say a res of 1024x768 is possible, the xorg file has this in, with the lowest res now being 800x600, but it still displays at 640x480, where is the system picking up the info if not from the xorg file?
attached is my xorg
i would love to use all the  screen as ubuntu and debian all seem to put the buttons just off screen.
i know its possible as knoppix once installed on another drive used all screen
apologies for the cut and paste
any ideas

Section "Monitor"
        Identifier      "L367"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "S3 Inc. ViRGE/MX"
        Monitor         "L367"
        DefaultDepth    24
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "832x624" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "832x624" "800x600"
               EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "832x624" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "832x624" "800x600"
        EndSubSection
EndSection


i know its gotta be something simple, i'd just love to have ubuntu running in crystal clear full res

problem solved

---

