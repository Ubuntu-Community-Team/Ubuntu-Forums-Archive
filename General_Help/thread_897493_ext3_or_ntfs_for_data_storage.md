---
title: "ext3 or ntfs for data storage?"
date: 2008-08-22
forum: General Help
---

### Post by sink on 2008-08-22
ext3 seems to be faster.

---

### Post by livestockPimp on 2008-08-22
ext3 is much better since it is native to linux.
however there are ext3 readers you can get for windows.

If you are need Windows to access it I would use fat32 personally. I have had some bad experiences getting Linux to write to ntfs volumes.

---

### Post by mixmaster on 2008-08-22
The onlyt reason I could see to use ntfs would be if you had to share it with windoze on a dual-boot machine.

---

### Post by insane_alien on 2008-08-22
if only dealing with *nix's the ext3
if need to ssaher with XP/vista then ntfs

---

### Post by WRDN on 2008-08-22
For data storage, I would choose Ext3, because it's much (much) less susceptible to fragmentation than NTFS. With the ext3 filesystem, fragmentation only starts to occur with 90%+ disk usage. If you want to access the data in Windows (if you have Windows), then you could use the [FS-Driver]("http://www.fs-driver.org/").

---

### Post by sink on 2008-08-22
Thank you for the advice .:D

---

### Post by cybrsaylr on 2008-08-22
> **mixmaster said:**
> The onlyt reason I could see to use ntfs would be if you had to share it with windoze on a dual-boot machine.

This is what I've done and so far no problems on my dual boot system.

---

### Post by MaxIBoy on 2008-08-22
Since there are ext3 drivers for windows, and since you definitely want a journaling filesystem (instead of something like Fat32,) and since NTFS fragments so easily, go for ext3.

---

