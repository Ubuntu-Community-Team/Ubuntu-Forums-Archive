---
title: "Logitech USB Keyboard Installation"
date: 2007-12-26
forum: Hardware &amp; Laptops
---

### Post by shear on 2007-12-26
Hi there.

I'm having trouble getting my new keyboard to work. It's part of a Logitech MX 3200 Laser wireless keyboard+mouse combo. The mouse works fine when I plug in the wireless dongle, but the keyboard is unresponsive. Any help would be appreciated. 

EDIT: I've checked the BIOS, as other threads seem to indicate, but there is nothing relating to USB Keyboards in there, and the USB Legacy option is on. 

Thanks

---

### Post by chewearn on 2007-12-26
> **shear said:**
> Hi there.

I'm having trouble getting my new keyboard to work. It's part of a Logitech MX 3200 Laser wireless keyboard+mouse combo. The mouse works fine when I plug in the wireless dongle, but the keyboard is unresponsive. Any help would be appreciated. 

EDIT: I've checked the BIOS, as other threads seem to indicate, but there is nothing relating to USB Keyboards in there, and the USB Legacy option is on. 

Thanks

Does the keyboard works in another machine?

---

### Post by shear on 2007-12-26
Well, the only computers I have to try it on are running 7.10, and no, it doesn't work on any of them.

Unfortunately, that's pretty useless information, as it doesn't tell us whether it's an Ubuntu problem or a hardware problem. 

To be honest though, I suspect the former. I've never had a problem with Logitech shipping faulty hardware before.

~shear

---

### Post by chewearn on 2007-12-27
> **shear said:**
> Well, the only computers I have to try it on are running 7.10, and no, it doesn't work on any of them.

Unfortunately, that's pretty useless information, as it doesn't tell us whether it's an Ubuntu problem or a hardware problem. 

To be honest though, I suspect the former. I've never had a problem with Logitech shipping faulty hardware before.

~shear

Well, check with another OS is the fastest way to rule out hardware problem.  But another thing you can check; after plug in the USB dongle, check dmesg.  See if the hardware is properly detected.
```
$ dmesg
or
$ dmesg | tail 
```

---

### Post by shear on 2007-12-27
Well, looks like it's being recognized. Here's the relevant output of dmesg.

```
[19547.076216] usb 3-1: new low speed USB device using uhci_hcd and address 4
[19547.254026] usb 3-1: configuration #1 chosen from 1 choice
[19547.271185] input: Logitech USB Receiver as /class/input/input10
[19547.271272] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.2-1
[19547.302818] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: Fixing up Logitech keyboard report descriptor
[19547.303875] input: Logitech USB Receiver as /class/input/input11
[19547.304065] input,hiddev96: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.2-1

```

Now, all that's left is to get it working I suppose.

~shear

---

### Post by chewearn on 2007-12-27
Then, it could be you need to sync the keyboard and receiver?  Did you press the respective sync buttons?

Sometimes, I have to press these buttons a few times for it to stick; but only on no-brand stuff.  Logitech stuff seemed to be better designed.

---

### Post by shear on 2007-12-27
Yeah, I've done the syncing. Still no dice. I've got a wired KB that works, I'm going to try and find another computer to give it a shot on. Barring that, the only thing that occurs to me is that both the mouse and kb seems to bind to the same "address"?

[21200.043338] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.0-2

[21200.074670] input,hiddev96: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-2

No idea what that even really means, let alone whether it's a problem.

~shear

---

### Post by shear on 2007-12-28
Yeah, the hardware works fine when connected to a windows machine. I'm kind of stumped, it'd be great to get this working.

I tried to cat the location that dmesg says the keyboard is mounted, and it works, but there is no output.

When I tried the same with the location the mouse was mounted to, I get a bunch of gibberish, as one would expect.

~shear

---

### Post by shear on 2007-12-28
Anyone? I'm working on a borrowed keyboard right now, any ideas on how to get this sucker working would be much appreciated.

When I cat /proc/bus/input/devices I get the following:

I: Bus=0003 Vendor=046d Product=c517 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.0-1/input0
S: Sysfs=/class/input/input10
U: Uniq=
H: Handlers=kbd event2 
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: LED=1f

I: Bus=0003 Vendor=046d Product=c517 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.0-1/input1
S: Sysfs=/class/input/input11
U: Uniq=
H: Handlers=kbd mouse1 event3 
B: EV=f
B: KEY=7fff 42c332f bf084440 0 0 ff0001 1f84 8837cc00 667bfa dd71dfed 9e0000 0 0 0
B: REL=1c3
B: ABS=1 0

