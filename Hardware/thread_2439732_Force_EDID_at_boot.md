---
title: "Force EDID at boot"
date: 2020-03-31
forum: Hardware
---

### Post by Pnumekin on 2020-03-31
Hi all
I hope someone here will have a clue how to fix my problem after a lot of unsuccessful attempts.

Description:
I have a PC running Lubuntu 19.10 x64 freshly installed, everything works and I have a display on a test screen. The screen is connected via a DVI to VGA adapter.
I need to use this PC on its dedicated screen (via DVI to VGA too) and this screen only accepts VESA 1024x768@75hz, to make things harder this screen doesn't send any EDID info (and it never did, it's not a malfunction). Attention this resolution and refresh are important, if I have 1024x768@60hz I have no display on the monitor.
The PC used to run Lubuntu 14.04 x64 and I had set the switch to the right resolution/frequency when loading the desktop and it worked without any problem.

The problem:
After reinstalling the system with 19.10, I wanted to go further and get the right resolution/frequency earlier in the boot sequence. The goal is to avoid a screen without display before landing on the desktop, and especially to have a display to manage possible problems that sometimes block the boot before the desktop (disk analysis, etc...).
I saw that it was possible to force an edid at boot in grub, for example here [https://wiki.archlinux.org/index.php/kernel_mode_setting#Forcing_modes_and_EDID](https://wiki.archlinux.org/index.php/kernel_mode_setting#Forcing_modes_and_EDID) and here [https://github.com/Ansa89/linux-15khz-patch](https://github.com/Ansa89/linux-15khz-patch) .
So I extracted the edid from my test screen, removed all unwanted resolution/frequency pairs and tried the operation, but the resolution is not applied and when I look with dmesg I get an error message about loading the file.

Does anyone have an idea to help me move forward? or an edid file with only 1024x768@75hz?

```
raven@Frankenmac:~$ dmesg | grep edid
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-5.3.0-18-generic root=UUID=3648da32-d938-4093-a966-324190c6f733 ro quiet splash resume=UUID=c399c055-9cc2-4940-895d-94924f462950 drm.edid_firmware=edid/1024x768-75.bin vt.handoff=7
[    0.056786] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-5.3.0-18-generic root=UUID=3648da32-d938-4093-a966-324190c6f733 ro quiet splash resume=UUID=c399c055-9cc2-4940-895d-94924f462950 drm.edid_firmware=edid/1024x768-75.bin vt.handoff=7
[    5.006427] platform DVI-I-1: Direct firmware load for edid/1024x768-75.bin failed with error -2
[    5.006580] [drm:edid_load [drm]] *ERROR* Requesting EDID firmware "edid/1024x768-75.bin" failed (err=-2)
[    5.039822] platform DVI-I-1: Direct firmware load for edid/1024x768-75.bin failed with error -2
[    5.040020] [drm:edid_load [drm]] *ERROR* Requesting EDID firmware "edid/1024x768-75.bin" failed (err=-2)
[    5.123609] platform DVI-I-1: Direct firmware load for edid/1024x768-75.bin failed with error -2
[    5.123829] [drm:edid_load [drm]] *ERROR* Requesting EDID firmware "edid/1024x768-75.bin" failed (err=-2)
[    5.556933] platform DVI-I-1: Direct firmware load for edid/1024x768-75.bin failed with error -2
[    5.557135] [drm:edid_load [drm]] *ERROR* Requesting EDID firmware "edid/1024x768-75.bin" failed (err=-2)
[   45.754052] [drm] Got external EDID base block and 0 extensions from "edid/1024x768-75.bin" for connector "DVI-I-1"
[   45.787743] [drm] Got external EDID base block and 0 extensions from "edid/1024x768-75.bin" for connector "DVI-I-1"
[   60.593108] [drm] Got external EDID base block and 0 extensions from "edid/1024x768-75.bin" for connector "DVI-I-1"
[   61.496669] [drm] Got external EDID base block and 0 extensions from "edid/1024x768-75.bin" for connector "DVI-I-1"
[   61.529635] [drm] Got external EDID base block and 0 extensions from "edid/1024x768-75.bin" for connector "DVI-I-1"
```

---

### Post by TheFu on 2020-04-01
[https://ubuntuforums.org/showthread.php?t=2436653](https://ubuntuforums.org/showthread.php?t=2436653)
There are a few threads here about manually setting EDID, but they are GPU specific.

---

