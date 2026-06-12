---
title: "ubuntu 11.4 touch screen madness help please"
date: 2011-09-11
forum: Hardware
---

### Post by cmttmp on 2011-09-11
first things first.. fresh/updated install of ubuntu 11.4 

Linux STRIPPED 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

So i run the live cd. im hooked up to a 40" samsung monitor with irtouch everything works FINE. touch screen functions and is not having any issues when run in landscape mode.

so i dug though a tonne of documentation to get the monitor rotated 90 CW great runs in protrait woohoo. 

ofcourse this now leaves the touch screen disassociated with the screen
so i attempted to swapaxes and inver the Y axis. 

this leaves me with a very "jittery" touchscreen with the cursor 
jumping to the 0 line every scan and i dont know why but desperately 
need to have a fix. ugh

pretty much all the debug outputs are found inline below. 

/usr/share/X11/xorg.conf.d/11-iptouch-quirks.conf

> 
Section "InputClass"
Identifier "IRTOUCH SYSTEMS"
MatchUSBID "6615:0012"
# MatchIsTouchscreen "on"
#MatchDevicePath "/dev/input/event2"
Driver "evdev"
Option "SwapAxes" "1"
Option "InvertY" "1"
Option "Calibration" "0 32767 0 32767"
EndSection

Output from xinput list --long 9 (my device number) 

> 

Beijing IRTOUCH SYSTEMS Co.,LtD IRTOUCH InfraRed TouchScreen    id=9    [slave  pointer  (2)]
        Reporting 3 classes:
                Class originated from: 9
                Buttons supported: 12
                Button labels: Button Left Button Middle Button Right Button Wheel Up Button Wheel Down Button Horiz Wheel Left Button Horiz Wheel Right Button Side Button Extra Button Forward Button Back Button Task
                Button state:
                Class originated from: 9
                Detail for Valuator 0:
                  Label: Abs X
                  Range: 0.000000 - 32767.000000
                  Resolution: 10000 units/m
                  Mode: absolute
                  Current value: 540.000000
                Class originated from: 9
                Detail for Valuator 1:
                  Label: Abs Y
                  Range: 0.000000 - 32767.000000
                  Resolution: 10000 units/m
                  Mode: absolute
                  Current value: 960.000000
excerpt from /var/log/Xlog.0.log

> 
[  1614.766] (II) config/udev: Adding input device Beijing IRTOUCH SYSTEMS Co.,LtD IRTOUCH InfraRed TouchScreen (/dev/input/event2)
[  1614.766] (**) Beijing IRTOUCH SYSTEMS Co.,LtD IRTOUCH InfraRed TouchScreen: Applying InputClass "evdev pointer catchall"
[  1614.766] (**) Beijing IRTOUCH SYSTEMS Co.,LtD IRTOUCH InfraRed TouchScreen: Applying InputClass "evdev TouchScreen catchall"
[  1614.766] (II) Using input driver 'evdev' for 'Beijing IRTOUCH SYSTEMS Co.,LtD IRTOUCH InfraRed TouchScreen'
[  1614.766] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1614.767] (**) Beijing IRTOUCH SYSTEMS Co.,LtD IRTOUCH InfraRed TouchScreen: always reports core events
[  1614.767] (**) Beijing IRTOUCH SYSTEMS Co.,LtD IRTOUCH InfraRed TouchScreen: Device: "/dev/input/event2"
[  1614.770] (--) Beijing IRTOUCH SYSTEMS Co.,LtD IRTOUCH InfraRed TouchScreen: Found 12 mouse buttons
[  1614.770] (--) Beijing IRTOUCH SYSTEMS Co.,LtD IRTOUCH InfraRed TouchScreen: Found absolute axes
[  1614.771] (II) evdev-grail: failed to open grail, no gesture support
[  1614.771] (--) Beijing IRTOUCH SYSTEMS Co.,LtD IRTOUCH InfraRed TouchScreen: Found x and y absolute axes
[  1614.771] (**) Option "InvertY" "1"
[  1614.771] (**) Option "SwapAxes" "1"
[  1614.771] (II) Beijing IRTOUCH SYSTEMS Co.,LtD IRTOUCH InfraRed TouchScreen: Configuring as mouse
[  1614.771] (**) Beijing IRTOUCH SYSTEMS Co.,LtD IRTOUCH InfraRed TouchScreen: YAxisMapping: buttons 4 and 5
[  1614.771] (**) Beijing IRTOUCH SYSTEMS Co.,LtD IRTOUCH InfraRed TouchScreen: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  1614.771] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/input/input2/event2"
[  1614.771] (II) XINPUT: Adding extended input device "Beijing IRTOUCH SYSTEMS Co.,LtD IRTOUCH InfraRed TouchScreen" (type: MOUSE)
[  1614.771] (II) Beijing IRTOUCH SYSTEMS Co.,LtD IRTOUCH InfraRed TouchScreen: initialized for absolute axes.
[  1614.772] (**) Beijing IRTOUCH SYSTEMS Co.,LtD IRTOUCH InfraRed TouchScreen: (accel) keeping acceleration scheme 1
[  1614.772] (**) Beijing IRTOUCH SYSTEMS Co.,LtD IRTOUCH InfraRed TouchScreen: (accel) acceleration profile 0
[  1614.772] (**) Beijing IRTOUCH SYSTEMS Co.,LtD IRTOUCH InfraRed TouchScreen: (accel) acceleration factor: 2.000
[  1614.772] (**) Beijing IRTOUCH SYSTEMS Co.,LtD IRTOUCH InfraRed TouchScreen: (accel) acceleration threshold: 4
[  1614.773] (II) config/udev: Adding input device Beijing IRTOUCH SYSTEMS Co.,LtD IRTOUCH InfraRed TouchScreen (/dev/input/js0)
[  1614.773] (II) No input driver/identifier specified (ignoring)
[  1614.774] (II) config/udev: Adding input device Beijing IRTOUCH SYSTEMS Co.,LtD IRTOUCH InfraRed TouchScreen (/dev/input/mouse0)
[  1614.774] (II) No input driver/identifier specified (ignoring)
and finally my lsusb 
> 
root@kiosktwo:~# lsusb
Bus 006 Device 002: ID 2109:0811  
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 003: ID 046d:c318 Logitech, Inc. Illuminated Keyboard
Bus 005 Device 002: ID 6615:0012 IRTOUCHSYSTEMS Co. Ltd. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c51b Logitech, Inc. V220 Cordless Optical Mouse for Notebooks
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
does anyone know what/how i can have the touchscreen function better?
thank you for your help

---

