---
title: "Clamtk virus definition update error"
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by deerhunter on 2009-05-16
When I try to update Clamtk virus definitions by typing sudo freshclam I get the following error

ERROR: cdiff_apply: lseek(desc, -350, SEEK_END) failed
ERROR: getpatch: Can't apply patch
WARNING: Incremental update failed, trying to download daily.cvd
Downloading daily.cvd [100%]
daily.cvd updated (version: 9365, sigs: 5249, f-level: 42, builder: mcichosz)
Database updated (550284 signatures) from db.local.clamav.net (IP: 64.246.134.219)
Clamd successfully notified about the update.
 
can anybody help me and tell me what this means? 
I am also trying to update the GUI version but I do not know how to do it.

Thanks

---

### Post by the_phenom on 2009-05-16
No, it looks to me like the signatures successfully updated.  To update the GUI, go to [http://clamtk.sf.net]("http://clamtk.sf.net"), follow the Downloads link, grab the .deb file, and double-click it.

---

### Post by Clyssus on 2011-05-04
Just the info I needed! Thanks!

---

