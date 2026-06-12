---
title: "how to access ubuntu partition from vista"
date: 2008-09-07
forum: General Help
---

### Post by cheaptrick on 2008-09-07
hi, my ubuntu parition is not detected and shown in My Computer in vista.. How do i access it?

---

### Post by forger on 2008-09-07
You can use the driver from [www.fs-driver.org](www.fs-driver.org)

---

### Post by demios on 2008-10-01
> **forger said:**
> You can use the driver from [www.fs-driver.org](www.fs-driver.org)

wow, that thing works like a charm.

---

### Post by gus_393 on 2008-10-01
I hate to be a "downer", and for all I know things have improved alot since I last tried it, but I thnk I should give you the heads up.

The public domain drivers that work with NTFS arent 100% last time I checked. If you have production critical data there, you might want to be mindful. I had a friend who experienced some corruption when mounting an NTFS drive in linux, and also on the reverse, I`ve heard there can be issues going the otherway.

I know thats all very vague, I just thought that if I was you I`d want someone to just give me a polite heads up that some people have had issues before. Generally, myself, I`ve had alot more success just using fat32 partitions for "linux/win32" swap.

---

### Post by kokkus on 2008-10-01
It's ok to set up NTFS and FAT32 drivers from linux, but NOT reverse as you're asking for. It's a damn big security risk to take.
It's like an open door for hackers when you're running windows.
So you shouldn't. Run the seperated or just from Linux to read the Windows driver, and not reverse.

---

### Post by demios on 2008-10-01
I'm using ext2, is that as big of a liability?

---

### Post by TeXtonyx on 2008-10-01
Linux Reader from DiskInternals only sets up with read permissions from Vista to Linux.
You can copy a file from Ubuntu to Vista. I think fs-driver assigns a drive Letter to Linux
and have you checked to see if Windows is now monitoring that drive letter for restore?

---

