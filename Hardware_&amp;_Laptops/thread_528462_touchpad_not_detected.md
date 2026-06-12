---
title: "touchpad not detected"
date: 2007-08-17
forum: Hardware &amp; Laptops
---

### Post by dmizer on 2007-08-17
have an old NEC sub-laptop that's turned out to be a very nice computer.  at 650mhz cpu and 128meg of ram, it runs xubuntu feisty very well.

problem is that the touchpad is not functioning, which leaves me tethered to a usb mouse.  it's worked before, but only after i plugged in a wireless usb mouse.  that wireless usb mouse no longer functions so i can't use it to activate the touchpad.

here's some information on the system:
```
$ dmesg | egrep -i 'input|touch|track'
[   22.758624] input: Macintosh mouse button emulation as /class/input/input0
[   22.819113] input: AT Translated Set 2 keyboard as /class/input/input1
[   29.712811] input: Logitech Optical USB Mouse as /class/input/input2
[   29.713211] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:0d.0-1
[   29.713269] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   51.111647] input: PC Speaker as /class/input/input3
[   57.653711] input: Power Button (FF) as /class/input/input4
[   57.689740] input: Power Button (CM) as /class/input/input5
[   57.709731] input: Lid Switch as /class/input/input6
```

```
$ cat /proc/bus/input/devices
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
H: Handlers=mouse0 event0 ts0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd event1 
B: EV=120013
B: KEY=4 2000000 3802078 f840d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=046d Product=c016 Version=0110
N: Name="Logitech Optical USB Mouse"
P: Phys=usb-0000:00:0d.0-1/input0
S: Sysfs=/class/input/input2
H: Handlers=mouse1 event2 ts1 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input3
H: Handlers=kbd event3 
B: EV=40001
B: SND=6

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=ACPI_FPB/button/input0
S: Sysfs=/class/input/input4
H: Handlers=kbd event4 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/class/input/input5
H: Handlers=kbd event5 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/class/input/input6
H: Handlers=event6 
B: EV=21
B: SW=1
```

