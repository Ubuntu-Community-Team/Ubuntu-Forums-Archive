---
title: "WMC remote no longer works - Very odd"
date: 2011-02-26
forum: Hardware
---

### Post by HelloIndustries on 2011-02-26
Hello all.
I hope i've posted in the right area....

Anyway: I have a WMC remote and receiver (RC6 remote & Philips eHome Infrared Receiver) and has always worked after installing LIRC, no trouble. However: Recently did a fresh install and the remote refuses to work.

Remote and reciever activity indicator both work.

Followed advice of #2: [http://ubuntuforums.org/showthread.php?t=1408059](http://ubuntuforums.org/showthread.php?t=1408059)
Ran irw in terminal, pressed some buttons, nothing.

LIRC config dialogue test area shows no response.
Also states that 'cannot find such receiver'

[B]FIXED:
[/B]Turns out the line REMOTE_DEVICE="" in /etc/lirc/hardware.conf
Needed to be changed to: REMOTE_DEVICE="/dev/lirc0"

I ran cat /proc/bus/input/devices and got:

```
$ cat /proc/bus/input/devices
I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input2
U: Uniq=
H: Handlers=mouse0 event2 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0003 Vendor=045e Product=00db Version=0111
N: Name="Microsoft Natural® Ergonomic Keyboard 4000"
P: Phys=usb-0000:00:0a.0-8/input0
S: Sysfs=/devices/pci0000:00/0000:00:0a.0/usb2/2-8/2-8:1.0/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=120013
B: KEY=10000 7 ff800000 7ff febeffdf f3cfffff ffffffff fffffffe
B: MSC=10
B: LED=107

I: Bus=0003 Vendor=045e Product=00db Version=0111
N: Name="Microsoft Natural® Ergonomic Keyboard 4000"
P: Phys=usb-0000:00:0a.0-8/input1
S: Sysfs=/devices/pci0000:00/0000:00:0a.0/usb2/2-8/2-8:1.1/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=10001f
B: KEY=837fff 2c3027 bf004444 0 0 1 10f84 8a27c007 ff7f7bfa d9415fff febeffdf ffefffff ffffffff fffffffe
B: REL=40
B: ABS=1 0
B: MSC=10

I: Bus=0003 Vendor=0c12 Product=0005 Version=0110
N: Name="Zeroplus PS Vibration Feedback Converter "
P: Phys=usb-0000:00:0a.0-5/input0
S: Sysfs=/devices/pci0000:00/0000:00:0a.0/usb2/2-5/2-5:1.0/input/input5
U: Uniq=
H: Handlers=event5 js0 
B: EV=20001b
B: KEY=fff 0 0 0 0 0 0 0 0 0
B: ABS=30027
B: MSC=10
B: FF=1 7030000 0 0

I: Bus=0011 Vendor=0002 Product=0005 Version=0000
N: Name="ImPS/2 Generic Wheel Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input6
U: Uniq=
H: Handlers=mouse1 event6 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103

I: Bus=0001 Vendor=10ec Product=0882 Version=0001
N: Name="HDA Digital PCBeep"
P: Phys=card0/codec#0/beep0
S: Sysfs=/devices/pci0000:00/0000:00:0e.1/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: EV=40001
B: SND=6
```Tried:
```
$ sudo mode2
mode2: could not get file information for /dev/lirc
mode2: default_init(): No such file or directory
```Checked: /dev/lirc0 & /dev/lircd both exist

USB port is the same i've always used, and has always worked.
Tested in alternative known working port - No joy.

Tried installing: lirc-modules-source
and ran: 

```
sudo /etc/init.d/lirc restart
```No joy

Tried
```
$ sudo dpkg-reconfigure lirc
```No joy

Any help would be greatly appreciated.

I'm running 10.04x86

---

