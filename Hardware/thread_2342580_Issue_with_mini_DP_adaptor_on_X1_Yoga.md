---
title: "Issue with mini DP adaptor on X1 Yoga"
date: 2016-11-08
forum: Hardware
---

### Post by Felix_Binder on 2016-11-08
Hi All,

I've been trying in vain to get a mini displayport to VGA adaptor working on my X1 Yoga (which comes with Intel Skylake graphics). I'm using Ubuntu 16.10.

With the adaptor attached to the mini DP port and to the external screen via VGA cable it's shown as disconnected:
```
xrandr --current
Screen 0: minimum 320 x 200, current 2560 x 1440, maximum 8192 x 8192
eDP-1 connected primary 2560x1440+0+0 (normal left inverted right x axis y axis) 310mm x 174mm
   2560x1440     60.00*+
   1920x1440     60.00  
   1856x1392     60.01  
   1792x1344     60.01  
   1920x1200     59.95  
   1920x1080     59.93  
   1600x1200     60.00  
   1680x1050     59.95    59.88  
   1600x1024     60.17  
   1400x1050     59.98  
   1280x1024     60.02  
   1440x900      59.89  
   1280x960      60.00  
   1360x768      59.80    59.96  
   1152x864      60.00  
   1024x768      60.04    60.00  
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   960x600       60.00  
   960x540       59.99  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   800x512       60.17  
   700x525       59.98  
   640x512       60.02  
   720x450       59.89  
   640x480       60.00    59.94  
   680x384       59.80    59.96  
   576x432       60.06  
   512x384       60.00  
   400x300       60.32    56.34  
   320x240       60.05  
DP-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)
HDMI-2 disconnected (normal left inverted right x axis y axis)
```
If I type in
```
xrandr --addmode DP1 1680x1050
xrandr --output DP1 --mode 1680x1050 --left-of eDP-1
```
the external display does turn on with what seems to be the correct resolution (1680x1050 is its native resolution). There is a lot of flickering though and the laptops internal screen ends up with the wrong resolution: The menu remains in the right place but all windows are distorted and the mouse doesn't click where the cursor is but somewhere else instead. This distortion persists when I disconnect the internal screen and I have to reset it manually with ```
xrandr --output eDP-1 -- mode 2560x1440
``` When I reboot the machine without the adaptor attached it automatically resets the screen to the distorted resolution.

I should add that the adaptor works just fine on a friends Macbook.

How do I get the adaptor to work correctly? I'd greatly appreciate your help or any pointers you might have!

Further information, in case it's useful:
```
lspci
00:00.0 Host bridge: Intel Corporation Skylake Host Bridge/DRAM Registers (rev 08)
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 520 (rev 07)
00:08.0 System peripheral: Intel Corporation Skylake Gaussian Mixture Model
00:13.0 Non-VGA unclassified device: Intel Corporation Device 9d35 (rev 21)
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI #1 (rev 21)
00:17.0 SATA controller: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] (rev 21)
00:1c.0 PCI bridge: Intel Corporation Device 9d10 (rev f1)
00:1c.2 PCI bridge: Intel Corporation Device 9d12 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Sunrise Point-LP LPC Controller (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection I219-V (rev 21)
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS525A PCI Express Card Reader (rev 01)
04:00.0 Network controller: Intel Corporation Wireless 8260 (rev 3a)
```

---

### Post by noleti on 2017-01-31
Hi Felix,

Did you manage to solve the problem? I seem to have the same setup and I face the same problem. I'm using a mini-displayport to VGA adapter that works on my X1 Carbon, but not on the X1 Yoga. Both run 16.10. Using your method I was able to activate the external screen, thanks! After activation, xrandr still lists DP1 as disconnected, but I can use it correctly.

---

### Post by wildmanne39 on 2017-01-31
> **noleti said:**
> Hi Felix,

Did you manage to solve the problem? I seem to have the same setup and I face the same problem. I'm using a mini-displayport to VGA adapter that works on my X1 Carbon, but not on the X1 Yoga. Both run 16.10. Using your method I was able to activate the external screen, thanks! After activation, xrandr still lists DP1 as disconnected, but I can use it correctly.
Welcome to the forum you should start your own thread with a descriptive title for best support, the OP of this thread has not logged in since he made this post.
Thanks

---

