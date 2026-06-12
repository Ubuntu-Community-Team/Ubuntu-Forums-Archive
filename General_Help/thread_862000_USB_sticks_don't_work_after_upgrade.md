---
title: "USB sticks don't work after upgrade"
date: 2008-07-17
forum: General Help
---

### Post by mariuszkopec on 2008-07-17
After upgrade to 8.04.01 from 6.06.1 LTS the system cannot mount USB sticks. I tried 1GB Kingston, 2GB PQI and 16GB PQI. They still work perfectly on other systems (Windows, Fedora, Ubuntu 7). On the previous system I had problems with 16GB, but 2GB worked fine. The last mesg lines are as follows:
...
[17179916.232000] sd 4:0:0:0: Attached scsi removable disk sdb
[17179916.232000] sd 4:0:0:0: Attached scsi generic sg1 type 0
[17179916.232000] usb-storage: device scan complete
[17179922.044000] FAT: Unrecognized mount option "flush" or missing value

Any hints how to solve this problem?

---

### Post by ibuclaw on 2008-07-17
Press **Alt+F2** and type in:
```
gconf-editor
```
Now scroll through the gnome registry:
**/system/storage/default_options/vfat**

And remove "flush" from the **mount_options** string value.

Double clicking on it will bring up an edit box.

Regards
Iain

---

### Post by mariuszkopec on 2008-07-17
Iain, thank you for your help. Now everything is ok.

Regards,

Mariusz

---

