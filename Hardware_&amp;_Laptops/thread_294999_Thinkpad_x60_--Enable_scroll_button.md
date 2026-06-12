---
title: "Thinkpad x60 --Enable scroll button"
date: 2006-11-07
forum: Hardware &amp; Laptops
---

### Post by RayNiu on 2006-11-07
Hi, everyone,i am a new user of Ubuntu, I have some questions about my thinkpad x60's scroll button(the middle button between right and left buttons), it can not work. I've read some threads and find some solutions, most of them are telling to insert two lines into xorg.conf, i tried, still doesnt work, here is my xorg.conf, please help me, it is so annoying without the scroll button. Thanks!

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "EmulateWheel"          "ture"
        Option          "EmulateWheelButton"    "2"
endSection

---

### Post by tedrogers on 2006-11-07
I would be very interested to learn about this too....us IBM users are lost without our scroll buttons.

In the meantime...if you're missing your OSD for volume etc....then try installing tpb from the repositories.

[http://www.columbia.edu/~em36/ubuntuhoarythinkpadt42.html#tpbosd](http://www.columbia.edu/~em36/ubuntuhoarythinkpadt42.html#tpbosd)

EDIT:

Found it, check it:

[http://ubuntuforums.org/showthread.php?p=1729103#post1729103](http://ubuntuforums.org/showthread.php?p=1729103#post1729103)

All I did was copy and replace the entire contents of the 3rd post (just above mine) in the relevant section of my xorg.conf file...it worked a treat!

---

### Post by Spif on 2006-12-15
Try this program: [http://tpctl.sourceforge.net/configure-trackpoint.html](http://tpctl.sourceforge.net/configure-trackpoint.html)

It is in the Ubuntu repos somewhere.

To get the middle button working, you must have the following in your xorg.conf:

       Option          "EmulateWheel"          "on"
       Option          "EmulateWheelButton"    "2"

These two may be necessary too:

       Option "YAxisMapping" "4 5"
       Option "XAxisMapping" "6 7"

Source: [http://thinkwiki.org/wiki/How_to_configure_the_TrackPoint#Scrolling](http://thinkwiki.org/wiki/How_to_configure_the_TrackPoint#Scrolling)

---

### Post by emdeem on 2006-12-15
> **RayNiu said:**
> 
        Option          "EmulateWheel"          "ture"

"true"

---

