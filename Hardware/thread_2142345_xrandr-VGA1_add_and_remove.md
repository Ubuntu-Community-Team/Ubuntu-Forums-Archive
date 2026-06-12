---
title: "xrandr-VGA1 add and remove"
date: 2013-05-05
forum: Hardware
---

### Post by ramy1313 on 2013-05-05
I need help

I'm using ubuntu 13.04 on Dell Inspiron 1545
Mobile Intel® GM45 Express Chipset x86/MMX/SSE2
VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

The problem is my screen flickers a lot, sometimes switches to 1024x768 then back to 1366x768sometimes shrinks other times get wider and larger sometimes shifts to the lift or the right, also sometimes freezes, but most of times only flicker (I used to have this problem too on 12.10, 12.04 and others but this time flickers a lot) 

I noticed that each time the screen flickers syslog file adds a new line "Device added: xrandr-VGA1" and then flickers again and add new line "device removed: xrandr-VGA1" and so on many many times sometimes with a very short time interval other time with a very large time interval

P.S. I'm not connect to any external monitor I'm only working on LVDS1 
P.S. P.S. I tried long time ago to connect to external monitor and data show but I failed 

Also I used to have a similar problem on ubuntu 11.04 but syslog file used to have a lot of "i2c i2c-10:send bytes: error -110" line which is still printed in syslog file but rarely and the screen stopped flickering when the line " echo 0 > /sys/module/drm_kms_helper/parameters/poll" was added to "/etc/rc.local" which is still there

---

