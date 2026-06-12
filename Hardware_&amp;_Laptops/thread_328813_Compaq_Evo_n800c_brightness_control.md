---
title: "Compaq Evo n800c brightness control"
date: 2006-12-31
forum: Hardware &amp; Laptops
---

### Post by pabloyepes on 2006-12-31
I have been running kubuntu on my compaq evo n800c for a few weeks, and overall I am quite satisfy.
I have two issues I have not figured out
1) I cannot control the screen brightness. Actually when the laptop is on battery power the screen is brighter than when it is on AC. So the system has some control over the brightness of the screen. 
2) When the computer boots the fan is on for "ever", until the CPU temperature increases a certain level (around 50C) and then cools down again. The the fan stops. But if the CPU temp does not increase (CPU is idle) the fan is on for "ever". My solution is to start a dummy process to bring the CPU Usage to 100% until the temperature reaches 50C, then stop the process and let the CPU cool down.

Any help would be appreciated. 

Pablo

---

### Post by skale on 2006-12-31
There's a good chance the brightness is not controlled by the OS, but in the bios setup.  Reboot, and press the key for "SETUP" or the equivalent (F2 on my laptop) Look for the settings for brightness there.

Section two, I have no idea.

---

### Post by pabloyepes on 2006-12-31
I checked the bios, and I could not find any controls for the brightness. Thank you for trying anyway.

Py

---

### Post by 900i on 2007-01-01
Ok, go into terminal and enter

gconf-editor

goto apps>gnome-power-manager

In right hand pane scroll to battery_brightness, and double click and change value.

---

### Post by pabloyepes on 2007-01-01
Interesting, I did not know about that control. 
I did change the values of ac_brightness and battery_brightness. Actually they were set to ac_brightness=100 and battery_brightness=70. However I see the opposite (battery brighter than ac). Nothing happened. I rebooted and nothing happened either. 
I am using Kubuntu, I don't know whether that is a factor. 
Thank you anyway, and happy new year!

Pablo

---

### Post by pabloyepes on 2007-01-05
I could not acpi to control the LCD brightness, but using the xorg.conf setting from [http://www.ailis.de/~k/docs/evon800c/](http://www.ailis.de/~k/docs/evon800c/), I could get the brightness keys (Fn 7 and Fn 8) to work.

---

