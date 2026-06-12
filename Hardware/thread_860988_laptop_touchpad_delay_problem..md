---
title: "laptop touchpad delay problem."
date: 2008-07-16
forum: Hardware
---

### Post by kienseng on 2008-07-16
i'm a new user here, using Ubuntu 8.04...

whenever i use my touchpad to click, it will have a delay after i click on the touchpad, but i dont have this problem when i'm using window XP, any solutions to decrease the delay time?

---

### Post by stats on 2008-07-16
1. backup your xorg.conf
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```

2. ```
gksudo gedit /etc/X11/xorg.conf
```

3. Find the section 
```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        ....
        ....
EndSection
```

4. Add the lines

  ```
Option          "SHMConfig"             "on"
  Option          "FastTaps"             "1"
```

before the EndSection line

save the file

5. Restart X with ctrl-alt-backspace

---

### Post by kienseng on 2008-07-16
sry, it doesn't help, still the same....

---

### Post by animesh nath on 2008-07-16
> **kienseng said:**
> sry, it doesn't help, still the same....

  re my laptop touchpad doesn,t work at all can any body help me please

---

