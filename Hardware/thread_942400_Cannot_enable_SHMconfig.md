---
title: "Cannot enable SHMconfig"
date: 2008-10-09
forum: Hardware
---

### Post by Tommy Rydling on 2008-10-09
Okay, here's my problem:

I have an Eee PC 901 with Ubuntu 8.04 and want to run Syndaemon to disable the touchpad while writing.

In order to do this I need to enable SHMConfig by editing xorg.conf. So I do that. But when running Syndaemon it says that I should enable SHMConfig.

The same problem appears if I try to go through the Gsynaptics GUI. It says to enable SHMConfig and doesn even start.

I even tried disabling the touchpad totally in xorg.conf but it worked anyway.

Yes, I restarted the computer after editing xorg.conf
I have tried using both "true" and "on" as parameters for SHMConfig in xorg.conf

Please help.

This is my xorg.conf section regarding the touchpad and SHMConfig:
```

Section "InputDevice"
 Identifier "Synaptics Touchpad"
 Driver "synaptics"
 Option "SendCoreEvents" "true"
 Option "Device" "/dev/psaux"
 Option "Protocol" "auto-dev"
 Option "HorizEdgeScroll" "0"
 Option "SHMConfig" "true"
 Option "CorePointer"
EndSection
```

This is what happens when running syndaemon or synclient in a terminal:
```

trydling@trydling-eee:~$ syndaemon
Can't access shared memory area. SHMConfig disabled?
trydling@trydling-eee:~$ synclient -l
Can't access shared memory area. SHMConfig disabled?

```

---

### Post by hugo491 on 2008-10-12
I too have been having this issue. What you need to do is add the following lines to your /etc/modprobe.d/options file:

options psmouse elantech=1

Then reboot the machine. It worked for me, and now I see the "touchpad" tab in my mouse preferences too.

---

### Post by Tommy Rydling on 2008-10-13
Thanks! It works now, although I seem to have lost some of the nicer features of the touchpad, like multitouch support. =/

I am kind of hoping the touchpad support will work better in version 8.10 Intrepid.

---

### Post by Endolith on 2008-11-16
> **Tommy Rydling said:**
> 
I am kind of hoping the touchpad support will work better in version 8.10 Intrepid.

Still doesn't work in Intrepid.  The above solution just killed my mouse, too. Gsynaptics still won't start, and the mouse doesn't move.

---

### Post by psoulocybe on 2008-11-17
In 8.10, you're supposed to enable SHMconfig in hal.

I'm running 8.04 and have spend many hours trying to enable SHMConfig to use syndaemon, but to get it to work, I lose most multi-touch features.  I've decided for the time being that I prefer two finger scrolling to syndaemon, but it's a toss up every day.

---

### Post by Endolith on 2008-11-17
Got it working following these instructions: [https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig](https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig)

---

### Post by dog_simpson on 2008-11-20
Hello, I have never worked tachpad
roverbook voyager v551, ubuntu 8.04
In the live CD works tachpad .. 

$ synclient TouchpadOff=1
> Can't access shared memory area. SHMConfig disabled?

$ sudo nano /etc/modprobe.d/options
> # Enable double-buffering so gstreamer et. al. work
options quickcam compatible=2
options psmouse elantech=1
# Default hostap to managed mode
options hostap_pci iw_mode=2
options hostap_cs iw_mode=2

$ xinput list
> "Virtual core keyboard"   id=0   [XKeyboard]
   Num_keys is 248
   Min_keycode is 8
   Max_keycode is 255
"Virtual core pointer"   id=1   [XPointer]
   Num_buttons is 32
   Num_axes is 2
   Mode is Relative
   Motion_buffer is 256
   Axis 0 :
      Min_value is 0
      Max_value is -1
      Resolution is 0
   Axis 1 :
      Min_value is 0
      Max_value is -1
      Resolution is 0
"Mouse0"   id=2   [XExtensionPointer]
   Num_buttons is 9
   Num_axes is 2
   Mode is Relative
   Motion_buffer is 256
   Axis 0 :
      Min_value is -1
      Max_value is -1
      Resolution is 1
   Axis 1 :
      Min_value is -1
      Max_value is -1
      Resolution is 1
"Keyboard0"   id=3   [XExtensionKeyboard]
   Num_keys is 248
   Min_keycode is 8
   Max_keycode is 255

$ sudo gedit /etc/hal/fdi/policy/shmconfig.fdi
> <?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="input.x11_driver" string="synaptics">
   <merge key="input.x11_options.SHMConfig" type="string">True</merge>
  </match>
 </device>
</deviceinfo>

$ nano /etc/X11/xorg.conf
> Section "InputDevice"
   Identifier   "Synaptics Touchpad"
   Driver      "synaptics"
   Option      "SendCoreEvents"   "true"
   Option      "Device"      "/dev/psaux"
   Option      "Protocol"      "auto-dev"
   Option      "HorizEdgeScroll"   "0"
   Option      "SHMConfig"      "true"
       #Option            "SHMConfig"            "on" - &#1088;&#1077;&#1079;&#1091;&#1083;&#1100;&#1072;&#1090; &#1090;&#1086;&#1090;&#1078;&#1077;
EndSection

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Synaptics Touchpad"
    InputDevice    "Mouse0" "CorePointer"
EndSection


$ cat /proc/bus/input/devices
> I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input0
U: Uniq=
H: Handlers=mouse0 event0
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input1
U: Uniq=
H: Handlers=kbd event1
B: EV=120013
B: KEY=4 2000000 3803078 f800d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/devices/platform/pcspkr/input/input2
U: Uniq=
H: Handlers=kbd event2
B: EV=40001
B: SND=6

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/virtual/input/input3
U: Uniq=
H: Handlers=kbd event3
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/virtual/input/input4
U: Uniq=
H: Handlers=kbd event4
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button (CM)"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/virtual/input/input5
U: Uniq=
H: Handlers=kbd event5
B: EV=3
B: KEY=4000 0 0 0 0

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/virtual/input/input6
U: Uniq=
H: Handlers=event6
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:04/LNXVIDEO:00/input/input7
U: Uniq=
H: Handlers=kbd event7
B: EV=3
B: KEY=3f000b 0 0 0 0 0 0 0

I: Bus=0003 Vendor=09da Product=000a Version=0110
N: Name="A4Tech PS/2+USB Mouse"
P: Phys=usb-0000:00:10.1-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:10.1/usb2/2-1/2-1:1.0/input/input8
U: Uniq=
H: Handlers=mouse1 event8
B: EV=17
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=343
B: MSC=10

sudo gedit /var/log/Xorg.0.log

> [http://dog-simpson.ru/xorg.log]("http://dog-simpson.ru/xorg.log")

What can I do?

---

### Post by dog_simpson on 2008-12-10
&#1041;&#1083;&#1103;&#1090;&#1100; &#1090;&#1091;&#1090; &#1082;&#1090;&#1086;&#1085;&#1080;&#1090;&#1100; &#1095;&#1090;&#1086;&#1085;&#1080;&#1073;&#1091;&#1076;&#1100; &#1079;&#1085;&#1072;&#1077;&#1090; ??

---

### Post by orengolan on 2010-01-25
I am not sure if it's the same issue, but take a look at the bug I just submitted on Launchpad:
[https://bugs.launchpad.net/ubuntu/+s...cs/+bug/512192](https://bugs.launchpad.net/ubuntu/+s...cs/+bug/512192)

Please go there and change the status to 'Confirm' so Ubuntu developers will understand that it's a hardware issue and not something specific to me.

Thanks!

---

