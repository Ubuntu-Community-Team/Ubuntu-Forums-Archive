---
title: "GE Dual Scroll Mouse (HO97769 rev. 2) not working well"
date: 2005-12-31
forum: Hardware &amp; Laptops
---

### Post by jake on 2005-12-31
Hi recently bought a new mouse.  A GE Ergonomic Dual Scroll Optical Mouse, model number HO97769 rev. 2, from Target.  This mouse has dual scroll wheels although only one can be pressed as a button and forward an back buttons on the side.  The mouse is a USB interface and works with Kubuntu as you would expect a standard scroll mouse to work, but the extra buttons don't work.  I found an old thread for Hoary that I thought would help me.

[http://ubuntuforums.org/archive/index.php/t-22203.html]("http://ubuntuforums.org/archive/index.php/t-22203.html")

I thought I followed the directions near the bottom of the thread that would produce the desired results.  However, when I restarted X to see what I had.  It looked fine until I attempted to move the mouse and then the X server would hang.  Does anybody have one of these mice that they have successfully gotten to work with Ubuntu.  I really don't care much if the second scroll wheel doesn't work, but I'd really love to have the forward and back buttons.  The pertinent portions of my xorg.conf file are posted below.

```
Section "InputDevice"
       Identifier      "Configured Mouse"
       Driver          "mouse"
       Option          "Potocol"               "evdev"
       Option          "Dev Name"              "A4Tech USB Optical Mouse"
       Option          "Dev Phys"              "usb-0000:00:10.0-2/input0"
       Option          "Device"                "/dev/input/event1"
       Option          "Buttons"               "9"
       Option          "ZAxisMapping"          "4 5"
EndSection

```
Thanks for any help

Jake

---

### Post by yangeryanger on 2007-12-25
heh, I just got the GE Ergonomic Dual Scroll Optical Mouse, model number HO97769 rev. **3** ... works right out of the box, kinda... like you have, the side buttons don't work, and the horizontal scroll doesn't work (actually scrolls vertically, same as the vertical scroll wheel) ... will try what you have and see what it does in a bit... ;)

---

