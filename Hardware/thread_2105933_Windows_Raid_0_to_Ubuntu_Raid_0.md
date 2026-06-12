---
title: "Windows Raid 0 to Ubuntu Raid 0"
date: 2013-01-17
forum: Hardware
---

### Post by Aoifern on 2013-01-17
I just switched over from Windows 8 to Ubuntu and want to switch my raid 0 drivers over if that is possible?

---

### Post by lukeiamyourfather on 2013-01-17
How are you implementing the RAID 0 currently? Hardware based RAID controller? Software based RAID controller? Windows software RAID utility?

---

### Post by Aoifern on 2013-01-17
> **lukeiamyourfather said:**
> How are you implementing the RAID 0 currently? Hardware based RAID controller? Software based RAID controller? Windows software RAID utility?

I used the windows raid utility, and I still have 8 installed.

---

### Post by lukeiamyourfather on 2013-01-17
Try dmraid, it should be able to mount Windows software RAID volumes. Backup anything you don't want to lose just in case.

```

sudo apt-get install dmraid
sudo dmraid -ay

```

The first command installs dmraid if you don't already have it. The second command tells dmraid to mount all of the software RAID volumes it finds. For more information on dmraid check out the manual for it (only available if dmraid is installed).

```

man dmraid

```

---

