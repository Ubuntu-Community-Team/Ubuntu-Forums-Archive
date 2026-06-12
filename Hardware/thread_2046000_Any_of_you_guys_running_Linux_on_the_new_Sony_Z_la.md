---
title: "Any of you guys running Linux on the new Sony Z laptops?"
date: 2012-08-22
forum: Hardware
---

### Post by SuperMiguel on 2012-08-22
Any of you guys running Linux on the new Sony Z laptops?

---

### Post by SuperMiguel on 2012-08-23
bump specially looking for the touchpad settings

---

### Post by SimonBugs on 2012-09-01
I'm using the SV-Z1here311C5E. For touchpad, I've used this patch found [here]("http://ubuntuforums.org/showpost.php?p=11918367&postcount=18")

Also create this file:  /etc/X11/xorg.conf.d/51-clickpad.conf file.
```

Section "InputClass"
    Identifier "Default clickpad buttons"
    MatchDriver "synaptics"
    Option "SoftButtonAreas" "50% 6000 70% 5000 0 0 0 0"
        Option "AreaBottomEdge" "3800"
EndSection

```[FONT=Fixedsys]
[/FONT]
This makes the pad workable, but selecting is still not perfect, and when you rest a finger on one of the buttons (without clicking,  you cannot move the mouse. In windows this does work.

---

