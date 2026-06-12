---
title: "Wacom tablet"
date: 2016-11-13
forum: Hardware
---

### Post by ELMIT on 2016-11-13
I bought a new tablet Intuos Art Creative Pen & Touch Tablet S


I use Ubuntu 15.10 now. The device is not recognized. Can you help me to get it to work? Thanks.


Here I gathered some information:

Wacom tablet

desktop:~$ xsetwacom --list devices

desktop:~$ lsusb | grep -i wacom
Bus 001 Device 008: ID 056a:033c Wacom Co., Ltd

desktop:~$ ls /dev/input/wacom*
ls: cannot access /dev/input/wacom*: No such file or directory

desktop:~$ ls /dev/input/event??
/dev/input/event10  /dev/input/event13  /dev/input/event16 /dev/input/event19
/dev/input/event11  /dev/input/event14  /dev/input/event17
/dev/input/event12  /dev/input/event15  /dev/input/event18

desktop:~$ cat /proc/bus/input/devices
I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
U: Uniq=
H: Handlers=kbd event1
B: PROP=0
B: EV=3
B: KEY=4000 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
U: Uniq=
H: Handlers=kbd event2
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0003 Vendor=0b05 Product=1795 Version=0111
N: Name="ASUS Compuer Inc. ASUS ROG GAMING MOUSE GX900"
P: Phys=usb-0000:00:1d.0-1.8/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb4/4-1/4-1.8/4-1.8:1.0/0003:0B05:1795.0001/input/input6
U: Uniq=
H: Handlers=mouse0 event3
B: PROP=0
B: EV=17
B: KEY=ff0000 0 0 0 0
B: REL=143
B: MSC=10

I: Bus=0003 Vendor=0b05 Product=1795 Version=0111
N: Name="ASUS Compuer Inc. ASUS ROG GAMING MOUSE GX900"
P: Phys=usb-0000:00:1d.0-1.8/input1
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb4/4-1/4-1.8/4-1.8:1.1/0003:0B05:1795.0002/input/input7
U: Uniq=
H: Handlers=sysrq kbd event4 leds
B: PROP=0
B: EV=12001f
B: KEY=3007f 0 0 483ffff17aff32d bf54444600000000 1 130f938b17c007 ffff7bfad9415fff febeffdfffefffff fffffffffffffffe
B: REL=40
B: ABS=100000000
B: MSC=10
B: LED=1f

I: Bus=0003 Vendor=1c4f Product=0002 Version=0110
N: Name="SIGMACHIP USB Keyboard"
P: Phys=usb-0000:00:14.0-13/input0
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb1/1-13/1-13:1.0/0003:1C4F:0002.0003/input/input8
U: Uniq=
H: Handlers=sysrq kbd event5 leds
B: PROP=0
B: EV=120013
B: KEY=1000000000007 ff800000000007ff febeffdff3cfffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=1c4f Product=0002 Version=0110
N: Name="SIGMACHIP USB Keyboard"
P: Phys=usb-0000:00:14.0-13/input1
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb1/1-13/1-13:1.1/0003:1C4F:0002.0004/input/input9
U: Uniq=
H: Handlers=kbd event6
B: PROP=0
B: EV=1f
B: KEY=3007f 0 0 483ffff17aff32d bf54444600000000 1 130c130b17c000 267bfad941dfed 9e168000004400 10000002
B: REL=40
B: ABS=100000000
B: MSC=10

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Front Mic"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input10
U: Uniq=
H: Handlers=event7
B: PROP=0
B: EV=21
B: SW=10

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Rear Mic"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input11
U: Uniq=
H: Handlers=event8
B: PROP=0
B: EV=21
B: SW=10

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Line"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input12
U: Uniq=
H: Handlers=event9
B: PROP=0
B: EV=21
B: SW=2000

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Line Out Front"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input13
U: Uniq=
H: Handlers=event10
B: PROP=0
B: EV=21
B: SW=40

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Line Out Surround"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input14
U: Uniq=
H: Handlers=event11
B: PROP=0
B: EV=21
B: SW=40

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Line Out CLFE"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input15
U: Uniq=
H: Handlers=event12
B: PROP=0
B: EV=21
B: SW=40

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Front Headphone"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input16
U: Uniq=
H: Handlers=event13
B: PROP=0
B: EV=21
B: SW=4

