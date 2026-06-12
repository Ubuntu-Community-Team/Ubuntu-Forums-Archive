---
title: "Hard Disk Temperature"
date: 2007-03-21
forum: Hardware &amp; Laptops
---

### Post by galeron on 2007-03-21
Hi people,

I just installed hddtemp on my RAID1 server, and I got a big shock.

I have 3 hard disks
1) Maxtor IDE harddisk - 43deg - this seems normal

2) & 3) Identical SATA Maxtor 250gb HDD connected to a SiL3112 SATA card - 72deg

I have the impression that it's much too high. Is there any way to lower the temperatures? I suspect that the SATA card (software RAID with mdadm) is not spinning down the hard disks when they are not being used. Any way to verify this?

TIA

---

### Post by futz on 2007-03-21
> **galeron said:**
> Hi people,

I just installed hddtemp on my RAID1 server, and I got a big shock.

I have 3 hard disks
1) Maxtor IDE harddisk - 43deg - this seems normal

2) & 3) Identical SATA Maxtor 250gb HDD connected to a SiL3112 SATA card - 72deg

I have the impression that it's much too high. Is there any way to lower the temperatures?
If you mean 72 C, then yes, that's pretty warm.

If possible, get them separated from each other by one drive space. This helps with convection to get that heat away. When they're close to each other they keep each other warm and air flow is minimal.

Try to get some airflow over them from front to back. Many cases have a fan mount in front of the drive cage. Install a fan in there to pull air from the front of the case and move air across the drives toward the back of the case. It will exhaust out the PSU. Another extra exhaust fan on the rear of the case is a good idea too to help airflow, as many PSU fans are pretty lazy. With a fan moving air across the drives it's ok if they're mounted adjacent to each other. It doesn't take much airflow to carry that heat away and keep em nice and cool.

If they're rubber mounted, they can't use the drive cage as a heat sink, so either remove the rubber and hard mount them to metal, or do the fan(s) thing.

> I suspect that the SATA card (software RAID with mdadm) is not spinning down the hard disks when they are not being used. Any way to verify this?
Use a "stethescope" when you think they should be spun down. Just a pencil or something held to your ear and touching the drive. You can tell if they're spinning usually. Listen to one spin up so you know what they sound like not-spinning and spinning.

---

