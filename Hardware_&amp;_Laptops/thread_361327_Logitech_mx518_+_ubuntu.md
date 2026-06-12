---
title: "Logitech mx518 + ubuntu"
date: 2007-02-14
forum: Hardware &amp; Laptops
---

### Post by uNiverSus on 2007-02-14
Hi , 2 days ago something crashed in my lixnu system ;/ The scroll of my mouse isn't working anymore like it should. When i scroll down on a internet site , the site dont goes down and up . The scroll is programed now for going up a page and going down a page ;/ I hope u know what i mean . For example the 2 arrows in firefox under file and edit ;C 

Can someone help me to fix it ??

And maybe someone knew a how-to where i can use the other buttons of my mouse ?? 

Sry for my bad english . Plz someone help me !

---

### Post by Daveth on 2007-02-14
try
[http://ubuntuforums.org/showthread.php?t=219894&highlight=logitech+mouse](http://ubuntuforums.org/showthread.php?t=219894&highlight=logitech+mouse)

---

### Post by ness0216 on 2007-06-21
I'm having the same problem. My mouse was configured and working fine and then after I rebooted one time my mouse wheel is acting like my forward and back buttons on the side and my back button is acting like I'm scrolling down. I'm not sure what happened but it's really frustrating when surfing the internet with this type of behavior.

---

### Post by hyperq on 2008-02-06
I got the side mouse buttons on my Logitech MX518 working in Firefox. I am using the "evdev" driver, not the "mouse" driver. I am using Kubuntu 7.10 Gutsy, which already has the package "xserver-xorg-input-evdev" installed by default.

Simply change the mouse section of your /etc/X11/xorg.conf to this:

[HTML]
Section "InputDevice"
       Identifier      "Configured Mouse"
       Driver          "evdev"
       Option          "CorePointer"
       Option          "Buttons"       "7"
       Option          "ZAxisMapping"  "4 5"
       Option          "ButtonMapping" "1 2 3 6 7"
       Option          "Name"  "Logitech USB-PS/2 Optical Mouse"
EndSection
[/HTML]

---

