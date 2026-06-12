---
title: "Multitouch only working via Terminal enable"
date: 2011-05-08
forum: Hardware
---

### Post by dave1403 on 2011-05-08
Im running 11.04 on a Compaq Mini 110c.
When i go to Pointing Devices options and enable two finger scroll it doesn't work at all.
But if I enable two finger scrolling in the terminal it works perfectly (until the next reboot or hibernation). here is the commands i used:
> xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Two-Finger Scrolling" 8 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 8 1 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 32 10
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 32 8

got the code from this thread:
[http://ubuntuforums.org/showthread.php?t=1419833](http://ubuntuforums.org/showthread.php?t=1419833)

I created a script to run the command on startup, which works fine but if i put the laptop in hibernation and start it up again the script doesnt run and im left without scrolling.

it would be ideal to find out why the ubuntu pointing devices menu doesn't enable this feature properly.

any help would be much apreciated!

---

