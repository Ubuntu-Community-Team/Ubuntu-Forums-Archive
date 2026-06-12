---
title: "If device shows up in Dev. Manager, R drivers installed?"
date: 2006-05-10
forum: Hardware &amp; Laptops
---

### Post by mak90 on 2006-05-10
My onboard SATA controller (SiL 1134) and PCI SATA Controller both show un in device manager with their correct names, and # of ports - but when I do a gparted or install of dapper it doesn't detect any drives? My BIOS sees them all so I know there there...... thanks!

---

### Post by ranf on 2006-05-11
Do you get any errors when youi run gparted from a terminal?

sudo gparted

---

### Post by mak90 on 2006-05-11
Yes I get a warning that /dev/hda is read only, and then an error that /dev/hda is not accessible or something like that.

Which of course is because I am running on a Dapper LIVE cd, and the cdrom is read only.

I have no devices in the /dev folder named sda,sd* .  But the device manger lists some linux.sysfs_path as /sys/class/scsi_host/host0 in the properties of my SiL 3114 SATA controller host0 channel....

thank you!

---

