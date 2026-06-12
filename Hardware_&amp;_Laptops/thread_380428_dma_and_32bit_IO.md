---
title: "dma and 32bit IO"
date: 2007-03-09
forum: Hardware &amp; Laptops
---

### Post by finite9 on 2007-03-09
i've just bought a new laptop with SATA drives and setting DMA and io32_support does not seem to work.  I can set DMA on cdrom just fine with:
```

sudo hdparm -d1 /dev/cdrom
```

but
```

sudo hdparm -d1 /dev/sdb
```

gives following error:
```

/dev/sdb:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
```


anyone know why I cannot set DMA or 32bit IO on SATA drives?  Btw, this all works on non-SATA drives in old laptop.

---

