---
title: "Upgrade to 9.10 /dev/mapper/isw_dihahicich_Raid_Volume1"
date: 2009-10-24
forum: Installation &amp; Upgrades
---

### Post by sjrixon on 2009-10-24
Help..

I did an in place upgrade to the beta 9.10. I used to have a raid(Mirror) setup with mdadm. 

Now I have something called /dev/mapper/isw_dihahicich_Raid_Volume1 and I can't start the raid. It fails on the 2 drives.

Any ideas?

---

### Post by sjrixon on 2009-10-24
used 

dmraid -rE to remove it.. Then removed the mapper ones..

Then I could restart.. and use mdadm to setup my old raid up correctly.. Worked liked a charm.

---

