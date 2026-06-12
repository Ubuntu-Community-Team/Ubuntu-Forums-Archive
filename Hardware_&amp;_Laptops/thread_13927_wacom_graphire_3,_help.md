---
title: "wacom graphire 3, help"
date: 2005-02-03
forum: Hardware &amp; Laptops
---

### Post by forcotton on 2005-02-03
Hi all,
I've followed [http://www.ubuntulinux.org/wiki/WacomTabletIssue](http://www.ubuntulinux.org/wiki/WacomTabletIssue) to set up my graphire 3 tablet. 

Everything was fine until I try to set up gimp. It didn't detect any "extension device". 
I have set up udev correctly I think 'cause I have the /dev/wacom0 device and the tablet works in xorg as a mouse. I am using the wacom.ko from 2.6.10-686-smp kernel in hoary. 
$ xsetpointer -l
"Logitech MX510"        [XPointer]
"Generic Keyboard"      [XKeyboard]
"cursor"        [XExtensionDevice]
"stylus"        [XExtensionDevice]
"eraser"        [XExtensionDevice]
$ xsetwacom list
cursor           cursor
stylus           stylus
eraser           eraser
$ sudo wacdump /dev/wacom0
WacomOpenTablet: Invalid argument

I just don't know what did I do wrong?  :confused:

---

### Post by jjramsey on 2005-02-03
[QUOTE=forcotton]Hi all,
I've followed [http://www.ubuntulinux.org/wiki/WacomTabletIssue](http://www.ubuntulinux.org/wiki/WacomTabletIssue) to set up my graphire 3 tablet. 

Everything was fine until I try to set up gimp. It didn't detect any "extension device". 
I have set up udev correctly I think 'cause I have the /dev/wacom0 device and the tablet works in xorg as a mouse. I am using the wacom.ko from 2.6.10-686-smp kernel in hoary. 
[/QUOTE]

Maybe udev didn't "take" for some reason?

Try running wacdump on the devices /dev/input/event0, /dev/input/event1, etc., and see what you get. Not sure if that will solve the problem but it may rule out some things.

---

### Post by forcotton on 2005-02-03
[QUOTE=jjramsey]Maybe udev didn't "take" for some reason?

Try running wacdump on the devices /dev/input/event0, /dev/input/event1, etc., and see what you get. Not sure if that will solve the problem but it may rule out some things.[/QUOTE]
 wacdump runs on /dev/input/event0, 1,2, but all says model Unknown.

I just don't know why, xorg has it, but gimp does not. if I didn't do wacdump, i'll probably conclude this is a gimp thing...

---

### Post by forcotton on 2005-02-03
[QUOTE=forcotton]Hi all,
I've followed [http://www.ubuntulinux.org/wiki/WacomTabletIssue](http://www.ubuntulinux.org/wiki/WacomTabletIssue) to set up my graphire 3 tablet. 

Everything was fine until I try to set up gimp. It didn't detect any "extension device". 
I have set up udev correctly I think 'cause I have the /dev/wacom0 device and the tablet works in xorg as a mouse. I am using the wacom.ko from 2.6.10-686-smp kernel in hoary. 
$ xsetpointer -l
"Logitech MX510"        [XPointer]
"Generic Keyboard"      [XKeyboard]
"cursor"        [XExtensionDevice]
"stylus"        [XExtensionDevice]
"eraser"        [XExtensionDevice]
$ xsetwacom list
cursor           cursor
stylus           stylus
eraser           eraser
$ sudo wacdump /dev/wacom0
WacomOpenTablet: Invalid argument

I just don't know what did I do wrong?  :confused:[/QUOTE]
 some more info:
$ cat /var/log/Xorg.0.log |sed '/[wW]acom/,+5!d'
(II) LoadModule: "wacom"
(II) Loading /usr/X11R6/lib/modules/input/wacom_drv.o
(II) Module wacom: vendor="X.Org Foundation"
        compiled for 4.3.99.902, module version = 1.0.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.4
(II) Wacom driver level: 26-j0.6.4 $
(II) v4l driver for Video4Linux
(II) ATI Radeon/FireGL: The following chipsets are supported:
        FireGL - (RV250 4964), FireGL - (RV250 4965),
        RADEON 9000/9000 PRO (RV250 4966), RADEON 9000 LE (RV250 4967),
        MOBILITY FireGL 9000 (M9 4C64), MOBILITY FireGL - (M9 4C65),
