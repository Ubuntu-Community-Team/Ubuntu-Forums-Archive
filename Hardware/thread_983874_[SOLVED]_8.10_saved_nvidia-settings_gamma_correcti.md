---
title: "[SOLVED] 8.10 saved nvidia-settings gamma correction values not getting applied on st"
date: 2008-11-16
forum: Hardware
---

### Post by anomalous_underdog on 2008-11-16
I've adjusted my monitor's gamma corrections via nvidia-settings but upon reboot, the gamma values go back to default and I have to run nvidia-settings again manually everytime.

Where did the gamma correction settings for kubuntu go? in 8.04 it used to be in the system-settings. Did it have a bug and was forced to be removed momentarily, or is it simply not supported anymore?

EDIT: Should this thread be moved to "Multimedia & Video"? I cannot move it myself. This concerns a monitor's gamma values so I thought it should be under "Hardware".

---

### Post by anomalous_underdog on 2008-11-22
The only workaround for me to fix this is to add "nvidia-settings -l" to my openbox autostart.sh (.xinitrc doesn't work) but that's only because I use openbox though

---

