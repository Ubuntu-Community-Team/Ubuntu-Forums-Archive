---
title: "amdgpu displayport"
date: 2017-07-12
forum: Hardware
---

### Post by hexadeximal on 2017-07-12
I have had major problems with the new amdgpu driver 
It cannot properly detect my monitor, it is detected as unknown display and limits the resolution to 1024x768
This monitor only has a displayport output.
The other monitors using DVI or HDMI work fine.

The problem does not occur with the old fglrx drivers in early version and Debian 8.
I have tried Ubuntu 16.04 / 17.04 / Debian 9 and all have the same issue.
I have tried amdgpu-pro drivers and updating the kernel to 4.11 but still the same.

The only thing i see in the Xorg.log is a segfault

My gpu is an r9 380x

any one know how to get displayport working properly?

---

### Post by QIII on 2017-07-12
Hello!  

My R9 380X detects and uses the Asus monitor I have connected via DP using AMDGPU-PRO.

What make and model is your monitor?  It may not be providing an EDID back to your system.

---

### Post by hexadeximal on 2017-07-12
Interesting!
My monitor is a ASUS ROG Swift PG278Q 27" QHD


This is the output of 
find . | grep -i edid  
in /sys

./kernel/debug/dri/0/HDMI-A-2/edid_override
./kernel/debug/dri/0/DP-1/edid_override
./kernel/debug/dri/0/HDMI-A-1/edid_override
./kernel/debug/dri/0/VGA-1/edid_override
./kernel/debug/dri/1/DVI-I-1/edid_override
./kernel/debug/dri/1/DVI-D-1/edid_override
./kernel/debug/dri/1/HDMI-A-3/edid_override
./kernel/debug/dri/1/DP-2/edid_override
./devices/pci0000:00/0000:00:1c.4/0000:07:00.0/drm/card1/card1-HDMI-A-3/edid
./devices/pci0000:00/0000:00:1c.4/0000:07:00.0/drm/card1/card1-DP-2/edid
./devices/pci0000:00/0000:00:1c.4/0000:07:00.0/drm/card1/card1-DVI-D-1/edid
./devices/pci0000:00/0000:00:1c.4/0000:07:00.0/drm/card1/card1-DVI-I-1/edid
./devices/pci0000:00/0000:00:02.0/drm/card0/card0-HDMI-A-2/edid
./devices/pci0000:00/0000:00:02.0/drm/card0/card0-VGA-1/edid
./devices/pci0000:00/0000:00:02.0/drm/card0/card0-DP-1/edid
./devices/pci0000:00/0000:00:02.0/drm/card0/card0-HDMI-A-1/edid
./module/drm_kms_helper/parameters/edid_firmware
./module/drm/parameters/edid_fixup

more info from Xorg.0.log

EDID for output DisplayPort-1
[     3.227] (II) AMDGPU(0): Printing probed modes for output DisplayPort-1
[     3.227] (II) AMDGPU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[     3.227] (II) AMDGPU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[     3.227] (II) AMDGPU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[     3.227] (II) AMDGPU(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz e)
[     3.227] (II) AMDGPU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     3.228] (II) AMDGPU(0): EDID for output HDMI-A-2
[     3.230] (II) AMDGPU(0): EDID for output DVI-D-0
[     3.266] (II) AMDGPU(0): EDID for output DVI-I-1
[     3.266] (II) AMDGPU(0): Manufacturer: BNQ  Model: 78a5  Serial#: 21573
[     3.266] (II) AMDGPU(0): Year: 2013  Week: 43
[     3.266] (II) AMDGPU(0): EDID Version: 1.3
[     3.266] (II) AMDGPU(0): Digital Display Input
[     3.266] (II) AMDGPU(0): Max Image Size [cm]: horiz.: 53  vert.: 30
[     3.266] (II) AMDGPU(0): Gamma: 2.20
[     3.266] (II) AMDGPU(0): DPMS capabilities: Off

Since the other monitor (the BNQ) is identified here with name it seems like the EDID is not detected for the ASUS monitor

---

### Post by hexadeximal on 2017-07-12
Alright....
After adding the mode manually with xrandr it works.
Thought i tried that before but hey it finally works!

xrandr --newmode "2560x1440" 241.5 2560 2608 2640 2720 1440 1443 1448 1481 -hsync +vsync
xrandr --addmode  DisplayPort-1  2560x1440
xrandr --output DisplayPort-1 --mode 2560x1440

---

