---
title: "Laptop Resoultion on Login Screen"
date: 2008-08-18
forum: General Help
---

### Post by ilovelinux33467 on 2008-08-18
Hello I have installed ubuntu 8.04.1 on my laptop. I have changed the resoultion to the laptops native resoultion (1400x1050 -- Laptop is Compaq Evo N800v). When i am logged on the resolution is fine but when it is on the login screen the resolution is wrong it it looks quite strange. How would I solve this so the login screen resolution was also 1400x1050?


Thanks

---

### Post by Dejavou42 on 2008-08-18
Define quite strange..... If possible please post a screenshot

---

### Post by Too Late on 2008-08-18
It's a common problem. [http://ubuntuforums.org/showthread.php?t=891938](http://ubuntuforums.org/showthread.php?t=891938)
Editing the xorg.conf usually solves the problem (but not in that case).

---

### Post by ilovelinux33467 on 2008-08-18
I have already tried editing xorg.conf but still no luck :(

---

### Post by cdtech on 2008-08-18
You have to have a "virtual" setting within your "xorg.conf" file such as I have here:
```
Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "NoLogo" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        **Virtual     1440 900**
        Depth       24
        Modes      "1440x900"
    EndSubSection
EndSection
```

Hope this helps.....

---

### Post by ilovelinux33467 on 2008-08-18
I have already tried putting the virtual line xorg.conf. That didn't work either :mad:

---

### Post by greatscott on 2008-11-08
This should work.

```
sudo gedit /etc/gdm/Init/Default
```

Go the end of the file and add this before the exit 0 line:
```
xrandr -s 1400x1050
```

Now the resoultion of GDM will be 1400x1050.

---