I: Bus=0003 Vendor=093a Product=2700 Version=0100
N: Name="USB2.0_Camera"
P: Phys=usb-0000:00:14.0-11/button
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb1/1-11/1-11:1.0/input/input26
U: Uniq=
H: Handlers=kbd event15
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA NVidia HDMI/DP,pcm=3"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input27
U: Uniq=
H: Handlers=event16
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA NVidia HDMI/DP,pcm=7"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input28
U: Uniq=
H: Handlers=event17
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA NVidia HDMI/DP,pcm=8"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input29
U: Uniq=
H: Handlers=event18
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA NVidia HDMI/DP,pcm=9"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input30
U: Uniq=
H: Handlers=event19
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0003 Vendor=056a Product=033c Version=0110
N: Name="Wacom Co.,Ltd. Intuos PTS Pen"
P: Phys=usb-0000:00:14.0-12.5.4/input0
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb1/1-12/1-12.5/1-12.5.4/1-12.5.4:1.0/0003:056A:033C.0008/input/input31
U: Uniq=
H: Handlers=event14
B: PROP=2
B: EV=b
B: KEY=0
B: ABS=0


desktop:~$ locate xorg.conf
/usr/share/X11/xorg.conf.d
/usr/share/X11/xorg.conf.d/10-evdev.conf
/usr/share/X11/xorg.conf.d/10-quirks.conf
/usr/share/X11/xorg.conf.d/11-evdev-quirks.conf
/usr/share/X11/xorg.conf.d/11-evdev-trackpoint.conf
/usr/share/X11/xorg.conf.d/50-synaptics.conf
/usr/share/X11/xorg.conf.d/50-vmmouse.conf
/usr/share/X11/xorg.conf.d/50-wacom.conf
/usr/share/X11/xorg.conf.d/51-synaptics-quirks.conf
/usr/share/X11/xorg.conf.d/glamoregl.conf
/usr/share/man/man5/xorg.conf.5.gz
/usr/share/man/man5/xorg.conf.d.5.gz



desktop:~$ cat /usr/share/X11/xorg.conf.d/50-wacom.conf
Section "InputClass"
        Identifier "Wacom USB device class"
        MatchUSBID "056a:*"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom PnP device class"
        MatchPnPID "WACf*|WCOM*|WACM*|FUJ02e5|FUJ02e7|FUJ02e9"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
EndSection

Section "InputClass"
    Identifier "Wacom class"
    MatchProduct "Wacom|WACOM|PTK-540WL|ISD-V4"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
EndSection

Section "InputClass"
    Identifier "Wacom serial class"
    MatchProduct "Serial Wacom Tablet"
    Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7|FUJ02e9"
        Driver "wacom"
EndSection

# Hanwang tablets
Section "InputClass"
    Identifier "Hanwang class"
    MatchProduct "Hanwang"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
EndSection

# Waltop tablets
Section "InputClass"
    Identifier "Waltop class"
    MatchProduct "WALTOP"
    MatchIsTablet "on"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
    Identifier "Wacom N-Trig class"
    MatchProduct "HID 1b96:0001|N-Trig Pen|N-Trig DuoSense"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
    Option "Button2" "3"
EndSection


desktop:~$ dmesg|grep wacom
[    2.689748] wacom 0003:056A:033C.0005: hidraw4: USB HID v1.10 Device [Wacom Co.,Ltd. Intuos PTS] on usb-0000:00:14.0-12.5.4/input0
[    2.689791] wacom 0003:056A:033C.0006: Unknown device_type for 'Wacom Co.,Ltd. Intuos PTS'. Ignoring.
[    2.689853] wacom 0003:056A:033C.0007: Unknown device_type for 'Wacom Co.,Ltd. Intuos PTS'. Ignoring.
[  197.649089] wacom 0003:056A:033C.0008: hidraw4: USB HID v1.10 Device [Wacom Co.,Ltd. Intuos PTS] on usb-0000:00:14.0-12.5.4/input0
[  197.650086] wacom 0003:056A:033C.0009: Unknown device_type for 'Wacom Co.,Ltd. Intuos PTS'. Ignoring.
[  197.651264] wacom 0003:056A:033C.000A: Unknown device_type for 'Wacom Co.,Ltd. Intuos PTS'. Ignoring.



