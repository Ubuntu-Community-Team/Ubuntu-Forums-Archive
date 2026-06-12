---
title: "X Problems with Acer TravelMate 613TVX"
date: 2009-03-08
forum: Hardware
---

### Post by Zhengtonic on 2009-03-08
Hi there,
i have a little problem with X on my Acer TravelMate 613TVX. Maybe you guys have an idea. I recently installed 8.10 on the TravelMate and almost every thing except WiFi and X resolution worked out of the box. WiFi was expected and i think i can figure it out on my own, but X is really giving me a hard time. Resolutions up to 800x600 work well, but 1024x768 does not.

I played around a little bit,
but even this generic configuration
doesn't work. X tells me that there is not enough
video memory and switches to 640x480. 800x600 works with
the standard xorg.conf of 8.10.

```

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "de"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Configured Video Device"
        Monitor         "Configured Monitor"
        SubSection "Display"
                Virtual  1024  768
                Modes   "1024x768" "800x600" "640x480"
                Depth   24
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection

```

Does anyone of you have a working xorg.conf for the travelmate?
Thanks in advance!


Best regards,

Zhengtonic

---

