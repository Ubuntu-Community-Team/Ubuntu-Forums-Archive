---
title: "--Need Help-- Configuring Logitech Input Devices"
date: 2008-12-02
forum: Hardware
---

### Post by heroes_on_a_half_shell on 2008-12-02
Hey guys,

I've narrowed down my problem by running a game through the terminal and reading the 50 or so input/output errors afterwards.  It appears that my Logitech keyboard/mouse combo (MX 3200 keyboard & MX 600 mouse operating off a single usb receiver) isn't configured properly.

I might have been able to configure these devices in the now obsolete xorg.conf file, but I have no idea what to do with the new hal and fdi system.  I've done a lot of reading, and I'm just getting frustrated.

Here's the output of my $cat /proc/bus/input/devices:

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3

I: Bus=0003 Vendor=046d Product=c517 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.1-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.1/usb2/2-2/2-2:1.0/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=120013
B: KEY=1000000000007 ff800000000007ff febeffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=1f

I: Bus=0003 Vendor=046d Product=c517 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.1-2/input1
S: Sysfs=/devices/pci0000:00/0000:00:1d.1/usb2/2-2/2-2:1.1/input/input2
U: Uniq=
H: Handlers=kbd mouse1 event2 
B: EV=1f
B: KEY=837fff042c332f bf08444400000000 ff0001 1f848a37cc00 667bfadd71dfed 9e000000000000 0
B: REL=1c3
B: ABS=100000000
B: MSC=10

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=3
B: KEY=10000000000000 0

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/devices/platform/pcspkr/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=40001
B: SND=6


If anyone has a working model of the appropriate fdi files, I would greatly appreciate it.  I want to learn how to configure such devices (so I can help my ubuntu converts), but I'm just not following the sparse information I can find.

Thanks in advance

---

