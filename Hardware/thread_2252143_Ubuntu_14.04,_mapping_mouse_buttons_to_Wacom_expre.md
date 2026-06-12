---
title: "Ubuntu 14.04, mapping mouse buttons to Wacom express keys"
date: 2014-11-09
forum: Hardware
---

### Post by Naggobot on 2014-11-09
In ubuntu 12.04 I had Wacom Bamboo CTH-470 tablet buttons 1 and 3 mapped to mouse events 1 and 3. Mapping was done in startup with a script containing 

```

xsetwacom set "Wacom Bamboo 16FG 4x5 Finger pad" Button 1 1
xsetwacom set "Wacom Bamboo 16FG 4x5 Finger pad" Button 3 3

```

now in Ubuntu 14.04 after driver updates (see my post on [http://ubuntuforums.org/showthread.php?t=2244061](http://ubuntuforums.org/showthread.php?t=2244061)) the button mappings are working but buttons are not mapped as mouse events but as key strokes. 

i.e. if I press button 1 then number 1 is output to screen instead of mouse click. 

Is there a way to map express keys as mouse buttons in Ubuntu 14.04?

---

### Post by Naggobot on 2014-11-15
Solved using info from

[http://sourceforge.net/p/linuxwacom/mailman/message/32093263/](http://sourceforge.net/p/linuxwacom/mailman/message/32093263/)

My steps were

0. Install Gnome Ubuntu (probably not necessary)
1. Compile and install latest drivers
2. Navigate to 
org/gnome/settings-daemon/plugins/gsdwacom 

and disable the "active" key. 
3. Reboot
4. Use xsetwacom to setup keys from terminal. 
5. Save working configuration commands to .sh script
6. Set script to start up applications.
7. Reboot.

---

