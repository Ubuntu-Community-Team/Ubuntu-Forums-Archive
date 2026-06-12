---
title: "slow trackpoint on ThinkPad E420s under Ubuntu 11.04"
date: 2011-08-23
forum: Hardware
---

### Post by omghero on 2011-08-23
Hi everyone!
I installed Ubuntu 11.04 on ThinkPad Edge 420s. I was able to recover scrolling using trackpoint, but I could not increase the speed and sensitivity of it.
Thise comands do what I whant,
```
 echo -n 255 > /sys/devices/platform/i8042/serio1/serio2/speed 

 echo -n 255 > /sys/devices/platform/i8042/serio1/serio2/sensitivity 
``` but after rebooting all changes gone.

changing /etc/rc.local doesn't work.

does anybody know how to fix this problem?

Thanks!

---

