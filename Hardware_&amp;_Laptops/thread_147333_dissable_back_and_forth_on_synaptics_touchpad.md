---
title: "dissable back and forth on synaptics touchpad"
date: 2006-03-20
forum: Hardware &amp; Laptops
---

### Post by sublime on 2006-03-20
all i would like my touchpad to do is scroll up and down and horizontal scrolling.  however, i do have a problem where ill be using the scroll feature and all of a sudden ill be going back 27 pages (exagerated greatly) and ill completely lose my spot on the page finding my way back.  its extremely annoying.  how can i dissable this?  heres my the touchpad portion f my xorg.conf:

```
Section "InputDevice"
        Identifier  "Synaptics Touchpad"
        Driver      "synaptics"
        Option      "SendCoreEvents" "true"
        Option      "Device" "/dev/psaux"
        Option      "Protocol" "auto-dev"
        Option      "HorizScrollDelta" "10"
EndSection

```

---

### Post by Defcon1 on 2006-03-20
Hey, I had the same problem, but I found this website : [http://ubuntu.wordpress.com/2005/11/15/fixing-my-alps-touchpad-with-the-synaptics-driver/](http://ubuntu.wordpress.com/2005/11/15/fixing-my-alps-touchpad-with-the-synaptics-driver/)

My touchpad is working fine now (touch wood). just don't forget to implement the extra change mentioned in the comments at the bottom of the page...

good luck...

---