This corresponds to dmesg which has:

[ 8531.664000] usb 1-1: new low speed USB device using ohci_hcd and address 4
[ 8531.876000] usb 1-1: configuration #1 chosen from 1 choice
[ 8531.888000] input: Logitech USB Receiver as /class/input/input10
[ 8531.888000] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:02.0-1
[ 8531.896000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: Fixing up Logitech keyboard report descriptor
[ 8531.896000] input: Logitech USB Receiver as /class/input/input11
[ 8531.896000] input,hiddev96: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:02.0-1

So the keyboard is there, it's synced, ubuntu knows about it, but it still isn't working. The hardware is fine, I checked on a windows machine.

Thanks.

---

### Post by shear on 2007-12-28
So, I've tried adding a device to xorg.conf. Here's what I added. Dev Phys, Device, and Dev Name were taken from cat /proc/bus/input/devices and dmesg.

Section "InputDevice"
	Identifier	"Logitech Keyboard"
	Driver		"kbd"
	Option		"SendCoreEvents"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"intl"
	Option		"Dev Name"	"Logitech USB Reciever"
	Option		"Dev Phys"	"usb-*/input0"
	Option 		"Device"	"/dev/input/event2"
EndSection

and under Section ServerLayout I added the line:

InputDevice "Logitech Keyboard" "SendCoreEvents"

Unfortunately, this didn't work.

shear

---

### Post by johnaaronrose on 2007-12-30
Hi shear,

I'm having similar problems with USB wireless Belkin keyboard & mouse.
I've had it working with an incorrect xorg.conf but I corrected it and I can no longer get it working even when I revert back!

/proc/bus/input/devices shows:
I: Bus=0003 Vendor=1020 Product=0006 Version=0110
N: Name="PATEN USB HID Device        "
P: Phys=usb-0000:00:13.0-1/input0
S: Sysfs=/class/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: LED=7

I: Bus=0003 Vendor=1020 Product=0006 Version=0110
N: Name="PATEN USB HID Device        "
P: Phys=usb-0000:00:13.0-1/input1
S: Sysfs=/class/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=3
B: KEY=800 300000 3878 d801d101 1e0000 0 0 0

I: Bus=0003 Vendor=1020 Product=0006 Version=0110
N: Name="PATEN USB HID Device        "
P: Phys=usb-0000:00:13.0-1/input2
S: Sysfs=/class/input/input5
U: Uniq=
H: Handlers=mouse1 event5 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103

I: Bus=0003 Vendor=1267 Product=0210 Version=0100
N: Name="PS/2+USB Mouse"
P: Phys=usb-0000:00:13.1-1/input0
S: Sysfs=/class/input/input6
U: Uniq=
H: Handlers=mouse2 event6 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103

I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/class/input/input7
U: Uniq=
H: Handlers=mouse3 event7 
B: EV=b
B: KEY=6420 0 70000 0 0 0 0 0 0 0 0
B: ABS=11000003

Working xorg.conf:
Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "gb"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ImPS/2"
    Option        "ZAxisMapping"        "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
    Identifier    "Wireless Keyboard:1"
    Driver        "kbd"
    Option        "SendCoreEvents"
        Option          "Dev Name""PATEN SB HID Device"
        Option          "Dev Phys" "usb-*/input0"
        Option          "Device" "/dev/input/event3"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "gb"
EndSection

Section "InputDevice"
    Identifier    "Wireless Keyboard:2"
    Driver        "kbd"
    Option        "SendCoreEvents"
        Option          "Dev Name""PATEN SB HID Device"
        Option          "Dev Phys" "usb-*/input1"
        Option          "Device" "/dev/input/event4" 
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "gb"
EndSection

Section "InputDevice"
    Identifier    "Wireless Mouse"
    Driver        "mouse"
    Option        "SendCoreEvents"
    Option        "Device"        "/dev/input/mouse1"
    Option        "Protocol"        "ImPS/2"
    Option        "ZAxisMapping"        "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"        "/dev/psaux"
    Option        "Protocol"        "auto-dev"
    Option        "HorizEdgeScroll"    "0"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "stylus"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "eraser"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "cursor"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "Device"
    Identifier    "ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]"
    Driver        "fglrx"
    BusID        "PCI:1:5:0"
    Option        "VideoOverlay"    "on"
    Option        "OpenGLOverlay"    "off"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection "Display"
        Modes        "1280x800"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
#       InputDevice     "Wireless Keyboard:1" "SendCoreEvents"
#       InputDevice     "Wireless Keyboard:2" "SendCoreEvents"
#       InputDevice     "Wireless Mouse" "SendCoreEvents"

# Uncomment if you have a wacom tablet
#    InputDevice     "stylus"    "SendCoreEvents"
#    InputDevice     "cursor"    "SendCoreEvents"
#    InputDevice     "eraser"    "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Extensions"
    Option        "Composite"    "Enable"
EndSection

In the Dev Name for the USB wireless keyboard & mouse, I mistyped USB as SB (BTW you had Reciever instead of Receiver in your xorg.conf). I also commented the Server Layout lines so as to reach the end result in stages. So I was very surprised when it worked. I then corrected the spelling and uncommented it  with no success.  

One thing I don't like about using "Dev Phys" is that  it relies on using the same USB socket  each time.  As I'm using a laptop, so that sometimes I don't have the combo connected, this relies on my remembering to always plug the reeiver into the same socket.

The combo used to work under Feisty but I had problems with wireless usb dongles connections to my router. So I did a clean install of Gutsy which is fine for that. So I'm scratching my head. Have you had any joy?

---

### Post by shear on 2007-12-31
No, nothing further here. I'm pretty sure I've reached the limit of my xorg.conf savvy.

It's going to take someone more knowledgeable than me to get these things working.

I re-tried with the correct spelling of receiver (oops), but that didn't change anything.

---

### Post by chewearn on 2007-12-31
> **shear said:**
> No, nothing further here. I'm pretty sure I've reached the limit of my xorg.conf savvy.

It's going to take someone more knowledgeable than me to get these things working.

I re-tried with the correct spelling of receiver (oops), but that didn't change anything.

You could try filing a bug in lauchpad.  A developer might be able to investigate, if there is enough users who report the same issue.

---

### Post by johnaaronrose on 2007-12-31
Hi AstaLaVista & shear

I just searched through Launchpad bugs. Bug 120074 suggests unplugging & plugging the USB receiver. It worked! I've posted to this Launchpad bug. Shear, can you also post to Launchpad? The more postings, the more chance of geting it fixed. Launchpad bug URL is:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/120074](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/120074)

---

### Post by shear on 2008-01-06
Well, I posted to the bug report, I guess we'll see if anything comes of it. 

~shear

---

### Post by thebinz on 2008-01-06
My Cordless Desktop® MX™ 3200 Laser mouse and keyboard work perfectly fine in Gutsy. They worked right out of the box with a fresh install. I have never had a problem with the hardware except for the back and forward buttons on the mouse... i wish i could find some way to get those to work.

---

### Post by shear on 2008-01-07
Could you post your /etc/X11/xorg.conf file, the output of "dmesg | grep -i usb", and output of "cat /proc/bus/input/devices"? It would likely be a great help in getting the thing working. Thanks!

---

### Post by Skidpad on 2008-01-07
I have the exact same KB/Mouse, and both work fine on the Gutsy LiveCd.  I booted into that just to see if it would work prior to installation (which I will do when home from business trip I am on now).  

The fwd/back buttons didn't work, but it was a simple re-mapping of the buttons on my Logitech MX610 mouse to get them to work in Edgy, so I am hoping the 3200 combo will be the same thing on Gutsy.  I will let you know next week.

Pardon my ignorance if I didn't see it in your posts above, but have you tried booting into the LiveCd to see if what a "standard" environment would be like?  If the KB works there, then obviously something is wrong with your xorg, etc files.  Worth a shot...

---

### Post by thebinz on 2008-01-17
Sorry i just got back from a nice vacation to the Florida Keys. :-P

Here is my xorg.conf 
```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
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

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation G70 [GeForce 7600 GT]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G70 [GeForce 7600 GT]"
	Monitor		"SyncMaster"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	Option		"AddARGBGLXVisuals"	"True"
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
Section "Module"
	Load		"glx"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection
```

my dmesg...
```
[   23.512826] usbcore: registered new interface driver usbfs
[   23.512847] usbcore: registered new interface driver hub
[   23.519964] usbcore: registered new device driver usb
[   23.521376] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[   23.525296] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   23.525369] usb usb1: configuration #1 chosen from 1 choice
[   23.525384] hub 1-0:1.0: USB hub found
[   23.526091] USB Universal Host Controller Interface driver v3.0
[   23.629126] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 2
[   23.629209] usb usb2: configuration #1 chosen from 1 choice
[   23.629223] hub 2-0:1.0: USB hub found
[   23.733227] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 3
[   23.733326] usb usb3: configuration #1 chosen from 1 choice
[   23.733338] hub 3-0:1.0: USB hub found
[   23.837437] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 4
[   23.837523] usb usb4: configuration #1 chosen from 1 choice
[   23.837544] hub 4-0:1.0: USB hub found
[   23.941963] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[   23.942054] usb usb5: configuration #1 chosen from 1 choice
[   23.942078] hub 5-0:1.0: USB hub found
[   24.046553] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[   24.046641] usb usb6: configuration #1 chosen from 1 choice
[   24.046664] hub 6-0:1.0: USB hub found
[   24.078654] usb 3-2: new low speed USB device using uhci_hcd and address 2
[   24.151187] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[   24.151276] usb usb7: configuration #1 chosen from 1 choice
[   24.151299] hub 7-0:1.0: USB hub found
[   24.261336] usb 3-2: configuration #1 chosen from 1 choice
[   24.276459] usbcore: registered new interface driver hiddev
[   24.290419] input: Logitech USB Receiver as /class/input/input1
[   24.290426] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1a.1-2
[   24.319175] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: Fixing up Logitech keyboard report descriptor
[   24.319575] input: Logitech USB Receiver as /class/input/input2
[   24.319604] input,hiddev96: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1a.1-2
[   24.319609] usbcore: registered new interface driver usbhid
[   24.319611] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   24.912291] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
[   24.916186] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   24.916254] usb usb8: configuration #1 chosen from 1 choice
[   24.916271] hub 8-0:1.0: USB hub found
[12144.658411] usb 1-1: new high speed USB device using ehci_hcd and address 3
[12144.793114] usb 1-1: configuration #1 chosen from 2 choices
[12144.904123] usbcore: registered new interface driver libusual
[12144.988717] Initializing USB Mass Storage driver...
[12144.988786] scsi6 : SCSI emulation for USB Mass Storage devices
[12144.988861] usb-storage: device found at 3
[12144.988862] usb-storage: waiting for device to settle before scanning
[12144.988871] usbcore: registered new interface driver usb-storage
[12144.988872] USB Mass Storage support registered.
[12149.976423] usb-storage: device scan complete
[16336.273328] usb 1-1: USB disconnect, address 3

```

and finally cat...
```
phil ~ $  cat /proc/bus/input/devices
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3

I: Bus=0003 Vendor=046d Product=c517 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1a.1-2/input0
S: Sysfs=/class/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=120003
B: KEY=1000000000007 ff800000000007ff febeffdfffefffff fffffffffffffffe
B: LED=1f

I: Bus=0003 Vendor=046d Product=c517 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1a.1-2/input1
S: Sysfs=/class/input/input2
U: Uniq=
H: Handlers=kbd mouse1 event2 
B: EV=f
B: KEY=7fff042c332f bf08444000000000 ff0001 1f848837cc00 667bfadd71dfed 9e000000000000 0
B: REL=1c3
B: ABS=100000000

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
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/class/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=3
B: KEY=10000000000000 0

```

i hope this helps.

---

### Post by shear on 2008-02-05
Ok, so, update.

Everything is the same as the one that works (thebinz), and no, it doesn't work under the LiveCD, yet I know that the hardware works fine on Windows.

I really don't know that's going on.

---

### Post by yodauser on 2008-05-08
Hi guys i just found a new software for linux providing  support for the Logitech devices. check out [http://www.hidpoint.com](http://www.hidpoint.com)

hope this helps.

---

### Post by yodauser on 2008-05-08
Hi there i just found a new software that might solve al the problem of USB driver issues with HID devices.. check out [http://www.hidpoint.com](http://www.hidpoint.com)

---

### Post by shear on 2008-05-27
Well, I just tried the HIDPoint program. From the screenshots on the website, it would appear to be the solution.

However.

The last version of Ubuntu the program runs on is 6.06. When I attempt to install under 8.04 Desktop, it is supposed to prompt for root password, but instead hangs and quits.

It seems to be a known issue with the developers of the HIDPoint program, so I'm going to be checking by every so often, and if they release a version compatible with 8.04, I'll post here.

Thanks to yodauser for pointing me to the website.

---

### Post by Ozdemon on 2008-06-26
The ubuntu 8.04 drivers for the MX3200 keyboard and the MX600 mouse are available at [www.hidpoint.com](www.hidpoint.com)

:)

---

