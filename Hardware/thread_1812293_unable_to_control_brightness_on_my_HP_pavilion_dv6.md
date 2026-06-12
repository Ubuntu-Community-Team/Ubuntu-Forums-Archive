---
title: "unable to control brightness on my HP pavilion dv6"
date: 2011-07-26
forum: Hardware
---

### Post by harshakc01 on 2011-07-26
Can any1 help me out.i am using ubuntu 10.04 on my notebook with ATI radeon HD m6490 graphics and i cannot adjust the screen brightness.the ATI catalyst control centre doesnt open, says no ATI graphics driver installed..

And there is no folder called VGA in /etc/proc/acpi..i tried xbacklight..it says no outputs have backlight property..i cannot find my brightness file to edit also..can any1 plzz help!

thanks

---

### Post by bruise on 2011-07-29
try this command on your laptop:

 xrandr --output LVDS1 --brightness 0.7

---

### Post by lifelike27 on 2011-08-13
This is because of the onboard Intel graphics card that you're experiencing this problem.

Two possible fixes for it:
[http://linuxenvy.blogspot.com/2011/01/tackling-switchable-graphics.html](http://linuxenvy.blogspot.com/2011/01/tackling-switchable-graphics.html)

[http://superuser.com/questions/302489/use-sandy-bridges-integrated-graphics-or-activate-switchable-graphics-in-ubuntu](http://superuser.com/questions/302489/use-sandy-bridges-integrated-graphics-or-activate-switchable-graphics-in-ubuntu)

---

