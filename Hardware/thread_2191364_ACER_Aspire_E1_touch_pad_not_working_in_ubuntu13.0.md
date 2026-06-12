---
title: "ACER Aspire E1 :touch pad not working in ubuntu13.04"
date: 2013-12-02
forum: Hardware
---

### Post by vs-punn on 2013-12-02
I have a ACER Aspire E1 572 laptop.
I installed Ubuntu 13.04 on it. 
Almost all things are working, except the touch pad.
When I move my finger on the touchpad nothing happens. So I have use external mouse for it.

What could be done, so that touch pad starts working.

The mod probe device report is as under:

:~$ cat /proc/bus/input/devices
I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0D:00/input/input0
U: Uniq=
H: Handlers=event0 
B: PROP=0
B: EV=21
B: SW=1


I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0C:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0


I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0E:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: PROP=0
B: EV=3
B: KEY=4000 0 0 0 0


I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0


I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input4
U: Uniq=
H: Handlers=sysrq kbd event4 
B: PROP=0
B: EV=120013
B: KEY=10000 c0200 0 0 0 0 0 700f 2000003 3803078 f830f401 febfffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7


I: Bus=0003 Vendor=040b Product=2011 Version=0110
N: Name="2.4G wireless Mouse"
P: Phys=usb-0000:00:14.0-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb2/2-2/2-2:1.0/input/input5
U: Uniq=
H: Handlers=mouse0 event5 
B: PROP=0
B: EV=1f
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=143
B: ABS=7f00 0
B: MSC=10


I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="Acer WMI hotkeys"
P: Phys=wmi/input0
S: Sysfs=/devices/virtual/input/input6
U: Uniq=
H: Handlers=rfkill kbd event6 
B: PROP=0
B: EV=13
B: KEY=1c0000 0 0 0 0 0 0 0 0 16008 c00 80000000 300000 0 0 0 0
B: MSC=10


I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="Acer BMA150 accelerometer"
P: Phys=wmi/input1
S: Sysfs=/devices/virtual/input/input7
U: Uniq=
H: Handlers=event7 js0 
B: PROP=0
B: EV=9
B: ABS=7


I: Bus=0003 Vendor=064e Product=e330 Version=0100
N: Name="HD WebCam"
P: Phys=usb-0000:00:14.0-8/button
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb2/2-8/2-8:1.0/input/input8
U: Uniq=
H: Handlers=kbd event8 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0 0 0 0


I: Bus=0011 Vendor=0002 Product=000e Version=0000
N: Name="ETPS/2 Elantech Touchpad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input9
U: Uniq=
H: Handlers=mouse1 event9 
B: PROP=1
B: EV=b
B: KEY=6420 0 30000 0 0 0 0 0 0 0 0
B: ABS=2608000 11000003


I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input10
U: Uniq=
H: Handlers=kbd event10 
B: PROP=0
B: EV=3
B: KEY=3e000b 0 0 0 0 0 0 0


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel MID HDMI/DP,pcm=3"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:03.0/sound/card0/input11
U: Uniq=
H: Handlers=event11 
B: PROP=0
B: EV=21
B: SW=140


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Headphone"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card1/input12
U: Uniq=
H: Handlers=event12 
B: PROP=0
B: EV=21
B: SW=4

---

### Post by varunendra on 2013-12-03
Please try these -

```
sudo modprobe -rv psmouse
sudo modprobe -v psmouse
```

If that doesn't help, try -
```
xinput float "ETPS/2 Elantech Touchpad"
xinput reattach "ETPS/2 Elantech Touchpad" "Virtual core pointer"
```

If none of these help, please post back the outputs of -
```
xinput
lsmod
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

