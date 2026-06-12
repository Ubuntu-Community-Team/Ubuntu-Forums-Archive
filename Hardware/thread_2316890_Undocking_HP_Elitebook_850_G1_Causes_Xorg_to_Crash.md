---
title: "Undocking HP Elitebook 850 G1 Causes Xorg to Crash"
date: 2016-03-11
forum: Hardware
---

### Post by cdillard-hsp on 2016-03-11
I have an HP Elitebook 850 G1 laptop that I use with a docking station, and the docking station has an HP E231 display connected to it via DisplayPort.

When I undock the laptop (most of the time) the X server crashes.

**Graphics Card Info**
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)

**Xorg Log**
[  4989.056] (II) intel(0): Output DP1-1 has no monitor section
[  4989.056] (II) intel(0): Enabled output DP1-1
[  4989.056] (II) intel(0): Output DP1-2 has no monitor section
[  4989.056] (II) intel(0): Enabled output DP1-2
[  4989.056] (II) intel(0): Output DP1-3 has no monitor section
[  4989.056] (II) intel(0): Enabled output DP1-3
[  4989.077] (II) intel(0): switch to mode 1920x1080@60.0 on DP1-2 using pipe 0, position (0, 0), rotation normal, reflection none
[  4989.614] (II) intel(0): resizing framebuffer to 3840x1080
[  4989.631] (II) intel(0): switch to mode 1920x1080@60.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[  4990.324] (II) intel(0): switch to mode 1920x1080@60.0 on DP1-2 using pipe 1, position (1920, 0), rotation normal, reflection none
[  5978.596] (EE) intel(0): page flipping failed, on CRTC:25 (pipe=1), disabling synchronous page flips
[  5978.609] (EE) intel(0): failed to set mode: No such file or directory [2]
[  5978.609] (II) intel(0): Disabled output DP1-1
[  5978.609] (II) intel(0): Disabled output DP1-2
[  5978.617] (EE) intel(0): Failed to restore display configuration
[  5978.617] (EE) 
[  5978.617] (EE) Backtrace:
[  5978.619] (EE) 0: /usr/bin/X (xorg_backtrace+0x4e) [0x55d133c8468e]
[  5978.619] (EE) 1: /usr/bin/X (0x55d133ad0000+0x1b89f9) [0x55d133c889f9]
[  5978.619] (EE) 2: /lib/x86_64-linux-gnu/libc.so.6 (0x7f214ffa5000+0x352f0) [0x7f214ffda2f0]
[  5978.619] (EE) 3: /usr/lib/xorg/modules/drivers/intel_drv.so (0x7f214c37c000+0x103bf0) [0x7f214c47fbf0]
[  5978.619] (EE) 4: /usr/lib/xorg/modules/drivers/intel_drv.so (0x7f214c37c000+0x106c19) [0x7f214c482c19]
[  5978.619] (EE) 5: /usr/bin/X (DRI2SwapBuffers+0x1c8) [0x55d133c56d58]
[  5978.619] (EE) 6: /usr/bin/X (0x55d133ad0000+0x1886dc) [0x55d133c586dc]
[  5978.620] (EE) 7: /usr/bin/X (0x55d133ad0000+0x5818f) [0x55d133b2818f]
[  5978.620] (EE) 8: /usr/bin/X (0x55d133ad0000+0x5c34b) [0x55d133b2c34b]
[  5978.620] (EE) 9: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xf0) [0x7f214ffc5a40]
[  5978.620] (EE) 10: /usr/bin/X (_start+0x29) [0x55d133b166c9]
[  5978.620] (EE) 
[  5978.621] (EE) Segmentation fault at address 0x47168
[  5978.621] (EE) 
Fatal server error:
[  5978.621] (EE) Caught signal 11 (Segmentation fault). Server aborting
[  5978.621] (EE) 
[  5978.621] (EE) 
Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[  5978.621] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[  5978.621] (EE) 
[  5978.621] (II) AIGLX: Suspending AIGLX clients for VT switch
[  5978.748] (EE) Server terminated with error (1). Closing log file.

---

