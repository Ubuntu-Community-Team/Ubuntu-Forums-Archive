---
title: "Samsung Syncmaster 205bw will not show native res."
date: 2007-05-15
forum: Hardware &amp; Laptops
---

### Post by apeman_spaceman on 2007-05-15
Hello -

I just upgraded flat panels, from a 19" to a 20" wide screen, and I cannot get it to display 1680x1050 under X.  Right now, using the Alternate Intel driver (instead of i810) I can set X to 1680x1050, and it believes that is what it is using, but the monitor is showing 1400x1050. I've tried many different modelines as well.

I'm using a built in Intel video, 845G. I've included the relevant sections of xorg.conf  below. If anybody can shed some light on this, it would be much appreciated. I've been googling forever it seems.

------------
Xorg.conf:

Section "Device"
        Identifier      "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
        Driver          "intel"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "SyncMaster"
        VendorName   "Samsung"
        ModelName    "SyncMaster 205BW"
        Option       "dpms"
#       Modeline "1680x1050"  146.25  1680 1784 1960 2240  1050 1053 1059 1089
#       ModeLine "1680x1050" 146.8 1680 1784 1960 2240 1050 1053 1059 1089
        ModeLine "1680x1050_60"  146.25  1680 1784 1960 2240 1050 1053 1059 1089 -hsync -vsync
#       ModeLine "1680x1050" 146.8  1680 1784 1960 2240  1050 1053 1059 1089 -hsync -vsync
#       ModeLine "1680x1050"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +hsync -vsync

        # Important. At least on my setup it doesn't detect the size correctly.
        # If not specified, the fonts may look very tiny.
        # Numbers found on a random web site using Google.
        DisplaySize  433 270

        # Those are the magic values that make it all work.

        HorizSync    30.0 - 83.0
        VertRefresh  56.0 - 63.0
        # This allowed for resolutions in the 19AAxBBBB
        # See also the Virtual directive in Display subsection below
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
        Monitor         "SyncMaster"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1680x1050_60"
        EndSubSection
EndSection

-------------

Output of xrandr -q:
 SZ:    Pixels          Physical       Refresh
*0   1680 x 1050   ( 431mm x 270mm )  *60  
 1   1280 x 1024   ( 431mm x 270mm )   75   60  
 2   1280 x 960    ( 431mm x 270mm )   60  
 3   1152 x 864    ( 431mm x 270mm )   75  
 4   1024 x 768    ( 431mm x 270mm )   75   70   60  
 5    832 x 624    ( 431mm x 270mm )   75  
 6    800 x 600    ( 431mm x 270mm )   72   75   60   56  
 7    640 x 480    ( 431mm x 270mm )   75   73   67   60  
 8    720 x 400    ( 431mm x 270mm )   70  
 9   1680 x 1680   ( 431mm x 270mm )   60  
Current rotation - normal
Current reflection - none
Rotations possible - normal left inverted right 
Reflections possible - none

---

### Post by apeman_spaceman on 2007-05-16
Bump....

---

### Post by tib0r on 2007-07-27
did you solve the problem please? My setup works on 1680x1050 with the only twist, that my Samsung Syncmaster thinks it's 1400x1050 (info menu) and apperently doesn't align the pixels from signal properly. Result is blurry text.
Tibor

---

### Post by MrHippocampus on 2007-07-27
If your using the intel driver your probably going to have to look into using the 915resolution program, I've never used this myself but searching the forums for "915resolution" should come up with something.

---

### Post by manusharma on 2007-09-12
After much time trying to configure a dell optiplex with an 845g video card to diplay 1680x1050 properly on a Samsung 205bw, I've had some luck by upgrading to gutsy.  However, I still get slightly blurry text; actually more like slight shadowing.  Has anyone been able to get crisp display using the 845g + 205bw combination?  (I am currently using the intel driver that comes with gutsy). 

Thanks,

---

