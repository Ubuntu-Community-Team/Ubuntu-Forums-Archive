---
title: "How to access NTFS partition"
date: 2008-01-25
forum: Hardware &amp; Laptops
---

### Post by kosmonov on 2008-01-25
hi guys..iam new to linux and i've enjoyed the experience with ubuntu so far..i have two doubts..the first being is there any option to access the windows partition when its been hibernated and my second doubt being one that of java..Though i've installed java runtime on my ubuntu i cant access java webpages..what should i do..thx 4 ur help..cheers

---

### Post by mexpolk on 2008-01-25
* Hibernated NTFS patirion mount:

When you hibernate your NTFS partition you can't unless you force the mount, wich can cause a data corruption.

To do so, you must add the parameter --force to the mount command.

* Java:

To be able to see java content on firefox use the following command:

```
sudo apt-get install sun-java6-plugin
```

Best...

---

