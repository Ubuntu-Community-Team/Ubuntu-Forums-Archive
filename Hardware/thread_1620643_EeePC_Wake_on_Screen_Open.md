---
title: "EeePC Wake on Screen Open"
date: 2010-11-13
forum: Hardware
---

### Post by skykooler on 2010-11-13
I have an EeePC 1000he with 1GB RAM. When using Windows XP there is an option to resume from sleep when I open the lid. Is there any way to do this in Ubuntu? I checked /proc/acpi/wakeup but there is no LID option Here is what I have: 
```
$ cat /proc/acpi/wakeup 
Device	S-state	  Status   Sysfs node
P0P2	  S4	 disabled  
P0P1	  S4	 disabled  pci:0000:00:1e.0
HDAC	  S4	 enabled   pci:0000:00:1b.0
P0P4	  S4	 disabled  pci:0000:00:1c.0
P0P8	  S4	 disabled  
P0P5	  S4	 disabled  pci:0000:00:1c.1
P0P7	  S4	 disabled  pci:0000:00:1c.3
P0P9	  S4	 disabled  
P0P6	  S4	 disabled  

```

Any help?

---

