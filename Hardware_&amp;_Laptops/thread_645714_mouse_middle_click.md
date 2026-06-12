---
title: "mouse middle click"
date: 2007-12-20
forum: Hardware &amp; Laptops
---

### Post by Leion on 2007-12-20
Hi, 

Can anyone tell me how to configure my USB mouse that has a scroll wheel in the middle?

I am  able to use the scroll wheel to scroll pages in firefox and can use the middle click to close pages but i am not able to use the middle click to scroll pages ...

Thanks

---

### Post by linuxwizard on 2007-12-20
[https://help.ubuntu.com/community/ManyButtonsMouseHowto](https://help.ubuntu.com/community/ManyButtonsMouseHowto)

---

### Post by Leion on 2007-12-22
Thanks but I am not able to fix the mouse wheel click myself
hence I installed this "drag and drop" firefox extension 
not the best solution but is close...

---

### Post by Whiffle on 2007-12-22
Are you trying to make it so that when you hold the middle button you can scroll pages by using the mouse?  If so...this is the mouse section in my /etc/X11/xorg.conf that allows me to do it.

```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option      "Emulate3Buttons"     "on"
        Option      "Emulate3TimeOut"     "50"
        Option      "EmulateWheel"        "on"
        Option      "EmulateWheelTimeOut" "200"
        Option      "EmulateWheelButton"  "2"
        Option      "YAxisMapping"        "4 5"
        Option      "XAxisMapping"        "6 7"
        Option      "ZAxisMapping"        "4 5"
EndSection

```

---

### Post by Leion on 2007-12-22
Thanks.
I used your entries and now it worked. :)

---

### Post by Leion on 2007-12-23
Actually the horizontal scroll still cannot work.

This is what i did.
besides adding the config above, I go to the about:config page in firefox 
and then i change the following settings

mousewheel.horizscroll.withnokey.action = 0
mousewheel.horizscroll.withnokey.numlines = 1

NOW i am able to get horizontal and vertical scroll with my middle click.

:)

nice !

---

