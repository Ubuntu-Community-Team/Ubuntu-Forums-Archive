---
title: "Non-essential home folder contents?"
date: 2008-12-20
forum: Installation &amp; Upgrades
---

### Post by melat0nin on 2008-12-20
Hello all

I have an Ubuntu installation which has become a little corrupt, which I would like to reinstall.  I have a separate home partition however, with my documents on it.

I'd like to clear out all the configuration stuff from the home folder, leaving just my documents, so when I reinstall Ubuntu and tell it to use the partition as my home folder, the existing broken settings won't be used and new ones will be created instead.

On that basis, what can I delete from my home folder which is just settings etc, leaving just my documents?

---

### Post by taurus on 2008-12-20
All those directories with a . in front.

```
ls -la ~
```

---

