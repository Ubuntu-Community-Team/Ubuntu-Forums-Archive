---
title: "Touchpad problems with Samsung X420"
date: 2010-03-09
forum: Hardware
---

### Post by sroschke on 2010-03-09
hey,

I'm struggeling with a Samsung X420 notebok for several days now and can not get the touchpad to work correctly. 

Problem:
When the *psmouse* module is loaded by the kernel, the touchpad produces frequent (app. 2-5 per second) click events even when the touchpad is not touched at all. It is really annoying as any window stuff can not be used. Any attached USB mouse is working fine.

It seems to be a synaptics touchpad: 

$> grep -B 5 mouse /proc/bus/input/devices
I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input10
U: Uniq=
H: Handlers=mouse2 event10 

I tried several things to fix this problem:
*) trying different kernel boot options - i8042.nomux=1 and/or acpi_osi=!Linux
*) trying different module options - proto={imps,any,exps}
*) trying the Option "MaxTapTime" "0" in the xorg configuration

The mouse shows the same behavior with gpm as well, so I guess it is not xserver related. 

Do you have any ideas how to circumvent this problem? I will appreciate any hint for a direction I can dig into!

Thanks a lot,
sroschke

---

