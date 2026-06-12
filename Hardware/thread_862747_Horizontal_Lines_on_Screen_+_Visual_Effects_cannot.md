---
title: "Horizontal Lines on Screen + Visual Effects cannot be turned on"
date: 2008-07-17
forum: Hardware
---

### Post by anuragji on 2008-07-17
Hello,

I just installed Ubuntu 8.04 on my Lenovo n100 laptop. All went well, it just took a while to set up the dual monitor support, but after manually editing the xorg.conf file it all was working fine.

Then a day later, for no apparent reason at all (at least unbeknownst to me), two things started happening.

1) My screens started to show horizontal lines, which come and go. They seem to be right in the center of the desktop, so they show up on both screens, especially when scrolling.

2) The Visual Effects in the Desktop Appearance are switched off and cannot be turned on again.

Now I somehow assume that those two are related. I could not find a solution anywhere, thats why I am here. 

The laptop has an intel graphic card which shows up as a "Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller" in the device manager.

I don't have any propriatory drivers installed. Below is the display related part of the xorg.conf


```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "Intel"
        Option          "RandRRotation"         "on"
        Option          "RandR"                 "on"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection      "Display"
                Virtual 2560 1024
        EndSubSection
EndSection
```

Any suggestion on how to fix this issue is highly appreciated!

Anurag

---

### Post by anuragji on 2008-07-25
For whatever reason (maybe the weather - it was rather humid lately) the problem seems to have solved itself.

---

