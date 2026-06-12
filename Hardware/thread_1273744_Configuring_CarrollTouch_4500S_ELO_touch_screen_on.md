---
title: "Configuring CarrollTouch 4500S ELO touch screen on 9.04"
date: 2009-09-23
forum: Hardware
---

### Post by john_schimandle on 2009-09-23
I have a 4500S CarrollTouch Serial Elo touchscreen connected to the COM1 port on a VIA EPIA-M MiniITX motherboard running Ubuntu 9.04 with Xorg X-windows. Package xserver-xorg-input-elographics is installed. I know the hardware is good because the touchscreen works on Windows XP. 
 
The touch screen is connected to COM1 which maps to serial device file /dev/ttyS0. I can see that the touchscreen is hooked up because the output in /proc/tty/drivers/serial shows the CTS/DSR/CD lines connected. Removing the touchscreen DB9 connector from the serial port and rebooting removes these signals. So there is something driving these lines.
 
serinfo:1.0 driver revision:
0: uart:16550A port:000003F8 irq:4 tx:0 rx:0 CTS|DSR|CD
1: uart:16550A port:000002F8 irq:3 tx:0 rx:0
2: uart:unknown port:000003E8 irq:4
3: uart:unknown port:000002E8 irq:3
 
After boot Xorg does not automatically recognize the touch screen. I 
checked in HAL with lshal and there is no touchscreen device attached to 
the /dev/ttyS0. I read some posts on utility called inputattach which 
attaches a touchscreen to a specific device file but that did not work, 
The utility just hangs when run and restarting HAL did not yield any 
change in devices.
 
My understanding is the device must show up in the HAL device list with 
the correct device driver before Xorg can automatcially detect and 
configure it. This may be incorrect but it was the source of the problem 
with a different touch screen that was USB based.
 
I also tried directly configuring the touchscreen in /etc/X11/xorg.conf as 
follows with no results.
 
Section "InputDevice"
Identifier "Touchscreen"
Driver "elographics"
Option "Device" "/dev/ttyS0"
Option "DeviceName" "Touchscreen"
Option "MinX" "3800"
Option "MaxX" "300"
Option "MinY" "3800"
Option "MaxY" "300"
Option "SwapXY" "True"
Option "ScreenNumber" "0"
Option "UntouchDelay" "10"
Option "ReportDelay" "10"
EndSection
 
I can see the elographics driver located at /usr/lib/xorg/modules/input so 
it appears the Xorg driver is present.
 
