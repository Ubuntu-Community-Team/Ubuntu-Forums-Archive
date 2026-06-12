---
title: "AMD64 will not mount secondary hard drive"
date: 2006-06-09
forum: Hardware &amp; Laptops
---

### Post by Az7 on 2006-06-09
Fresh build from Dapper 6.06 AMD64 Desktop.  Ubuntu doesn't want to mount my slaved HD.  Going to (System > Administrator > Disks) shows it but its status is "inaccessible".  The filesystem is detected as vfat, but doing a "sudo fdisk -l" yields the following:
```

  Device Boot      Start         End      Blocks       Id  System
  /dev/hdc1             1       24321   195358401   42  SFS

```

Doing a "sudo mount -t vfat /dev/hdc1 /files" yields:
```

mount: special device /dev/hdc1 does not exist

```

---

