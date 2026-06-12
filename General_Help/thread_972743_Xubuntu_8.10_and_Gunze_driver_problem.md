---
title: "Xubuntu 8.10 and Gunze driver problem"
date: 2008-11-06
forum: General Help
---

### Post by maddis on 2008-11-06
I installed Xubuntu 8.10 to my PC with touchscreen. In previous version (8.04) I used ploptouch driver with Xorg to get touchscreen working. In 8.10 it seems that HAL recognizes the Gunze driver, but then evdev says it doesn't know how to use the driver thus touchscreen is not working. This with inputattach modified to support Gunze. If I remove the inputattach then the evdev isn't even loaded at the Xorg startup.

I tried with ploptouch driver, but there is something different in configuration system since I cannot get the driver even loaded. One thing though that the ploptouch driver is compiled in 8.04 and not in 8.10, but there isn't even any complains that could not load that driver.

I'll continue my testing, but if you have any ideas, please tell.

Here is what reads in Xorg log after startup. The Device is the one that inputattach makes. If that really is gunze driver then it probably should use the device I give to inputattach instead. I have tried to configure evdev for that device, but it seems that xorg.conf has no effect what so ever. Only thing is that if you make a typo there the whole Xorg starts up on low resolution mode.

```

(II) config/hal: Adding input device Gunze AHL-51S TouchScreen
(**) Gunze AHL-51S TouchScreen: always reports core events
(**) Gunze AHL-51S TouchScreen: Device: "/dev/input/event5"
(II) Gunze AHL-51S TouchScreen: Found x and y absolute axes
(II) Gunze AHL-51S TouchScreen: Found absolute touchpad
(WW) Gunze AHL-51S TouchScreen: Don't know how to use device
(II) UnloadModule: "evdev"
(EE) PreInit returned NULL for "Gunze AHL-51S TouchScreen"
(EE) config/hal: NewInputDeviceRequest failed

```

---

