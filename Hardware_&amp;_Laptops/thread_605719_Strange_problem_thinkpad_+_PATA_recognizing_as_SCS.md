---
title: "Strange problem thinkpad + PATA recognizing as SCSI/SATA pls hlp.."
date: 2007-11-07
forum: Hardware &amp; Laptops
---

### Post by comfortablynumb on 2007-11-07
I got a strange problem with a new install of 7.10 on my IBM T23 **(latest bios 10/2006)**, it has an Intel 82801CAM chipset. I checked [Thinkwiki]("http://www.thinkwiki.org/wiki/Intel_82801CAM") and they state "This chipset is supported by recent 2.4 and 2.6 kernels" . My hard drive is showing up as SDA and not HDA, it's listed under SCSI device in device manager and also my DVD drive is listed under SCSI devices as well.  The interesting thing is Device Manager lists the chip right as Intel 8201CAM IDE100.

My main concern is I was experiencing the high Load count bug, it was climbing more than a hundred an hour. The only way I could fix it was by turning off power management hdparm -B 254 /dev/sda and it stopped the  high counting,   Here is my [post on that issue]("http://ubuntuforums.org/showthread.php?t=604854") as well

**Hard drive**:
Seagate Momentus ST92811A 20GB 5400 RPM ATA-6

IBM T23 Laptop with latest BIOS from IBM

---

### Post by comfortablynumb on 2007-11-07
bump

---

