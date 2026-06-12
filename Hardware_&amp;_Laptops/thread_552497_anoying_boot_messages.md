---
title: "anoying boot messages"
date: 2007-09-16
forum: Hardware &amp; Laptops
---

### Post by 0darn on 2007-09-16
Hi , i recently installed Xubuntu 7.04 (using alternativ CD) - really kicks life in my old test laptop,ok some tweaks needed :) ( puts dsl 3.4 and elive 1.0 behind in smothness on same machine ! )
But i have some errors on bootup that disturbs me ..
Is it possible to do something about the 2 first ( autoprobes? ),but they doesnt affect system

From dmesg log:

1. [    0.000000] ACPI: Unable to locate RSDP

2. [   40.524236] PCI: device 0000:00:00.0 has unknown header type 7f, ignoring.

3. [  143.005905] acx: loading firmware for acx100 chipset with radio ID 0D
[  143.483488] acx: firmware image 'acx/default/tiacx100c0D' was not provided. 
Check your hotplug scripts
[  143.848101] acx: loading radio image for radio 0D

This (3.) pcmcia loads correctly couple of lines later*, why this config?hotplugscript?- issue would be wonderful to get deleted - but where? Is it an 'Upstart'-config?

*
[  144.387974] acx: === chipset TNETW1100A, radio type 0x0D (Maxim), form factor 0x01 ((mini-)PCI / CardBus), EEPROM version 0x05: uploaded firmware 'Rev 1.9.8.b' ===
[  144.391622] acx v0.3.36: net device wlan0, driver compiled against wireless extensions 21 and Linux 2.6.20-16-generic

edit: killed acpi services oldway in rc, but with Upstart?, noacpi make no diff.

// greetings 0darn

---

### Post by 0darn on 2007-09-21
I see Udev handle this in : /etc/udev/rules.d/80-programs.rules> # This file causes programs to be run on device insertion.
# See udev(7) for syntax.
# "Hotplug replacement" is handled in 90-modprobe.rules;  this file only
# specifies rules for those programs that are shipped in the minimal Ubuntu
# system, programs outside of that may ship their own rules.
# Load firmware on demand
SUBSYSTEM=="firmware", ACTION=="add", RUN+="firmware_helper"
and this line in : /etc/udev/rules.d/90-modprobe.rules> 
ENV{VIO_TYPE}=="network",		RUN+="/sbin/modprobe -Qba ibmveth"
..Still cant find the script/line to edit/delete...

---

### Post by 0darn on 2007-09-21
Ok - its a bug from 2.6.15 that has reoccured, still in 2.6.20.16 generic....
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/42896](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/42896)
[https://lists.ubuntu.com/archives/kernel-bugs/2006-May/015482.html](https://lists.ubuntu.com/archives/kernel-bugs/2006-May/015482.html)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/121244](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/121244)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/77849](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/77849)

Looks like an Udev script error as the udev-acx-default 
"acx: firmware image 'acx/default/tiacx100c0D' was not provided.
Check your hotplug scripts" 
then "acx v0.3.36: net device wlan0, driver compiled against wireless extensions 21 and Linux 2.6.20-16-generic" loads a working driver..

- so I'll do with that error-msg for now, if no-one knows a solution , as card works fine..

---

