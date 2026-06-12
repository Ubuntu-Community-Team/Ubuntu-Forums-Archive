---
title: "USB Keyboard configuration"
date: 2005-02-17
forum: Hardware &amp; Laptops
---

### Post by AndyS on 2005-02-17
I am having an issue getting Ubuntu Warty working correctly with my USB Keyboard. It is detected and responds to the majority of key presses but when in use I am finding that letters are failing to appear when typed. At first I thought this was just typos on my part but it is far too regular for that.

After a bit of detective work I think I might have worked out what is going on. When I do a *cat /proc/bus/input/devices* (see below) I have the USB keyboard listed twice. I am guessing therefore that these two entries are conflicting with each other and a percentage of my keypresses are being "eaten" in the process.

Does this sound like a plausable explanation and if so how can I get Ubuntu to only detect my keyboard once?

Many thanks.

Andy

```

andy@espresso:~ $ cat /proc/bus/input/devices
I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
H: Handlers=kbd event0
B: EV=120003
B: KEY=4 2000000 3802078 f840d001 f2ffffdf ffefffff ffffffff fffffffe
B: LED=7

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
H: Handlers=kbd event1
B: EV=40001
B: SND=6

I: Bus=0003 Vendor=045e Product=0039 Version=0300
N: Name="Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)"
P: Phys=usb-0000:00:11.2-1/input0
H: Handlers=mouse0 event2 ts0
B: EV=f
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=103
B: ABS=100 0

I: Bus=0003 Vendor=05a4 Product=9739 Version=0300
N: Name="ORTEK USB Hub/Keyboard"
P: Phys=usb-0000:00:11.2-2.1/input0
H: Handlers=kbd event3
B: EV=12000b
B: KEY=10000 7 ff87207a c14057ff febeffdf ffefffff ffffffff fffffffe
B: ABS=300 0
B: LED=1f

I: Bus=0003 Vendor=05a4 Product=9739 Version=0300
N: Name="ORTEK USB Hub/Keyboard"
P: Phys=usb-0000:00:11.2-2.1/input1
H: Handlers=kbd event4
B: EV=12000b
B: KEY=3fff ffff0000 8000 986 d000 100000 0 0 0
B: ABS=100 0
B: LED=500


```

---

