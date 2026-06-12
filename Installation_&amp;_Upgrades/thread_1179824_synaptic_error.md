---
title: "synaptic error"
date: 2009-06-06
forum: Installation &amp; Upgrades
---

### Post by Bigneil on 2009-06-06
when i download something from the repository or install updates i recieve this error message, after i click the close button the program still downloads and installs, but i find it worrying none the less.

any ideas?

---

### Post by Partyboi2 on 2009-06-06
Hi, you seem to have a duplicate entry in your sources.list, you will need to remove the duplicate entry which is the deb [http://archieve.canonical.com](http://archieve.canonical.com) entry. If you are unsure how to remove the entry open a terminal and post the output to
```
cat /etc/apt/sources.list
```

---

