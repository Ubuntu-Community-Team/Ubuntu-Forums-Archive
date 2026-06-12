---
title: "HP DM3 laptop touchpad issues"
date: 2010-01-07
forum: Hardware
---

### Post by catswhiskers on 2010-01-07
HP DM3 laptop problem (Athlon Neo processor). 
1) Touchpad mouse works ok but not as a touchpad. HAL identifies it wrongly
  eg (II) config/hal: Adding input device ImPS/2 Generic Wheel Mouse. I've tried manually amending configuration file but that simply breaks the mouse driver. 
  
2) This model has a switch to isolate the touchpad.  LED is permanently lit and I am unable to see it being detected in log files or using lspci, am unable to turn it on/off either via software or hardware.

---

### Post by avilella on 2010-01-08
This has been reported as a solution by another HP dm3 series user to turn off the touchpad:
[http://ubuntuforums.org/showpost.php?p=8590673&postcount=9](http://ubuntuforums.org/showpost.php?p=8590673&postcount=9)

[http://launchpad.net/~hp-dm3](http://launchpad.net/~hp-dm3)

---

### Post by catswhiskers on 2010-01-09
Many thanks. My DM3 is now sweeter than ever. Just shows how stupid I am: because the LED was permanently on I didn't think to test if it was detected at all in X. KISS. Much appreciated.

---

### Post by MichaelRX8 on 2010-06-27
This fix no longer works for me on lucid...anybody got any ideas?

---

### Post by tyr14 on 2010-08-12
Works extremely fine with DM3 and Lucid Lynx x64

> **avilella said:**
> This has been reported as a solution by another HP dm3 series user to turn off the touchpad:
[http://ubuntuforums.org/showpost.php?p=8590673&postcount=9](http://ubuntuforums.org/showpost.php?p=8590673&postcount=9)

[http://launchpad.net/~hp-dm3](http://launchpad.net/~hp-dm3)

---

### Post by mescobal on 2010-11-23
Works fine with Ubuntu 10.10
You can also make press the switch when it asks for a combination of keys... then you get a fully functional device.

---

### Post by Votti on 2011-07-05
This script for **"Automatically disable touchpad when external mouse connected" ([http://ubuntuforums.org/showthread.php?t=1629433](http://ubuntuforums.org/showthread.php?t=1629433)) **works also like a charm for the DM3. Only two little adjustments have to be made:

This part of the code:

```
touchpadString="TouchPad"
touchpadID=$(xinput list | grep $touchpadString | awk -F " " '{print $6}' | awk -F "=" '{print $2}')
touchpadEnabled=$(xinput list-props $touchpadID | grep "Device Enabled" | awk -F ":" '{print $2}')
sleeptime=1
```has to be changed to:

```
[COLOR=#000000][COLOR=#FF8000]
[COLOR=Black]touchpadString="[COLOR=Red]PS/2 Mouse[/COLOR]"
touchpadID=$(xinput list | grep [COLOR=Red]"PS/2 Mouse"[/COLOR] | awk -F " " '{print [COLOR=Red]$[/COLOR][/COLOR][SIZE=4][COLOR=Red]5[/COLOR][/SIZE][COLOR=Black]}' | awk -F "=" '{print $2}')
touchpadEnabled=$(xinput list-props $touchpadID | grep "Device Enabled" | awk -F ":" '{print $2}')
sleeptime=1[/COLOR]
[/COLOR][/COLOR]
```(the change 6 to 5 could also be due to a change in xinput in ubuntu 11.04)

The only minor issue is, that it does not inactivate the touchpad when the mouse is already plugged in when you start your computer. I solved this by a little launcher on my desk, by which I can execute the "toggleTouchpad" command.

---

