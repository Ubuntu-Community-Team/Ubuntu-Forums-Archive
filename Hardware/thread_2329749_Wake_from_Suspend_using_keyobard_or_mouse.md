---
title: "Wake from Suspend using keyobard or mouse"
date: 2016-07-04
forum: Hardware
---

### Post by Mopar1973Man on 2016-07-04
I'm trying to get my computer to wake up from suspend using my keyboard or mouse. I've been through the whole acpitool the USB ports are enabled but S4 mode which I think is my hang up and the ports are power down. How do I change to S3? The BIOS setting is disabled for S4 suspend. 
```

michael@michael:~$ acpitool -w
   Device    S-state      Status   Sysfs node
  ---------------------------------------
  1. SBAZ      S4    *disabled  pci:0000:00:14.2
  2. ECIR      S4    *disabled
  3. PS2K      S4    *disabled
  4. PS2M      S4    *disabled
  5. UAR1      S4    *disabled
  6. OHC1      S4    *enabled   pci:0000:00:12.0
  7. EHC1      S4    *enabled   pci:0000:00:12.2
  8. OHC2      S4    *enabled   pci:0000:00:13.0
  9. EHC2      S4    *enabled   pci:0000:00:13.2
  10. OHC3      S4    *disabled
  11. EHC3      S4    *disabled
  12. OHC4      S4    *disabled
  13. XHC0      S4    *enabled   pci:0000:00:10.0
  14. XHC1      S4    *enabled   pci:0000:00:10.1
  15. PE21      S4    *disabled
  16. PE22      S4    *disabled  pci:0000:00:15.2
  17. RLAN      S4    *enabled   pci:0000:03:00.0
  18. PE23      S4    *disabled
  19. PCE2      S4    *disabled
  20. PCE3      S4    *disabled
  21. PCE4      S4    *disabled
  22. PCE5      S4    *disabled
  23. PCE6      S4    *disabled
  24. PCE7      S4    *disabled
  25. PE20      S4    *disabled  pci:0000:00:15.0
  26. P0PC      S4    *disabled  pci:0000:00:14.4

```

---

### Post by Mopar1973Man on 2016-07-05
Bump... Any help me out here...???

---

