---
title: "Raid is not recognized :("
date: 2007-05-16
forum: Hardware &amp; Laptops
---

### Post by burzum on 2007-05-16
I have an old Asus P4PE with the Promise PDC20376 SATA Raid. The raid itself is functional and working. Im using mirroring.

Now i've tried to install this image ubuntu-6.06.1-server-i386.iso but im stuck at the partitioning.

Instead of showing one raiddevice it displays me:

```
SCSI1 (0,0,0) (sda) - 500.1gb...
SCSI2 (0,0,0) (sdb) - 500.1gb...
```

lspci | grep pro shows this

```

sata_promise 11780 0
libdata 78992 1 sata_promise
scsi_mod 139496 7 sr_mod,sbp2,usb_storage,sg,sd_mod,sata_promise,libdata

```

Any ideas how to get ubuntu to recognize the raid device? :(

---

### Post by wh33t on 2007-05-16
Did you install the raid driver?

---

### Post by burzum on 2007-05-17
I guess that the module sata_promise is loaded shows that the driver is already loaded.

---

### Post by wh33t on 2007-05-17
Well that doesn't make sense. If its loaded it should be working eh? Try looking up the raid controller on the web and see if there is a new driver available for it.

---

