---
title: "HDMI Daewoo TV 32' lcd DLT-32H1 sinc issue"
date: 2018-11-24
forum: Hardware
---

### Post by danjde on 2018-11-24
Hi Friends!
I'm using Ubuntu 16.04, kernel 4.15.0-33-generic #36~16.04.1-Ubuntu SMP. on HP Pavilion laptop.
This is my hardware listed by lspci:

```
00:00.0 Host bridge: Intel Corporation Device 5904 (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Device 5916 (rev 02)
00:04.0 Signal processing controller: Intel Corporation Skylake Processor Thermal Subsystem (rev 02)
00:13.0 Non-VGA unclassified device: Intel Corporation Device 9d35 (rev 21)
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:15.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller (rev 21)
00:15.1 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI (rev 21)
00:17.0 SATA controller: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] (rev 21)
00:1d.0 PCI bridge: Intel Corporation Device 9d18 (rev f1)
00:1d.1 PCI bridge: Intel Corporation Device 9d19 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Device 9d4e (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Device 9d71 (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
01:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS522A PCI Express Card Reader (rev 01)
02:00.0 Network controller: Intel Corporation Device 24fb (rev 10)
```


This my device and video driver:

```
  *-display               
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
```


Connecting the laptop HDMI port to the television HDMI port, obtain a sort of fast flickering/flashing, that obviously does not permit to view the laptop screen on television lcd.
I've try customizing the resolution with xrandr, with no luck.


This the xrandr output with TV connected:

```
xrandr
Screen 0: minimum 8 x 8, current 3280 x 1080, maximum 32767 x 32767
eDP1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 308mm x 173mm
   1920x1080     60.01*+  59.93    40.00  
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
HDMI1 connected 1360x768+1920+0 (normal left inverted right x axis y axis) 580mm x 330mm
   1360x768      60.02*+
   1920x1080i    60.00    50.00    59.94  
   1280x1024     75.02    60.02  
   1280x960      60.00  
   1920x540      60.05  
   1152x864      75.00  
   1280x768      60.00  
   1280x720      60.00    50.00    59.94  
   1024x768      75.03    70.07    60.00  
   832x624       74.55  
   800x600       72.19    75.00    60.32    56.25  
   720x576i     100.00    50.00  
   720x576       50.00  
   720x480       60.00    59.94  
   720x480i      60.00    59.94  
   640x480       75.00    72.81    78.86    66.67    60.00    59.94  
   720x400       70.08  

```


These are my attempts:


1) 
```
xrandr --newmode "1366x768_60" 85.86  1368 1440 1584 1800  768 769 772 795  -HSync +Vsync
xrandr --addmode HDMI1 1366x768_60
xrandr --output HDMI1 --mode 1366x768_60
```


2) 
```
xrandr --output HDMI1 --mode 1360x768 --rate 60
```

3)
```
xrandr --output HDMI1 --mode 1920x1080i --rate 60
```

4)
```
xrandr --output HDMI1 --mode 1920x1080i
```

5)
```
xrandr --output HDMI1 --mode 1280x960
```



Anyone of you could help me to solve this issue? :-)

Many thanks!

---

### Post by danjde on 2018-11-24
I've found that playing a video with audio content, the television show correctly, withouth flashing.
Running xrandr in this scenario:

```
xrandr
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 32767 x 32767
eDP1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 308mm x 173mm
   1920x1080     60.01*+  59.93    40.00  
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
HDMI1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 580mm x 330mm
   1360x768      60.02 +
   1920x1080i    60.00*   50.00    59.94  
   1280x1024     75.02    60.02  
   1280x960      60.00  
   1920x540      60.05  
   1152x864      75.00  
   1280x768      60.00  
   1280x720      60.00    50.00    59.94  
   1024x768      75.03    70.07    60.00  
   832x624       74.55  
   800x600       72.19    75.00    60.32    56.25  
   720x576i     100.00    50.00  
   720x576       50.00  
   720x480       60.00    59.94  
   720x480i      60.00    59.94  
   640x480       75.00    72.81    78.86    66.67    60.00    59.94  
   720x400       70.08  
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

```

---

