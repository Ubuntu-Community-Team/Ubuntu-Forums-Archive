---
title: "tv-out dell inspiron 9400 intel 945GM"
date: 2007-01-15
forum: Hardware &amp; Laptops
---

### Post by jvelasco on 2007-01-15
Please help if you have any clue, I lost a lot of time with this issue, I cant figure out how to tv-out on my dell laptop, here is my xorg.conf but it does not work when I do tv-out:

Section "Device"
        Identifier      "ONLY_LCD"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Option "UseFBDev" "true"
        Option "EnablePageFlip"
        Option "ColorTiling"
        #Option          "XAANoOffscreenPixmaps" "true"
        #Might be deprecated but worth trying
        #Option          "TripleBuffer" "true"
        #Screen          0
EndSection

Section "Device"   #LCD + TV (Config LCD)
        Identifier      "LCD_TV"
        Driver          "i810"
        Option          "MonitorLayout" "TV,LFP+TV"
        #VideoRam        16384  #131072
        #Option          "UseFBDev"              "true"
        #Option          "DDCMode" "True"
        Screen          0
        BusID           "PCI:0:2:0"
EndSection

Section "Device"   #LCD + TV (Config TV)
        Identifier      "TV"
        Driver          "i810"
        Option          "MonitorLayout" "TV,LFP+TV"
        #VideoRam        16384  #131072
        Option          "TVStandard" "PAL-H"   #Belgium
        Option          "TVOutFormat" "SVIDEO" #VIDEO
        Option          "ConnectedMonitor" "TV"
        #Option          "UseFBDev"              "true"
        #Option          "DDCMode" "True"
        Screen 1
        BusId "PCI:0:2:1"
EndSection

###################################################

Section "Monitor"
        Identifier      "TV"
        Option          "DPMS" #MAYBE TAKE THIS OUT
        #HorizSync 30.0-50.0
        #VertRefresh 60
EndSection

Section "Monitor"
        Identifier      "LCD"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160
EndSection

####################################################
Section "Screen"
        Identifier      "TV"
        Device          "TV"
        Monitor         "TV"
        DefaultDepth   16
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "Screen" #LCD Config when LCD+TV
        Identifier "LCD_TV"
        Device "LCD_TV"
        Monitor "LCD"
        DefaultDepth   16
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
EndSection




Section "Screen"
        Identifier      "ONLY_LCD"
        Device          "ONLY_LCD"
        Monitor         "LCD"
        Option "AddARGBGLXVisuals" "True"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1920x1200" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1920x1200" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1920x1200" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1920x1200" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1920x1200" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1920x1200" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

########################################

Section "ServerLayout" #Output only LCD (default)
        Identifier  "ONLY_LCD"
        Screen      "ONLY_LCD"
        InputDevice "Generic Keyboard"
        InputDevice "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
        InputDevice "Synaptics Touchpad"
EndSection


Section "ServerLayout"   #Output for LCD and TV
        Identifier      "LCDandTV"
        Screen          0 "LCD_TV" 0 0
        Screen          1 "TV" LeftOf "LCD_TV"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "ServerFlags"
       Option   "Xinerama" "true"
EndSection

#######################################

Section "ServerFlags"
  #Option "DefaultServerLayout" "ONLY_LCD"
  #Option "DefaultServerLayout" "ONLY_TV"
  Option "DefaultServerLayout" "LCDandTV"
EndSection

#Section "Extensions"
#  Option "Composite" "Enable"
#EndSection

# note that enabling xinerama disables Direct Rendering...
Section "DRI"
        Mode    0666
EndSection

---

### Post by discord on 2007-01-16
you may need to name your screen sections screen0 or screen1 for the identifier. have another look at the dual monitor post on the ubuntu forums. Xinerama etc.

---

### Post by featherking on 2007-02-20
I wrote up an actual 'How To' for this and it is posted [[COLOR="Red"]here[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=361124")

---