relevant sections of xorg.conf:
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "VertScrollDelta"       "0"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad" "AlwaysCore"
EndSection
```

i think the problem is related to this:
```
[   22.759234] PNP: PS/2 Controller [PNP0f0e:PS2M] at 0x0,0x0 irq 12
[   22.759244] PNP: PS/2 controller has invalid data port 0x0; using default 0x60
[   22.759252] PNP: PS/2 controller has invalid command port 0x0; using default 0x64
[   22.759260] PNP: PS/2 controller doesn't have KBD irq; using default 1
[   22.761572] serio: i8042 KBD port at 0x60,0x64 irq 1
[   22.761587] serio: i8042 AUX port at 0x60,0x64 irq 12
```

there's a bug related to touchpads connected via ps/2 porting [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/129477](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/129477) , but it assumes that a ps/2 mouse is found in /proc/bus/input/devices

any ideas on where to proceed from here?

---

### Post by dmizer on 2007-08-20
bump ... this remains unresolved.  i know the mouse works in linux.  i simply don't know how to make it happen.

---

### Post by dmizer on 2007-10-12
bump bump bump ... please help me.

if i do > tpconfig i get this output:
```
Found Synaptics Touchpad.
Firmware: 8.96 (multiple-byte mode).
```

cat /proc/bus/input/devices still shows no touchpad.

---

### Post by dmizer on 2007-10-12
found this:
> 1. Check that the touchpad is correctly detected by the kernel
--------------------------------------------------------------

If you are using a 2.6 linux kernel, check the /proc/bus/input/devices
file. The touchpad must be identified a "SynPS/2 Synaptics TouchPad"
or an "AlpsPS/2 ALPS TouchPad". If it is identified as a "PS/2 Generic
Mouse" or "PS/2 Synaptics TouchPad", something is wrong.

Possible fixes:

1. Check your BIOS settings. Some BIOSes can do USB -> PS/2 mouse
   emulation which can interfere with the touchpad. There may be a way
   to disable the legacy mouse emulation from the BIOS setup program.

2. Arrange so that the kernel initializes the USB subsystem before the
   PS/2 touchpad. Initializing the USB mouse sometimes disables the
   BIOS emulation. Compiling psmouse as a module and loading it in
   /etc/rc.d/rc.local usually assures the USB is initialized first.

3. Disconnect the USB mouse and restart the computer. (Not really a fix,
   but can help when trying to figure out what's wrong.)

4. Make sure your boot loader doesn't pass any parameter to the kernel
   that disables mouse extensions. ("psmouse_proto=bare" for example).
   Alternatively, if psmouse is compiled as a module, make sure that
   modprobe doesn't pass such parameters. Check /etc/modprobe.conf and
   "rmmod psmouse; modprobe -v psmouse".
source: [here](http://web.telia.com/~u89404340/touchpad/trouble-shooting.txt)

i can do step 3 and 4, and i've spent no small amount of time tinkering with my BIOS settings.  step 2 is a bit beyond me.  any tips?

---

### Post by DFreeze on 2007-10-16
I have a similar issue with a fairly recent laptop-model. My touchpad is also not detected at all (havent tried your "tpconfig" yet). My BIOS is so simple I can't change much more than the boot-order and the admin password, so I haven't gotten it to work still.

I've read that it's something with recent kernels, and I can confirm that PCLinuxOS (kernel 2.6.18?) detects the touchpad just fine. 

So just to pair up with you, dmizer, you're not alone! I'd like to have this fixed too...

::EDIT::

I just did tpconfig (with sudo), and my touchpad is detected. So it must be findable by Xorg or the kernel, you would say...

---

### Post by dmizer on 2007-10-21
i can't make tpconfig work.

bump for anything.

---

### Post by dmizer on 2007-10-22
tried:
```
options psmouse proto=exps
```
and
```
options psmouse proto=any
```
to /etc/modprobe.d/options per this thread: [http://ubuntuforums.org/showthread.php?t=75431](http://ubuntuforums.org/showthread.php?t=75431)

still nothing.

have an error in /var/log/Xorg.0.log that says synaptics not loaded because no device is found.

need some kernel help here.

---

### Post by Elitist_Phoenix on 2008-02-18
Hey mate same sorta problems (also commented in Dfreeze's thread). Did u ever get it working?

---

### Post by dmizer on 2008-02-18
nope.  still not working.

---

### Post by Elitist_Phoenix on 2008-03-02
Mate i just filed a bug report. Might want to add some of your details if u didn't get it working already. :)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/196808](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/196808)

---

### Post by wub on 2008-03-08
Hi all!

I have intermittant touchpad problems, which follow a pattern.  I'm pretty sure it has something to do with the BIOS.  For me the touchpad problem is more of a symptom to a larger problem with the shutdown process.  I'll spare you, unless anyone wants to know, but my system only pretends to halt.  I workaround this by pressing and holding the power switch until the power comes on, then goes off again (Thanks, Nathan!).

However, about once a week, I forget to do the powercycle.  Then my system wakes up at midnight, runs until the battery goes flat, >then< shuts down: hard and ugly.  When I power it up after this, the touchpad does not work in Ubuntu (now Feisty, but Edgy was the same).  If I boot from a live CD (Insert Linux or Knoppix) or hold my nose and dual-boot into XP, the touchpad returns to functionality the next time I boot into Ubuntu.

System: Fujitsu N3430 Lifebook, Intel chipset (wireless, video, ?).  Preferences/Hardware says I have a PS2 mouse with following details (left out some boring lines):

info.product       PS2/Mouse
input.device       /dev/input/event2
input.product      PS/2 Mouse
linux.device_file  /dev/input/event2
linux.sysfs_path   /sys/class/input/input2/event2

Now that I know about /proc/bus/input/devices, I took a look after booting from Input Linux:

BUS=0011 VENDOR=0002 PRODUCT=0008 VERSION=0000
Name="PS2/Mouse"
Phys=isa0060/serio1/input1
Sysfs=/class/input/input2
Handlers=Mouse0 event2
EV=7
KEY=70000 0 0 0 0 0 0 0 0
REL=3

BUS=0011 VENDOR=0002 PRODUCT=0008 VERSION=7322
Name="AlpsPS/2 ALPS GlidePoint"
Phys=isa0060/serio1/input0
Sysfs=/class/input/input3
Handlers=mouse1 event3
EV=f
KEY=420 0 670000 0 0 0 0 0 0 0 0
REL=3
ABS=1000003

OK, I suppose that makes sense, sorta.

After rebooting into Ubuntu, I see >almost< the same thing.

However the first section, Name="PS/2 Mouse"
has a new line:

  Sysfs=/class/input/input2
  Uniq=
  Handlers=mouse0 event2

and in the Alps section, I see that new line, and a change to Handlers:

  Sysfs=/class/input/input3
  Uniq=
  Handlers=mouse2 event3

Next time I blow out the battery, I'm going to open a terminal (cntl + alt + F2) so 
I can get a command line, and I'll have a peek into the devices file and see 
what the differences are.

Question:
If I >KNOW< that /proc/bus/input/devices is "wrong", how the heck can
I fix it?  I suspect this is not exactly like running ifconfig to change a network card's settings.

---

