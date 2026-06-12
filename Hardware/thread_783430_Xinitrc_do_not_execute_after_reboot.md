---
title: "Xinitrc do not execute after reboot ?"
date: 2008-05-05
forum: Hardware
---

### Post by MastaBullz on 2008-05-05
Hello everyone, I can not run the file. Xinitrc to boot my PC to restart my setup, I am French, starting on Linux and I have a little difficulty to understand or do I put this file. Xinitrc I has a wacom bamboo and the beta version 0.7.9-11 driver because I encounter some difficulties with version 0.8.0! 

To install the driver I have followed this procedure 
[http://ubuntuforums.org/showthread.php?t=765915](http://ubuntuforums.org/showthread.php?t=765915)

I would like to know if there is a special code to enter the file. Xinitrc or if he just returned my staff like this: 
```
xsetwacom set stylus button2 3 
xsetwacom set stylus button3 2 
xsetwacom set pad button1 "core key shift" 
xsetwacom set pad button1 "core key shift super" 
xsetwacom set pad button1 "core key ctrl" 
xsetwacom set pad button1 "core alt key super tab" 
```
and I wanted to know whether this file requires absolutely wacomcpl and if it depends on him because I have some problems with him, see screenshot below: 
[U]
[[IMG]http://apu.mabul.org/up-mini/apu/2008/05/06/img-001203s1ax1.png[/IMG]]("http://apu.mabul.org/up/apu/2008/05/06/img-001203s1ax1.png.html")
[/U]
Be indulgent with me and my English, I am not an expert ;) ! 

In addition I would like to fix any problems that I get with my Wacom graphire4, my Bamboo because I would soon receive my Cintiq 12WX! 

For those interested I send you my Xorg.0.log together with the results of diagnostic USB my machine: 
```

(II) LoadModule: "wacom" 
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so 
(II) Module wacom: vendor="X.Org Foundation" 
(II) Wacom driver level: 47-0.7.9-11 $ 
(**) stylus device is /dev/input/wacom 
(**) WACOM: suppress value is 2 
(**) cursor device is /dev/input/wacom 
(**) WACOM: suppress value is 2 
(**) eraser device is /dev/input/wacom 
(**) WACOM: suppress value is 2 
(**) pad device is /dev/input/wacom 
(**) WACOM: suppress value is 2 
(II) XINPUT: Adding extended input device "pad" (type: Wacom Pad) 
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser) 
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor) 
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus) 
(**) Option "Device" "/dev/input/wacom" 
pad Wacom X driver grabbed event device 
(==) Wacom using pressure threshold of 30 for button 1 
(==) Wacom USB Bamboo tablet speed=9600 maxX=14760 maxY=9225 maxZ=511 resX=2540 resY=2540  tilt=enabled 
(==) Wacom device "pad" top X=0 top Y=0 bottom X=14760 bottom Y=9225 resol X=2540 resol Y=2540 
(==) Wacom device "eraser" top X=0 top Y=0 bottom X=14760 bottom Y=9225 resol X=2540 resol Y=2540 
(==) Wacom device "cursor" top X=0 top Y=0 bottom X=14760 bottom Y=9225 resol X=2540 resol Y=2540 
(==) Wacom device "stylus" top X=0 top Y=0 bottom X=14760 bottom Y=9225 resol X=2540 resol Y=2540 
```
and lsusb result : 

```
Bus 005 Device 004: ID 0930:6545 Toshiba Corp. 
Bus 005 Device 001: ID 0000:0000 
Bus 004 Device 004: ID 1241:1503 Belkin 
Bus 004 Device 003: ID 15ca:00c3 
Bus 004 Device 002: ID 058f:9254 Alcor Micro Corp. Hub 
Bus 004 Device 001: ID 0000:0000 
Bus 003 Device 002: ID 056a:0065 Wacom Co., Ltd 
Bus 003 Device 001: ID 0000:0000 
Bus 002 Device 003: ID 046d:c512 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000 
Bus 001 Device 001: ID 0000:0000 
```

---

