---
title: "Thinkpad X201s - no brightness resuming from standby"
date: 2011-02-11
forum: Hardware
---

### Post by Wellconnected on 2011-02-11
Dear All,
I have a Thinkpad X201s on which ubuntu works very well, with one small problem. Occasionally, when resuming from standby, the screen brightness is really zero - I can see the screen in direct light, and can log into the machine, but just with zero brightness.

The brightness up and down buttons still make the brightness bar go up and down, but with no effect on the brightness.

I have this in dmesg coming out of suspend:
[ 8497.257798] video LNXVIDEO:00: Restoring backlight state
[ 8497.272761] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[ 8497.312380] Skipping EDID probe due to cached edid

How can I recover from this situation?

This happens both with 10.04 and 10.10.

Thanks
E

---

