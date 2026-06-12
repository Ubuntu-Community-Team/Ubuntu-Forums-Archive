---
title: "xorg file does not work w/o monitor"
date: 2011-03-07
forum: Hardware
---

### Post by bonfire89 on 2011-03-07
Hi there, every time I get home from school I have to re-enable my xorg and when I get to school I have to disable it (by renaming it) because the xorg file does not work without a monitor attached.

I'm using Ubuntu 10.10 and have Intel HD graphics on a Dell E6410.

Is there an issue in my xorg file, or is there a way that I can dynamically load it upon boot?

Here is the file.

```
Section "Device"
       Identifier      "Intel 945G "
      Driver         "intel"

       # Using the name of the output defined by the video driver plus the identifier of a
       #     monitor section, one associates a monitor section with an output by adding an
       #     option to the Device section in the following format:
       #     Option "Monitor-outputname" "monitor ID"
       Option          "monitor-VGA1" "foo"
EndSection

Section "Monitor"
       Identifier      "foo"
       Modeline        "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
       Option          "PreferredMode" "1440x900_60.00"
EndSection

Section "Screen"
       Identifier    "Default Screen"
       Device        "Intel Corporation 945G Integrated Graphics Controller"
       Monitor       "foo"
       DefaultDepth  24
       SubSection "Display"
               Depth          24
               Modes         "1440x900"
       EndSubSection
EndSection
```


thanks a bunch :)

---

### Post by bonfire89 on 2011-03-12
bumpity bump :)

---

