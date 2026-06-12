---
title: "Fujitsu Simens T4010D Wacom pen doesn't work until i restart X"
date: 2009-07-20
forum: Hardware
---

### Post by verb0ss on 2009-07-20
Hi all.
I have problem with my tablet. In order for my pen to work i have to restart X. Each time I'm restarting X pen works absolutely fine but never after fresh boot up. This is part of the X.log which says it can't initialize Wacom device while everything seems to work right in the example of X.log after restarting X.
X.log after fresh boot up. 
> usbDetect: can not ioctl version
Wacom ISDV4 control data (0) error in * query
(EE) Couldn't init device "PnP Device (FUJ02e5)"
(II) UnloadModule: "wacom"
(EE) config/hal: NewInputDeviceRequest failed (1)
(II) config/hal: Adding input device PnP Device (FUJ02e5) eraser
(**) PnP Device (FUJ02e5) eraser: always reports core events
(**) PnP Device (FUJ02e5) eraser device is /dev/ttyS0
(**) PnP Device (FUJ02e5) eraser is in absolute mode
(**) PnP Device (FUJ02e5) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) PnP Device (FUJ02e5) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "PnP Device (FUJ02e5) eraser" (type: Wacom Eraser)
(**) Option "Device" "/dev/ttyS0"
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
usbDetect: can not ioctl version
Wacom ISDV4 control data (0) error in * query
(EE) Couldn't init device "PnP Device (FUJ02e5) eraser"
(II) UnloadModule: "wacom"
(EE) config/hal: NewInputDeviceRequest failed (1)

and this one after restart X:
> 
(II) config/hal: Adding input device PnP Device (FUJ02e5)
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Wacom driver level: 47-0.8.3-2 $
(**) PnP Device (FUJ02e5): always reports core events
(**) PnP Device (FUJ02e5) device is /dev/ttyS0
(**) PnP Device (FUJ02e5) is in absolute mode
(**) PnP Device (FUJ02e5): forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) /dev/ttyS0: Tablet PC buttons are on 
(**) Option "BaudRate" "9600"
(**) PnP Device (FUJ02e5): serial speed 9600
(II) XINPUT: Adding extended input device "PnP Device (FUJ02e5)" (type: Wacom Stylus)
(**) Option "Device" "/dev/ttyS0"
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
usbDetect: can not ioctl version
(==) Wacom using pressure threshold of 15 for button 1
(==) Wacom General ISDV4 tablet speed=9600 (19200) maxX=24576 maxY=18432 maxZ=255 resX=2540 resY=2540  tilt=disabled
(==) Wacom device "PnP Device (FUJ02e5)" top X=0 top Y=0 bottom X=24576 bottom Y=18432 resol X=2540 resol Y=2540
(II) config/hal: Adding input device PnP Device (FUJ02e5) eraser
(**) PnP Device (FUJ02e5) eraser: always reports core events
(**) PnP Device (FUJ02e5) eraser device is /dev/ttyS0
(**) PnP Device (FUJ02e5) eraser is in absolute mode
(**) PnP Device (FUJ02e5) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) PnP Device (FUJ02e5) eraser: threshold = 15
(**) PnP Device (FUJ02e5) eraser: max x set to 24576 by xorg.conf
(**) PnP Device (FUJ02e5) eraser: max y set to 18432 by xorg.conf
(**) PnP Device (FUJ02e5) eraser: max z = 255
(**) Option "BaudRate" "9600"
(**) PnP Device (FUJ02e5) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "PnP Device (FUJ02e5) eraser" (type: Wacom Eraser)
(==) Wacom device "PnP Device (FUJ02e5) eraser" top X=0 top Y=0 bottom X=24576 bottom Y=18432 resol X=2540 resol Y=2540


---

