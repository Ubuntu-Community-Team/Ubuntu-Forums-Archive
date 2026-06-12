---
title: "Synaptics Touchpad Adjustments Don't Work in Lucid"
date: 2010-05-01
forum: Hardware
---

### Post by clevertomato on 2010-05-01
[FONT=Verdana]There were several things I needed to adjust with my Synaptics Touchpad in Karmic. I successfully used the method found at [http://brettshaffer.com/blog/linux/multi-touch-touchpad-in-ubuntu-9-10/](http://brettshaffer.com/blog/linux/multi-touch-touchpad-in-ubuntu-9-10/) which uses [/FONT]
/etc/hal/fdi/policy/11-x11-synaptics.fdi

[FONT=Verdana]to adjust some settings. My custom settings are being ignored in Lucid (it's a fresh install, 64-bit). Any ideas?[/FONT]

---

### Post by dino99 on 2010-05-01
the package is xserver-xorg-input-synaptics, try to reconfigure it:

sudo dpkg-reconfigure xserver-xorg-input-synaptics

---

### Post by clevertomato on 2010-05-01
I tried as you suggested. I was asked for my password (because of sudo) then returned to a prompt. When I did synclient -l again afterward, no settings had changed. (I'm unfamiliar with dpkg-reconfigure.)

---

### Post by airmertana on 2010-05-02
I have the same problems and using dpkg didn't work. I'm assuming the custom adjustments don't work because HAL has been removed.

---

### Post by clevertomato on 2010-05-17
I learned about xinput. This worked for me. I made a file with xinput commands that I wanted, made it executable, and added a startup application for it. Sample file:

```
#!/bin/bash
#
# list of synaptics device properties http://www.x.org/archive/X11R7.5/doc/man/man4/synaptics.4.html#sect4
# list  current synaptics device properties: xinput list-props '"SynPS/2 Synaptics TouchPad"'
#
sleep 5 #added delay...
# xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 8 1
# xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 4
# xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 9         #     Below width 1 finger touch, above width simulate 2 finger touch. - value=pad-pixels
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Area" 0, 0, 0, 4800 # set sensitive area of touchpad - value=left, top, right, bottom
xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Edge Scrolling" 1 0 0       #     vertical, horizontal, corner - values: 0=disable  1=enable
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Jumpy Cursor Threshold" 300 #     stabilize 2 finger actions - value=pad-pixels
# xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Tap Action" 0 0 0 0 1 2 3   # pad corners rt rb lt lb tap fingers 1 2 3 (can't simulate more then 2 tap fingers AFAIK) - values: 0=disable 1=left 2=middle 3=right etc. (in FF 8=back 9=forward)
# xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 1 0   #     vertical scrolling, horizontal scrolling - values: 0=disable 1=enable
# xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Circular Scrolling" 1
# xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Circular Scrolling Trigger" 3

exit
```

---

### Post by VeeDubb on 2010-05-17
From a different thread on the same topic, if you have trouble with your script not auto-starting even when you add it to your Startup Applications list, try adding "sleep 10" right below the /bin/bash to make the script wait 10 seconds before executing.  That means you'll have to wait a few seconds after login to use any of the extra features of your touchpad, but it's much less likely to not load your settings that way.

---

