---
title: "Setting up Synaptics Touchpad on FSC Lifebook S-6120"
date: 2007-05-18
forum: Hardware &amp; Laptops
---

### Post by Chrissss on 2007-05-18
Hello There!

Since a couple of weeks i try to set up the touchpad of my Siemens-Lifebook S-6120 notebook so that it's fully operable under Ubuntu 7.04 Feisty Fawn. E.g. scroll functions etc. The following looks like the main problem
```
cat /proc/bus/input/devices
```
shows
```
...
I: Bus=0011 Vendor=0002 Product=0001 Version=0000
N: Name="PS/2 Generic Mouse"
P: Phys=isa0060/serio4/input0
S: Sysfs=/class/input/input3
H: Handlers=mouse1 event3 ts1 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3...
```
Ubuntu thinks that the touchpad is a generic mouse. Usually it should be
```
N: Name="SynPS/2 Synaptics TouchPad"
or
N: Name="AlpsPS/2 ALPS GlidePoint"
```
but i get 
```
N: Name="PS/2 Generic Mouse"
```
When you tak a look at

[http://web.telia.com/~u89404340/touchpad/trouble-shooting.txt](http://web.telia.com/~u89404340/touchpad/trouble-shooting.txt)

they describe the problem
> If it is identified as a "PS/2 GenericMouse" or "PS/2 Synaptics TouchPad", something is wrong.
I tried a couple of things

* I searched the Bios for "USB -> PS/2 mouse emulation": Nothing
* I added "psmouse" to /etc/modules and rebooted: Nothing
* i booted the notebook without USB devices attached: Nothing

When I take a look inside **/var/log/Xorg.0.log** I find those error messages
```
...
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
        compiled for 4.2.0, module version = 1.0.0
        Module class: XFree86 XInput Driver
        ABI class: XFree86 XInput driver, version 0.3
...
(II) Synaptics touchpad driver version 0.14.6 (1406)
Synaptics Touchpad no synaptics event device found (checked 18 nodes)
(**) Option "Device" "/dev/psaux"
(**) Option "SHMConfig" "on"
(**) Option "LeftEdge" "1700"
(**) Option "RightEdge" "5000"A
(**) Option "TopEdge" "1700"
(**) Option "BottomEdge" "4200"
(**) Option "VertScrollDeltaa" "100"ac
(**) Option "MaxTapTime" "180"
(**) Option "MaxTapMove" "220"
(**) Option "FingerLow" "25"
(**) Option "FingerHigh" "30"
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
(II) UnloadModule: "synaptics"
```
Looks like the touchpad won't work correct... :(

Any ideas or similar problems?

Thanks
Christoph

---

