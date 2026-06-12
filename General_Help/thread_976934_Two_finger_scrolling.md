---
title: "Two finger scrolling"
date: 2008-11-09
forum: General Help
---

### Post by austin512 on 2008-11-09
How can I enable two finger scrolling for my touchpad like on Macs? I'm using Ubuntu 8.10, so from what I've read, I don't think I have to edit my xorg.conf, but that I should make an .fdi file in /etc/hal/fdi/policy. But no matter what I do, I can't use synclient because it yells at me saying I have SHMConfig disabled.

My touchpad was able to detect multifinger taps in Windows fine, so the hardware is definitely capable. My Synaptics driver is 0.15.2-0.

---

### Post by spupy on 2008-11-09
In /etc/X11/xorg.conf, in the touchpad section, add this line:
```
Option      "SHMConfig" "on"
```
It enables you to config the touchpad without restarting X - using synclient, gsynaptics, etc.

---

### Post by edgaruy1980 on 2008-11-10
[http://ubuntuforums.org/showpost.php?p=6077309&postcount=121](http://ubuntuforums.org/showpost.php?p=6077309&postcount=121)
it's different in the 8.10 than 8.04.
 : (

---

### Post by viralata00 on 2009-04-29
hello,

still can't get the two fingers working! but the SHMConfig is on...
How do I know if my touchpad suports two finger scrolling?

---

### Post by luopio on 2010-05-07
My two-finger-scroll-option was also greyed out, but there's a fix here: 
[http://swiss.ubuntuforums.org/showthread.php?t=1419833&page=2](http://swiss.ubuntuforums.org/showthread.php?t=1419833&page=2)

basically you just need to use xinput --set-prop. If anyone comes up with a valid udev-rule-file, I'd gladly switch to using that :)

---

