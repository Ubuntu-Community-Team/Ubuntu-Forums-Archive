---
title: "Graphic problems on kubuntu 8.10"
date: 2009-01-19
forum: Hardware
---

### Post by kjarli on 2009-01-19
Hi, i have some problems with the graphics. The video card is not super, but should be working properly. Atm my screen is at 1280x1024 but it goes as smooth as in xp with no video drivers installed, how can i fix this rather than installing a new video card?

Some more info:
card
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1520508&sku=TC3H-1027](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1520508&sku=TC3H-1027)

info
```
iltar@desktop:~$ grep VESA /var/log/Xorg.0.log
(II) MACH64(0): VESA BIOS detected
(II) MACH64(0): VESA VBE Version 2.0
(II) MACH64(0): VESA VBE Total Mem: 8128 kB
(II) MACH64(0): VESA VBE OEM: ATI MACH64
(II) MACH64(0): VESA VBE OEM Software Rev: 1.0
(II) MACH64(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) MACH64(0): VESA VBE OEM Product: MACH64GM
(II) MACH64(0): VESA VBE OEM Product Rev: 01.00
(II) MACH64(0): VESA VBE DDC supported
(II) MACH64(0): VESA VBE DDC Level 2
(II) MACH64(0): VESA VBE DDC transfer in appr. 2 sec.
(II) MACH64(0): VESA VBE DDC read successfully
(II) MACH64(0): Supported VESA Video Modes:

```

---

