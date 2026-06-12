---
title: "Problems with 4k External Display"
date: 2017-04-11
forum: Hardware
---

### Post by cbass123 on 2017-04-11
Hello, I've got a similar problem where I can't use 4k resolution on my mointor.

I have a Dell XPS-13-9360, with a usb-c to dp cable. It does work with 1920x1080
[B]
lspci -vk | grep -iA13 vga[/B]
```
00:02.0 VGA compatible controller: Intel Corporation Device 5916 (rev 02) (prog-if 00 [VGA controller])
    DeviceName:  Onboard IGD
    Subsystem: Dell Device 075b
    Flags: bus master, fast devsel, latency 0, IRQ 134
    Memory at db000000 (64-bit, non-prefetchable) [size=16M]
    Memory at 90000000 (64-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915_bpo
    Kernel modules: i915_bpo

00:04.0 Signal processing controller: Intel Corporation Skylake Processor Thermal Subsystem (rev 02)
    Subsystem: Dell Skylake Processor Thermal Subsystem
```

**lsusb**
```
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 0bda:8153 Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 2109:0812 VIA Labs, Inc. VL812 Hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 007: ID 0c45:670c Microdia 
Bus 001 Device 005: ID 04f3:20d0 Elan Microelectronics Corp. 
Bus 001 Device 003: ID 0cf3:e300 Atheros Communications, Inc. 
Bus 001 Device 008: ID 045e:07b6 Microsoft Corp. 
Bus 001 Device 006: ID 1038:1361 SteelSeries ApS Ideazon Sensei
Bus 001 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 2109:2812 VIA Labs, Inc. VL812 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

**xrandr**
```
Screen 0: minimum 8 x 8, current 3200 x 1800, maximum 32767 x 32767
eDP1 connected primary 3200x1800+0+0 (normal left inverted right x axis y axis) 294mm x 165mm
   3200x1800     59.98*+  47.99  
   2880x1620     60.00  
   2560x1440     60.00  
   2048x1536     60.00  
   1920x1440     60.00  
   1856x1392     60.01  
   1792x1344     60.01  
   2048x1152     60.00  
   1920x1200     59.95  
   1920x1080     60.00    59.93  
   1600x1200     60.00  
   1680x1050     59.95    59.88  
   1600x1024     60.17  
   1400x1050     59.98  
   1600x900      60.00  
   1280x1024     60.02  
   1440x900      59.89  
   1280x960      60.00  
   1368x768      60.00  
   1360x768      59.80    59.96  
   1152x864      60.00  
   1280x720      60.00  
   1024x768      60.00  
   1024x576      60.00  
   960x540       60.00  
   800x600       60.32    56.25  
   864x486       60.00  
   640x480       59.94  
   720x405       60.00  
   640x360       60.00  
DP1 connected (normal left inverted right x axis y axis)
   3840x2160     60.00 +  30.00    25.00    24.00    29.97    23.98    29.98  
   1920x2160     59.99  
   1920x1080     60.00    60.00    50.00    59.94  
   1920x1080i    60.00    50.00    59.94  
   1680x1050     59.95  
   1280x1024     75.02    60.02  
   1440x900      74.98    59.89  
   1280x960      60.00  
   1280x720      60.00    50.00    59.94  
   1024x768      75.08    60.00  
   800x600       75.00    60.32  
   720x576       50.00  
   720x480       60.00    59.94  
   640x480       75.00    72.81    66.67    60.00    59.94  
   720x400       70.08  
DP2 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
```


Anyone able to help?

---

### Post by howefield on 2017-04-11
Post moved to own thread.

---

### Post by cbass123 on 2017-04-11
Solved it by settings the refresh rate to 30hz. Not really what I wanted. But it works.

Used xrandr -s 3840x2160 -r 30

However, if someone could help find a way to run it in 60hz, I'd be greatful.

---

### Post by cbass123 on 2017-04-12
Ok, finally solved this issue by upgrading kernel to 4.9. Was prevously running 4.4

---

