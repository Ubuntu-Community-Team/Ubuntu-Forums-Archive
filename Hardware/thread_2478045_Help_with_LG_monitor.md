---
title: "Help with LG monitor"
date: 2022-08-15
forum: Hardware
---

### Post by chuchi on 2022-08-15
Hello there!

My old monitor, a LG 23mp48hq-p, broke and I have just bought a new one: LG 24BK550Y-i 24, to connect to my laptop.

The problem is that the image I see is not as sharp as with the old one, and after some minutes in front of the screen I feel dizzy.

I think I still have to configure my monitor, but I do not know how.

Could you please help me??

If it is helpful, this is the output information related to graphica cards after running 'lspci -v | less':



```
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09) (prog-if 00 [VGA controller])
        DeviceName: Intel(R) Graphics 4000
        Subsystem: Hewlett-Packard Company 3rd Gen Core processor Graphics Controller
        Flags: bus master, fast devsel, latency 0, IRQ 30
        Memory at 63000000 (64-bit, non-prefetchable) [size=4M]
        Memory at 50000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 5000 [size=64]
        Expansion ROM at 000c0000 [virtual] [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: i915
        Kernel modules: i915


01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Thames [Radeon HD 7500M/7600M Series] (prog-if 00 [VGA controller])
        DeviceName: Radeon HD 7670M
        Subsystem: Hewlett-Packard Company Radeon HD 7670M
        Flags: bus master, fast devsel, latency 0, IRQ 31
        Memory at 40000000 (64-bit, prefetchable) [size=256M]
        Memory at 62000000 (64-bit, non-prefetchable) [size=128K]
        I/O ports at 4000 [size=256]
        Expansion ROM at 62020000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: radeon
        Kernel modules: radeon

```

And I do not know why it shows two VGA entries when I am using an HDMI cable to connect to my computer.

Is it maybe because I have an old laptop? It is an HP Pavilion G6 bought on 2012.

Thanks a lot!!!

---

### Post by Yellow Pasque on 2022-08-18
With monitor connected, give the output of:
```
xrandr -q
```

---

### Post by chuchi on 2022-08-18
Hello Yellow!

Here is the output:

```

$ xrandr -q
Screen 0: minimum 320 x 200, current 3286 x 1080, maximum 16384 x 16384
LVDS-1 connected 1366x768+1920+7 (normal left inverted right x axis y axis) 344mm x 194mm
   1366x768      60.07*+  40.04  
   1360x768      59.80    59.96  
   1280x720      60.00    59.99    59.86    59.74  
   1024x768      60.04    60.00  
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   1024x576      59.95    59.96    59.90    59.82  
   960x600       59.93    60.00  
   960x540       59.96    59.99    59.63    59.82  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   864x486       59.92    59.57  
   800x512       60.17  
   700x525       59.98  
   800x450       59.95    59.82  
   640x512       60.02  
   720x450       59.89  
   700x450       59.96    59.88  
   640x480       60.00    59.94  
   720x405       59.51    58.99  
   684x384       59.88    59.85  
   680x384       59.80    59.96  
   640x400       59.88    59.98  
   576x432       60.06  
   640x360       59.86    59.83    59.84    59.32  
   512x384       60.00  
   512x288       60.00    59.92  
   480x270       59.63    59.82  
   400x300       60.32    56.34  
   432x243       59.92    59.57  
   320x240       60.05  
   360x202       59.51    59.13  
   320x180       59.84    59.32  
VGA-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 480mm x 270mm
   1920x1080     60.00*+  50.00    59.94  
   1680x1050     59.88  
   1400x1050     59.95  
   1600x900      60.00  
   1280x1024     75.02    60.02  
   1440x900      59.90  
   1280x800      59.91  
   1152x864      75.00  
   1280x720      60.00    50.00    59.94  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   720x576       50.00  
   720x480       60.00    59.94  
   640x480       75.00    60.00    59.94  
   720x400       70.08  
DP-1 disconnected (normal left inverted right x axis y axis)

Thanks a lot!

```

---

### Post by Yellow Pasque on 2022-08-18
You are running at the correct resolution. I would try adjusting the monitor's settings, particularly, adjusting sharpness and turning Super Resolution+ off if it is on.
You can see more description of the settings in the manual: [https://gscs-b2c.lge.com/downloadFile?fileId=VcyYZ836IBoR0mWwL9d9Cw](https://gscs-b2c.lge.com/downloadFile?fileId=VcyYZ836IBoR0mWwL9d9Cw)

---

