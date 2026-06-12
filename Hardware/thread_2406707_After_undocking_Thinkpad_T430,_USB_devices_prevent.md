---
title: "After undocking Thinkpad T430, USB devices prevent laptop from sleeping"
date: 2018-11-24
forum: Hardware
---

### Post by randomkudo on 2018-11-24
Running 18.04, Linux ilya 4.15.0-39-generic #42-Ubuntu SMP Tue Oct 23 15:48:01 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux. This happened on XUbuntu 18.04 as well.

By default, my /proc/acpi/wakeup looks like this:
```
shinichi@ilya:~ cat /proc/acpi/wakeup 
Device    S-state      Status   Sysfs node
LID      S4    *enabled   platform:PNP0C0D:00
SLPB      S3    *enabled   platform:PNP0C0E:00
IGBE      S4    *disabled  pci:0000:00:19.0
EXP3      S4    *disabled  pci:0000:00:1c.2
XHCI      S3    *enabled   pci:0000:00:14.0
EHC1      S3    *enabled   pci:0000:00:1d.0
EHC2      S3    *enabled   pci:0000:00:1a.0
HDEF      S4    *disabled  pci:0000:00:1b.0


```

Sometimes, only sometimes, after I undock my Thinkpad T430 from a Mini Dock Series 3 Plus (with a USB3 port), the system wakes up immediately after entering sleep. I have never observed this with my Thinkpad X230, only the T430.


To fix it, I have to disable all USB devices in /proc/acpi/wakeup. If I leave one out, the problem still remains.
```
shinichi@ilya:~ echo XHCI | sudo tee /proc/acpi/wakeup 
XHCI
shinichi@ilya:~ echo EHC1 | sudo tee /proc/acpi/wakeup 
EHC1
shinichi@ilya:~ echo EHC2 | sudo tee /proc/acpi/wakeup 
EHC2

```

But I'm not satisfied. I want to know why this is happening. What can I do, to dive deeper into the kernel and see what's going on? dmesg doesn't say anything extra.

---

