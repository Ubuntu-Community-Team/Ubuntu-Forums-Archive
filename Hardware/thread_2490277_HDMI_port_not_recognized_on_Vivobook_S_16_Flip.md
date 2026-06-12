---
title: "HDMI port not recognized on Vivobook S 16 Flip"
date: 2023-08-28
forum: Hardware
---

### Post by Tikhon03 on 2023-08-28
I have a new Asus Vivobook S 16 Flip, with kubuntu 22.04 installed.
```

uname -r
[FONT=monospace][COLOR=#000000]5.15.0-79-generic[/COLOR]
[/FONT]
```
It has an HDMI port, but the port is not detected. It does not even show up with xrandr
```

[FONT=monospace][COLOR=#000000]xrandr: Failed to get size of gamma for output default[/COLOR]
Screen 0: minimum 1920 x 1200, current 1920 x 1200, maximum 1920 x 1200
default connected primary 1920x1200+0+0 0mm x 0mm
   1920x1200     77.00* 
[/FONT]
```
The graphics card is intel iris Xe:
```

[COLOR=#000000][FONT=monospace]$ lspci -nn |grep  -Ei 'VGA|DISPLAY'[/FONT][/COLOR]
[FONT=monospace]00:02.0 [/FONT][COLOR=#FF5454][FONT=monospace]**VGA**[/FONT][/COLOR][COLOR=#000000][FONT=monospace] compatible controller [0300]: Intel Corporation Device [8086:a7a0] (rev 04)[/FONT][/COLOR]

```
[FONT=monospace]According to this website [https://dgpu-docs.intel.com/devices/hardware-table.html](https://dgpu-docs.intel.com/devices/hardware-table.html), the driver is under active development. I found this website, [https://dgpu-docs.intel.com/devices/iris-xe-max-graphics/index.html](https://dgpu-docs.intel.com/devices/iris-xe-max-graphics/index.html), but while it talks about both Iris Xe and Iris Xe Max, it is for Ubuntu 20.04.1. It is not clear to me if it still applies to 22.04. If it does apply to 22.04, it is not clear to me that I need to do the steps pertaining to the Xe Max specifically (which I do not have). I also tried
[/FONT]```
[FONT=monospace][COLOR=#000000]sudo dmesg | grep HDMI[/COLOR]  
[    0.300704] ACPI: Added _OSI(Linux-Lenovo-NV-[COLOR=#FF5454]**HDMI**[/COLOR][COLOR=#000000]-Audio)[/COLOR]
[/FONT]
```[FONT=monospace]
so at least HDMI audio seems to be supported. Does anyone have suggestions? Thank you.[/FONT]

---

### Post by TheFu on 2023-08-30
a) do case insensitive searches.
b) connect the HDMI port to a monitor that you know works.
c) ensure the HDMI port isn't disabled in the BIOS
d) ensure the HDMI port is enabled. In X11, I'd use **lxrandr** (but there are other choices).  For wayland, I don't have any clue.

I used a Vivabook for a few years with the iGPU in the 2017 Core i5. lxrandr made setting up with a projector for presentations trivial.  That system never had any OS newer than 18.04 on it and it doesn't have Iris Xe hardware.

Doubt I have any real help, but at least someone is reading your post. ;)

---

### Post by Tikhon03 on 2023-08-31
Thanks for reading my post, TheFu. You suggestions didn't help, although it generally seems like good advice to check connections, bios settings, and used monitors and cords that are known to work.

I did solve my own problem. IrisXe is in the oem kernel. This webpage [https://wiki.ubuntu.com/Kernel/OEMKernel](https://wiki.ubuntu.com/Kernel/OEMKernel) indicated that the latest oem kernel was linux-oem-22.04c. So I ran
```

sudo apt install linux-oem-22.04c

```
rebooted, and now the output of xrandr is
```

[FONT=monospace][COLOR=#000000]Screen 0: minimum 320 x 200, current 1920 x 1200, maximum 16384 x 16384[/COLOR]
eDP-1 connected primary 1920x1200+0+0 (normal left inverted right x axis y axis) 344mm x 215mm
   1920x1200     60.00*+  60.00    48.00   
   1920x1080     60.00   
   1600x1200     60.00   
   1680x1050     60.00   
   1400x1050     60.00   
   1600x900      60.00   
   1280x1024     60.00   
   1400x900      60.00   
   1280x960      60.00   
   1440x810      60.00   
   1368x768      60.00   
   1280x800      60.00   
   1280x720      60.00   
   1024x768      60.00   
   960x720       60.00   
   928x696       60.00   
   896x672       60.00   
   1024x576      60.00   
   960x600       60.00   
   960x540       60.00   
   800x600       60.00   
   840x525       60.00   
   864x486       60.00   
   700x525       60.00   
   800x450       60.00   
   640x512       60.00   
   700x450       60.00   
   640x480       60.00   
   720x405       60.00   
   684x384       60.00   
   640x360       60.00   
   512x384       60.00   
   512x288       60.00   
   480x270       60.00   
   400x300       60.00   
   432x243       60.00   
   320x240       60.00   
   360x202       60.00   
   320x180       60.00   
HDMI-1 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)
DP-3 disconnected (normal left inverted right x axis y axis)
DP-4 disconnected (normal left inverted right x axis y axis)
[/FONT]
```
So, the HDMI port is working now.

---

