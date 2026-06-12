---
title: "fancontrol issues, gateway nv53a running HOT."
date: 2013-01-30
forum: Hardware
---

### Post by digitalphiltv on 2013-01-30
I have read the forums... I have googled... I have modified kernel command line parameters... I have modified fancontrol configuration... I still need help. I have a CPU fan running at IDLE, a hot laptop, and a burning lap.

Ubuntu 12.10 on a 64-bit Gateway nv53a446u laptop.

sensors-detect wants to use k10temp, which it says is already loaded.

digitalphiltv@box2:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +91.0°C  (crit = +200.0°C)

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +90.0°C  (high = +70.0°C)
                       (crit = +97.0°C, hyst = +90.0°C)

How do I tell fancontrol to use the sensors? I need to know what information to put in /etc/fancontrol...

The file giving a reading of the cpu temp is at:
/sys/devices/virtual/hwmon/hwmon0/temp1_input

I'm getting "/usr/sbin/fancontrol: invalid path to sensors" when I try to load fancontrol.

All I can find is information about people saying their fan is too loud, or they have a different brand of laptop than I do.

HELP!!!! Tired of burning myself on this laptop... And the BIOS on this laptop is a piece of junk.

I'll add more information as I receive help and progress through this, and come to a solution. Right now, I am low on sleep.

---

### Post by Yellow Pasque on 2013-01-30
fancontrol is for PWM-controlled fans (while laptops generally use ACPI). 100C is pretty hot. Don't be surprised to see magic smoke soon.

Make sure your BIOS is updated, and if you're running the open-source ATI driver, that's probably causing the heat. Use fglrx/Catalyst until AMD figures out how to fix the power consumption of open driver (if ever).

---

### Post by digitalphiltv on 2013-01-30
/proc/acpi/ does not list anything to do with a fan...

however dmesg returned

[   20.105451] acpi device:02: registered as cooling_device2...

so... I'm not sure where to go next, on this...

---

