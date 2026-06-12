---
title: "Updater doesn't update anymore"
date: 2009-10-12
forum: Installation &amp; Upgrades
---

### Post by pchtsp on 2009-10-12
Hi, 
 
I installed Ubuntu netbook remix 9.04 (jaunty) in my netbook 2 days ago and somehow closed the updating manager when installing a hole bunch of updates. Later, when i opened the updater it said i needed to run "dpkg --configure -a" in terminal, whch i did. Then, when i tried to install the missing software it starts with a half-downloaded file named openoffice.org-emailmerge 1:3.0.1-9ubuntu3.1 and is stays there and crashes. It has also crashed installing openoffice.org-calc 1:3.0.1-9ubuntu3. Is the problem openoffice? What ca i do? I can't install anything while having this problem... because the updater or terminal always starts installing this incompleted packages.

I need help here, I'm not new with ubuntu but i consider myself a beginner.

Thanks

---

### Post by zvacet on 2009-10-13
```
sudo dpkg --configure -a
```

---

