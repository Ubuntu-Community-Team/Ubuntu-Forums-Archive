---
title: "Lirc updates broke MCE remote?"
date: 2008-11-24
forum: General Help
---

### Post by dartmusic on 2008-11-24
I had my MCE remote and receiver working perfectly with all players in Intrepid until today.  There was a lirc update this morning.  My remote stopped functioning so I opened the Lirc GUI and suddenly there IS no MCE remote option?  

Has anyone else noticed this?  Has something happened or changed that I just didn't know about or notice?

Thanks!

---

### Post by ariel on 2008-11-24
> **dartmusic said:**
> I had my MCE remote and receiver working perfectly with all players in Intrepid until today.  There was a lirc update this morning.  My remote stopped functioning so I opened the Lirc GUI and suddenly there IS no MCE remote option?  

Has anyone else noticed this?  Has something happened or changed that I just didn't know about or notice?

Thanks!

Today I noticed the same issue with my saa-based remote. It turned out that the update overwrote the /etc/lirc confi files (hardware.conf and lircd.conf); I had to restore them from a backup.

---

