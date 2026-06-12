---
title: "Asus F3jp problems"
date: 2010-10-02
forum: Hardware
---

### Post by Sda1986 on 2010-10-02
Hi all, my name is Stefano and I'm from Italy.
I have some trouble with my laptop and ubuntu 10.10, I searched online a lot, I found news and articles but no solution maybe someone can help me.

1. Ati mobility x1700 power management
Ati dropped driver support to this video card and some other like this, with open source driver we don't have very good power management but I read on Phoronix in Kernel 2.6.35 "more Radeon Power Management Improvements"

[http://www.phoronix.com/scan.php?page=news_item&px=ODE5Mg](http://www.phoronix.com/scan.php?page=news_item&px=ODE5Mg)

Now I have ubuntu 10.10 with 2.6.35.22-generic x64 kernel, how can I check if my video card works at minimum power? and how can I eventually change it?

With this [program]("http://code.google.com/p/ucc/") they say they can control the frequency but it doesn't work on my pc.

[IMG]http://sites.google.com/site/ubuntucontrolcenter/_/rsrc/1280704224283/home/screenshots/ucc052.png[/IMG]

2. Touchpad scroll zone
I have a scroll zone on my touchpad, I disabled it but if for some reason I pass with my finger over it my cursor make a big jump on left or right, depends where I'm coming. Can I solve it?

3. Webcam Led
I have a webcam, it works but one time I start it the controll led stay until I shutdown\reboot my pc. Can I solve it?
EDIT: I have an asus webcam (STKRealtek) can I have a better quality? Like windows? what kernel module i have to use?

4. Headphones red led.
In the hole where I can plug my headphones there is a led, usually this led (on old ubuntu and windows) isn't on, but on Ubuntu 10.04/10.10 it's always on. Can I shut it down?

5. High fan speed
My only fan is always on and almost always at the maximum speed, it's very noisy and I want crash my pc sometimes! there are any solution?
I found that but I'm not sure about it!

[http://www.aneas.org/knowledge/asus_f3jp_fan_control.php](http://www.aneas.org/knowledge/asus_f3jp_fan_control.php)

Really thanks, for any information you have only to ask!

Stefano

---

### Post by Sda1986 on 2010-10-04
Problem 1 Solved:

[http://wiki.x.org/wiki/RadeonFeature](http://wiki.x.org/wiki/RadeonFeature)
[http://www.overclock.net/linux-unix/731469-how-power-saving-radeon-driver.html](http://www.overclock.net/linux-unix/731469-how-power-saving-radeon-driver.html)

I made a nice script

```

#!/bin/bash
title="Video Frequency"
column="Option"
to=3
a="High Freq"
b="Mid Freq"
c="Low Freq"

choice=`zenity --list --title="$title" --column="$column0" "$a" "$b" "$c" --timeout=$to`

case $choice in
    $a)
    echo profile > /sys/class/drm/card0/device/power_method
    echo high > /sys/class/drm/card0/device/power_profile 
    ;;
    $b)
    echo profile > /sys/class/drm/card0/device/power_method    
    echo mid > /sys/class/drm/card0/device/power_profile 
    ;;
    $c)
    echo profile > /sys/class/drm/card0/device/power_method
    echo low > /sys/class/drm/card0/device/power_profile 
    ;;
    *) exit 1
esac

```
gksudo nomescript.sh

1 down 4 to go!

---

