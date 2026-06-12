---
title: "[SOLVED] Switching from PS/2 to USB Mouse/Keyboard problems"
date: 2008-02-06
forum: Hardware &amp; Laptops
---

### Post by linzer on 2008-02-06
I need some help getting Gutsy to recognize my new USB based wireless Logitech S 510 keyboard / mouse combination.  I don't need any fancy keys at this time, just the ability to type and move a mouse.

Initially my PS/2 mouse and keyboard was plugged into a KVM that also had a USB port.  From this I was trying to plug in the new Logitech wireless USB base but couldn't get X to recognize the devices.  Ultimately I pulled out the old PS/2 connections along with the USB hub portion of the KVM.

Now when I take a look at the /dev/input/ directory I see the following:

linzer@office:~$ ls -alh /dev/input/by-id/
total 0
drwxr-xr-x 2 root root 100 2008-02-05 23:37 .
drwxr-xr-x 4 root root 260 2008-02-05 23:37 ..
lrwxrwxrwx 1 root root   9 2008-02-05 23:37 usb-Logitech_USB_Receiver-event-kbd -> ../event1
lrwxrwxrwx 1 root root   9 2008-02-05 23:37 usb-Logitech_USB_Receiver-event-mouse -> ../event2
lrwxrwxrwx 1 root root   9 2008-02-05 23:37 usb-Logitech_USB_Receiver-mouse -> ../mouse1

Based upon what I read [HERE]("http://ubuntuforums.org/showthread.php?t=610302&highlight=logitech+S510") and [HERE]("http://ubuntuforums.org/showthread.php?t=219894&highlight=logitech+S510") I modified  my xorg.conf to read as follows:

Section "InputDevice"
        Identifier  "Logitech s510 Keyboard"
#    Driver      "kbd"
        Driver      "evdev"
        Option      "Device"    "/dev/input/event1"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "evdev"
        Option      "XkbLayout" "us"
EndSection

Section "InputDevice"
        Identifier  "Logitech s510 Mouse"
#    Driver      "mouse"
        Driver      "evdev"
        Option      "Device"    "/dev/input/event2"
        Option      "SendCoreEvents"   "true"
        Option      "Name" "Logitech USB Receiver"
        Option      "Resolution" "800"
#    Option        "CorePointer"
#    Option        "Device" "/dev/input/mice"
#    Option        "Protocol" "ImPS/2"
#    Option        "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "false"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        screen "Default Screen"
        InputDevice    "Logitech s510 Keyboard"
        InputDevice    "Logitech s510 Mouse"  "SendCoreEvents"
EndSection

Restarting X isn't really an option since I can't CTRL-ALT-Backspace so I reboot for X to run this config.

Upon reboot, I cannot move the mouse nor type my name to log in.

Any help would be appreciated.

---

### Post by Daelyn on 2008-02-06
Maybe a silly question, but, what happens if you try the "kbd" and "mouse" driver instead of the "evdev" one? That will hopefully give you the basic functionality you are asking about.

Just comment out "evdev" and remove the comment on "mouse" and "kbd".

---

### Post by linzer on 2008-02-06
> **Daelyn said:**
> Maybe a silly question, but, what happens if you try the "kbd" and "mouse" driver instead of the "evdev" one? That will hopefully give you the basic functionality you are asking about.

Just comment out "evdev" and remove the comment on "mouse" and "kbd".

I'll give that a try later tonight and follow up here.

I had meant to include the following info as well in case it can help anyone diagnose what is going on here.

linzer@office:~$ cat /proc/bus/input/devices 
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0003 Vendor=046d Product=c517 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.1-3/input0
S: Sysfs=/class/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: LED=1f

I: Bus=0003 Vendor=046d Product=c517 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.1-3/input1
S: Sysfs=/class/input/input2
U: Uniq=
H: Handlers=kbd mouse1 event2 
B: EV=f
B: KEY=7fff 42c332f bf084440 0 0 ff0001 1f84 8837cc00 667bfa dd71dfed 9e0000 0 0 0
B: REL=1c3
B: ABS=1 0

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=40001
B: SND=6

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=button_power/button/input0
S: Sysfs=/class/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/class/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=3
B: KEY=100000 0 0 0

---

### Post by linzer on 2008-02-06
OK, this has been solved.

Ultimately what I did was to boot to the Live Desktop CD and try different combinations until I got my mouse and keyboard working.

For MY system, this meant plugging into the PS/2 ports and not any of the USB ports.

The pertinent portion of my xorg.conf is as follows:

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Hope it helps others in the future.

---

### Post by Daelyn on 2008-02-07
> **linzer said:**
> OK, this has been solved.

Ultimately what I did was to boot to the Live Desktop CD and try different combinations until I got my mouse and keyboard working.

For MY system, this meant plugging into the PS/2 ports and not any of the USB ports.

The pertinent portion of my xorg.conf is as follows:

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Hope it helps others in the future.

As I suspected, the wrong driver was a part of the cause, but, I forgot the Device spec.

It's highly underestimated these days, to boot from the Live CD and check out the xorg from there :)

---

### Post by Stay on 2008-04-16
Hi, I have similar problem with my Logitech cordless S 510 keyboard/mouse. I'm on Ubuntu 7.10. The mouse works perfectly, but not the keyboard. I tried plugging it to USB and PS/2 with no effect. It doesn't work neither in LiveCD. I tried to modify xorg.conf as described in this thread, but nothing helps. 
At the moment I'm using S510 wireless mouse and normal PS/2 keyboard. Is there anything you could advice me to get the wireless keyboard working?

My xorg.conf:
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fr"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

```


ls -alh /dev/input/by-id/
```

total 0
drwxr-xr-x 2 root root 100 2008-04-16 08:03 .
drwxr-xr-x 4 root root 280 2008-04-16 08:03 ..
lrwxrwxrwx 1 root root   9 2008-04-16 08:03 usb-Logitech_USB_Receiver-event-kbd -> ../event2
lrwxrwxrwx 1 root root   9 2008-04-16 08:03 usb-Logitech_USB_Receiver-event-mouse -> ../event3
lrwxrwxrwx 1 root root   9 2008-04-16 08:03 usb-Logitech_USB_Receiver-mouse -> ../mouse1

```


cat /proc/bus/input/devices
```
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=120013
B: KEY=4 2000000 3802078 f840d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=046d Product=c517 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:13.1-1/input0
S: Sysfs=/class/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: LED=1f

I: Bus=0003 Vendor=046d Product=c517 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:13.1-1/input1
S: Sysfs=/class/input/input3
U: Uniq=
H: Handlers=kbd mouse1 event3 
B: EV=f
B: KEY=7fff 42c332f bf084440 0 0 ff0001 1f84 8837cc00 667bfa dd71dfed 9e0000 0 0 0
B: REL=1c3
B: ABS=1 0

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=40001
B: SND=6

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=button_power/button/input0
S: Sysfs=/class/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/class/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=3
B: KEY=100000 0 0 0
```

---

### Post by Stay on 2008-04-16
also output from
    sudo input-kbd 2
gives mapping only for 1 key:
```
/dev/input/event2
   bustype : BUS_USB
   vendor  : 0x46d
   product : 0xc517
   version : 272
   name    : "Logitech USB Receiver"
   phys    : "usb-0000:00:13.1-1/input0"
   uniq    : ""
   bits ev : EV_SYN EV_KEY EV_LED EV_REP

map: 1 keys, size: 1/64
0x0000 =  29  # KEY_LEFTCTRL

```

---

