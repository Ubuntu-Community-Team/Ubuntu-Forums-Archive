---
title: "Another Touchscreen calibration question"
date: 2013-06-22
forum: Hardware
---

### Post by alexlow8 on 2013-06-22
I am new to the Ubuntu family, so I may have missed something glaring obvious.  I have been able to calibrate my touch-screen using the xinput calibration tool on 10.04 (Unfortunately the software the machine has been built to run is not compatible with 12.xx) but I have not been successful in getting the changes to stick after a reboot.  I was able to acomplish this in 12.04 after following suggestions in other forums and editing the xorg config file.  I have been unable to locate a similar config file in 10.04.

I can get the touch-screen cofigured again by executing the following command in a terminal window, but I have to connect a mouse in order to open the terminal in the first place, as without calibration I cannot access the edges of the touch-screen.

xinput set-prop 9 "Evdev Axis Calibration" 117 912 136 866

As I can see there are two ways to fix my issue.
1. Find the appropriate config file to edit.
or
 2. Have the system execute the above terminal command on startup. - As mentioned earlier I am completely new to Ubuntu and don't have a clue how to get it to do so.

Any help will be met with great praise and personal kudos.

I posted too soon, found a config file. It is in a different location with a different name, and editing it does not appear to have any effect.

Config file edited on 12.04 was:** /usr/share/X11/xorg.conf.d/10-evdev.conf**

In 10.04 I found and edited: /usr/lib/X11/xorg.conf.d/05-evdev.conf

---

### Post by alexlow8 on 2014-03-16
This project has been on the back burner for a while now, I just resurrected it the other week and was successful in getting the xinput calibration script to run at start-up by adding an entry in startup applications and entering the script as the command.  Works brilliantly.

---

