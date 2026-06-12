---
title: "BTC 5213URFII mouse troubles"
date: 2006-04-16
forum: Hardware &amp; Laptops
---

### Post by Tiak on 2006-04-16
I recently got a BTC 5213URFII wireless USB mouse/keyboard combo as a gift, and that's all well and good...  Except none of my clicking buttons actually work on said mouse.  Now, the scroll wheel works with mose PS/2 protocols, and I haven't noticed a single problem  with mouse movement....  But no clicking of buttons 1-3 at all.

Said missing clicking doesn't show up in xev, /dev/input/mice, or /dev/input/mouse0, but does interestingly enough send stuff to /dev/input/event2 and /dev/input/ts0.  I've tried every xorg.conf setup under the sun for mice I can figure out, and nothing seems to work...   Right now I'm just ignoring the problem and am using xmodmap to make my scrollwheel up/down left click/right click, but I can't do this forever, it's supremely annoying...  X.org hasn't generated any errors in its log file...  That's about all I can think of to say, if people want more information, just ask...

And yes, I've already looked for information and can't find any...  I've read enough about linux mice by now that I could likely configure one of them niftier logitechs with my feet blindfolded...

Here are my relevant parts of my xorg.conf (I've switched between the commented out and non comment a couple times changing stuff):
> 
#Section "InputDevice"
#       Identifier      "Configured Mouse"
#       Driver          "mouse"
#       Option          "CorePointer"
#       Option          "Device"                "/dev/input/mice"
#       Option          "Protocol"              "ImPS/2"
#       Option          "ZAxisMapping"          "4 5"
#EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "Protocol"              "evdev"
        Option          "Dev Name"              "BTC USB Multimedia Cordless Kit"
        Option          "Dev Phys"              "usb-0000:00:10.0-1/input1"
        Option          "Device"                "/dev/input/event2"
        Option          "Buttons"               "5"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "ServerLayout"
        Identifier         "Default Layout"
        Screen            "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection



PS:That was really annoying to copy being that I was editing it in vi, and selecting text without being able to drag in my terminal window wasn't working out too well...  *mutters*

---

