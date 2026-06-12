---
title: "stmicroelectronics hdmi monitor"
date: 2021-04-11
forum: Hardware
---

### Post by Andrew F in Australia on 2021-04-11
Hi All,

I bought one of these monitors as a replacement for an old screen on a Zalman Home Theatre PC (Server for about 4000 ripped CDs)

[https://www.jaycar.com.au/1024x600-hdmi-7in-screen-with-usb-capacitive-touch/p/XC9026?pos=2&queryId=7bdd1b2188b188bb36643a9d5c3ac280](https://www.jaycar.com.au/1024x600-hdmi-7in-screen-with-usb-capacitive-touch/p/XC9026?pos=2&queryId=7bdd1b2188b188bb36643a9d5c3ac280)

[https://www.jaycar.com.au/medias/sys_master/images/images/9505029718046/XC9026-manualMain.pdf](https://www.jaycar.com.au/medias/sys_master/images/images/9505029718046/XC9026-manualMain.pdf)

The manual has config settings for kali and mint(?) that I couldn't get to work.

[https://linux-hardware.org/index.php?id=usb:0483-5750](https://linux-hardware.org/index.php?id=usb:0483-5750) might also have some pointers

Unfortunately, it only displays on Windows after the boot screen has finished loading.

Is there any way I can get this monitor recognised in either grub or in linux?

Outputs below:

dmesg when screen plugged in:
```
[  254.411581] usb 1-3: new full-speed USB device number 7 using xhci_hcd
[  254.561771] usb 1-3: New USB device found, idVendor=0483, idProduct=5750, bcdDevice= 2.00
[  254.561776] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  254.561780] usb 1-3: Product: ByQDtech &#35302;&#25511;USB&#40736;&#26631;
[  254.561784] usb 1-3: Manufacturer: &#28145;&#22323;&#24066;&#20840;&#21160;&#30005;&#23376;&#25216;&#26415;&#26377;&#38480;&#20844;&#21496;
[  254.561786] usb 1-3: SerialNumber: 8D6D58885353
[  254.564600] input: &#28145;&#22323;&#24066;&#20840;&#21160;&#30005;&#23376;&#25216;&#26415;&#26377;&#38480;&#20844;&#21496; ByQDtech &#35302;&#25511;USB&#40736;&#26631; as /devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.0/0003:0483:5750.0005/input/input33
[  254.565022] hid-multitouch 0003:0483:5750.0005: input,hidraw1: USB HID v1.10 Device [&#28145;&#22323;&#24066;&#20840;&#21160;&#30005;&#23376;&#25216;&#26415;&#26377;&#38480;&#20844;&#21496; ByQDtech &#35302;&#25511;USB&#40736;&#26631;] on usb-0000:00:14.0-3/input0

```

lsusb

```
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 1038:1122 SteelSeries ApS SteelSeries KLC
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 007: ID 0483:5750 STMicroelectronics LED badge -- mini LED display -- 11x44
Bus 001 Device 006: ID 8087:0aaa Intel Corp. 
Bus 001 Device 005: ID 5986:211c Acer, Inc HD Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

xrandr --query
```

Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 16384 x 16384
eDP-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 381mm x 214mm
   1920x1080    144.00*+  60.01    60.02    59.97    59.96    59.93  
   1680x1050     84.94    74.89    69.88    59.95    59.88  
   1600x1024     60.17  
   1400x1050     85.00    74.76    70.00    59.98  
   1600x900      59.99    59.94    59.95    59.82  
   1280x1024     85.02    75.02    60.02  
   1440x900      59.89  
   1400x900      59.96    59.88  
   1280x960      85.00    60.00  
   1440x810      60.00    59.97  
   1368x768      59.88    59.85  
   1360x768      59.80    59.96  
   1280x800      59.99    59.97    59.81    59.91  
   1152x864     100.00    85.06    85.00    75.00    75.00    70.00    60.00  
   1280x720      60.00    59.99    59.86    59.74  
   1024x768      85.00    75.05    60.04    85.00    75.03    70.07    60.00  
   1024x768i     86.96  
   960x720       85.00    75.00    60.00  
   928x696       75.00    60.05  
   896x672       75.05    60.01  
   1024x576      59.95    59.96    59.90    59.82  
   960x600       59.93    60.00  
   832x624       74.55  
   960x540       59.96    59.99    59.63    59.82  
   800x600       85.00    75.00    70.00    65.00    60.00    85.14    72.19    75.00    60.32    56.25  
   840x525       85.02    74.96    69.88    60.01    59.88  
   864x486       59.92    59.57  
   800x512       60.17  
   700x525       85.08    74.76    70.06    59.98  
   800x450       59.95    59.82  
   640x512       85.02    75.02    60.02  
   720x450       59.89  
   700x450       59.96    59.88  
   640x480       85.09    60.00    85.01    72.81    75.00    59.94  
   720x405       59.51    58.99  
   720x400       85.04  
   684x384       59.88    59.85  
   680x384       59.80    59.96  
   640x400       59.88    59.98    85.08  
   576x432      100.11    85.15    85.09    75.00    75.00    70.00    60.06  
   640x360       59.86    59.83    59.84    59.32  
   640x350       85.08  
   512x384       85.00    75.03    70.07    60.00  
   512x384i      87.06  
   512x288       60.00    59.92  
   416x312       74.66  
   480x270       59.63    59.82  
   400x300       85.27    72.19    75.12    60.32    56.34  
   432x243       59.92    59.57  
   320x240       85.18    72.81    75.00    60.05  
   360x202       59.51    59.13  
   360x200       85.04  
   320x200       85.27  
   320x180       59.84    59.32  
   320x175       85.27  


```

---

### Post by Andrew F in Australia on 2021-04-15
Issue was bigger - RAM wasn't seated in original machine - took a service tech ages to find it.

Clicked in the RAM, and works perfectly.

---

