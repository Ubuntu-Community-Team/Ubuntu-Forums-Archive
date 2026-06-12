---
title: "Make touchpad more senesitive"
date: 2007-12-25
forum: Hardware &amp; Laptops
---

### Post by PurposeOfReason on 2007-12-25
The current part of my xorg.conf reads as follows:
```
 Section "InputDevice"
   Driver      "synaptics"
   Identifier  "TouchPad"
   Option      "SendCoreEvents"
   Option      "Protocol" "auto-dev"
   Option "FingerLow" "25"
   Option "FingerHigh"	"30"
   Option "MaxTapTime"	"110"
   Option "MaxTapMove"	"220"
   Option "MinSpeed" "0.60"
   Option "MaxSpeed" "0.65"
   Option "TapButton1" "1"
   Option "TapButton2" "3"
   Option "TapButton3" "2"
   Option      "SHMConfig" "on"
 EndSection
```

I would like to make tapping more sensitive (like respond quicker, it is already a light tap) as it's disabled while I type so it's not going to bother me there. Also, if it's possible, I'd like to be able to middle click (three fingers) and right click(two fingers) tap with multiple fingers instead of like right now where I have to use corners for that.

---

### Post by SomeStupidHippie on 2007-12-26
Open up your applications manager and search for touchpad, there should be a little utility for setting the preferences.... I cant say I've ever used it before, but you might give it a shot and see if its what youre looking for:)

---

### Post by PurposeOfReason on 2007-12-26
I've tried gsynaptics and that didn't work. But I had to get that separate as I'm on arch. :)

---

### Post by ugm6hr on 2007-12-26
This might help:
```
Option "FastTaps" "1"
```

You also seem to have the TapButton options set already.

This will help you to find more information:
[http://ubuntuforums.org/showpost.php?p=3105368&postcount=2](http://ubuntuforums.org/showpost.php?p=3105368&postcount=2)

---

