---
title: "nVidia started overheating"
date: 2013-10-09
forum: Hardware
---

### Post by dankojoffrey on 2013-10-09
Hi,
I have been using bumblebee with nvidia-325 drivers on my Asus Vivobook S550C. It worked fine, but yesterday I updated drivers to nvidia-331 from org-edgers/ppa. Later I played Xonotic game and after like 20min of playing a got a sensor warning that CPU temp is 87°C, I continued playing and after a minute another warning that CPU is 90°C - that's when I turned off the game and checked the sensors - Core Temp and asus-isa cca 87°C and nVidia temp was about 90°C...
So I went back to nvidia-325 drivers, but the overheating problem remains... So, I installed nvidia-319 drivers, but still overheating... Even when I start "optirun glxspheres"...

Do you know what could be the problem and how to fix it...???

Thanks...

Update: Cpu usage while running optirun glxspheres is cca 80%... I use kernel 3.11.4

---

### Post by Kirboosy on 2013-10-09
Are all the fans working/spinning properly?

Are you sure that the fans are clean and nothing is blocking the ventilation on the laptop? I would try shutting the computer down and let it cool off completely. Then take a can of compressed air and blow the vents out on the laptop. Wait another couple minutes after cleaning the vents to turn it back on. (You don't want to turn it back on while the laptop is cold from the compressed air). See if that fixes anything.

Hope that helps!
~Caboose

---

### Post by dankojoffrey on 2013-10-09
The computer is new (2 moths old)  so I don't think it's dust... fans are working fine (while on nvidia they are going at full speed)... when I'm not using nVidia fans are sometimes even off and temp stays at cca 45°C... as I said the heating problem started after nvidia driver update... 

I tried olded kernel 3.10.15 and older drivers, but overheating remains... temperature goes up as soon as I use optirun command...

---

### Post by Yellow Pasque on 2013-10-09
```
optirun glxinfo
```

---

### Post by dankojoffrey on 2013-10-21
upgraded to 13.10 with nvidia-304 drivers... solved...

---

