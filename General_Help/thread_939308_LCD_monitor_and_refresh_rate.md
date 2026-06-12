---
title: "LCD monitor and refresh rate"
date: 2008-10-05
forum: General Help
---

### Post by natedagw824 on 2008-10-05
Hello all,

I have a Samsung 906BW LCD monitor and an Nvidia 9800GTX+ video card.  When I set my display resolution to 1440x900 the refresh rate defaults to 50.  Is that too low?  Could I damage my monitor if I leave this setting as is?

The highest the refresh rate goes to is to 52hz.

Thanks,

Nate

---

### Post by CEB2nd on 2008-10-05
This [thread]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=5700657") might help.

---

### Post by mikewhatever on 2008-10-05
Can you post the output of the following command from a terminal:
sudo xrandr -q
It should show what the driver and hardware are capable of.

---

### Post by Rhubarb on 2008-10-05
Make sure you have nvidia-settings installed:
```
sudo aptitude install nvidia-settings
```
Then run the nvidia settings manager:
System --> Administration --> NVIDIA X Server Settings
Then you can find the correct refresh rate in there (see attached picture).
xrandr reports an incorrect refresh rate in most applications in Ubuntu (when running the nvidia drivers), so it's best to use the nvidia x server settings manager to check the refresh rate yourself.

---

### Post by kaibob on 2008-10-06
This has been a confusing issue for some time. The "Screen and Graphics Preferences" dialog indicates that my LCD display is operating at 50 Hz. The xrandr utility indicates the same. However, the nvidia-settings utility and my monitor both show that the monitor is operating at 60 Hz.

I don't understand the discrepancy, but the monitor is great, so I don't worry about it.

---

