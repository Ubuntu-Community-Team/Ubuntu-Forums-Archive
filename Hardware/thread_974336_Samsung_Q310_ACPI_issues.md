---
title: "Samsung Q310 ACPI issues"
date: 2008-11-07
forum: Hardware
---

### Post by swf22 on 2008-11-07
I've just installed Ubuntu 8.1 on a Samsung Q310 laptop. It works pretty well in general, but ACPI seems to be rather broken. In order to get the system to work I've been booting with the "acpi=off" or "acpi=ht" options. If I don't, then the computer just continually reboots part-way through the boot process. It also reboots if you do things like plugging/unplugging the AC power, or using the "Fn+arrow key" combination that is supposed to adjust the display brightness.

Since this is a laptop I'd really like to get ACPI working! Does anyone have any ideas on what I can do? I've tried blacklisting the video.ko and battery.ko kernel modules, but that made no difference. Since the reboot happens well before dmesg is written to disk I can't get any useful information about what might be causing the problem from that either :(

---

### Post by TheBigF2 on 2008-11-13
Would I be right to think that you are trying 64-bit ubuntu 8.10? 

The 32-bit version hangs at the splash screen but boots fine on my Q310 provided you remove the references to "splash" in the grub boot command line. ACPI works okay for battery etc. But I can't get the Fn keys to work.

Anyone know how to get the Fn keys working?

---

### Post by swf22 on 2008-11-14
Yep - it's the 64-bit version. 32-bit runs fine off a Live-CD. However, I need to run code that allocates over 3GB of memory, so I can't really use the 32-bit version unfortunately.

---

