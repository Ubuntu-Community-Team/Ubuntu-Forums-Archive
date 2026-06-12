---
title: "Axioo NL 658: still can'tdisable touchpad"
date: 2007-11-07
forum: Hardware &amp; Laptops
---

### Post by yongqi on 2007-11-07
Anyone with the same problem? Here's what I've tried:

1. Add [Option "SHMConfig" "on"] to xorg.conf and restart X (and restart computer later). qsynaptics and syndaemon still complain about not being able to access shared memory.

2. Add kernel boot options [i8042.reset i8042.nomux] as suggested in [this thread](http://ubuntuforums.org/showthread.php?t=472021). qsynaptics and syndaemon still complain about shared memory.

3. Comment out [InputDevice "Synaptics Touchpad"] in xorg.conf and restart X/computer. The touchpad still works. (Note: when enabled, synaptics driver can be loaded successfully. When disabled, there's nothing about synaptics in Xorg.log, but the touchpad works nonetheless).

4. Remove "xserver-xorg-input-synaptics" package and restart X/computer. Touchpad still works.

5. Try using XFree86 driver as suggested in [this thread](http://ubuntuforums.org/showthread.php?t=196526). XFree86's module fails to load. Touchpad still works.

Unlike in my previous ECS laptop, this one doesn't have an option in BIOS to disable the touchpad. FWIW, here's the output of /proc/bus/input/devices:

```
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
U: Uniq=
H: Handlers=mouse0 event0
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input1
U: Uniq=
H: Handlers=kbd event1
B: EV=120013
B: KEY=4 2000000 3802078 f840d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=062a Product=0000 Version=0110
N: Name="HID 062a:0000"
P: Phys=usb-0000:00:1d.1-2/input0
S: Sysfs=/class/input/input2
U: Uniq=
H: Handlers=mouse1 event2
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103

I: Bus=0011 Vendor=0002 Product=0005 Version=0063
N: Name="ImPS/2 Logitech Wheel Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/class/input/input3
U: Uniq=
H: Handlers=mouse2 event3
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=button_power/button/input0
S: Sysfs=/class/input/input4
U: Uniq=
H: Handlers=kbd event4
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/class/input/input5
U: Uniq=
H: Handlers=kbd event5
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button (CM)"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/class/input/input6
U: Uniq=
H: Handlers=kbd event6
B: EV=3
B: KEY=4000 0 0 0 0

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/class/input/input7
U: Uniq=
H: Handlers=event7
B: EV=21
B: SW=1


```

Should I just start placing a sticker over the touchpad? I always use a USB mouse, I don't need the touchpad, I just want it off.

Thanks in advance.

---

### Post by mpierce on 2007-11-07
Remove the synaptic packages. 
   dpkg -l | grep synaptic
   dpkg -P synaptic, etc to remove packages and configuration files. 

Logout and restart the x-server. If you commented out synaptics in the xorg.conf, this should do the trick.

Hope this helps...

---

### Post by yongqi on 2007-11-07
> **mpierce said:**
> Remove the synaptic packages. 
   dpkg -l | grep synaptic
   dpkg -P synaptic, etc to remove packages and configuration files. 

Logout and restart the x-server. If you commented out synaptics in the xorg.conf, this should do the trick.

Hope this helps...

Perhaps you meant synaptics, not synaptic? I've tried uninstalling them and restart the computer. But the problem is, the touchpad still works nevertheless.

---

