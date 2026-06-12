---
title: "Rat 3 mouse not working...?"
date: 2013-03-16
forum: Hardware
---

### Post by -RYknow on 2013-03-16
Hey guys, looking for some assistance. I just picked up a Rat 3 mouse and can't seem to get it working. Google proves to me that I'm not the only one, and the popular fix (listed below) doesn't seem to fix my issue. Apparently the issue has something to do with the mode button causing an issue. When I plug the mouse in, it will work fine for the first two minutes. Then it gets all screwy. The mouse will move around on the screen but none of the buttons do anything. The fix I found listed elsewhere suggested editing the xorg.conf and adding this:

```
Section "InputClass"
    Identifier      "Mouse Remap"
    MatchProduct    "Saitek Cyborg R.A.T.7 Mouse"
    MatchDevicePath "/dev/input/event*"
    Option      "ButtonMapping" "1 2 3 4 5 6 7 8 9 10 11 12 0 0 0"
EndSection
```

While others using this solution seem to have some success, I'm getting nothing. I'm hoping that someone here can help me out. 

Running:
```
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.2 LTS
Release:	12.04
Codename:	precise
```

hmmm, not that it makes a big difference? But I'm running xubuntu.

Thanks, 
-RYknow

---

### Post by -RYknow on 2013-03-17
I also just found a thread that suggested this change to xorg:

```
Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "evdev"
    Option         "Name" "Saitek Cyborg R.A.T.3 Mouse"
    Option         "Vendor" "06a3"
    Option         "Product" "0ccc"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/input/event4"
    Option         "Emulate3Buttons" "no"
    Option         "Buttons" "7"
    Option         "ZAxisMapping" "4 5"
    Option         "ButtonMapping" "1 2 3 4 5 6 7 0 0 0 0 0 0 0"
    Option         "Resolution" "3200"
EndSection
```

This also doesn't work for me. The mouse will work perfectly fine for about 2 minutes, then buttons stop working. I have a few different launchers in panels that I can't click, but things on the desktop still work just fine. Sometimes I can click the launchers in the panels but nothing on the desktop. As soon as I disconnect this mouse, everything works perfectly fine. 

Any suggestions?
-RYknow

---

### Post by elpiloto on 2013-04-08
this worked for me, but the foward and back buttons seems to dont work :s

[http://ubuntuforums.org/showthread.php?t=2095829](http://ubuntuforums.org/showthread.php?t=2095829)

---

