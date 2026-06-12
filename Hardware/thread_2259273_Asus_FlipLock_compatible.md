---
title: "Asus FlipLock compatible ?"
date: 2015-01-03
forum: Hardware
---

### Post by raphael7 on 2015-01-03
Hi :) excuse me for my english,

I have a TP300LA, a 13inch asus laptop, that have a touche screen, a g sensor and a windows software that auto-lock keyboard/pad when rotating screen like that: [http://www.conrad.com/medias/global/ce/8000_8999/8000/8050/8059/1221166_ZB_01_FB.EPS_1000.jpg](http://www.conrad.com/medias/global/ce/8000_8999/8000/8050/8059/1221166_ZB_01_FB.EPS_1000.jpg) (use g-sensor i guess)

Asus FlipLock can be found here: [http://dlcdnet.asus.com/pub/ASUS/nb/Apps_for_Win8.1/ASUS_FlipLock/ASUS_FlipLock_Win81_64_VER105.zip](http://dlcdnet.asus.com/pub/ASUS/nb/Apps_for_Win8.1/ASUS_FlipLock/ASUS_FlipLock_Win81_64_VER105.zip)

I'm downloading ubuntu right now so I'll try things by myself but do you think that I could make somethink like Asus FlipLock on ubuntu ?

thanks

---

### Post by Tuxclear on 2015-01-03
That's a good question: Does Ubuntu support tablet-PC's that run Windows? See here for yourself:
[http://ubuntuforums.org/showthread.php?t=2214936](http://ubuntuforums.org/showthread.php?t=2214936)

---

### Post by raphael7 on 2015-01-03
thanks, touch screen work but not auto rotation :/

---

### Post by Tuxclear on 2015-01-04
There is a script that enables the rotation, but unfotunately it may not support your vendor. Do you want to try it?
[http://ubuntuforums.org/showthread.php?t=2116275](http://ubuntuforums.org/showthread.php?t=2116275)

---

### Post by mdbarton on 2015-12-04
A bit late, I too have an Asus TP300LA, recently acquired.  I've not been able to automate this when you flip the screen round to tablet mode, but I have created the following script that you can run to toggle the physical keyboard and trackpad with Ubuntu's Onboard Keyboard.  Touchscreen remains on. I've created an icon for this which I tap before flipping.  The device and property codes should be fine, but there are instructions at the links that will tell you how to find them out if there is a difference on your setup.

[FONT=Courier New]#!/bin/sh
#toggle keyboard and touchpad.  Based on [http://unix.stackexchange.com/questions/103230/capturing-key-input-from-events-device-and-mapping-it-toggle-touchpad-key-is-un](http://unix.stackexchange.com/questions/103230/capturing-key-input-from-events-device-and-mapping-it-toggle-touchpad-key-is-un)
key_device=12
key_property=139
touch_device=13
touch_property=139
flipped_state=$(xinput list-props "$key_device" |
                awk "/\\($key_property\\)/ {print 1 - \$NF}")
xinput set-prop "$touch_device" "$touch_property" "$flipped_state"
xinput set-prop "$key_device" "$key_property" "$flipped_state"
#toggle onboard: based on [http://bazaar.launchpad.net/~onboard/onboard/trunk/view/head:/README](http://bazaar.launchpad.net/~onboard/onboard/trunk/view/head:/README)
dbus-send --type=method_call --dest=org.onboard.Onboard /org/onboard/Onboard/Keyboard org.onboard.Onboard.Keyboard.ToggleVisible[/FONT]

---

