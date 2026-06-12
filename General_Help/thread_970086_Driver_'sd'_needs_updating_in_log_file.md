---
title: "Driver 'sd' needs updating in log file?"
date: 2008-11-03
forum: General Help
---

### Post by duanedesign on 2008-11-03
I was looking through my /var/log file and I noticed a line that says Driver 'sd' needs update. Does anyone know what this means and what I should do, if anything? Below is an excerpt of the log:

Nov  3 08:26:00 duanedesign-laptop kernel: [    5.533344] scsi 4:0:0:0: Direct-Access     ATA      TOSHIBA MK2552GS LV01 PQ: 0 ANSI: 5
Nov  3 08:26:00 duanedesign-laptop kernel: [    5.533483] scsi 4:0:0:0: Attached scsi generic sg1 type 0
**[COLOR="Red"]Nov  3 08:26:00 duanedesign-laptop kernel: [    5.555347] Driver 'sd' needs updating - please use bus_type methods[/COLOR]**
Nov  3 08:26:00 duanedesign-laptop kernel: [    5.555523] sd 4:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)

---

### Post by cariboo on 2008-11-03
See this bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/186167](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/186167)

It is a harmless warning.

Jim

---

