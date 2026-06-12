---
title: "Asus Q500a - Lid open does not &quot;wakeup&quot; after suspend"
date: 2014-06-29
forum: Hardware
---

### Post by Ron_Field on 2014-06-29
Asus Q500a - Ubuntu 14.04 - i5-3230, 6 Gb ram

Suspending by closing the lid on the laptop, opening the lid will not resume.  If I touch any key, Ubuntu "wakes up" and all is well.  I would like to be able to have the laptop "wakeup" with the "lid open" event.

This is the content of /proc/acpi/wakeup
```

Device  S-state   Status   Sysfs nod e
P0P1      S4    *disabled
EHC0      S3    *enabled   pci:0000:00:1d.0
USB0      S3    *disabled
USB1      S3    *disabled
USB2      S3    *disabled
USB3      S3    *disabled
EHC1      S3    *enabled   pci:0000:00:1a.0
USB4      S3    *disabled
USB5      S3    *disabled
USB6      S3    *disabled
XHC       S3    *enabled   pci:0000:00:14.0
RP01      S4    *disabled  pci:0000:00:1c.0
RP02      S4    *disabled  pci:0000:00:1c.1
WLAN      S3    *disabled  pci:0000:02:00.0
RP03      S4    *disabled  pci:0000:00:1c.2
GLAN      S4    *disabled  pci:0000:03:00.0
RP04      S4    *disabled
RP05      S4    *disabled
RP06      S4    *disabled
RP07      S4    *disabled
RP08      S4    *disabled
LID       S4    *enabled 
```

Suggestions?  Are there other files which control the "LID" open event in Ubuntu?

---

