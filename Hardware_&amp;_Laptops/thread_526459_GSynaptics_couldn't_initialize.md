---
title: "GSynaptics couldn't initialize"
date: 2007-08-15
forum: Hardware &amp; Laptops
---

### Post by Durmant on 2007-08-15
version: 0.9.7-3
Ubuntu 7.04 Feisty

when trying to launch GSynaptics I get an error:

GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics

I have already add that option to xorg.conf under the touchpad section.

I have a toshiba satellite 5105 with a synaptics cpad

---

### Post by ugm6hr on 2007-08-15
Have you restarted X?

Ctrl-Alt-Backspace should do it

If that doesn't work - you've not done the xorg.conf edit properly - post the contents here for us to look at.

---

### Post by Christof999 on 2007-08-15
Ive got the exact same problem. I edited the Xorg.conf properly. but still it asks me to turn on shared memory. 

Whats the exact line that must be added to xorg.conf ?

---

### Post by Durmant on 2007-08-15
Ive restarted the computer probably 15 times over the past day


Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "on"
EndSection


Ive have also tried putting yes....and "true" and "TRUE" and "True" lol

Oh ya I also added teh synaptics touchpad to the server layout section...

---

### Post by ugm6hr on 2007-08-15
That looks OK....

Have you put the settings in the other sections:
Inputdevice	"Synaptics Touchpad" (in ServerLayout)
Load		"synaptics" (in Module)

---

### Post by Durmant on 2007-08-15
yes....I put it into server layout and I put it into module but saw no change...

---

### Post by Durmant on 2007-08-16
bumpity bump bump bump

---

### Post by mrbrune on 2007-08-17
!!!!!!!

---

### Post by mrbrune on 2007-08-17
Try this and it should work if you are using a synaptics touchpad:

Edit your xorg.conf file using your root terminal type the following:
[I]
sudo gedit /etc/X11/xorg.conf[/I]

Insert the following section in the xorg.conf file

Section "InputDevice"
Driver "synaptics"
Identifier "touchpad"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "LeftEdge" "1700"
Option "RightEdge" "5300"
Option "TopEdge" "1700"
Option "BottomEdge" "4200"
Option "FingerLow" "25"
Option "FingerHigh" "30"
Option "MaxTapTime" "180"
Option "MaxTapMove" "220"
Option "VertScrollDelta" "100"
Option "MinSpeed" "0.09"
Option "MaxSpeed" "0.18"
Option "AccelFactor" "0.015"
Option "SHMConfig" "on"
Option "Emulate3Buttons" "on"
EndSection

and then, tell the ServerLayout about your new device, go to the Section "ServerLayout" and add the following like just before EndSection:

InputDevice "touchpad" "AlwaysCore"

Now you need to restart X. Make sure you save all your work, because restarting X will log you out. Now press ctrl-alt-backspace. Login and you should now be able to run System/Preferences/Touchpad.

Awaiting your feedback :-)

---

### Post by rafaelnonato on 2007-09-09
That worked fine on my Acer Aspire 5000. Only one weird harmless thing worth of telling happened -- when Gnome restarted, it said it couldn't open Nautilus. I restarted it again and ever since the touchpad scroll works (Nautilus too). Thanks.

---

### Post by maddentim on 2007-09-26
I was having the same issue.  Just adding the option:

Option "SHMConfig" "on"

to my xorg.conf file was all it took.  

Not sure why it was not there to start!!!  arggg.  

Saw this post in Ubuntu Blog that said the option allowed some configuration parameters to be changed without restarting xorg.

[http://ubuntu.wordpress.com/2006/03/24/disable-synaptics-touchpad/](http://ubuntu.wordpress.com/2006/03/24/disable-synaptics-touchpad/)

---

### Post by MrWhipplesNipple on 2007-10-26
> **mrbrune said:**
> Try this and it should work if you are using a synaptics touchpad:

Edit your xorg.conf file using your root terminal type the following:
[I]
sudo gedit /etc/X11/xorg.conf[/I]

Insert the following section in the xorg.conf file

Section "InputDevice"
Driver "synaptics"
Identifier "touchpad"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "LeftEdge" "1700"
Option "RightEdge" "5300"
Option "TopEdge" "1700"
Option "BottomEdge" "4200"
Option "FingerLow" "25"
Option "FingerHigh" "30"
Option "MaxTapTime" "180"
Option "MaxTapMove" "220"
Option "VertScrollDelta" "100"
Option "MinSpeed" "0.09"
Option "MaxSpeed" "0.18"
Option "AccelFactor" "0.015"
Option "SHMConfig" "on"
Option "Emulate3Buttons" "on"
EndSection

and then, tell the ServerLayout about your new device, go to the Section "ServerLayout" and add the following like just before EndSection:

InputDevice "touchpad" "AlwaysCore"

Now you need to restart X. Make sure you save all your work, because restarting X will log you out. Now press ctrl-alt-backspace. Login and you should now be able to run System/Preferences/Touchpad.

Awaiting your feedback :-)
mrbrune: thanks for the instructions, I was having the same problem with Gsynaptics on my laptop and your method fixed it.  Yippee!

---

### Post by yam125 on 2007-12-20
I changed the Xorg and now it won't boot!

I don't know how to edit the file back to what it was.

gedit wont work and nano says it is a blank file.

What do I do. please

---

### Post by ugm6hr on 2007-12-20
> **yam125 said:**
> What do I do. please

Did you backup xorg first?  If so - just rename.  If not - remember to do that next time.

If you have genuinley deleted the file - I think you can reconfigure xorg:
```
sudo dpkg-reconfigure xserver-xorg
```

Or reinstall X:
```
sudo apt-get install x-window-system-core
```

---

