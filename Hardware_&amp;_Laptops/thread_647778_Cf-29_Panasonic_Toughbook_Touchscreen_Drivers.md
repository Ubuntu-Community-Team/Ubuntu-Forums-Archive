---
title: "Cf-29 Panasonic Toughbook Touchscreen Drivers"
date: 2007-12-22
forum: Hardware &amp; Laptops
---

### Post by n00-B-1 on 2007-12-22
Greeting and happy HO-HO etc.I am completely noob to linux I have recently installed  7.1 along with XP Pro.(no divorce from winblos yet)The question I have is there someone out there who can help with the touchscreen driver for Panasonic CF-29 or a tut on configuring the pointing device or whatever.Again I am complete NOOB :)
                        THANX in Advance:confused:

---

### Post by bwhite82 on 2007-12-22
Touchscreen or touchpad?

Relevent page in the wiki for your laptop:

[https://wiki.ubuntu.com/LaptopTestingTeam/PanasonicTBCF29]("https://wiki.ubuntu.com/LaptopTestingTeam/PanasonicTBCF29")

Is it a synaptic touchpad?

[https://help.ubuntu.com/community/InputDevices]("https://help.ubuntu.com/community/InputDevices")

---

### Post by n00-B-1 on 2007-12-22
Touchscreen does not function .Any help much much appreciated.
                            THANX Again!!!!!!!!!!!!!!:confused:

---

### Post by ANNbot on 2007-12-28
I am also using a CF-29 running both Ubuntu and Kubuntu desktops. I am down to fixing three things that are to help me switch completely from Windows. 1) Sound, 2) GPS, 3) touchscreen. I am currently running Fiesty 7.04.

As a side note, this forum has been great to solve issues. I have used it to resolve any issues todate (sync Palm PDA, find excellent opensource software for Ubuntu, etc.)...hats off to all those that respond to the noobie questions

Yep, I am noobie....

---

### Post by idlewild on 2007-12-30
If you look in System->Preferences->Hardware Information there should be a USB Touch Panel. Look at linux.device_file at the lowest entry under USB Touch Panel. To get it to work you'll need xserver-xorg-input-evtouch from synaptic. 

To configure it you need to modify /etc/X11/xorg.conf

Add a new section
```
Section "InputDevice"
        Identifier      "Touch Screen"
        Driver          "evtouch"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/input/event2"
        Option          "MinX"                  "500"
        Option          "MinY"                  "1200"
        Option          "MaxX"                  "15555"
        Option          "MaxY"                  "15936"
        Option          "SwapX"                 "0"
        Option          "SwapY"                 "0"
EndSection
```
Change Device to the device file found earlier.

In ServerLayout section insert 
```
        InputDevice     "Touch Screen"

```

Calibrating the touchscreen is a little tricky I use a program called evtest, you can download the source off the net.

---

### Post by tscreenhelp on 2008-02-26
hey i want to get a panasonic toughbook cause it has the touchscreen capabilities but i wanna make sure if i get one that i can use ubuntu on it and utilize the touchscreen   does anyone have a definite fix that will calibrate it and make it usable?

---

### Post by ballin on 2008-05-22
I had it working perfectly in 7.10 but in 8.04 I can't get it going yet.

A strange thing is /proc/bus/input/devices shows 2 devices for the touchscreen and touchpad, ie.

touchpad = mouse1 event7
touchscreen = mouse2 event8

Not sure if that matters but I can't get it working regardless.

(Out of the box/fresh install touchscreen works which is a bonus over 7.10, but its just not calibrated which is what I can't figure)

---

### Post by ballin on 2008-06-06
anybody had any luck getting it to work?

---