From [https://wiki.archlinux.org/index.php/Wacom_Tablet](https://wiki.archlinux.org/index.php/Wacom_Tablet)  I learned:

Unknown device_type
If your tablet does not get recognized by xsetwacom and dmesg complains about an unknown device_type, then you need to install a patched version of input-wacom.
Download and install the for-4.4 branch from SourceForge. Your device should be recognized after you run
 # rmmod wacom
 # insmod /lib/modules/YOUR_KERNEL/extra/wacom.ko.gz

However, this information is very old and I did not figure out how to use the link from SourceForge ([http://sourceforge.net/p/linuxwacom/input-wacom/ci/jiri/for-4.4/~/tarball](http://sourceforge.net/p/linuxwacom/input-wacom/ci/jiri/for-4.4/~/tarball))

---

### Post by Bucky Ball on 2016-11-13
*Thread moved to **Hardware**.*

15.10 is no longer supported. Suggest you backup your valuable data and install a supported release, perhaps 16.04 LTS (long-term support until 2021).

Please use [code] tags for terminal output rather than posting screeds of terminal text. Thanks. See green link in my signature below for how.

---

### Post by ELMIT on 2016-11-13
To upgrade is on my list. However, from my past experience (since Ubuntu 5) I had NEVER, NEVER a smooth upgrade and for today I have no time to do a re-install (again).
Besides "never touch a running system" keeps me back too. I will try soon though. I am not sure if that would help to get the tablet working.

I am always confused, when to use code and quote. Will try to make it easier readable. Thanks!

---

### Post by Bucky Ball on 2016-11-14
If it is a newer tablet there is a better chance it may be supported in a newer release. It may be supported in 15.10, no idea. I never do a net upgrade, always a clean install.

How to use code tags is clearly explained in the link a the bottom of this post.

Good luck with it. ;)

---

### Post by ELMIT on 2016-11-14
More or less as expected:

Could not install the upgrades
The upgrade has aborted. Your system could be in an unusable state. A recovery will run now (dpkg --configure -a)

Processing was halted because there were too many errors.

---------------------------------

Upgrade complete
The upgrade has completed but there were errors during the upgrade process

---------------------------------

(Will ask another question, and come back if/when I got it to work with a 16.04 version)

---

### Post by ELMIT on 2016-11-14
Nice people in that forum helped me to get 16.04.1 (hopefully) up ;-)

It still did not change in dmesg:

Nov 15 03:33:36 desktop kernel: [70396.299171] usb 1-12.5.4: new full-speed USB device number 14 using xhci_hcd
Nov 15 03:33:36 desktop kernel: [70396.391258] usb 1-12.5.4: New USB device found, idVendor=056a, idProduct=033c
Nov 15 03:33:36 desktop kernel: [70396.391261] usb 1-12.5.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Nov 15 03:33:36 desktop kernel: [70396.391262] usb 1-12.5.4: Product: Intuos PTS
Nov 15 03:33:36 desktop kernel: [70396.391263] usb 1-12.5.4: Manufacturer: Wacom Co.,Ltd.
Nov 15 03:33:36 desktop kernel: [70396.396602] input: Wacom Co.,Ltd. Intuos PTS Pen as /devices/pci0000:00/0000:00:14.0/usb1/1-12/1-12.5/1-12.5.4/1-12.5.4:1.0/0003:056A:033C.001A/input/input85
Nov 15 03:33:36 desktop kernel: [70396.396728] wacom 0003:056A:033C.001A: hidraw4: USB HID v1.10 Device [Wacom Co.,Ltd. Intuos PTS] on usb-0000:00:14.0-12.5.4/input0
Nov 15 03:33:36 desktop kernel: [70396.397768] wacom 0003:056A:033C.001B: Unknown device_type for 'Wacom Co.,Ltd. Intuos PTS'. Ignoring.
Nov 15 03:33:36 desktop kernel: [70396.398938] wacom 0003:056A:033C.001C: Unknown device_type for 'Wacom Co.,Ltd. Intuos PTS'. Ignoring.
Nov 15 03:33:36 desktop mtp-probe: checking bus 1, device 14: "/sys/devices/pci0000:00/0000:00:14.0/usb1/1-12/1-12.5/1-12.5.4"
Nov 15 03:33:36 desktop mtp-probe: bus: 1, device: 14 was not an MTP device


What can we do next?

---

### Post by ELMIT on 2016-11-14
Finally we are getting somewhere:

dmesg |grep -i wacom
```
[  169.153807] usb 3-12.5.4: Manufacturer: Wacom Co.,Ltd.
[  169.171594] input: Wacom Intuos PT S 2 Pen as /devices/pci0000:00/0000:00:14.0/usb3/3-12/3-12.5/3-12.5.4/3-12.5.4:1.0/0003:056A:033C.0005/input/input22
[  169.171707] wacom 0003:056A:033C.0005: hidraw4: USB HID v1.10 Device [Wacom Co.,Ltd. Intuos PTS] on usb-0000:00:14.0-12.5.4/input0
[  169.174180] input: Wacom Intuos PT S 2 Finger as /devices/pci0000:00/0000:00:14.0/usb3/3-12/3-12.5/3-12.5.4/3-12.5.4:1.1/0003:056A:033C.0006/input/input26
[  169.174265] input: Wacom Intuos PT S 2 Pad as /devices/pci0000:00/0000:00:14.0/usb3/3-12/3-12.5/3-12.5.4/3-12.5.4:1.1/0003:056A:033C.0006/input/input27
[  169.174370] wacom 0003:056A:033C.0006: hidraw5: USB HID v1.10 Device [Wacom Co.,Ltd. Intuos PTS] on usb-0000:00:14.0-12.5.4/input1
```

xsetwacom --list devices
```
Wacom Intuos PT S 2 Pen stylus  	id: 14	type: STYLUS    
Wacom Intuos PT S 2 Pad pad     	id: 15	type: PAD       
Wacom Intuos PT S 2 Finger touch	id: 16	type: TOUCH  
```   

lsusb |grep -i wacom
```
Bus 003 Device 007: ID 056a:033c Wacom Co., Ltd 
```

[COLOR="#FF0000"]ls /dev/input/wacom*
```
ls: cannot access '/dev/input/wacom*': No such file or directory
```[/COLOR]

ls /dev/input/event??
```
/dev/input/event10  /dev/input/event12  /dev/input/event14  /dev/input/event16  /dev/input/event18  /dev/input/event20
/dev/input/event11  /dev/input/event13  /dev/input/event15  /dev/input/event17  /dev/input/event19  /dev/input/event21
ronald@ronald-desktop:~$ cat /proc/bus/input/devices
I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: PROP=0
B: EV=3
B: KEY=4000 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0003 Vendor=0b05 Product=1795 Version=0111
N: Name="ASUS Compuer Inc. ASUS ROG GAMING MOUSE GX900"
P: Phys=usb-0000:00:1d.0-1.8/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.8/2-1.8:1.0/0003:0B05:1795.0001/input/input6
U: Uniq=
H: Handlers=mouse0 event3 
B: PROP=0
B: EV=17
B: KEY=ff0000 0 0 0 0
B: REL=143
B: MSC=10

I: Bus=0003 Vendor=0b05 Product=1795 Version=0111
N: Name="ASUS Compuer Inc. ASUS ROG GAMING MOUSE GX900"
P: Phys=usb-0000:00:1d.0-1.8/input1
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.8/2-1.8:1.1/0003:0B05:1795.0002/input/input7
U: Uniq=
H: Handlers=sysrq kbd event4 leds 
B: PROP=0
B: EV=12001f
B: KEY=3007f 0 0 483ffff17aff32d bf54444600000000 1 130f938b17c007 ffff7bfad9415fff febeffdfffefffff fffffffffffffffe
B: REL=40
B: ABS=100000000
B: MSC=10
B: LED=1f

I: Bus=0003 Vendor=1c4f Product=0002 Version=0110
N: Name="SIGMACHIP USB Keyboard"
P: Phys=usb-0000:00:14.0-13/input0
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb3/3-13/3-13:1.0/0003:1C4F:0002.0003/input/input8
U: Uniq=
H: Handlers=sysrq kbd event5 leds 
B: PROP=0
B: EV=120013
B: KEY=1000000000007 ff800000000007ff febeffdff3cfffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=1c4f Product=0002 Version=0110
N: Name="SIGMACHIP USB Keyboard"
P: Phys=usb-0000:00:14.0-13/input1
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb3/3-13/3-13:1.1/0003:1C4F:0002.0004/input/input9
U: Uniq=
H: Handlers=kbd event6 
B: PROP=0
B: EV=1f
B: KEY=3007f 0 0 483ffff17aff32d bf54444600000000 1 130c130b17c000 267bfad941dfed 9e168000004400 10000002
B: REL=40
B: ABS=100000000
B: MSC=10

I: Bus=0003 Vendor=093a Product=2700 Version=0100
N: Name="USB2.0_Camera"
P: Phys=usb-0000:00:14.0-11/button
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb3/3-11/3-11:1.0/input/input17
U: Uniq=
H: Handlers=kbd event7 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Front Mic"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input10
U: Uniq=
H: Handlers=event8 
B: PROP=0
B: EV=21
B: SW=10

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Rear Mic"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input11
U: Uniq=
H: Handlers=event9 
B: PROP=0
B: EV=21
B: SW=10

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Line"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input12
U: Uniq=
H: Handlers=event10 
B: PROP=0
B: EV=21
B: SW=2000

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Line Out Front"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input13
U: Uniq=
H: Handlers=event11 
B: PROP=0
B: EV=21
B: SW=40

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Line Out Surround"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input14
U: Uniq=
H: Handlers=event12 
B: PROP=0
B: EV=21
B: SW=40

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Line Out CLFE"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input15
U: Uniq=
H: Handlers=event13 
B: PROP=0
B: EV=21
B: SW=40

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Front Headphone"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input16
U: Uniq=
H: Handlers=event14 
B: PROP=0
B: EV=21
B: SW=4

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA NVidia HDMI/DP,pcm=3"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input18
U: Uniq=
H: Handlers=event15 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA NVidia HDMI/DP,pcm=7"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input19
U: Uniq=
H: Handlers=event16 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA NVidia HDMI/DP,pcm=8"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input20
U: Uniq=
H: Handlers=event17 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA NVidia HDMI/DP,pcm=9"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input21
U: Uniq=
H: Handlers=event18 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0003 Vendor=056a Product=033c Version=0110
N: Name="Wacom Intuos PT S 2 Pen"
P: Phys=usb-0000:00:14.0-12.5.4/input0
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb3/3-12/3-12.5/3-12.5.4/3-12.5.4:1.0/0003:056A:033C.0005/input/input22
U: Uniq=
H: Handlers=mouse1 event19 
B: PROP=1
B: EV=1b
B: KEY=1c01 0 0 0 0 0
B: ABS=10003000003
B: MSC=1

I: Bus=0003 Vendor=056a Product=033c Version=0110
N: Name="Wacom Intuos PT S 2 Finger"
P: Phys=usb-0000:00:14.0-12.5.4/input1
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb3/3-12/3-12.5/3-12.5.4/3-12.5.4:1.1/0003:056A:033C.0006/input/input26
U: Uniq=
H: Handlers=mouse2 event20 
B: PROP=1
B: EV=2b
B: KEY=e520 0 0 0 0 0
B: ABS=263800000000003
B: SW=4000

I: Bus=0003 Vendor=056a Product=033c Version=0110
N: Name="Wacom Intuos PT S 2 Pad"
P: Phys=usb-0000:00:14.0-12.5.4/input1
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb3/3-12/3-12.5/3-12.5.4/3-12.5.4:1.1/0003:056A:033C.0006/input/input27
U: Uniq=
H: Handlers=mouse3 event21 js0 
B: PROP=0
B: EV=b
B: KEY=800 630000 0 0 0 0
B: ABS=3
```

lsusb | grep -i wacom
```
Bus 003 Device 007: ID 056a:033c Wacom Co., Ltd 
```

xrandr
```
Screen 0: minimum 8 x 8, current 3840 x 1080, maximum 16384 x 16384
DVI-I-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 521mm x 293mm
   1920x1080     60.00*+
   1680x1050     59.95  
   1440x900      74.98    59.89  
   1280x1024     75.02    60.02  
   1280x720      60.00  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   640x480       75.00    72.81    59.94  
VGA-0 connected 1920x1080+1920+0 (normal left inverted right x axis y axis) 521mm x 293mm
   1920x1080     60.00*+
   1680x1050     59.95  
   1440x900      74.98    59.89  
   1280x1024     75.02    60.02  
   1280x720      60.00  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   640x480       75.00    72.81    59.94  
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)

```

System Settings -> Wacom Tablet shows No tablet detected

---

### Post by mörgæs on 2016-11-15
General advice when dealing with new hardware is trying the newest software. 

Are you able to see and use the tablet in a live boot of 16.10?

---

