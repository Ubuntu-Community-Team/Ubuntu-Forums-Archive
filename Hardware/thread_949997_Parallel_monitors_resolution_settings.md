---
title: "Parallel monitors resolution settings"
date: 2008-10-16
forum: Hardware
---

### Post by jangari on 2008-10-16
I'm running 8.10 beta, and neither of my screens display the correct resolution. I've got a widescreen laptop monitor that's displaying only at 1024x768, and an external acer 22" LCD which will only work on the 'mirrored' desktop setting (cloned output in Hardy), and will also only display at 1024x768. I know from running Hardy that the acer will display at 1650x1050.

If I attempted to change it to anything higher than 1024x768, or to change the laptop monitor to 1280x768, to actually be widescreen, I'm prompted to enable virtual resolution settings. If I enable it, then when restarting an x-session, the output is entirely corrupted; only the mouse is visible and everything else is just a pastiche of vertical stripes resembling the background in rough patches. I'll try and post a screenshot later. The only way I can fix this and return to 1024x768 without virtual resolution settings enabled is to ctrl+alt+F1 into a console and restore xorg.conf from one of the backups. 

Any help on this would be greatly appreciated. I believe my video card is an Intel. Here's the output of dccprobe, I can't think of any other diagnostic tools:

```
vbe: VESA 3.0 detected.
oem: Intel(r)852GM/852GME/855GM/855GME Graphics Chip Accelerated VGA BIOS
vendor: Intel Corporation
product: Intel(r)852GM/852GME/855GM/855GME Graphics Controller Hardware Version 0.0
memory: 32576kb
mode: 1280x1024x256
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 1024x768x256
mode: 1024x768x64k
mode: 1024x768x16m
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 640x480x256
mode: 800x600x256
mode: 640x480x64k
edid: 
edid: 1 3
id: ad74
eisa: ACRad74
serial: 726002cd
manufacture: 26 2007
input: sync on green, analog signal.
screensize: 47 30
gamma: 2.200000
dpms: RGB, active off, no suspend, no standby
timing: 720x400@70 Hz (VGA 640x400, IBM)
timing: 720x400@88 Hz (XGA2)
timing: 640x480@60 Hz (VGA)
timing: 640x480@67 Hz (Mac II, Apple)
timing: 640x480@72 Hz (VESA)
timing: 640x480@75 Hz (VESA)
timing: 800x600@60 Hz (VESA)
timing: 800x600@72 Hz (VESA)
timing: 800x600@75 Hz (VESA)
timing: 832x624@75 Hz (Mac II)
timing: 1024x768@87 Hz Interlaced (8514A)
timing: 1024x768@70 Hz (VESA)
timing: 1024x768@75 Hz (VESA)
timing: 1280x1024@75 (VESA)
ctiming: 1280x1024@60
ctiming: 1280x960@60
ctiming: 1152x864@75
ctiming: 1440x1440@60
ctiming: 1440x1440@75
ctiming: 1680x1680@60
ctiming: 1280x800@60
ctiming: 1360x850@60
dtiming: 1680x1050@77
monitorrange: 30-82, 56-76
monitorname: Acer AL2216W
monitorserial: L74090226340

```

---

