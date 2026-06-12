---
title: "How to fix error reported by boot_info_script27.sh??"
date: 2009-03-04
forum: Installation &amp; Upgrades
---

### Post by MountainX on 2009-03-04
How do I clean up devices which don't seem to have a corresponding hard drive

boot_info_script27.sh reports:
==Devices which don't seem to have a corresponding hard drive====
sdh 

I would like to get rid of sdh, but I'm not sure how.

---

### Post by MountainX on 2009-03-05
Wow, I just learned about something new (to me): udevinfo

```
sudo udevinfo --query=all --name=/dev/sdh
```

It tells me that /dev/sdh is a "virtual floppy disk". So that mystery is solved.

---

