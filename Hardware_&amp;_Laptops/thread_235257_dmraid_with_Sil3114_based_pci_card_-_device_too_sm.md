---
title: "dmraid with Sil3114 based pci card - device too small for target error"
date: 2006-08-12
forum: Hardware &amp; Laptops
---

### Post by DROP on 2006-08-12
Hello,

I am running **4 ~250GB drives** in a **RAID 10** on a **Rosewill RC209** which uses the **Sil 3114 chipset**. Last week I was able to run two drives in a raid 0, but I purchased two more drives to change to RAID 10.

So, in the Bios level config I deleted the raid 0 set and created a new set with all 4 drives as raid 10. Now Ubuntu is not detecting the drive. There is no longer a device under **/dev/mapper/sil_########**

tail /var/log/messages shows:
```
Aug 12 18:09:45 drop-lin kernel: [4295675.083000] device-mapper: device /dev/sda too small for target
Aug 12 18:09:45 drop-lin kernel: [4295675.083000] device-mapper: error adding target to table

```

running "sudo lvmdiskscan" shows:
```
  /dev/ram0  [       64.00 MB]
  /dev/sda   [      232.89 GB]
  /dev/ram1  [       64.00 MB]
  /dev/hda1  [        9.32 GB]
  /dev/ram2  [       64.00 MB]
  /dev/hda2  [      957.00 MB]
  /dev/ram3  [       64.00 MB]
  /dev/hda3  [      138.80 GB]
  /dev/ram4  [       64.00 MB]
  /dev/ ...  [       ...   MB]
  /dev/sdb   [      232.89 GB]
  /dev/sdc   [      232.89 GB]
  /dev/sdd   [      232.89 GB]

```
as you can see the drives show up under, but they are individual /dev/sd*

---

### Post by niester on 2006-11-18
Hi,

I am getting the same error message:

device-mapper: device /dev/sda too small for target
device-mapper: dm-mirror: Device lookup failure
device-mapper: error adding target to table


Can any solve this problem?


Lukasz

---

