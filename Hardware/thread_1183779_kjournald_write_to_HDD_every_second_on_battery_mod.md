---
title: "kjournald write to HDD every second on battery mode"
date: 2009-06-10
forum: Hardware
---

### Post by sillyxone on 2009-06-10
Dell D620 on Hardy. When it's on battery (no power plug in), there is this constant HDD click (writing or seeking HDD, not parking) every second. It doesn't do this when the power is plugged in.

I checked with "pidstat -d 2" and found kjournald keeps writing to (not reading) the disk. I think it does so to prevent data loss in case the battery die suddenly. 

However, I wonder if that will do any harm to the HDD, and if I can squeeze the battery a little bit more by disabling or slowing down the frequency of disk journaling (I'm willing to loose data not written to disk in the last 30 seconds). 

Is there a way to customize this behavior? Is it part of the laptop-mode package?

BTW, somehow wicd (network manager) joins the wagon on this too. It behaves like kjournald: writing to disk every 1-2 seconds on battery mode. Any idea?

thanks

---

### Post by sillyxone on 2009-09-09
just in case anybody found it annoying:

I ran powertop and it immediately suggested to set VM dirty to longer interval instead of the current 0.3s interval (0.3 second!)

suggested by powertop:
```
echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
```

Apply that command, the clicking stopped. I think I can afford to lose 15 seconds of unsaved data if my laptop happens to crash :-)

---

