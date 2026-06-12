---
title: "Battery Issues"
date: 2007-02-17
forum: Hardware &amp; Laptops
---

### Post by artir on 2007-02-17
Hi. 
I have a laptop made with different parts since 4 years. It has a P4 2,6 Ghz, 256 Mb RAM, 64 MB Sis graphic card and the battery.
This is the uname -a: Linux PORTATIL 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686 GNU/Linux

I cant see the batt state except if i do a cat /proc/acpi/battery/BAT0/info,
present:                 yes
design capacity:         6000 mWh
last full capacity:      5798 mWh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 579 mWh
design capacity low:     289 mWh
capacity granularity 1:  181 mWh
capacity granularity 2:  8 mWh
model number:            34AS1
serial number:           00002
battery type:            LiIon
OEM info:                OEM

The battery applet, when added, say: Can't access ACPI events in /var/run/acpid.socket! Make sure the ACPI subsystem is working and the acpid daemon is running.
 
Once i can see the batt state from the applet but i dont know why. I cant disconect the AC and the batt runs good: 2 hours and 15 minutes of duration but i cant see the state. 
Can somebody help me?

---

### Post by peter_brewer on 2007-02-17
You may have to recompile the kernel adding support for acpi functions.  Do a google search.

---

