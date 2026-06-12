---
title: "Does the DVD image include all packages?"
date: 2009-04-22
forum: Installation &amp; Upgrades
---

### Post by MysticGold04 on 2009-04-22
I'm wondering if the DVD of Ubuntu includes all of the packages in the repos when downloaded.  That way I can install other apps I need offline.

---

### Post by adamitj on 2009-04-22
> **MysticGold04 said:**
> I'm wondering if the DVD of Ubuntu includes all of the packages in the repos when downloaded.  That way I can install other apps I need offline.

Unfortunately, no. DVD includes only extra packages for language support. You still need to download applications from repositories.

However, you can create a single "apt-get install" command line (or in a executable script file) to install all applications you need. So, after a successful installation in one computer, you can copy the directory /var/cache/apt/archives to other machine, and use the same script.

Every package downloaded with apt-get, aptitude or Synaptic are maintained in cache until you clean it.

---

### Post by MysticGold04 on 2009-04-22
I'll look into doing that, thanks! :)

---

### Post by cariboo on 2009-04-22
The dvd does include both the Live and Alternate installations.

---

