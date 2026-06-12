---
title: "ACPI Thermal shutdown false temperature"
date: 2009-12-14
forum: Hardware
---

### Post by oshunluvr on 2009-12-14
I have been having this issue since I built this computer (2 years) so I am familiar with my issue but I am new to Ubuntu (four months). I keep hoping each new kernel will be my savior, but not so far. I am looking for a fix to this long standing issue...please read on.

On bootup - my system immediately generates "Critical Temperature Reached 70c" error and shuts down - before it gets to the desktop. 

Obvious facts: It's NOT actually overheating. BIOS reports temps are normal (mid-40's) and it's never on long enough to do anything to make it hot.

Currently I can boot up if I use apci=off or acpi=ht in grub, but disabling most of acpi has other negative effects including slowing video speed down considerably and making shutdown not work.

I have tried "echo -n 99:80:30:70 > /proc/acpi/thermal_zone/THRM/trip_points" in rc.local but this appears to have no effect.

I would like to discover a suitable workaround for this so i can get full use of this computer. I don't want to have to do a kernel re-compile because (if you've noticed) we get a new kernel update almost weekly.

Hardware notes: Jetway J9F2 mobo with Intel T5500 cpu.

Any experts out there with ideas????

---

