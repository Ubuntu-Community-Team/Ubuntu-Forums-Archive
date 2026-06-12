---
title: "Newest version help"
date: 2009-07-24
forum: Installation &amp; Upgrades
---

### Post by kpgalligan on 2009-07-24
I have postgis 1.3.3 installed (postgis is postgresql's GIS database).  I've found that a feature that works in newer versions does not work in this version, and I can't really work around it.

So, looking for some advice on the best way to go about this.  I'm going to start looking into how to see if there's a newer version of the software available on some other repository (backports?).  Not sure yet quite how to do that.  Also, there's a newer source version. 1.3.6.  I feel pretty comfortable building, but not so sure about making postgre use the new build, and how to not blow away current data and package info, etc.

Any tips would be greatly appreciated.

Thanks in advance,
-Kevin

---

### Post by SuperSonic4 on 2009-07-24
Usually running ```
sudo make install
``` will make a compiled app work like a repo app but it would be wise to remove the installed version first

---

### Post by kpgalligan on 2009-07-24
Yeah.  I have this fear of the unknown with regards to uninstalls (current data, etc), but I guess its the way to go.

---

### Post by kpgalligan on 2009-07-24
Nevermind.  I think my brain took a break.  I can just backup the db.  Even if everything is shot, I can do a full reinstall and sort it out.

---

