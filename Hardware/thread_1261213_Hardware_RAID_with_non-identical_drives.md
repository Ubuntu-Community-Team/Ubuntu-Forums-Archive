---
title: "Hardware RAID with non-identical drives?"
date: 2009-09-08
forum: Hardware
---

### Post by Vunutus on 2009-09-08
I'm wanting to set up RAID 5 on a server I recently purchased. It came with one hard drive, but has a hardware RAID controller. 

I'm wanting to order two additional hard drives for it. The drive that came with the server is HP-brand and not very cheap. It's a 250GB 7200RPM non-hotplug SATA drive. If I go on newegg and purchase two drives with the same stats (but a cheaper brand), will that cause any problems with the RAID controller?

I know mixed drives are supported with software RAID, but I'm not sure about hardware RAID...

---

### Post by Fafler on 2009-09-08
It should work, but the drives might differ a bit in actual size. Boot with the drives in non-RAID mode and note their exact size, reboot and start creating the RAID with the smallest drive first.

What RAID controller do you have? I might be slower than software RAID 5.

---

