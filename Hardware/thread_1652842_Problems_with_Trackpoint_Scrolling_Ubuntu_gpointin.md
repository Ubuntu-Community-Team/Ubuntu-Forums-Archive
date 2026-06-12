---
title: "Problems with Trackpoint Scrolling Ubuntu gpointing-device-settings"
date: 2010-12-25
forum: Hardware
---

### Post by chwebb1 on 2010-12-25
Hello all,
I have a ThinkPad W510, type 4319-65U that I am trying to get middle button scrolling on, and I have it working, however, if I put my computer to sleep and wake it up again later, scrolling no longer works. I am using gpointing-device-settings. Does anyone have any suggestions on how to fix this, or any possible workarounds? I am running Ubuntu 10.10 64 bit. Thanks.

EDIT:
I've also tried adding 
<match key="info.product" string="TPPS/2 IBM TrackPoint">
 <merge key="input.x11_options.EmulateWheel" type="string">true</merge>
 <merge key="input.x11_options.EmulateWheelButton" type="string">2</merge>
 <merge key="input.x11_options.ZAxsisMapping" type="string">4 5</merge>
 <merge key="input.x11_options.Emulate3Buttons" type="string">true</merge>
</match>
to sudo gedit /etc/hal/fdi/policy/mouse-wheel.fdi and GEdit says that the file doesn't exist.

---

### Post by chwebb1 on 2010-12-28
Bump.

---

### Post by schnulzrich on 2011-01-06
yea i believe i am having the same problem on a fresh install of 10.10 on a t61p. any ideas out there?

---

### Post by pi/roman on 2011-01-06
hal daemon is no longer used. hal is not even installed on 10.10.
> :~$ hald
The program 'hald' is currently not installed.  You can install it by typing:
sudo apt-get install halYou can configure your devices in xorg.conf.

---

### Post by chwebb1 on 2011-01-06
> **pi/roman said:**
> hal daemon is no longer used. hal is not even installed on 10.10.
You can configure your devices in xorg.conf.
How might I go about configuring this trackpoint in Xorg?
Thanks!

---

### Post by pi/roman on 2011-01-06
For example in /etc/X11/xorg.conf using the settings from the earlier post
```

Section "ServerLayout"
    Identifier     "Default Layout"
    InputDevice "TPPS/2 IBM TrackPoint"
EndSection

Section "InputDevice"
    Identifier  "TPPS/2 IBM TrackPoint"
    Option        "EmulateWheel" "true"
    Option        "EmulateWheelButton" "2"
    Option        "Emulate3Buttons" "true"
    Option        "ZAxisMapping" "4 5"
EndSection
```That is just a quick untested configuration layout so you should look up a guide to get a better idea of how to put one together.

---

### Post by chwebb1 on 2011-01-06
I just tried to do that, and after I rebooted, Xorg failed to launch, so I had to reset it to defaults. Do you have any idea how to fix that?

---

### Post by pi/roman on 2011-01-06
Do you have an xorg.conf or are you creating one from scratch?

Actually this guide here looks like a good method:
[[COLOR=Blue]http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#xorg.conf.d[/COLOR]]("http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#xorg.conf.d") 

Use the method listed under "xorg.conf.d".

take note of this message:
> For Ubuntu 10.10 Maverick Meerkat, the correct path is /usr/share/X11/xorg.conf.d

---

### Post by chwebb1 on 2011-01-07
> **pi/roman said:**
> ...

Actually this guide here looks like a good method:
[[COLOR=Blue]http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#xorg.conf.d[/COLOR]]("http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#xorg.conf.d") 

Use the method listed under "xorg.conf.d".
...
Works perfectly for me, thanks a ton.

---

