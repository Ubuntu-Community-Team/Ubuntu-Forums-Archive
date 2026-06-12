---
title: "USB HD wont mount"
date: 2011-01-19
forum: Hardware
---

### Post by ginopappaterra on 2011-01-19
Last month I got a WD 500GB SATA HD and USB case.  I connected it to my computer and it worked great for a few weeks.  One day it stop appearing on my desktop.  I tried mounting it with Disk Utility but it says it is unknown.  I tried it in a Mini Mac running OSX and it worked fine, tried it again in Ubuntu, no luck.  Any ideas???

---

### Post by wilee-nilee on 2011-01-19
> **ginopappaterra said:**
> Last month I got a WD 500GB SATA HD and USB case.  I connected it to my computer and it worked great for a few weeks.  One day it stop appearing on my desktop.  I tried mounting it with Disk Utility but it says it is unknown.  I tried with Mini Mac running OSX and it worked fine, tried it again in Ubuntu, no luck.  Any ideas???

Is the partition a NTFS?

Install gparted in Ubuntu and open it and look at the HD by using the drop-down in the top right panel, for disc choice. look for any flags on the HD's partition, if so right click it then information.

---

### Post by ginopappaterra on 2011-01-20
No it's a FAT32...

---

### Post by ginopappaterra on 2011-01-20
No it's FAT32...

---

### Post by ginopappaterra on 2011-01-20
No it's FAT32...

---

### Post by ginopappaterra on 2011-01-21
SOLVED!  I got Gparted to repair the Filesystem and Voila! afterwards I was able to mount it with Disk Utility.  **Thanks a lot!**

---

