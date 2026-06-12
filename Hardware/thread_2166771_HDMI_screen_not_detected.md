---
title: "HDMI screen not detected"
date: 2013-08-11
forum: Hardware
---

### Post by vichor on 2013-08-11
Hi,

I have a low end Acer laptop with 13.04 installed. The overall behavior is excellent but I am facing an issue with the HDMI output. 

If I boot the laptop with the HDMI cable connected with a monitor on the other end of the cable, then everything works properly: the TV is detected, the sound works, etc.

But, if the laptop is already booted and then I connect the HDMI cable, the output is not detected: not for the video and not for the sound.

Any hints about what may be happening?

Just if this is needed:```

$ lspci -k -s 00:02.0
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
	Subsystem: Acer Incorporated [ALI] Device 048a
	Kernel driver in use: i915
```

---

### Post by carlwsnyder on 2013-08-11
This is normal.  You can reboot to get the monitor to be detected, but your HDMI output does NOT support connection/re-connection while the OS is running.

---

### Post by vichor on 2013-08-14
I had no idea! thanks

---

