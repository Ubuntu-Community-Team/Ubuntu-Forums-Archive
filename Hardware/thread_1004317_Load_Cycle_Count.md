---
title: "Load Cycle Count"
date: 2008-12-07
forum: Hardware
---

### Post by Stephen_at on 2008-12-07
OK I've followed all the instructions here [http://ubuntuforums.org/showthread.php?t=994598](http://ubuntuforums.org/showthread.php?t=994598) and I still have problems.

I'm running Intrepid with the latest packaged kernel. Laptop is a Intel Core Duo CPU.

Hard Drive details:

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD3200BEVT-22ZCT0
Serial Number:    WD-WXH208069430
Firmware Version: 11.01A11
User Capacity:    320,072,933,376 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sun Dec  7 09:23:44 2008 GMT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

On Mains power the load cycle count increases very slowly (like it didn't do one in 5 minutes) but on battery power its going up by about 3 a minute which is totally crazy.

So is there any fix for this because I'd like to power cycle my battery but its got an approximate 2 hour drain time and at 3 load cycles a minute I'd rather not do it. If I need to flatten the battery I have to reboot into Vista.

Why is Ubuntu so damned vicious on load cycles? I looked at my old workstation and it was hammering away doing it to. I've now set Laptop mode on my workstation and its drives no longer get anywhere near as hot.

---

### Post by Stephen_at on 2008-12-07
I think I might have found it.

In  /etc/laptop-mode/laptop-mode.conf

the hdparm -B values for battery and AC were different.

which is what I think could be causing the problem. So even if I do enable laptop mode then the power management is still very different.

---

