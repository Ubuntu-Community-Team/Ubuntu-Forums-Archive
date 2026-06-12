---
title: "Touchpad not working on Lenovo V330"
date: 2018-06-17
forum: Hardware
---

### Post by leif-s-o on 2018-06-17
Hi,

I got a Lenovo V330 and installed Ubuntu 18.04. Everything works, except for the touchpad. It doesn't react at all, no mouse movement, clicks or scrolling. An external mouse works. Also the touchpad works using Windows on the same Laptop. Here is the output of the /proc/bus/input/devices, which doesn't seem to list the touchpad. Is there any hope?

```
I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:19/PNP0C0D:00/input/input0
U: Uniq=
H: Handlers=event0 
B: PROP=0
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input3
U: Uniq=
H: Handlers=sysrq kbd event3 leds 
B: PROP=0
B: EV=120013
B: KEY=402000000 3803078f800d001 feffffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: PROP=0
B: EV=3
B: KEY=3e000b00000000 0 0 0

I: Bus=0003 Vendor=046d Product=1024 Version=0111
N: Name="Logitech M310"
P: Phys=usb-0000:00:14.0-2:1
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.2/0003:046D:C52B.0003/0003:046D:1024.0004/input/input5
U: Uniq=1024-47-8a-cc-d2
H: Handlers=mouse0 event5 
B: PROP=0
B: EV=17
B: KEY=ffff0000 0 0 0 0
B: REL=143
B: MSC=10

I: Bus=0003 Vendor=046d Product=2011 Version=0111
N: Name="Logitech K520"
P: Phys=usb-0000:00:14.0-2:2
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.2/0003:046D:C52B.0003/0003:046D:2011.0005/input/input6
U: Uniq=2011-75-f9-be-db
H: Handlers=sysrq kbd event6 leds 
B: PROP=0
B: EV=12001f
B: KEY=3007f 0 0 483ffff17aff32d bf54444600000000 1 130f938b17c007 ffff7bfad941dfff febeffdfffefffff fffffffffffffffe
B: REL=40
B: ABS=100000000
B: MSC=10
B: LED=1f

I: Bus=0003 Vendor=04f2 Product=b604 Version=0027
N: Name="Integrated Camera: Integrated C"
P: Phys=usb-0000:00:14.0-5/button
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5:1.0/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="Ideapad extra buttons"
P: Phys=ideapad/input0
S: Sysfs=/devices/pci0000:00/0000:00:1f.0/PNP0C09:00/VPC2004:00/input/input8
U: Uniq=
H: Handlers=rfkill kbd event8 
B: PROP=0
B: EV=13
B: KEY=81000800100c03 4400000000300000 0 2
B: MSC=10

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Mic"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1f.3/sound/card0/input9
U: Uniq=
H: Handlers=event9 
B: PROP=0
B: EV=21
B: SW=10

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Headphone"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1f.3/sound/card0/input10
U: Uniq=
H: Handlers=event10 
B: PROP=0
B: EV=21
B: SW=4

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH HDMI/DP,pcm=3"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1f.3/sound/card0/input11
U: Uniq=
H: Handlers=event11 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH HDMI/DP,pcm=7"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1f.3/sound/card0/input12
U: Uniq=
H: Handlers=event12 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH HDMI/DP,pcm=8"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1f.3/sound/card0/input13
U: Uniq=
H: Handlers=event13 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH HDMI/DP,pcm=9"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1f.3/sound/card0/input14
U: Uniq=
H: Handlers=event14 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH HDMI/DP,pcm=10"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1f.3/sound/card0/input15
U: Uniq=
H: Handlers=event15 
B: PROP=0
B: EV=21
B: SW=140
```

---

### Post by leif-s-o on 2018-06-18
Ok I actually made some progress: I found that other people also have problems with the touchpad on the Lenovo V330, see [here]("https://unix.stackexchange.com/questions/427566/touchpad-on-lenovo-v330-thinkpad-v-series-is-not-recognized"). The solution suggested there is to add the correct ACPI ID, which is ELAN0618, into the file drivers/input/mouse/elan_i2c_core.c.

I am not sure how to achieve this, though. First, in the kernel folder, I only find a file named drivers/input/mouse/elan_i2c.ko. So this is compiled code and not source code, and also, the file name is a little different ("_core" is missing). It seems like I have to compile the kernel by myself, is that correct? Is there an easy way to add this line of code?

I also found, that there was actually a commit in the linux kernel some days ago that adds a specific ACPI ID to the kernel, see [here]("https://github.com/torvalds/linux/commit/e6e7e9cd8eed0e18217c899843bffbe8c7dae564"). I made a kernel update with ubuntu to use the version 4.17, but the touchpad still doesn't work, so maybe the mentioned commit is not part of that kernel or the ACPI ID is wrong? How can I find out the ACPI ID of the touchpad?

So I think there is a solution for my problem, I just don't have any knowledge about compiling the kernel by myself. I would be very thankful if anyone can help me with this!

---

### Post by palme2 on 2018-08-07
i had the same Prob now... and yes the problem is, that the acpi id is missing in default ubuntu kernel of 18.04 (v4.15.0).

installing the latest mainline kernel solved this problem.

Steps:
a) find acpi-id of your touchpad
```
dmesg | grep -i elan
```

on my lenovo V330 15ikb it was ELAN0618 

b) Check if ACPI ID is in at the end of elan_i2c_core.c of the latest mainline kernel. 
check here: [URL="https://elixir.bootlin.com/linux/v4.17.4/source/drivers/input/mouse/elan_i2c_core.c"]https://elixir.bootlin.com/linux/v4.17.4/source/drivers/input/mouse/elan_i2c_core.c
[/URL]
c) Get the Kernel-Packages (headers image modules) from here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
d) Install all packages: ```
sudo dpkg -i *.deb
```
f) update grup and reboot. ```
sudo update-grubl; sudo reboot;
```

if there are no prebuild kernel with your acpiid, you must add your id to elan_i2c_core.c file, patch and build your kernel packages manual.

---

