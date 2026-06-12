---
title: "Synaptics Touchpad - Disabling Tapping"
date: 2007-07-05
forum: Hardware &amp; Laptops
---

### Post by commike37 on 2007-07-05
I upgraded from Edgy to Feisty via a fresh install.  In Edgy, I disabled tapping and the like for the Synaptics Touchpad in xorg.conf with the "TouchpadOff" option set to 2.  In Feisty, I did the same thing, but after a while, tapping will start to work again.  It seems like given enough time, the touchpad will break and somehow enable tapping.

---

### Post by kerry_s on 2007-07-05
```
**Option		"MaxTapTime"		"0"**
```

---

### Post by commike37 on 2007-07-07
I gave that solution a try, but it did not work as I had suspected.  If it was just a matter of modifying xorg.conf, then disabling tapping in xorg.conf with the "TouchpadOff" option should have solved the problem in the first place.  It appears like some sort of touchpad failure is causing the settings in xorg.conf to be reset or something like that.

---

### Post by drpaul on 2007-07-07
I have the MaxTapTime option in my conf [on Edgy] and it has reenabled the tapping action after a month or two??????

Paul

---

### Post by strabes on 2007-07-07
Post your xorg.conf in here please

---

### Post by commike37 on 2007-07-27
Sorry I kind of forgot about this thread.  But if anyone sees this, here's the xorg.conf excerpt

```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "TouchpadOff"           "2"
EndSection
```

It's probably worth mentioning to that this problem only happens in Feisty.  I've had no such problems when I had Dapper or Edgy.

---

### Post by commike37 on 2007-07-27
Actually, I think I found something that popped up in another thread while I ignored this one for two weeks :P

[http://ubuntuforums.org/showthread.php?t=493601&highlight=synaptics+tapping](http://ubuntuforums.org/showthread.php?t=493601&highlight=synaptics+tapping)

Apparently the infamous Broadcom wireless chip and fwcutter are the culprit.

But if anyone sees anything else that could be wrong, please point it out.

---

