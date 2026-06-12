---
title: "Logitech v450 mouse not working"
date: 2010-06-16
forum: Hardware
---

### Post by nipuna.royal@gmail.com on 2010-06-16
I am using 10.04LTS and I cant seem to get my Logitech v450 to work. I followed a different thread and edited my xorg.conf file but it doesnt seem to work. Here is my xorg.conf

```
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

Section "InputDevice"
        Identifier      "Logitech v450"
        Driver          "evdev"
        Option          "Name" "Logitech USB Receiver"
        Option          "Dev Phys" "usb-0000:00:1d.0-1/input0"
        Option          "HWHEELRelativeAxisButtons" "7 6"
        Option          "SendCoreEvents" "true"
	Option 		"Device" "/dev/input/mice"
EndSection

Section "InputDevice"
	Identifier "Synaptics Touchpad"
	Driver "synaptics"
	Option "CorePointer"
	Option "Device" "/dev/psaux"
	Option "Protocol" "auto-dev"
	Option "HorizScrollDelta" "0"
	Option "SHMConfig" "true"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        #InputDevice "Logitech USB Receiver" "SendCoreEvents"
        InputDevice     "Logitech v450"
EndSection
```

Please help me get this working.. Thanks!

---

### Post by nipuna.royal@gmail.com on 2010-06-17
I am wondering if its a problem with the xorg.conf or the mouse. The mouse powers on fine and looks to work. It did the same thing with ubuntu 9.04. Please Send Suggestions.

Thanks!

---

### Post by stafio on 2010-06-23
The problem could be in your InputDevice section for the v450. You have 
> Option          "Dev Phys" "usb-0000:00:1d.0-1/input0"
and
> Option 		"Device" "/dev/input/mice"

If I'm not mistaken, you should only need one of these lines. Also, the "Device" entry does not look correct. To see your mice according to /dev/input.. you can use the following command```
ls /dev/input/mouse*
```
The value should look something like /dev/input/mouse0.

To get the correct "Dev Phys" entry, you use ```
cat /proc/bus/input/devices
```
Your entry looks like it is correct, so I'm guessing you already did that. 

I would try removing one and see if it works. If not, remove the other and try that. Also, you can safely remove the 'Option          "Name"' line just to help keep things minimal.

---

### Post by nipuna.royal@gmail.com on 2010-06-23
Thanks for the reply but I still cant seem to get it working.. 

Here is my devices

```
I: Bus=0003 Vendor=046d Product=c521 Version=0111
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.2-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.0/input/input698
U: Uniq=
H: Handlers=mouse2 event12 
B: EV=17
B: KEY=ffff0000 0 0 0 0
B: REL=143
B: MSC=10
```

and here is the modified xorg.conf

```

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

Section "InputDevice"
        Identifier      "Logitech v450"
        Driver          "evdev"
        Option          "Name" "Logitech USB Receiver"
	Option 		"Device" "/dev/input/mouse2"
#       Option          "Dev Phys" "usb-0000:00:1d.2-1/input0"
        Option          "HWHEELRelativeAxisButtons" "7 6"
        Option          "SendCoreEvents" "true"
	
EndSection

Section "InputDevice"
	Identifier "Synaptics Touchpad"
	Driver "synaptics"
	Option "CorePointer"
	Option "Device" "/dev/psaux"
	Option "Protocol" "auto-dev"
	Option "HorizScrollDelta" "0"
	Option "SHMConfig" "true"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        #InputDevice "Logitech USB Receiver" "SendCoreEvents"
        InputDevice     "Logitech v450"
EndSection
```

I tried removing one of the Device or Dev Phys options and either of them didn't work. Do I need the ServerLayout part or am I doing something wrong with that part? Thanks in advance. My mouse is useless without being able to get it work on ubuntu!

---

### Post by stafio on 2010-06-23
You could try scrapping your xorg.conf completely and trying [HIDPoint]("http://www.hidpoint.com/"). If it works as well as the site claims, that is probably your easiest solution to get it up and working.

---

### Post by nipuna.royal@gmail.com on 2010-06-24
Thanks but HIDpoint doesnt detect my mouse either.. I sent them an email as well. I removed the previous config from xorg before using HIDpoint as well.

---

