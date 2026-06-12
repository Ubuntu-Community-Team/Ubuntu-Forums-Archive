---
title: "HP Spectre x360 TouchPad - Palm Rejection"
date: 2018-08-03
forum: Hardware
---

### Post by falonyn on 2018-08-03
Hey there. I have a late 2017 HP Spectre x360 with 8th gen Core i5. Everything works pretty well, though I don't usually use the touch screen, so perhaps there are some Gnome extensions I should research to make the a little more pleasant of an experience. For me, the palm rejection on the unusually wide trackpad. I have done everything in the settings/Gnome Tweaks to turn it on, and while I am actively typing, it does turn off the trackpad, but then the trackpad turns on again if I pause at typing at all. 

The one solution that I have found works for sure is to disable that half of the trackpad using synclient AreaRightEdge=4600. This disables enough that I can wrest my wrist on it and everything is fine. 

I would really prefer to not have to disable part of the trackpad, but apart from that, I would like to not have to run that command every time I start it up. Any suggestions? Thank you.

---

### Post by arm-c on 2018-10-26
Hello,

I too am having a lot of frustrations with the damn trackpad / clickpad.  Coming from running Linux on a Apple Macbook Air (2011), I was looking forward to the upgrade... and I do like a lot of things about this computer... but damn if the palm rejection aspect doesn't frustrate me to death.

I will be posting back as I start to dig-in on this more....

Another aspect that I think may be connected (or not) is that my use of libinput-gestures has mixed results.  My trackpad oddly appears to get stuck and cannot interpret three-finger swipes properly for a period of time and usually interprets them as either two finger scroll or pinches.  After a do a couple of 4-finger gestures... I can again execute 3-finger gestures.  It is with the trackpad and it's quirks (settings).  I have confirmed that while experiencing this weird behavior, a second apple trackpad (bluetooth) works flawlessly on the gesture recognition.

Lets keep this going to find some solutions.

---

### Post by arm-c on 2018-10-28
OK.

In general, libinput used to have no configuration options; however, recent versions have added ability to provide local over-rides.  These are called quirks and are well documented on the website:  
[https://wayland.freedesktop.org/libinput/doc/latest/touchpad-pressure-debugging.html]("https://wayland.freedesktop.org/libinput/doc/latest/touchpad-pressure-debugging.html")

Now, the specific approach; however, is designed to facilitate building a refined database of default settings, so you must customize the file to your specific hardware per instructions on that page.

I believe I have a version very close to what you reference (mine is i7 from late 2017 i believe).  Here are the contents of my local-overrides.quirks (path: /etc/libinput/local-overrides.quirks  
Create the path and file if you don't have one.

My file's contents are:

[Touchpad Pressure Override]
MatchUdevType=touchpad
MatchName=*SynPS/2 Synaptics TouchPad
MatchDMIModalias=dmi:*svnHP:pnHPSpectrex360Convertible15-bl1XX:*
AttrPressureRange=55:40
AttrPalmPressureThreshold=90
AttrThumbPressureThreshold=100


This touchpad still has quirks and issues to work through; however, this is like night and day now.   You will need to reboot to ensure they take effect.  Read the link above to learn more about customizing or building your own custom config.

---

