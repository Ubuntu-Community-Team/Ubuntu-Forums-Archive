---
title: "Secondary screen detected but black screen with Intel UHD graphics card"
date: 2020-12-12
forum: Hardware
---

### Post by juanchomdiaz on 2020-12-12
Hi! I have an HP ProBook 440 G7 with i7-10510U and INTEL UHD GRAPHICS.

The problem:
When i connect to my external monitor (a Samsung BX2250) via HDMI, the screen is detected (i can see it in display settings) but the external monitor remains black. Seams like a bad frequency or resolution. I tried adding a new mode to xrandr with no luck. Also i tried different versions of kernels from 5.4 to 5.9.12

I am using Ubuntu 20.10

This is my lspci:

```
0:00.0 Host bridge: Intel Corporation Device 9b61 (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics (rev 02)
00:04.0 Signal processing controller: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem (rev 0c)
00:12.0 Signal processing controller: Intel Corporation Comet Lake Thermal Subsytem
00:14.0 USB controller: Intel Corporation Device 02ed
00:14.2 RAM memory: Intel Corporation Device 02ef
00:14.3 Network controller: Intel Corporation Wireless-AC 9462
00:14.5 SD Host controller: Intel Corporation Device 02f5
00:15.0 Serial bus controller [0c80]: Intel Corporation Serial IO I2C Host Controller
00:16.0 Communication controller: Intel Corporation Comet Lake Management Engine Interface
00:17.0 SATA controller: Intel Corporation Comet Lake SATA AHCI Controller
00:1d.0 PCI bridge: Intel Corporation Device 02b0 (rev f0)
00:1d.4 PCI bridge: Intel Corporation Device 02b4 (rev f0)
00:1f.0 ISA bridge: Intel Corporation Device 0284
00:1f.3 Multimedia audio controller: Intel Corporation Device 02c8
00:1f.4 SMBus: Intel Corporation Device 02a3
00:1f.5 Serial bus controller [0c80]: Intel Corporation Comet Lake SPI (flash) Controller
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
02:00.0 Non-Volatile memory controller: Sandisk Corp Device 5009 (rev 01)
```


inxi -Gx output:

```
Graphics: Device-1: Intel UHD Graphics vendor: Hewlett-Packard driver: i915 v: kernel bus ID: 00:02.0
           Device-2: Lite-On HP HD Camera type: USB driver: uvcvideo bus ID: 1-2:2
           Display: x11 server: X.Org 1.20.9 driver: modesetting unloaded: fbdev,vesa resolution: 1366x768~60Hz
           OpenGL: renderer: Mesa Intel UHD Graphics (CML GT2) v: 4.6 Mesa 20.2.1 direct render: Yes
```

xrandr output (with hdmi cable connected to external monitor and black screen):

```
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 16384 x 16384
eDP-1 connected primary 1366x768+0+0 (normal left inverted right x axis y axis) 309mm x 173mm
   1366x768 60.06*+ 40.04
   1360x768 59.80 59.96
   1280x720 60.00 59.99 59.86 59.74
   1024x768 60.04 60.00
   960x720 60.00
   928x696 60.05
   896x672 60.01
   1024x576 59.95 59.96 59.90 59.82
   960x600 59.93 60.00
   960x540 59.96 59.99 59.63 59.82
   800x600 60.00 60.32 56.25
   840x525 60.01 59.88
   864x486 59.92 59.57
   800x512 60.17
   700x525 59.98
   800x450 59.95 59.82
   640x512 60.02
   720x450 59.89
   700x450 59.96 59.88
   640x480 60.00 59.94
   720x405 59.51 58.99
   684x384 59.88 59.85
   680x384 59.80 59.96
   640x400 59.88 59.98
   576x432 60.06
   640x360 59.86 59.83 59.84 59.32
   512x384 60.00
   512x288 60.00 59.92
   480x270 59.63 59.82
   400x300 60.32 56.34
   432x243 59.92 59.57
   320x240 60.05
   360x202 59.51 59.13
   320x180 59.84 59.32
HDMI-1 connected (normal left inverted right x axis y axis)
   1920x1080 60.00 + 50.00 59.94
   1920x1080i 60.00 50.00 59.94
   1600x1200 60.00
   1680x1050 59.88
   1280x1024 75.02 60.02
   1440x900 74.98 59.90
   1280x960 60.00
   1280x800 59.91
   1152x864 75.00
   1280x720 60.00 50.00 59.94
   1024x768 75.03 70.07 60.00
   832x624 74.55
   800x600 72.19 75.00 60.32 56.25
   720x576 50.00
   720x480 60.00 59.94
   640x480 75.00 72.81 66.67 60.00 59.94
   720x400 70.08
DP-1 disconnected (normal left inverted right x axis y axis)
HDMI-2 disconnected (normal left inverted right x axis y axis)
```

THANKS IN ADVANCED!!!
Juan Manuel Diaz

---

