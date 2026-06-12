---
title: "Multiple Displays"
date: 2009-06-07
forum: Hardware
---

### Post by bradsarg on 2009-06-07
Hello everyone, I'm currently having a slight problem with setting up multiple displays, it actually works extremely well with the Ubuntu default drivers but whenever I try to install the proprietary ones all it wants to do is clone. ATI Catalylst Center doesn't give me the option to do a Big Desktop, I've searched around the forums and Google I found similar problems with no solutions.

If I can't get this to work I'll simply remove the ATI proprietary drivers and live without any 3D visuals, I would just be grateful for any help anyone can offer I've used Ubuntu for awhile but am still trying to learn.

The graphics card is a Saphire ATI Radeon HD 3850
Monitors are HP f1905 19" LCD and a HP w1907 19"
Ubuntu 9.04 Gnome 2.26.1

Here are some screen shots
[IMG]http://i3.photobucket.com/albums/y78/osiris_san/Tech/Screenshot-CatalystControlCenter.png[/IMG]
[IMG]http://i3.photobucket.com/albums/y78/osiris_san/Tech/Screenshot-CatalystControlCenter-1.png[/IMG]

My xorg.conf file

Section "ServerLayout"
        Identifier     "amdcccle Layout"
        Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
        Load  "glx"
EndSection

Section "ServerFlags"
        Option      "Xinerama" "off"
EndSection

Section "Monitor"
        Identifier   "Configured Monitor"
EndSection

Section "Monitor"
        Identifier   "amdcccle-Monitor[1]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "Configured Video Device"
        Driver      "fglrx"
EndSection

Section "Device"
        Identifier  "amdcccle-Device[1]-0"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "Configured Video Device"
        Monitor    "Configured Monitor"
        DefaultDepth     24
        SubSection "Display"
                Virtual   2720 1042
        EndSubSection
EndSection

Section "Screen"
        Identifier "amdcccle-Screen[1]-0"
        Device     "amdcccle-Device[1]-0"
        Monitor    "amdcccle-Monitor[1]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

---

### Post by bradsarg on 2009-06-07
Also I notice that it drastically slows down my performance so I suppose its just crappy ATI support for linux but if anyone has any ideas I'm all ears.

---

### Post by bradsarg on 2009-07-04
I did post this in the correct place right?

---

### Post by francis85 on 2009-08-02
I've been having the exact same issue. Still trying to figure it out.. next step is to find an old version of Catalyst.. I know it worked with 8.10 and whatever Catalyst version I had at that point.

---

### Post by ArmenianLeader4 on 2009-08-02
Why are you using catalyst? Just go to System>Prefrences>Display and then select "Detect Monitors." Works perfectly on Jaunty for me everytime.

---

