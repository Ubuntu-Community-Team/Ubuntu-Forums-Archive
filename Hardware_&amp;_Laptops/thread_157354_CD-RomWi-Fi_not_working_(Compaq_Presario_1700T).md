---
title: "CD-Rom/Wi-Fi not working (Compaq Presario 1700T)"
date: 2006-04-09
forum: Hardware &amp; Laptops
---

### Post by bachstradb4sprana on 2006-04-09
I'm setting up 5.10 on my old Presario 1700 laptop, but I've hit a few snags.  My D-Link DWL-G650 works intermittently, and my CD-ROM isn't working at all.  I followed the wiki's instructions to update the firmware for the Wi-Fi card, and it worked until I shut the laptop lid (no, I'm not making this up).  Now, it doesn't show up at all, except as an "unrecognized device" under the PCMIA cardbus.  The "ACT" LED flashes, but the "LNK" LED doesn't come on at all.  The "acx_pci" driver doesn't appear in the module list.  As far as the CD-ROM goes, it shows up in the file browser, but when I try to open it, I get the "unable to mount selected volume" error, saying that "mount: special device /dev/hdc does not exist".  My fstab for the CDROM reads: /dev/hdc     media/cdrom0    udf,iso9660 user,noauto.

Any help would be appreciated greatly.

---

