---
title: "Monitor resolution undetected"
date: 2009-11-03
forum: Hardware
---

### Post by pjs59 on 2009-11-03
I have a Samsung T220 connected to the DVI port on my NVIDIA card. I can't get Ubuntu to recognise the monitor's native resolution, which is 1680x1050. It defaults at 1024x768, and will only go as high as 1280x1024. I've tried following this: [https://wiki.ubuntu.com/X/Config/Resolution#Resetting%20an%20out-of-range%20resolution](https://wiki.ubuntu.com/X/Config/Resolution#Resetting%20an%20out-of-range%20resolution), but when I try to apply the new resolution in System > Preferences > Display I get a message saying "The selected configuration for displays could not be applied. Could not set the configuration for CRTC 321"

xrandr -q gives:

Screen 0: minimum 320 x 175, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       50.0*    51.0     52.0     53.0     54.0     55.0  
   960x720        56.0  
   960x600        57.0  
   960x540        58.0  
   928x696        59.0  
   896x672        60.0     61.0  
   840x525        62.0     63.0     64.0     65.0     66.0  
   832x624        67.0  
   800x600        68.0     69.0     70.0     71.0     72.0     73.0     74.0     75.0     76.0     77.0  
   800x512        78.0  
   720x450        79.0  
   720x400        80.0  
   700x525        81.0     82.0     83.0     84.0  
   680x384        85.0     86.0  
   640x512        87.0     88.0     89.0  
   640x480        90.0     91.0     92.0     93.0     94.0     95.0     96.0     97.0  
   640x400        98.0  
   640x350        99.0  
   576x432       100.0    101.0    102.0    103.0    104.0    105.0    106.0  
   512x384       107.0    108.0    109.0    110.0    111.0  
   416x312       112.0  
   400x300       113.0    114.0    115.0    116.0    117.0  
   360x200       118.0  
   320x240       119.0    120.0    121.0    122.0  
   320x200       123.0  
   320x175       124.0  

xorg.conf looks like:

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


[What's especially odd is that this is a replacement monitor for the previous (identical) one which broke - but the resolution worked fine on previous one.]

Thanks for any help.

---

