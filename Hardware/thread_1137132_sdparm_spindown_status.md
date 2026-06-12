---
title: "sdparm spindown status"
date: 2009-04-25
forum: Hardware
---

### Post by vw_man99 on 2009-04-25
Hi All,
Have been having issues with power management on a dual core Atom (primarily a media NAS) setup running Lenny so ended up disabling all PM. Now I want to spin down just my data drives from cron using sdparm which works fine with the 500GB Seagates. I want to include in the scripts status of the drives (spun down? spun up?) but haven't been able to find much docs on the attribute abbreviations like TST, TMF_ONLY, D_SENSE, etc. Anyone know which attribute would show spin status?

I tried doing diff's from output of  "sdparm --all /dev/sdb" before and after spin down but no diff's found. Drive does not sound like its spinning up when I do "sdparm --all /dev/sdb" until I actually access it. Thanks.

vw

---

