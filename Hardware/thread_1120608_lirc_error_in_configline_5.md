---
title: "lirc error in configline 5"
date: 2009-04-09
forum: Hardware
---

### Post by Omeil on 2009-04-09
Hi all when i try to run lirc using "sudo lircd -n /etc/lirc/hardware.conf" i keep getting this following error:

```

oliver@oliver-desktop:~$ sudo lircd -n /etc/lirc/hardware.conf
lircd-0.8.4a[7479]: error in configfile line 5
lircd-0.8.4a[7479]: reading of file '/etc/lirc/hardware.conf' failed
lircd-0.8.4a[7479]: reading of config file failed
lircd-0.8.4a[7479]: lircd(default) ready
^Clircd-0.8.4a[7479]: caught signal

```
And nothing is working, this is my current hardware.conf config:

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Linux input layer (/dev/input/eventX)"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/event5"
REMOTE_LIRCD_CONF="generic/devinput.conf"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""
```

And cat:

```
cat /proc/bus/input/devices
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0003 Vendor=046d Product=c049 Version=0111
N: Name="Logitech USB Gaming Mouse"
P: Phys=usb-0000:00:03.0-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:03.0/usb2/2-2/2-2:1.0/input/input1
U: Uniq=
H: Handlers=mouse1 event1 
B: EV=17
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143
B: MSC=10

I: Bus=0003 Vendor=046d Product=c221 Version=0110
N: Name="Gaming Keyboard"
P: Phys=usb-0000:00:03.2-1.1/input0
S: Sysfs=/devices/pci0000:00/0000:00:03.2/usb4/4-1/4-1.1/4-1.1:1.0/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: EV=120013
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=1f

I: Bus=0003 Vendor=046d Product=c221 Version=0110
N: Name="Gaming Keyboard"
P: Phys=usb-0000:00:03.2-1.1/input1
S: Sysfs=/devices/pci0000:00/0000:00:03.2/usb4/4-1/4-1.1/4-1.1:1.1/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=13
B: KEY=78 0 e0000 0 0 0
B: MSC=10

I: Bus=0003 Vendor=1233 Product=e006 Version=0100
N: Name="HOLTEK USB Keyboard"
P: Phys=usb-0000:00:03.2-1.2/input0
S: Sysfs=/devices/pci0000:00/0000:00:03.2/usb4/4-1/4-1.2/4-1.2:1.0/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=120013
B: KEY=10000 7 ff9f207a c14057ff febeffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=1233 Product=e006 Version=0100
N: Name="HOLTEK USB Keyboard"
P: Phys=usb-0000:00:03.2-1.2/input1
S: Sysfs=/devices/pci0000:00/0000:00:03.2/usb4/4-1/4-1.2/4-1.2:1.1/input/input5
U: Uniq=
H: Handlers=kbd mouse2 event5 
B: EV=17
B: KEY=70000 0 2010000 3978 d840d000 1e0000 0 0 0
B: REL=103
B: MSC=10

I: Bus=0003 Vendor=046d Product=c222 Version=0111
N: Name="G15 Keyboard G15 Keyboard"
P: Phys=usb-0000:00:03.2-1.4/input0
S: Sysfs=/devices/pci0000:00/0000:00:03.2/usb4/4-1/4-1.4/4-1.4:1.0/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=100013
B: KEY=10000 7 ff980000 7ff febeffdf ffefffff ffffffff fffffffe
B: MSC=10

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input8
U: Uniq=
H: Handlers=kbd event8 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/devices/platform/pcspkr/input/input9
U: Uniq=
H: Handlers=kbd event9 
B: EV=40001
B: SND=6


```

The Holtek Keyboard is the infra-red receiver obviously its a cheapy a remote mimicking a keyboard/mouse.

Any input would be greatly appreciated.

Kind Regards,

Omeil

---

