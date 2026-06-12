---
title: "ACPI Resume from USB on 945GCLF2 Atom.."
date: 2010-05-08
forum: Hardware
---

### Post by KamakazieX on 2010-05-08
I am trying to use my Streamzap usb remote receiver to resume the PC from hibernate for XBMC. Currently running x86 10.04 (Base 10.04 with xbmc packages not mythbuntu). Clean install as of today. Remote works fine on resume spite recent bugs. Searching google gives results saying to enable acpi resume for USB*n* which is not listed as a feature for this board? Here are the results:

```

Device	S-state	  Status   Sysfs node
SLPB	  S4	*enabled   
P32	  S4	 disabled  pci:0000:00:1e.0
UAR1	  S4	 disabled  pnp:00:0a
PEX0	  S4	 disabled  pci:0000:00:1c.0
PEX1	  S4	 disabled  
PEX2	  S4	 disabled  pci:0000:00:1c.2
PEX3	  S4	 disabled  pci:0000:00:1c.3
PEX4	  S4	 disabled  
PEX5	  S4	 disabled  
UHC1	  S3	 disabled  pci:0000:00:1d.0
UHC2	  S3	 disabled  pci:0000:00:1d.1
UHC3	  S3	 disabled  pci:0000:00:1d.2
UHC4	  S3	 disabled  pci:0000:00:1d.3
EHCI	  S3	 disabled  pci:0000:00:1d.7
AC9M	  S4	 disabled  
AZAL	  S4	 disabled  pci:0000:00:1b.0

```

---

