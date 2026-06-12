---
title: "Configuring DVD drive"
date: 2011-09-02
forum: Hardware
---

### Post by c.washington.h on 2011-09-02
So I installed a SATA LG DVD burner into my fresh built desktop. The BIOS sees my drive but ubuntu does not. Is there some king of configuration that I need to do?

---

### Post by 2F4U on 2011-09-03
When I built my desktop I didn't need to do anything to configure the DVD burner. So, you don't see the drive, which would be ok if the drive is empty (I don't see my drive if there is no medium inserted). What happens if you insert a medium?

---

### Post by c.washington.h on 2011-09-03
When I put in media it spins up for 5 seconds or so and then nothing happens.

---

### Post by .... on 2011-09-03
Maybe Ubuntu sees it and has trouble mounting. Look at:
```
sudo lshw -C disk
```

---

### Post by c.washington.h on 2011-09-04
This came up. This is my Hard Disk: 

description: ATA Disk
       product: WDC WD3200AAKX-0
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/sda
       version: 15.0
       serial: WD-WCAYUH756359
       size: 298GiB (320GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0002f542

---

