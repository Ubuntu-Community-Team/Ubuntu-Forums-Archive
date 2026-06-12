---
title: "No pci Devices recogniced"
date: 2007-01-16
forum: Hardware &amp; Laptops
---

### Post by mikelruiz on 2007-01-16
I hava a DUAL PIII 800, in a Tyan Tiger S1834 133 board, with 1Gb RAM. The chipset is a VIA APollo Pro 133A which I wonder if is supported by linux. When I write lsPCI there is no result. Any Idea??

Thanks a lot

---

### Post by kextyn on 2007-02-03
It may be a little late now but I just found a 5 page thread on this problem.  I was having the same issues with mine (Ubuntu newbie.)  The solution I see they came up with was disabling ACPI in BIOS as well as enabling the PnP OS option.  I just tried it and it's booting so I'll return with my results.

[http://www.ubuntuforums.org/showthread.php?t=255713&highlight=via+133a](http://www.ubuntuforums.org/showthread.php?t=255713&highlight=via+133a)

---

### Post by kextyn on 2007-02-03
After making that one change (disabling ACPI) it seems to be working pretty well now.  I am using Dapper BTW.

---

