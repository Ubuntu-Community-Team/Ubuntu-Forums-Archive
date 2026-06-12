---
title: "Razer Diamondback"
date: 2007-08-30
forum: Hardware &amp; Laptops
---

### Post by Ritchstorm on 2007-08-30
I am using this USB mouse atm and was wondering whether I could get the extra buttons to work and how? Doing a quick google search i found this [http://razertool.sourceforge.net/](http://razertool.sourceforge.net/) but it's for the copperhead (different razer mouse). However this is the sort of thing I am looking for only for diamondback not copperhead. Anyone know of a program? It's not the end of the world it's just a shame I can't use them :(

---

### Post by 1/0 on 2007-11-20
I've got the same mouse but I really dislike third party add-ons. Instead I configured the mouse in xorg, like this:

```

Section "InputDevice"
       Identifier "Configured Mouse"
       Driver "mouse"
       Option "Name" "Razer Diamondback Optical Mouse"
       Option "Device" "/dev/input/mice"
       Option "CorePointer"
       Option "Resolution" "1600"
       Option "Buttons" "9"
       Option "Protocol" "ExplorerPS/2"
       Option "ZAxisMapping" "4 5"
       Option "ButtonMapping" "1 2 3 6 7 8 9"
       Option "one page back" "4"
       Option "one page forward" "5"
EndSection

```

It set up most things I need. (The buttons on the right are impossible for me to reach anyway.) Oh and in order to get the buttons correct, you'll have to issue:

```

sudo xmodmap -e "pointer = 1 2 3 6 7 4 5"

```

You can add it permanently by putting the above (without sudo ofc) in /etc/X11/xinit/xinitrc

Hope it helps

---

### Post by AbtZ on 2007-12-14
WARNING

Copy+pasting the above xorg settings will crash X. There's a typo in the text -- it's supposed to be "Driver" not "Drive" (without quotation marks, of course).

Otherwise these settings worked great for me -- and the mappings are exactly as I wanted them, with the "Back" button on the upper left side of the mouse and the "Forward" button on the upper right side.

Thanks :D

---

### Post by 1/0 on 2007-12-15
> **AbtZ said:**
> WARNING

Copy+pasting the above xorg settings will crash X. There's a typo in the text -- it's supposed to be "Driver" not "Drive" (without quotation marks, of course).

Otherwise these settings worked great for me -- and the mappings are exactly as I wanted them, with the "Back" button on the upper left side of the mouse and the "Forward" button on the upper right side.

Thanks :D

Ooops! Corecting it...

---

### Post by bluesnow on 2008-01-30
> **1/0 said:**
> I've got the same mouse but I really dislike third party add-ons. Instead I configured the mouse in xorg, like this:

```

Section "InputDevice"
       Identifier "Configured Mouse"
       Driver "mouse"
       Option "Name" "Razer Diamondback Optical Mouse"
       Option "Device" "/dev/input/mice"
       Option "CorePointer"
       Option "Resolution" "1600"
       Option "Buttons" "9"
       Option "Protocol" "ExplorerPS/2"
       Option "ZAxisMapping" "4 5"
       Option "ButtonMapping" "1 2 3 6 7 8 9"
       Option "one page back" "4"
       Option "one page forward" "5"
EndSection

```

It set up most things I need. (The buttons on the right are impossible for me to reach anyway.) Oh and in order to get the buttons correct, you'll have to issue:

```

sudo xmodmap -e "pointer = 1 2 3 6 7 4 5"

```

You can add it permanently by putting the above (without sudo ofc) in /etc/X11/xinit/xinitrc

Hope it helps

i have entered the above into xorg but nothing happened after the restart. i enter the info right at the bottom on xorg do i need to replace 
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

with it or was i right to just include it to the bottom of the xorg. 
I'm a complete noob btw, been running ubuntu for just 2 days now, loving it though.

Thanks in advance for any help

---

### Post by AbtZ on 2008-01-30
You need to replace the old mouse config.

---

### Post by bluesnow on 2008-01-30
> **AbtZ said:**
> You need to replace the old mouse config.

Makes sense really :) silly me. All done and works a treat. 
Thank you

---

