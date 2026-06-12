---
title: "Setting to spin down hard drives after 30 min"
date: 2006-11-21
forum: Hardware &amp; Laptops
---

### Post by ankle on 2006-11-21
I have 3 SATA drives and 1 PATA/IDE drive, not all of which are in use at the same time. Which settings should I use (hdparm? laptop-mode-tools?) to tell the drives to spin down after 30 minutes of non-usage?

---

### Post by ankle on 2006-11-21
So far I have

sudo smartctl -d ata -s on -a /dev/sda
(enable SMART)
sudo hdparm -B 128 /dev/sda
(advanced power management)
sudo hdparm -S 241 /dev/sda
(spindown: 30 min)

for each of the SATA drives, and

sudo smartctl -s on -a /dev/hdb
sudo hdparm -B 128 /dev/hdb
sudo hdparm -S 241 /dev/hdb

for the PATA/IDE drive.

Does that seem reasonable (I haven't found out the recommended setting for the advanced power management, and the recommended acoustic management value of 192 isn't valid, apparently)?

---

