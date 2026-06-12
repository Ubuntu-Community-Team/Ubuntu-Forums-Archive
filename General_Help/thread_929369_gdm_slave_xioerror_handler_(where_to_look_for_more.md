---
title: "gdm_slave_xioerror_handler (where to look for more info?)"
date: 2008-09-24
forum: General Help
---

### Post by crazywizzard on 2008-09-24
X crashed, and did not recover (before the computer got the power yanked), and all I can see in the syslog is the lines

```

Sep 24 21:17:01 desktop-lin /USR/SBIN/CRON[6155]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 24 21:35:56 desktop-lin -- MARK --
Sep 24 21:36:16 desktop-lin gdm[5557]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 

```

That cron entry is the only one I can find in the log, so I don't know if there is a schedule causing problems. (After posting this I will manually run it to see what happens.

I don't know where to look next and I would appreciate any help.

I am running the binary fglrx driver from the ati website, (was 8.8 just now upgraded to 8.9, hopefully that fixes it)

I am running Ubuntu 8.04 x86_64 on:
MSI K9A2 CF-F motherboard (AM2+)
ATI RadeonHD 4850 (from sapphire w/ 1G video RAM)

---

