---
title: "ASUS T300 Touchpad and Touchscreen"
date: 2014-01-11
forum: Hardware
---

### Post by evgenymarkov on 2014-01-11
Hello. Sorry for my bad english if it is a reality. I have new Asus Transformer Book T300 with touchscreen and dock station. My touchscreen defined as a mouse and touchpad too.The touchpad is connected via radiochannel, as well as keyboard. Probably, Touchpad manufacturer is Elantech becouse Asus laptops use only elantech touchpads.
[LIST]
[*]Ubuntu Version : 13.10
[*]Kernel version: i tried 3.11, 3.12.6, 3.12.7, 3.13 RC7(myself compilled and drivers for touchpad, ps/2 mouse(and more) marked)
[*]X.Org X Server 1.14.5
[*]Mesa last version from Oibaf repository.
[*]xserver-xorg-input-multitouch,xserver-xorg-input-evdev, xserver-xorg-input-synaptics packages installed
[/LIST]
part of xorg.0.log:
```

I: Bus=0003 Vendor=03eb Product=8856 Version=0111 
N: Name=«Atmel Atmel maXTouch Digitizer» 
P: Phys=usb-0000:00:14.0-7/input0 
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.0/input/input17 
U: Uniq= 
H: Handlers=mouse2 event17 
B: PROP=2 
B: EV=b 
B: KEY=400 0 0 0 0 0 
B: ABS=260800000000003 

I: Bus=0003 Vendor=0b05 Product=1823 Version=0111 
N: Name=«ASUS ASUS Wireless Input Receiver» 
P: Phys=usb-0000:00:14.0-1/input1 
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.1/input/input5 
U: Uniq=D76AB195BF 
H: Handlers=mouse0 event5 
B: PROP=0 
B: EV=17 
B: KEY=30000 0 0 0 0 
B: REL=103 
B: MSC=10 

```
xinput
```

&#9121; Virtual core pointer id=2    [master pointer (3)] 
&#9116; &#8627; Virtual core XTEST pointer id=4    [slave pointer (2)]
&#9116; &#8627; ASUS ASUS Wireless Input Receiver id=9    [slave pointer (2)]
&#9116; &#8627; ASUS ASUS Wireless Input Receiver id=10    [slave pointer (2)]
&#9116; &#8627; Atmel Atmel maXTouch Digitizer id=15    [slave pointer (2)]
&#9123; Virtual core keyboard id=3    [master keyboard (2)]
&#8627; Virtual core XTEST keyboard id=5    [slave keyboard (3)]
&#8627; Power Button id=6    [slave keyboard (3)]
&#8627; Video Bus id=7    [slave keyboard (3)]
&#8627; Sleep Button id=8    [slave keyboard (3)]
&#8627; Asus 2.0 USB Webcam id=13    [slave keyboard (3)]
&#8627; Asus 2.0 USB Webcam id=14    [slave keyboard (3)]
&#8627; Asus WMI hotkeys id=16    [slave keyboard (3)]
&#8627; AT Translated Set 2 keyboard id=17    [slave keyboard (3)]
```
lspci
```
00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)
00:03.0 Audio device: Intel Corporation Device 0a0c (rev 09)
00:04.0 Signal processing controller: Intel Corporation Device 0a03 (rev 09)
00:14.0 USB controller: Intel Corporation Lynx Point-LP USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation Lynx Point-LP HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation Lynx Point-LP HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 1 (rev e4)
00:1c.3 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 4 (rev e4)
00:1f.0 ISA bridge: Intel Corporation Lynx Point-LP LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Lynx Point-LP SMBus Controller (rev 04)
00:1f.6 Signal processing controller: Intel Corporation Lynx Point-LP Thermal (rev 04)
02:00.0 Network controller: Intel Corporation Wireless 7260 (rev 6b)


```
lsusb
```

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 007: ID 03eb:8856 Atmel Corp. 
Bus 001 Device 006: ID 0bda:5747 Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 0bda:5738 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 0483:91d1 STMicroelectronics 
Bus 001 Device 003: ID 24ae:2002  
Bus 001 Device 002: ID 0b05:1823 ASUSTek Computer, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
i tried recommends from[ laptopwiki ]("http://www.linlap.com/asus_x201e") , but but it did not help.
Please give advice! I would be very grateful!

---

### Post by evgenymarkov on 2014-01-15
Up, i need help. xinput list-props:
> Device 'ASUS ASUS Wireless Input Receiver':	Device Enabled (134):	1
	Coordinate Transformation Matrix (136):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (260):	0
	Device Accel Constant Deceleration (261):	1.000000
	Device Accel Adaptive Deceleration (262):	1.000000
	Device Accel Velocity Scaling (263):	10.000000
	Device Product ID (254):	2821, 6179
	Device Node (255):	"/dev/input/event5"
	Evdev Axis Inversion (264):	0, 0
	Evdev Axes Swap (266):	0
	Axis Labels (267):	"Rel X" (144), "Rel Y" (145), "Rel Vert Wheel" (281)
	Button Labels (268):	"Button Left" (137), "Button Unknown" (257), "Button Right" (139), "Button Wheel Up" (140), "Button Wheel Down" (141), "Button Horiz Wheel Left" (142), "Button Horiz Wheel Right" (143)
	Evdev Middle Button Emulation (269):	0
	Evdev Middle Button Timeout (270):	50
	Evdev Third Button Emulation (271):	0
	Evdev Third Button Emulation Timeout (272):	1000
	Evdev Third Button Emulation Button (273):	3
	Evdev Third Button Emulation Threshold (274):	20
	Evdev Wheel Emulation (275):	0
	Evdev Wheel Emulation Axes (276):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (277):	10
	Evdev Wheel Emulation Timeout (278):	200
	Evdev Wheel Emulation Button (279):	4
	Evdev Drag Lock Buttons (280):	0

---

### Post by aruth on 2014-03-03
I am having the same problem as the previous poster with an Asus T300 series laptop. It looks like the synaptics driver is not installed for my touchpad. I have searched online, but could not find a driver to install. Could anyone recommend a driver, or another way to get two finger scrolling to work?

```
~$ xinput list&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; ASUS ASUS Wireless Input Receiver       	id=9	[slave  pointer  (2)]
&#9116;   &#8627; ASUS ASUS Wireless Input Receiver       	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Atmel Atmel maXTouch Digitizer          	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; Asus 2.0 USB Webcam                     	id=11	[slave  keyboard (3)]
    &#8627; Asus 2.0 USB Webcam                     	id=12	[slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                        	id=14	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=15	[slave  keyboard (3)]



```

```
:~$ synclient -l
Couldn't find synaptics properties. No synaptics driver loaded?
```

---

### Post by bjorndolvik on 2014-03-06
Bump! Also need help with this! Both for mutlitouch on screen and touchpad as well!

---

