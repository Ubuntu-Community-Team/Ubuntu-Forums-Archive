---
title: "HP dv4-3011 and Radeon 6750"
date: 2011-05-31
forum: Hardware
---

### Post by colordrops on 2011-05-31
I've got several problems getting Natty to run on this laptop, but I'll only mention the critical ones.  I'm hoping that others may have solved these problems and could lend a hand:

a) Trackpad does not work. "GPointing Device Settings" shows as enabled, /var/log/Xorg.0.log shows that the driver loaded properly. dmesg has tons of "psmouse.c: bad data from KBC - timeout" messages

I've tried all the various trackpad troubleshooting pages and threads out there but no luck.

b) Radeon HD 6750M does not work. Tried Open Source driver, fglrx from "Additional Drivers", and also downloaded 11.5 directly from AMD. Drivers appear to be loaded (Radeon and fglrx) based on lsmod. Tried using vgaswitcheroo for both immediate and delayed switching. Immediate switch has no effect. Delayed switch causes screen to go black upon X restart. Powering DIS on and off DOES work though. lspci reports "Unknown header type 7f". Card is 6750, but reported as 6741. Driver reports that it is loading "TURKS" microcode. fglrx driver segfaults on glxinfo and glxgears.

This card is pretty new, and I've found almost nothing on it through search.

c) Wifi doesn't work on battery power.  lspci is reporting it as a "Intel Corporation Centrino Wireless-N 1030 (rev 34)", using iwlagn driver.  I've tried looking at the following, but nothing is different whether power is plugged in or not:

sudo for i in /sys/bus/pci/devices/*/power/control ; do cat $i ; done
sudo cat /sys/class/net/wlan0/dormant

Also can't find any thing like "power_level" in the sys folder for iwlagn.  

I'm assuming this has something to do with ACPI, as suspend and resume also have serious problems.

Thanks for any shared experiences.

-- colordrops

---

### Post by thejranjan on 2011-08-19
> **colordrops said:**
> I've got several problems getting Natty to run on this laptop, but I'll only mention the critical ones.  I'm hoping that others may have solved these problems and could lend a hand:

a) Trackpad does not work. "GPointing Device Settings" shows as enabled, /var/log/Xorg.0.log shows that the driver loaded properly. dmesg has tons of "psmouse.c: bad data from KBC - timeout" messages

I've tried all the various trackpad troubleshooting pages and threads out there but no luck.

b) Radeon HD 6750M does not work. Tried Open Source driver, fglrx from "Additional Drivers", and also downloaded 11.5 directly from AMD. Drivers appear to be loaded (Radeon and fglrx) based on lsmod. Tried using vgaswitcheroo for both immediate and delayed switching. Immediate switch has no effect. Delayed switch causes screen to go black upon X restart. Powering DIS on and off DOES work though. lspci reports "Unknown header type 7f". Card is 6750, but reported as 6741. Driver reports that it is loading "TURKS" microcode. fglrx driver segfaults on glxinfo and glxgears.

This card is pretty new, and I've found almost nothing on it through search.

c) Wifi doesn't work on battery power.  lspci is reporting it as a "Intel Corporation Centrino Wireless-N 1030 (rev 34)", using iwlagn driver.  I've tried looking at the following, but nothing is different whether power is plugged in or not:

sudo for i in /sys/bus/pci/devices/*/power/control ; do cat $i ; done
sudo cat /sys/class/net/wlan0/dormant

Also can't find any thing like "power_level" in the sys folder for iwlagn.  

I'm assuming this has something to do with ACPI, as suspend and resume also have serious problems.

Thanks for any shared experiences.

-- colordrops


Hi, i am also experiencing all the above problems with HP Pavillion DV4-3015tx.

The trackpad issue is still a headache for me. Really getting mad of these issues.

The Display problem is solved by switching back to the native intel graphics without using the AMD Radeon one.

Please let me know if you get any solution for atleast the touchpad issue.
Or please let me know whether you succeeded in using any linux distro with touchpad enabled


Thank you.

---

