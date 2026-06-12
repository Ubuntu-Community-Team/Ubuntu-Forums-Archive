---
title: "Intel X3100 resolution"
date: 2008-08-27
forum: Hardware
---

### Post by sonderlich on 2008-08-27
Hi,

I have freshly installed 32bit xubuntu hardy 8.0.4 and performed an update/dist-upgrade. My problem relates to not being able to run X at the desired resolution. The highest resolution shown by the display preferences dialogue in XFCE is 1280x800.

I am using the onboard intek X3100 graphics adapter that is connected, via a PCI-E dvi card, to a lenovo "Thinkvision" screen with a native resolution of 1920x1200.

I am suspecting that the lack of high resolution options might be a video memory problem. The total video memory can be set to 8 MB + 256 MB shared in the bios, which works under Windows Vista. However, ddcprobe only shows 8 MB.

Please let me know if you have any suggestions, or if you need further information about the system settings. I would very much appreciate your help. Thanks!

Till


output from ddcprobe follows below, followed by the relevant sections of xorg.conf

vbe: VESA 3.0 detected.
oem: Intel(r)Q33/Q35/G33 Graphics Chip Accelerated VGA BIOS
vendor: Intel Corporation
product: Intel(r)Q33/Q35/G33 Graphics Controller Hardware Version 0.0
memory: 8128kb
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
id: 1151
eisa: LEN1151
serial: 01010101
manufacture: 17 2008
input: analog signal.
screensize: 47 30
gamma: 2.200000
dpms: RGB, active off, suspend, standby
timing: 720x400@70 Hz (VGA 640x400, IBM)
timing: 640x480@60 Hz (VGA)
timing: 640x480@67 Hz (Mac II, Apple)
timing: 640x480@75 Hz (VESA)
timing: 800x600@60 Hz (VESA)
timing: 800x600@72 Hz (VESA)
timing: 800x600@75 Hz (VESA)
timing: 832x624@75 Hz (Mac II)
timing: 1024x768@87 Hz Interlaced (8514A)
timing: 1024x768@75 Hz (VESA)
timing: 1280x1024@75 (VESA)
ctiming: 1280x1024@60
ctiming: 1440x1440@60
ctiming: 1440x1440@75
ctiming: 1680x1680@60
ctiming: 1600x1200@60
dtiming: 1920x1200@59
monitorrange: 30-75, 50-75
monitorname: LEN L220xwC
monitorserial: VL-45203


-------------


Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

---

### Post by sonderlich on 2008-08-27
Update: If I use the VGA (analog) connector, everything works fine. However, this is not an optimal solution, but it should indicate that the problem lies with the screen or the dvi adapter card.

---

