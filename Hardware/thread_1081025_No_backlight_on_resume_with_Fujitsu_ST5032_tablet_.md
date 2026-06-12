---
title: "No backlight on resume with Fujitsu ST5032 tablet in Hardy"
date: 2009-02-26
forum: Hardware
---

### Post by bcw on 2009-02-26
I updated Hardy on my Fujitsu ST5032D tablet and the backlight does not come on automatically when resuming from suspend.  It has been working fine up until now.

This is the work-around I've discovered:
```
sudo nano /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux
```

... make this change (was false, is true):
```
if [ "$NEW_INTEL" ] || [ -d /sys/module/nvidia ] || [ -d /sys/module/fglrx ];
then
    HAL_PROP_POWER_MANAGEMENT_QUIRK_DPMS_ON=**[COLOR="Red"]true[/COLOR]**
```

This is working for me.  If anyone knows a better fix, please post it.  I have filed a [**[COLOR="Red"]bug[/COLOR]**]("https://bugs.launchpad.net/ubuntu/+bug/334712") about this.

Cheers.

---

