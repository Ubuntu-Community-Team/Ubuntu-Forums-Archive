---
title: "Issue with trackpad once logged in"
date: 2020-05-08
forum: Hardware
---

### Post by nethfel on 2020-05-08
Hi all,

I seem to be having an issue with me trackpad.  I'm using a Dell Venue Pro 7140 with the docked keyboard/trackpad.  When I'm at the login manager, the trackpad seems to work ok - I can move the cursor around, usually I can use the left click to select (yes, sometimes the left click hasn't worked), etc.  When I log in and it brings up the actual gnome (or KDE) desktop the trackpad stops working completely.  I can still use the keyboard so I know it's not completely ignoring the dock.  If I plug in a regular mouse - that mouse works, but the trackpad still does not.  The touch display always works and has not been an issue, just the trackpad.

 I've tried this on Ubuntu 20.04 and Kubuntu 20.04 and PopOS! 20.04.  On Ubuntu and Kubuntu I tried both X and Wayland (Wayland seemed to work better, but I'd still loose trackpad control the instant I launched the app store).  I've included a list of all of my detected devices (trimmed to just the synaptic or what I believe to be synaptic entries) below - I'm not sure where else to look for trying to get this thing to work like it should.

```

I: Bus=0003 Vendor=06cb Product=2819 Version=0110
N: Name="Synaptics T Pad V 01.31"
P: Phys=usb-0000:00:14.0-4/input1
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.1/0003:06CB:2819.0004/input/input10
U: Uniq=0672FF515354885087135415
H: Handlers=sysrq kbd event8 leds 
B: PROP=0
B: EV=120013
B: KEY=1000000000007 ff9f207ac14057ff febeffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7


I: Bus=0003 Vendor=06cb Product=2819 Version=0110
N: Name="Synaptics T Pad V 01.31 Consumer Control"
P: Phys=usb-0000:00:14.0-4/input2
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.2/0003:06CB:2819.0005/input/input11
U: Uniq=0672FF515354885087135415
H: Handlers=kbd event9 
B: PROP=0
B: EV=13
B: KEY=302000000 1000000000 e000000000000 0
B: MSC=10


I: Bus=0003 Vendor=06cb Product=2819 Version=0110
N: Name="Synaptics T Pad V 01.31"
P: Phys=usb-0000:00:14.0-4/input2
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.2/0003:06CB:2819.0005/input/input12
U: Uniq=0672FF515354885087135415
H: Handlers=event10 
B: PROP=0
B: EV=100001


I: Bus=0003 Vendor=06cb Product=2819 Version=0110
N: Name="Synaptics T Pad V 01.31 Wireless Radio Control"
P: Phys=usb-0000:00:14.0-4/input2
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.2/0003:06CB:2819.0005/input/input13
U: Uniq=0672FF515354885087135415
H: Handlers=rfkill kbd event11 
B: PROP=0
B: EV=13
B: KEY=80000000000000 0 0 0
B: MSC=10


I: Bus=0018 Vendor=06cb Product=780e Version=0100
N: Name="SYNA7500:00 06CB:780E"
P: Phys=i2c-SYNA7500:00
S: Sysfs=/devices/pci0000:00/INT3433:00/i2c-1/i2c-SYNA7500:00/0018:06CB:780E.0002/input/input22
U: Uniq=
H: Handlers=mouse0 event17 
B: PROP=2
B: EV=1b
B: KEY=c03 0 0 0 0 0
B: ABS=1000003
B: MSC=10


I: Bus=0018 Vendor=06cb Product=780e Version=0100
N: Name="SYNA7500:00 06CB:780E"
P: Phys=i2c-SYNA7500:00
S: Sysfs=/devices/pci0000:00/INT3433:00/i2c-1/i2c-SYNA7500:00/0018:06CB:780E.0002/input/input23
U: Uniq=
H: Handlers=mouse1 event18 
B: PROP=2
B: EV=1b
B: KEY=400 0 0 0 0 0
B: ABS=260800000000003
B: MSC=20


I: Bus=0003 Vendor=06cb Product=2819 Version=0111
N: Name="Synaptics T Pad V 01.31 Mouse"
P: Phys=usb-0000:00:14.0-4/input0
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.0/0003:06CB:2819.0003/input/input26
U: Uniq=0672FF515354885087135415
H: Handlers=mouse2 event19 
B: PROP=0
B: EV=17
B: KEY=30000 0 0 0 0
B: REL=3
B: MSC=10


I: Bus=0003 Vendor=06cb Product=2819 Version=0111
N: Name="Synaptics T Pad V 01.31 Touchpad"
P: Phys=usb-0000:00:14.0-4/input0
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.0/0003:06CB:2819.0003/input/input27
U: Uniq=0672FF515354885087135415
H: Handlers=mouse3 event20 
B: PROP=5
B: EV=1b
B: KEY=6420 10000 0 0 0 0
B: ABS=2e0800000000003
B: MSC=20



```

Any thoughts of what I could try would be most appreciated.

---

