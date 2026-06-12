---
title: "Problems with Logitech MX900 Dongle and Apple Bluetooth Keyboard"
date: 2009-05-03
forum: Hardware
---

### Post by gnat man on 2009-05-03
I am trying to use the charging station that came with my Logitech MX900 as a bluetooth dongle, and it seems to be able to connect to the mouse just fine, but the keyboard is another story.

The first connect went just fine, but then when the batteries drained, and it lost it's connection, it would not reconnect.  I have been playing around with this for a long time, and it seems that I can get it to work if I run:

sudo hid2hci
sudo hidd --search (or sudo hidd -connect KEYBOARD_ADDRESS)

However even that only works 50% of the time, and I sometimes have to power cycle the keyboard.  This isn't an ideal situation, because I really just want my keyboard to be completely wireless, so I can't be inputting commands to get it to detect and fighting with it every time.

I am running Ubuntu 9.04, Jaunty Jackalope.

Do I need to get a new dongle?  It seems that my keyboard works just fine with my Macbook Pro.  I would like to try clearing away all the bluetooth preferences on Ubuntu to start from scratch (I've been fiddling with it a lot) but I've tried to completely remove the bluetooth packages, and when I reinstall them, I still see the keyboard still listed in the "known devices" section.

Any help or advice would be appreciated.

---

