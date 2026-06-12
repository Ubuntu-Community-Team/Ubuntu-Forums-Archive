---
title: "open with is the same for all file types"
date: 2009-10-07
forum: Installation &amp; Upgrades
---

### Post by beemzet on 2009-10-07
Hi guys,
I've 9.10 beta installed. When I try to open any type of a file it opens with the same program (gedit by default). I changed this to VLC for AVI files and now any other file (doc, pdf, etc) opens in VLC. What might be a problem?

Thanks

---

### Post by beemzet on 2009-10-07
update-mime-database /usr/local/share/mime does the trick

---

### Post by oboedad55 on 2009-10-07
> **beemzet said:**
> update-mime-database /usr/local/share/mime does the trick

I had to do a restart to get this to work, btw.

---

### Post by beemzet on 2009-10-07
> **oboedad55 said:**
> I had to do a restart to get this to work, btw.

i just logged out and back in

---

