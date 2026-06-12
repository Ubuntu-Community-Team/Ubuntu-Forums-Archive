---
title: "Notebook internal HDD temperature high, not even mounted"
date: 2011-05-22
forum: Hardware
---

### Post by karatedog on 2011-05-22
I installed Ubuntu to an external HDD, and I boot from it on a Lenovo T400, which has as internal HDD as well. After 10-15 minutes of use the **internal** HDD heats up, which is not even mounted!
I had temperature issues with Ubuntu before (9.10, 10.04, 10.10). The problem is that the HDD is under my right palm, and the heating makes it very-very uncomfortable to use the notebook.
I tried everything the forums could offer (relatime settings, journaling tweaking, etc.)

However my question is, how a not-mounted, not-used internal HDD could heat up, as no disk activity should occur there? 

$ fuser -m /dev/sda1 -> returned nothing.
$ hddtemp -> reports 43 celsius degrees. In Windows, it never goes above 35 degrees (and the HDD is used there)

---

