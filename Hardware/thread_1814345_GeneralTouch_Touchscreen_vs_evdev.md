---
title: "GeneralTouch Touchscreen vs evdev"
date: 2011-07-29
forum: Hardware
---

### Post by Attid on 2011-07-29
Hi
i have touchscreen 

lsusb
```
Bus 004 Device 002: ID 0dfc:0001 GeneralTouch Technology Co., Ltd Touchscreen
```

but ubuntu not see it

```

part of /var/log/Xorg.0.log
[ 32.795] (II) config/udev: Adding input device General Touch Co.,Ltd GeneralTouch Touchscreen (/dev/input/event3)
[ 32.795] (II) No input driver/identifier specified (ignoring)
[ 32.796] (II) config/udev: Adding input device General Touch Co.,Ltd GeneralTouch Touchscreen (/dev/input/js0)
[ 32.796] (II) No input driver/identifier specified (ignoring)

```

i create /usr/share/X11/xorg.conf.d/10-touch.conf
```

Section "InputClass"
        Identifier "touchscreen"
        MatchDevicePath "/dev/input/event1"
        Driver "evdev"
EndSection

```


now Xorg.0.log
```
[ 152.203] (II) config/udev: Adding input device General Touch Co.,Ltd GeneralTouch Touchscreen (/dev/input/event1)
[ 152.203] (**) General Touch Co.,Ltd GeneralTouch Touchscreen: Applying InputClass "touchscreen"
[ 152.203] (II) LoadModule: "evdev"
[ 152.204] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 152.238] (II) Module evdev: vendor="X.Org Foundation"
[ 152.238] compiled for 1.10.0.902, module version = 2.6.0
[ 152.238] Module class: X.Org XInput Driver
[ 152.238] ABI class: X.Org XInput driver, version 12.3
[ 152.238] (II) Using input driver 'evdev' for 'General Touch Co.,Ltd GeneralTouch Touchscreen'
[ 152.238] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 152.239] (**) General Touch Co.,Ltd GeneralTouch Touchscreen: always reports core events
[ 152.239] (**) General Touch Co.,Ltd GeneralTouch Touchscreen: Device: "/dev/input/event1"
[ 152.239] (--) General Touch Co.,Ltd GeneralTouch Touchscreen: Found absolute axes
[ 152.241] (--) General Touch Co.,Ltd GeneralTouch Touchscreen: Found x and y absolute axes
[ 152.242] (II) General Touch Co.,Ltd GeneralTouch Touchscreen: Configuring as mouse
------------------------------------------------------------------------------------^^^^^^^^^^
[ 152.242] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input1/event1"
[ 152.242] (II) XINPUT: Adding extended input device "General Touch Co.,Ltd GeneralTouch Touchscreen" (type: MOUSE)
[ 152.259] (WW) Touch X valuator does not match pointer X valuator, pointer emulation may be incorrect
[ 152.260] (WW) Touch Y valuator does not match pointer Y valuator, pointer emulation may be incorrect
[ 152.260] (II) General Touch Co.,Ltd GeneralTouch Touchscreen: initialized for absolute axes.
[ 152.260] (**) General Touch Co.,Ltd GeneralTouch Touchscreen: (accel) keeping acceleration scheme 1
[ 152.260] (**) General Touch Co.,Ltd GeneralTouch Touchscreen: (accel) acceleration profile 0
[ 152.260] (**) General Touch Co.,Ltd GeneralTouch Touchscreen: (accel) acceleration factor: 2.000
[ 152.260] (**) General Touch Co.,Ltd GeneralTouch Touchscreen: (accel) acceleration threshold: 4
[ 152.261] (II) config/udev: Adding input device General Touch Co.,Ltd GeneralTouch Touchscreen (/dev/input/js0)
[ 152.261] (II) No input driver/identifier specified (ignoring)
```

xserver try use my touchscreen as mouse, but must as touchscreen. how i can setup it ?

---

### Post by alponme on 2011-12-15
Hello,

0. If you have a kernel version lower than 3.2 you must patch the kernel: 

    Change in file linux/drivers/hid/hid-ids.h the line 
      #define USB_DEVICE_ID_GENERAL_TOUCH_WIN7_TWOFINGERS 0x0001 
   by
      #define USB_DEVICE_ID_GENERAL_TOUCH_WIN7_TWOFINGERS 0x0003 
    
Recompile kernel and reboot.


1.Power on the touchscreen and plug in the USB cable;
2.Unpack attached file gencalib.bz2 and run the calibration tool by
./gencalib
*****NOTE*****
Usage:
./gencalib --list
then you can see a input device which names like Generaltouch or 0dfc, replace its id in next command
./gencalib --device id
***************

3.After you pressed the four buttons shown on the display,you got output on the console like this,
Recalibration:
        New calibration data: 12493, 12493, 28070, 28070 is applied
  copy the snippet below into '/etc/X11/xorg.conf.d/99-calibration.conf'
Section "InputClass"
        Identifier      "calibration"
        MatchProduct    "USB Touchscreen 0dfc:0001"
        Option  "Calibration"   "1000 1000 4096 4096"
EndSection

4.Just put the line contains "Calibration" into the configuration file
/etc/X11/xorg.conf.d/10-evdev.conf(/usr/share/X11/xorg.conf.d/10-evdev.conf for ubuntu 11.04),to the section contains "touchscreen catchall",like this

Section "InputClass"
        Identifier "evdev touchscreen catchall"
#        MatchIsTouchscreen "on"
        MatchDevicePath "/dev/input/event*"
				MatchUSBID "0dfc:000c"     
				#MatchProduct	"HID 0dfc:000c"
				Driver "evdev"
				Option  "Calibration"   "1000 1000 4096 4096"
EndSection

then save it and close this file

5.Logout and login again,the touchscreen works correctly now.


*Tested under Opensuse 11.3 / ubuntu 11.04

---

