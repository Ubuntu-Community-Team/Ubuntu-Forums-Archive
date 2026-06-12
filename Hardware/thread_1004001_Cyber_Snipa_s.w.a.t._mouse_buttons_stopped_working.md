---
title: "Cyber Snipa s.w.a.t. mouse buttons stopped working"
date: 2008-12-06
forum: Hardware
---

### Post by Shasmo on 2008-12-06
Hi everyone.

I have a Cyber Snipa S.W.A.T. laser mouse and it has the standard two mouse buttons on top with a scroll wheel, as well as three buttons at the tumb position.

The other day, I was able to use these buttons for various things (mostly while playing games) and yet now, for some reason, they aren't getting recognised.

The only thing that has happened in the meantime is a system update via the auto-updater, and I turned down the Compiz settings (although I don't think this would affect the mouse).

When I go to Preferences -> Mouse, it doesn't give me any extra options in there to configure these extra buttons. How do I get them back?

---

### Post by Shasmo on 2008-12-08
*bump*

As extra information, I have run 'xev' and pressed these buttons whilst the cursor was in the window, but I don't get any events coming up. I have had a look at the xorg.conf file, but it's alot emptier than I can remember it being and it doesn't seem to contain any mouse info in there whatsoever.

I have tried to follow this guide at [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Mouse+Buttons](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Mouse+Buttons) but I get stuck at the first step. Below is the result of the cat /proc/bus/input/devices command:
```

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0003 Vendor=099a Product=7501 Version=0100
N: Name="Gaming Keyboard "
P: Phys=usb-0000:00:02.0-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.0/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=120013
B: KEY=10000 7 ff9f207a c14057ff febeffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=099a Product=7501 Version=0100
N: Name="Gaming Keyboard "
P: Phys=usb-0000:00:02.0-2/input1
S: Sysfs=/devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.1/input/input2
U: Uniq=
H: Handlers=kbd mouse1 event2 
B: EV=10001f
B: KEY=837fff 2c3027 bf004444 0 0 30001 c04 a27c000 267bfa d9415fed e08effdf 1cfffff ffffffff fffffffe
B: REL=47
B: ABS=1 0
B: MSC=10

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/devices/platform/pcspkr/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: EV=40001
B: SND=6

I: Bus=0003 Vendor=fffc Product=0041 Version=0100
N: Name="HID fffc:0041"
P: Phys=usb-0000:00:02.0-3/input0
S: Sysfs=/devices/pci0000:00/0000:00:02.0/usb1/1-3/1-3:1.0/input/input8
U: Uniq=
H: Handlers=mouse2 event3 
B: EV=17
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=103
B: MSC=10

I: Bus=0003 Vendor=fffc Product=0041 Version=0100
N: Name="HID fffc:0041"
P: Phys=usb-0000:00:02.0-3/input1
S: Sysfs=/devices/pci0000:00/0000:00:02.0/usb1/1-3/1-3:1.1/input/input9
U: Uniq=
H: Handlers=kbd mouse3 event4 
B: EV=12001f
B: KEY=70000 10000 7 ff9f207a c14057ff febeffdf ffefffff ffffffff fffffffe
B: REL=103
B: ABS=3f00 0
B: MSC=10
B: LED=1f
```
Which mouse event do I use? Why do I have two?

---

