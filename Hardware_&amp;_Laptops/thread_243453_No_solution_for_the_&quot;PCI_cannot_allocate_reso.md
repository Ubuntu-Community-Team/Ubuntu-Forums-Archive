---
title: "No solution for the: &quot;PCI: cannot allocate resource region ...&quot; ?!?"
date: 2006-08-25
forum: Hardware &amp; Laptops
---

### Post by pmilin@ptt.yu on 2006-08-25
Hello!
I am trying and reading many posts, but it seems that there is no solution for PCI ALLOCATION OF THE RESOURCE REGION. I realised that there are few typical problems regarding this issue, grouped by the number of the region. In my case the allocation regions are, 7, 8 and 9. As I saw, meny users have problems with the region 3.

Here is the part of the dmesg, which contains error message:
```

[17179574.684000] PCI: Using ACPI for IRQ routing
[17179574.684000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179574.684000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
[17179574.684000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[17179574.684000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.1
[17179574.796000] PCI: Bridge: 0000:00:01.0
[17179574.796000] PCI: Bridge: 0000:00:1c.0
[17179574.800000] PCI: Bridge: 0000:00:1c.1

```

What is it: "try 'pci=routeirq'"? Where to look for it, to change it?
Is there a solution to the problems of many? I can see many questions, but no answers!

Sincerely,
[email]pmilin@ptt.yu[/email]

---

### Post by MrSoussey on 2007-01-14
try a bios update... worked for me

---

