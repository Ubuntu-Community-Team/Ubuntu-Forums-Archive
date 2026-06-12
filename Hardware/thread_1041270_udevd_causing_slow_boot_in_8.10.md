---
title: "udevd causing slow boot in 8.10"
date: 2009-01-16
forum: Hardware
---

### Post by kwakr on 2009-01-16
I recently installed 8.10.  Bootchart shows my boot time is 1:31.  37 seconds is spent in udevd where scsi_scan is being called twice.  See the attached boot chart.  My PC has a SCSI controller with one CD/RW attached.  What can I do, if anything, to speed this up?

---

