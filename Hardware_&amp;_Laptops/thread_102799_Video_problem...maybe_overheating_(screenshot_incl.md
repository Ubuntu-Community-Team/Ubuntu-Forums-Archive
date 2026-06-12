---
title: "Video problem...maybe overheating? (screenshot included)"
date: 2005-12-12
forum: Hardware &amp; Laptops
---

### Post by Chua-Chua on 2005-12-12
Hello,

I've been having some weird video problems.
My screen started going gibberish after I left it on all night.
Now, I notice that whenever this gibberish happens, the fan(s) of the laptop are off. When I try to run a heavy app, which triggers the fan, the gibberish mostly goes away, except for the gnome-panel.

I don't think my video card fan turns on anymore. When I run a heavy app, the case/cpu fan turns on, but not the secondary fan (which is connected to the video card, I think). I just started getting this problem and I don't want to fiddle with the case and stuff.

Specs:
eMachines m6809
Ubuntu 5.10 AMD64 x86_64 generic
AMD 64 3200+ @ 2GHz
512MB RAM
ATI Radeon m9600pro 64MB Mobility

Also, I noticed that the /proc/acpi/fan and /proc/acpi/thermal_zone is empty and I can't install/run lm_sensors or any temp sensors.

Any help would be fabulous.

---

### Post by 23meg on 2005-12-12
Do you have nvidia-settings installed? If so, check out the temperature reading for your video chip there.

---

### Post by Chua-Chua on 2005-12-13
I'll try that when I get home.
Does nvidia-setting work for ATI cards?

---

### Post by Chua-Chua on 2005-12-19
Okay...so I've installed the default installation of Hoary from the install disk (from Shipit). 

However, I still get the same problem; the video goes gibberish and I think it may be the fan. 
Like I said, /proc/thermal_zone is empty as well as the fan directory. 
Can anybody help?

```
.:
ac_adapter  button               event  info            sleep         video
alarm       dsdt                 fadt   power_resource  sony          wakeup
battery     embedded_controller  fan    processor       thermal_zone

./ac_adapter:
AC

./ac_adapter/AC:
state

./battery:
BAT0

./battery/BAT0:
alarm  info  state

./button:
lid  power  sleep

./button/lid:
LID

./button/lid/LID:
info  state

./button/power:
PWRF

./button/power/PWRF:
info

./button/sleep:
SLPB

./button/sleep/SLPB:
info

./embedded_controller:
EC

./embedded_controller/EC:
info

./fan:

./power_resource:

./processor:
CPU0

./processor/CPU0:
info  limit  power  throttling

./sony:

./thermal_zone:

./video:
VGA

./video/VGA:
CRT  DOS  info  LCD  POST  POST_info  ROM  TVO

./video/VGA/CRT:
brightness  EDID  info  state

./video/VGA/LCD:
brightness  EDID  info  state

./video/VGA/TVO:
brightness  EDID  info  state

```

---

