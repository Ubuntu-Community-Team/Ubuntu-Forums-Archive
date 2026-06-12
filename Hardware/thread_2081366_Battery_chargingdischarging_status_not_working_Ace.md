---
title: "Battery charging/discharging status not working Acer 5820T"
date: 2012-11-06
forum: Hardware
---

### Post by mesimms on 2012-11-06
I'm running Xubuntu 10.10 Maverick (yes, still) on an Acer Aspire Timeline 5820T. Out of the box, Maverick had the problem that the AC being seen by the system as always being plugged in, so you've no idea when the battery is going to run out. 

The patch published here [HTML]http://download.tuxfamily.org/3v1deb/acer-timelinex/TimelineX-ACPI-fix.patch[/HTML] works perfectly for the kernel version linux-2.6.35.9, and the battery/AC status is reported correctly. It makes two changes to drivers/acpi/ec.c. But as the code has evolved this patch is no longer relevant, so I can't upgrade to the newest version of Xubuntu. 

Anyone understand what the patch is doing or otherwise met and solved this problem? I'm a programmer, I'd look into how the patch works but I'd need some help from someone who understands this bit of kernel code.

---

