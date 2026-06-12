---
title: "nvidia settings coolbits thermal settings fan speed SAVE between restarts"
date: 2013-02-26
forum: Hardware
---

### Post by xekon on 2013-02-26
nvidia settings coolbits thermal settings fan speed SAVE between restarts

I have created a xorg.conf (did not have one by default)

Xorg :1 -configure

I then added

    Option         "Coolbits" "4"

to the device section.

I rebooted, and now Thermal Settings are available in my nvidia x server settings.

The problem I have now is that every time I restart my computer I have to open the nvidia x server settings, and then check the "enable GPU fan settings" box and accept the disclaimer and adjust my fan speed. I have to do this EVERY TIME I reboot.

My GPU with default settings runs at 74 C, with the fan speed set to 80, my card runs at 49 C, which is preferable.

Anyone have an idea how to have my fan speed set automatically every reboot?

---

### Post by Jaginus on 2013-09-12
Hi,  Easy !.   

1- You have to do exactly what you did in xorg.conf  

2- Create a bash file and run it at start. The file must contain:  

#!/bin/bash
nvidia-settings \
    -a "[gpu:0]/GPUFanControlState=1" \
    -a "[fan:0]/GPUCurrentFanSpeed=40" &

3- Enjoy a silent nvidia

---

