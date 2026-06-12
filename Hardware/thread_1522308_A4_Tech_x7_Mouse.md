---
title: "A4 Tech x7 Mouse"
date: 2010-07-02
forum: Hardware
---

### Post by do0b on 2010-07-02
Hey all, 

i'm trying to configure the extra buttons on my x7. i've looked through the forum and found: [http://ubuntuforums.org/showthread.php?t=336836](http://ubuntuforums.org/showthread.php?t=336836) 

they came up with a solution [http://tinyurl.com/5nvt5l](http://tinyurl.com/5nvt5l) but i'm stuck because my xorg.conf doesnt look or contain the same information like they have describe. here's is wat was printed out

```

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

```

instead of 
```
Section "InputDevice"
        [LEFT]Identifier      "Configured Mouse"[/LEFT] Identifier "Configured Mouse"
        [LEFT]Driver          "mouse"[/LEFT] Driver "mouse"
        [LEFT]Option          "CorePointer"[/LEFT] Option "CorePointer"
        [LEFT]Option          "Device"                "/dev/input/mice"[/LEFT] Option "Device" "/ dev / input / mice"
        [LEFT]Option         "Protocol"              "ImPS/2"[/LEFT] Option "Protocol" "IMPS / 2"
[LEFT]#      Option          "Emulate3Buttons"       "false"[/LEFT] # Option "Emulate3Buttons" "false"

[LEFT]EndSection[/LEFT] EndSection 
```

what am i doing wrong?

---