(**) cursor serial device is /dev/wacom0
(**) cursor is in relative mode
(**) WACOM: suppress value is 2
(**) Option "USB" "on"
(**) cursor: reading USB link
(**) Option "BaudRate" "9600"
(**) stylus serial device is /dev/wacom0
(**) stylus is in absolute mode
(**) WACOM: suppress value is 2
(**) Option "USB" "on"
(**) stylus: reading USB link
(**) Option "BaudRate" "9600"
(**) eraser serial device is /dev/wacom0
(**) eraser is in absolute mode
(**) WACOM: suppress value is 2
(**) Option "USB" "on"
(**) eraser: reading USB link
(**) Option "BaudRate" "9600"
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "Logitech MX510" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/wacom0"
Wacom xf86WcmWrite error : Invalid argument
Wacom xf86WcmWrite error : Invalid argument
(**) Option "Device" "/dev/wacom0"
Wacom xf86WcmWrite error : Invalid argument
Wacom xf86WcmWrite error : Invalid argument
(**) Option "Device" "/dev/wacom0"
Wacom xf86WcmWrite error : Invalid argument
Wacom xf86WcmWrite error : Invalid argument
(II) Logitech MX510: ps2EnableDataReporting: succeeded
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0

I guess the 'Invalid argument' means there is something wrong between x and the wacom kernel module?... hmm

---

### Post by jjramsey on 2005-02-03
Check if there is actually a file named "wacom0" in the /dev directory. I also suggest that you post the actual udev rule that you put in /etc/udev/rules.d/udev.rules.

---

### Post by forcotton on 2005-02-03
[QUOTE=jjramsey]Check if there is actually a file named "wacom0" in the /dev directory. I also suggest that you post the actual udev rule that you put in /etc/udev/rules.d/udev.rules.[/QUOTE]
 $ cat /etc/udev/udev.rules |grep wacom
BUS="usb",SYSFS{manufacturer}="WACOM",SYSFS{product}="CTE-430-UV3.1-4",NAME="wacom0"

$ ll /dev/wacom0
crw-rw----  1 root root 13, 129 2005-02-03 17:57 /dev/wacom0

Actually it works as a mouse, both the pen and eraser. Just gimp don't find any "extended input device" (preference-> Input devices -> Configure extended devices) Since it's the only app that can test the "pressure sesitivity", I am not sure if it is not correctly configured or it's gimp...

---

### Post by jjramsey on 2005-02-03
[QUOTE=forcotton]$ cat /etc/udev/udev.rules |grep wacom
BUS="usb",SYSFS{manufacturer}="WACOM",SYSFS{product}="CTE-430-UV3.1-4",NAME="wacom0"

$ ll /dev/wacom0
crw-rw----  1 root root 13, 129 2005-02-03 17:57 /dev/wacom0

Actually it works as a mouse, both the pen and eraser. Just gimp don't find any "extended input device" (preference-> Input devices -> Configure extended devices) Since it's the only app that can test the "pressure sesitivity", I am not sure if it is not correctly configured or it's gimp...[/QUOTE]

If X gives an "Invalid argument" error message about "/dev/wacom0", then I doubt it's just the Gimp.

Ok, two more questions.

1) Is "evdev" listed in /etc/hotplug/blacklist?
2) What does the output from dmesg say about your Wacom?

---

### Post by forcotton on 2005-02-04
[QUOTE=jjramsey]If X gives an "Invalid argument" error message about "/dev/wacom0", then I doubt it's just the Gimp.

Ok, two more questions.

1) Is "evdev" listed in /etc/hotplug/blacklist?
2) What does the output from dmesg say about your Wacom?[/QUOTE]
 Problem solved :)

The problem is I did follow the instuctions exactly (or, too exactly?) Since I am using hoary, I thought I can bypass the blacklist editing and go on to the next section. After I added evdev in the blacklist, all problem solved. Not gimp can detect the device and get pressure input. 

Hmmm... gimp itself looks buggy though. The pen/eraser got "locked up" occasionaly, I can move the cursor but can't draw. This happens when I switch tool (every time) or I change between pen and eraser (not every time).

jjramsey, thank you for replying.

---

### Post by jjramsey on 2005-02-04
[QUOTE=forcotton]Problem solved :)
Hmmm... gimp itself looks buggy though. The pen/eraser got "locked up" occasionaly, I can move the cursor but can't draw. This happens when I switch tool (every time) or I change between pen and eraser (not every time).
[/QUOTE]

From [http://www.ubuntulinux.org/wiki/WacomTabletIssue](http://www.ubuntulinux.org/wiki/WacomTabletIssue)

> 
The current version of The Gimp included in Ubuntu does not handle tablet input very nicely, but the newest stable version (as of writing, 2.2) is very smooth indeed, and is a worthwhile upgrade. Before building from source,  sudo apt-get build-dep gimp  will get all the build requirements.


Also, check the output from dmesg to check that the Wacom *kernel* driver is a recent version.

BTW, glad that I could help.

---

### Post by downtime on 2005-03-23
[QUOTE=forcotton]Hmmm... gimp itself looks buggy though. The pen/eraser got "locked up" occasionaly, I can move the cursor but can't draw. This happens when I switch tool (every time) or I change between pen and eraser (not every time).
[/QUOTE]

did you ever resolve this? i got the pressure sensitivity and ability to draw to work somewhat by setting the stylus and eraser to 'window' instead of 'screen', but gimp locks up pretty quickly. 

i followed the instructions from the wiki entry. i have gimp 2.2.2. i have evdev in blacklist. i don't know why it's not working.

---

