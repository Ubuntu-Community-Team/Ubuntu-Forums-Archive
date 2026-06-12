---
title: "Mouse Problem on Dell Latitude D820"
date: 2008-08-10
forum: Hardware
---

### Post by lolov on 2008-08-10
Hi everybody

I want to use the trackpoint on my laptop as a mouse and the touchpad for scrolling (or as a mouse for girlfirend who doesn't like the nipple).
Anyway. The Problem is, if I enable the driver "synaptics", i have scrolling on the edge of the touchpad, but the trackpoint doesn't work. If i use the driver "mouse", the scrolling doesn't work, but both trackpoint and touchpad are usable. I searched the forums, but didn't find anything usable, although i tried a lot of variants. Here's the Mouse part from xorg.conf:
```

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse" 
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "yes"
    Option         "ZAxisMapping" "4 5"   
    Option         "SendCoreEvents" "true"
    Option         "HorizScrollDelta" "0" 
EndSection                                
Section "InputDevice"                     
        Identifier      "Configured Mouse"
        Driver          "mouse"                                                                                                                                                                                                              
        Option          "CorePointer"                                                                                                                                                                                                        
        Option          "Device"                "/dev/input/mice"                                                                                                                                                                            
        Option          "Protocol"              "auto"                                                                                                                                                                                       
        Option          "ZAxisMapping"          "4 5"                                                                                                                                                                                        
EndSection        
```

Any ideas? It would be nice to have horizontal and vertical scrolling as well. Thanks for any help!

---

