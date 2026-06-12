---
title: "Refresh Rate issues"
date: 2007-08-08
forum: Hardware &amp; Laptops
---

### Post by dokdoom on 2007-08-08
I just upgraded one of our machines to 7.04 from 6.10 I have this box hooked up to a 46 inch LCD screen running at 1920x1080 60hz. All I wanted to do was upgrade ubuntu figured I could just copy the x file over and everything would be the same. Not so much the case, been tweaking the x file for 4 days now trying different modelines but no matter what I cannot achieve a resolution of 60hz. In the System > Preferences > Screen Resolution I am only given one refresh option and that is 29hz. I was hoping someone would be able to look at my xorg file and tell me where I went wrong or just maybe a nudge in the right direction. Here is my xorg file

Section "Screen"
        Identifier "screen_primary"
        Device          "device_primary"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Depth     24
                Modes    "1920x1080@60"
        EndSubSection
EndSection


Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
        #HorizSync      31.5 - 91.1
        #VertRefresh    60-85
#       DisplaySize  1018       572 # 1018.35 x 572,82 mm
#        HorizSync    31.0 - 92.0
#        VertRefresh  60
#        Modeline     "1366x768"   70.0   1360 1392 1712 1724   768 783 791 817
#       Modeline "1920x1080" 172.798 1920 2040 2248 2576 1080 1081 1084 1118 -hsync -vsync
#       Modeline "1920x1080@30i"    36.11  1920 1952 2088 2120   1080 1106 1109 1135 interlace
#       Modeline "1920x1080@29i"    34.83  1920 1952 2080 2112   1080 1106 1109 1135 interlace
#       Modeline  "1920x1080" 74.723 1920 1976 2104 2216 1080 1084 1094 1124 -hsync -vsync
#72hz   Modeline "1920x1080@120i" 182.28 1920 1952 2640 2672 1080 1102 1113 1135 interlace
#       Modeline  "1920x1080" 89.505 1920 1976 2104 2216 1080 1084 1094 1124 interlace -hsync -vsync

        #Modeline "1920x1080@29" 74.64 1920 1952 2232 2264 1080 1105 1110 1135
        #Modeline "1920x1080@30" 77.60 1920 1952 2240 2272 1080 1104 1110 1135
        #Modeline "1920x1080@85i" 117.18 1920 1952 2392 2424 1080 1103 1111 1135 interlace

 # TV error: H: 68 V: 120
        #Modeline "1920x1080@120ins" 182.28 1920 1952 2640 2672 1080 1102 1113 1135 interlace -hsync -vsync

        # better... still wavy & interlaced-looking
        #Modeline "1920x1080@60ins" 77.60 1920 1952 2240 2272 1080 1104 1110 1135 interlace -hsync -vsync

        # TV error: H: 17 V:30
        #Modeline "1920x1080@30ins" 36.11 1920 1952 2088 2120 1080 1106 1109 1135 interlace -hsync -vsync

        # looks better, but still slightly small, wavy & flickery
        #Modeline "1920x1080@30ns" 77.60 1920 1952 2240 2272 1080 1104 1110 1135 -hsync -vsync

        # TV error: H: 63 V: 110
        #Modeline "1920x1080@55ns" 162.00 1920 1952 2560 2592 1080 1102 1112 1135 -hsync -vsync # hf: 62.5 kHz

        # TV error: H: 74kHz V: 130Hz
        #Modeline "1920x1080@65ns" 203.39 1920 1952 2720 2752 1080 1101 1113 1135 -hsync -vsync # hf: 73.9 kHz
# same deal, too small
        #Modeline "1920x1080@65" 203.39 1920 1952 2720 2752 1080 1101 1113 1135 -hsync -vsync # hf: 73.9 kHz

        # this one works, but it is shorter and darker and flickery, moreso than 1920x1080@60
        #Modeline "1920x1080@55" 162.00 1920 1952 2560 2592 1080 1102 1112 1135 # hf: 62.5 kHz

        # this one works, but it is weird... too short and dark
        Modeline "1920x1080@60" 182.28 1920 1952 2640 2672 1080 1102 1113 1135 # hf: 68.21 kHz

        # TV error: H: 34kHz V: 30Hz
        #Modeline "1920x1080@60i" 77.60 1920 1952 2240 2272 1080 1104 1110 1135 interlace# hf: 34.15 kHz

        # the ORIGINAL one that was working on the old MVT installation
        #ModeLine  "1920x1080orig" 172.798 1920 2040 2248 2576 1080 1081 1084 1118 -hsync -vsync
EndSection

---

### Post by dokdoom on 2007-08-08
Turns out someone else had altered the xorg file and now that we have the option of a 60hz refresh rate we cannot get the resolution to fit 1920x1080. The screen says its set to that resolution however it doesn't fit the screen, seems dark and on the left side of the screen itself there's an inch of black covering the desktop.  All I would like to know is how to configure the file to display a 1980x1020 resolution with a 60hz refresh rate.

---

### Post by EXCiD3 on 2007-08-08
System > Preferences > Screen Resolution is a terrible way of changing Resolution/Refresh Rates... Use your graphics card driver to change it as it should detect everything correctly. What video card are you using?

---

