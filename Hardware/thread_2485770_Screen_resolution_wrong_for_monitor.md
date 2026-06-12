---
title: "Screen resolution wrong for monitor"
date: 2023-04-09
forum: Hardware
---

### Post by kotgc on 2023-04-09
I installed Ubuntu 22.04 and the monitor needs a Screen Display Resolution of 1280 x 1024 (5:4) Refresh Rate 75.02 Hz.
However, Ubuntu sets the Screen Display Resolution 1024 x 768 (4:3) Refresh Rate 60.00 Hz.
There is no option for the correct Screen Display Resolution?
Here's the GPU output:
```
ubuntu@ubuntu:~$ inxi -Gxx:
  Device-1: NVIDIA GK208B [GeForce GT 710] vendor: ASUSTeK driver: nvidia
    v: 470.182.03 pcie: speed: 5 GT/s lanes: 8 ports: active: none
    off: DVI-D-1,HDMI-A-1,VGA-1 empty: none bus-ID: 01:00.0
    chip-ID: 10de:128b
  Display: x11 server: X.Org v: 1.21.1.3 compositor: gnome-shell v: 42.5
    driver: X: loaded: nvidia unloaded: fbdev,modesetting,nouveau,vesa
    gpu: nvidia display-ID: :1 screens: 1
  Screen-1: 0 s-res: 3584x1024 s-dpi: 96
  Monitor-1: DVI-D-0 pos: center res: 1280x1024 dpi: 68 diag: 551mm (21.7")
  Monitor-2: HDMI-0 pos: primary,left res: 1280x1024 dpi: 68
    diag: 551mm (21.7")
  Monitor-3: VGA-0 pos: primary,right res: 1024x768 size: N/A
  OpenGL: renderer: NVIDIA GeForce GT 710/PCIe/SSE2
    v: 4.6.0 NVIDIA 470.182.03 direct render: Yes
ubuntu@ubuntu:~$ 

```

I installed the NVIDIA Settings and this doesn't offer the correct resolution.

---

### Post by lucio-a on 2023-04-09
You can set the resolution and refresh rate using Gnome Settings, but if you have no option for the resolution you want it's possible to force using a kernel parameter like this, [FONT=times new roman]video=*desired_display*:1280x1024[/FONT][FONT=times new roman]@75[/FONT].

---

### Post by kotgc on 2023-04-12
Thanks, I ran the command and rebooted, however no change?
```

ubuntu@ubuntu:~$ xrandr 
Screen 0: minimum 8 x 8, current 3584 x 1024, maximum 16384 x 16384
VGA-0 connected 1024x768+2560+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00*+
   1600x900      59.82  
   1400x900      59.88  
   1368x768      59.88    59.85  
   1280x800      59.91    59.81  
   1280x720      59.86    59.74  
   1024x576      59.90    59.82  
   960x540       59.82    59.63  
   864x486       59.92    59.57  
   800x600       72.19    60.32    56.25  
   800x450       59.82  
   700x450       59.88  
   684x384       59.88    59.85  
   640x480       59.94  
   640x400       59.98    59.88  
   640x360       59.86    59.83  
   512x384       60.00  
   512x288       60.00    59.92  
   480x270       59.82    59.63  
   432x243       59.92    59.57  
   400x300       72.19  
   320x240       60.05  
DVI-D-0 connected primary 1280x1024+1280+0 (normal left inverted right x axis y axis) 480mm x 270mm
   1920x1080     60.00 +  74.97    59.94    50.00    60.00    50.04  
   1680x1050     59.95  
   1440x900      59.89  
   1280x1024     75.02*   60.02  
   1280x960      60.00  
   1280x720      60.00    59.94    50.00  
   1024x768      75.03    70.07    60.00  
   800x600       75.00    72.19    60.32    56.25  
   720x576       50.00  
   720x480       59.94  
   640x480       75.00    72.81    59.94    59.93  
HDMI-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 480mm x 270mm
   1920x1080     60.00 +  74.97    59.94    50.00    60.00    50.04  
   1680x1050     59.95  
   1440x900      59.89  
   1280x1024     75.02*   60.02  
   1280x960      60.00  
   1280x720      60.00    59.94    50.00  
   1024x768      75.03    70.07    60.00  
   800x600       75.00    72.19    60.32    56.25  
   720x576       50.00  
   720x480       59.94  
   640x480       75.00    72.81    59.94    59.93  
ubuntu@ubuntu:~$ video=VGA-0:1280x1024@75

```

---

### Post by kotgc on 2023-04-30
Apparently I need to use Nouveau, but I haven't figured it out yet?

---