There is some long installation procedure documented at [http://www.elotouch.com/files/install/elo_linux_serial_driver_v3.1_installation_instructions.txt](http://www.elotouch.com/files/install/elo_linux_serial_driver_v3.1_installation_instructions.txt)
which involves compiling a driver named elo_drv.so and using that instead of elographics_drv.so. Procedure looks like it predates HAL so I'm a little nervous about doing that. I tried the diagnostic suggested in this procedure but it did not work. Touching the screen did not put characters on stdout. Diagnostic command is as follows.
 
od -h -w10 </dev/ttyS0
 
Any help would be appreciated on how to configure this serial port ELO touch 4500S controller on Ubuntu 9.04 and working with Xorg X-windows.

---

### Post by john_schimandle on 2009-09-25
[SIZE=1]After some research I found the following link for Linux drivers and modules for ELO Touch touchscreens.[/SIZE]
[SIZE=1][/SIZE] 
[[SIZE=1]http://www.elotouch.com/Support/Downloads/dnld.asp[/SIZE]]("http://www.elotouch.com/Support/Downloads/dnld.asp")
[SIZE=1][/SIZE] 
[SIZE=1]I downloaded the tgz file and followed the instructions. The OS driver elok_s.ko is now installed and at least I get a beep when I touch the screen.[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]The problem now is an incompatibliity between the Xorg serial ELO module (elo_drv.so) and the Xorg 1.6.0. The following messages are displayed in the Xorg.0.log file.[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1](II) LoadModule: "elo"
(II) Loading /usr/lib/xorg/modules/input//elo_drv.so
(II) Module elo: vendor="X.Org Foundation"
        compiled for 1.4.99.901, module version = 1.1.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 2.0
(EE) module ABI major version (2) doesn't match the server's version (4)
(II) UnloadModule: "elo"
(II) Unloading /usr/lib/xorg/modules/input//elo_drv.so
(EE) Failed to load module "elo" (module requirement mismatch, 0)[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]After researching this error it appears the elo_drv.so Xorg module needs to be be recompiled under Xorg 1.6.0.[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]ELO Touch support was able to provide a Xorg 1.5RC compatible elo_drv.so module but that still gives the same error when starting X.[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]I have not been able to find the elo_drv.so source on-line so I am assuming this source is not released for general use. Too bad.[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]I guess my options are,[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]1. downgrade to Ubuntu 8.04 which is supported but that is a much larger job.[/SIZE]
[SIZE=1]2. downgrade to Xorg 1.5RC on Ubuntu 9.04 but there would probably be a host of incompatibility issues to deal with.[/SIZE]
[SIZE=1]3. Find the elo_drv.so source and recompiled it under Ubuntu 9.04.[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]Sometimes problems like this make you want to use Windows solutions. The touchscreen works perfect under windows.[/SIZE]
[SIZE=1]
Anyone know where I can find the elo_drv.so Xorg module source?[/SIZE]

---

### Post by prsmk on 2009-11-13
> **john_schimandle said:**
> [SIZE=1]After some research I found the following link for Linux drivers and modules for ELO Touch touchscreens.[/SIZE]
[SIZE=1][/SIZE] 
[[SIZE=1]http://www.elotouch.com/Support/Downloads/dnld.asp[/SIZE]]("http://www.elotouch.com/Support/Downloads/dnld.asp")
[SIZE=1][/SIZE] 
[SIZE=1]I downloaded the tgz file and followed the instructions. The OS driver elok_s.ko is now installed and at least I get a beep when I touch the screen.[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]The problem now is an incompatibliity between the Xorg serial ELO module (elo_drv.so) and the Xorg 1.6.0. The following messages are displayed in the Xorg.0.log file.[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1](II) LoadModule: "elo"
(II) Loading /usr/lib/xorg/modules/input//elo_drv.so
(II) Module elo: vendor="X.Org Foundation"
        compiled for 1.4.99.901, module version = 1.1.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 2.0
(EE) module ABI major version (2) doesn't match the server's version (4)
(II) UnloadModule: "elo"
(II) Unloading /usr/lib/xorg/modules/input//elo_drv.so
(EE) Failed to load module "elo" (module requirement mismatch, 0)[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]After researching this error it appears the elo_drv.so Xorg module needs to be be recompiled under Xorg 1.6.0.[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]ELO Touch support was able to provide a Xorg 1.5RC compatible elo_drv.so module but that still gives the same error when starting X.[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]I have not been able to find the elo_drv.so source on-line so I am assuming this source is not released for general use. Too bad.[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]I guess my options are,[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]1. downgrade to Ubuntu 8.04 which is supported but that is a much larger job.[/SIZE]
[SIZE=1]2. downgrade to Xorg 1.5RC on Ubuntu 9.04 but there would probably be a host of incompatibility issues to deal with.[/SIZE]
[SIZE=1]3. Find the elo_drv.so source and recompiled it under Ubuntu 9.04.[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]Sometimes problems like this make you want to use Windows solutions. The touchscreen works perfect under windows.[/SIZE]
[SIZE=1]
Anyone know where I can find the elo_drv.so Xorg module source?[/SIZE]

Try Elo Tech support again. They now have an updated elo_drv.so module compatible with Xserver 1.6 that works on Ubuntu 9.04 and Ubuntu 9.10. That should fix your issue.

---

