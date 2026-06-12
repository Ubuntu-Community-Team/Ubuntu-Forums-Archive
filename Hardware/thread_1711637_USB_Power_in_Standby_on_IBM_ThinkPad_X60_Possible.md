---
title: "USB Power in Standby on IBM ThinkPad X60 Possible?"
date: 2011-03-21
forum: Hardware
---

### Post by nawk168 on 2011-03-21
I just installed Ubuntu 10.10 on my ThinkPad X60. Everything seems to work flawlessly compared to previous versions except for the fact that my USB ports lose power when I put the computer in standby.

I have Windows 7 on the same computer and all 3 USB ports retain power. Is there a way to enable this feature in Ubuntu?

'acpitool -w' returns the following:

```
   Device	S-state	  Status   Sysfs node
  ---------------------------------------
  1. LID	  S3	*enabled   
  2. SLPB	  S3	*enabled   
  3. EXP0	  S4	*disabled  pci:0000:00:1c.0
  4. EXP1	  S4	*disabled  pci:0000:00:1c.1
  5. EXP2	  S4	*disabled  pci:0000:00:1c.2
  6. EXP3	  S4	*disabled  pci:0000:00:1c.3
  7. PCI1	  S4	 disabled  pci:0000:00:1e.0
  8. USB0	  S3	 disabled  pci:0000:00:1d.0
  9. USB1	  S3	 disabled  pci:0000:00:1d.1
  10. USB2	  S3	 disabled  pci:0000:00:1d.2
  11. USB7	  S3	 disabled  pci:0000:00:1d.7
  12. HDEF	  S4	 disabled  pci:0000:00:1b.0

```

When I run 'acpitool -W' to enable the USB items, I still do not get power from the USB ports in standby. Also, when I restart the computer, the configuration resets to what is shown above.

Does anyone know if it's possible to maintain power to the USB ports in standby?

---

### Post by nawk168 on 2011-03-21
If anybody has done this to any other laptop, please share.

---

