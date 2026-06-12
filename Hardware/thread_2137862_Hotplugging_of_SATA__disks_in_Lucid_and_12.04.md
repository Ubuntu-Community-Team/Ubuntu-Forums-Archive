---
title: "Hotplugging of SATA  disks in Lucid and 12.04"
date: 2013-04-22
forum: Hardware
---

### Post by cogset on 2013-04-22
What's the status of SATA disks hotplugging in Ubuntu Lucid and in  the current 12.04 LTS ? 

If the motherboard has SATA hotplugging capabilities,is it enough to enable this in the Bios?

Are there any differences (I would guess so) in the way Lucid and 12.04 handle this ?

EDIT : Once the hotpugging is activated in the Bios,is it enough to unmount the drive from the file manager and put it in standby** with sudo hdparm -y** before removing it ?

---

### Post by cogset on 2013-09-23
I'll answer myself this time:in Lucid with a 3.0.0-20-generic  kernel,hotswapping works fairly well,apparently:upon inserting my spare  SATA drive in the tray,it immediately appears in the Removable devices  (although,it is not auto-mounted,but I can live with this)-as for  removing it,I unmount it and then run this command 
```
echo 1 > /sys/block/sd$/device/delete
```
for good measure,as explained here[URL="http://I'll answer myself this time:in Lucid with a 3.0.0-20-generic kernel,hotswapping works fairly well,apparently:upon inserting my spare SATA drive in the tray,it immediately appears in the Removable devices (although,it is not auto-mounted,but I can live with this)-as for removing it,I unmount it and then run this command ```
echo 1 > /sys/block/sd$/device/delete
``` for good measure,as explained here http://www.sakana.fr/blog/2009/05/04/linux-sata-hot-plug-unplug/"] http://www.sakana.fr/blog/2009/05/04/linux-sata-hot-plug-unplug/[/URL] ,which makes the heads park or powers down the drive for good,as I can hear a last click and then it disappears from the system and can be removed.

---

### Post by cogset on 2013-09-24
wrong thread please delete -thanks

---

