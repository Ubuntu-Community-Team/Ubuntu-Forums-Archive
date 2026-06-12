---
title: "ATI/AMD Crossfire fan noise control issue on 2nd card"
date: 2011-12-11
forum: Hardware
---

### Post by Trax007 on 2011-12-11
I just got Ubuntu 11.10 64bit setup on my system that's a got  a ATI Crossfire setup (I already installed the proprietary ATI drivers  and Catalyst with no issues) however I don't seem to be able to control  the second video cards fan speed that seems to be running at max (I have  lm-sensors & fancontrol setup).
[B]
# aticonfig --pplib-cmd 'set fanspeed 1 31'
PPLIB command execution has failed!
ati_pplib_cmd: execute "set" failed!


[/B]Works just fine on the first card:


[B]# aticonfig --pplib-cmd 'set fanspeed 0 31'
PPLIB command execution is Successful![/B]


Both cards are being detected as you can see here:


**# aticonfig --lsch**

[B]CrossFire chain for adapter 0, status: enabled 
[/B]
[B]0. 0f:00.0 ATI Radeon HD 5900 Series 
[/B]
**1. 0e:00.0 ATI Radeon HD 5900 Series**
  



Some help please.

---

### Post by Electric.Head on 2012-01-19
[FONT=Arial][SIZE=2]Apologies, this isn't exactly a positive response but I figured I'd chip in as this plagued me for quite some time and I feel your pain. Read on for a solution of sorts if it's still a problem...  

I have 2x 3870 in crossfire and I spent far too many hours trying to fix the second card noise issue as, like you, the fan was always on high. A long story short, I gave up trying to fix it in fglrx. I suspect you may well suffer the same issue as me, which is even though you can create a crossfire chain via aticonfig, it won't activate and the drivers don't seem to control the second card; at some point in the process it'll say something like "Crossfire chain enabled, restart X" followed swiftly by "Crossfire is not support on this platform" (despite it being supported, considering I have crossfire running happily in W7 on the same machine). I got the same symptoms (commands not working for the second card).

 I put up with the noise for far too long but was somewhat saved by the inclusion of something resembling functional power-management in the open source radeon drivers. Obviously if fglrx is handling your cards then this won't apply, and it goes without saying there is no functioning crossfire ...but I don't need it in Ubuntu and at least it shuts it up (not to mention the latest fglrx releases are *actually surpassed by the open source stack* on my system). 

(with root privileges)

```
$ echo profile > /sys/class/drm/card0/device/power_method
$ echo profile > /sys/class/drm/card1/device/power_method

$ echo low > /sys/class/drm/card0/device/power_profile
$ echo low > /sys/class/drm/card1/device/power_profile
```Ahh. Peace and quiet. You can go for "default" "auto" and "high" iirc in power_profile, and you can use "dynpm" in power_method instead if you want it to be automatic but this doesn't appear to do much good on my system.
 [/SIZE][/FONT][FONT=Arial][SIZE=2]```
cat /sys[COLOR=#000000]**/**[/COLOR]kernel[COLOR=#000000]**/**[/COLOR]debug[COLOR=#000000]**/**[/COLOR]dri[COLOR=#000000]**/**[/COLOR][COLOR=#000000]0[/COLOR][COLOR=#000000]**/**[/COLOR]radeon_pm_info
```Gives me current card clocks, my second card's radeon_pm_info is at /sys/kernel/debug/dri/64/ but this is probably system-dependent. 
[/SIZE][/FONT]

---

