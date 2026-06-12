---
title: "xfig related"
date: 2005-11-29
forum: General Help
---

### Post by melgrim on 2005-11-29
Hi,

I need do install **xfig** in my machine but can't find it with synaptic.
Can anyone tell me where can I find a repository with the package?

---

### Post by Xian on 2005-11-29
It's in the Breezy Universe repos:

```
$ apt-cache policy xfig
xfig:
  Installed: (none)
  Candidate: 1:3.2.5-alpha5-4
  Version table:
     1:3.2.5-alpha5-4 0
        500 http://archive.ubuntu.com breezy/universe Packages
```

---

### Post by melgrim on 2005-12-04
Thanks.

I would expect that to be one of the default repositories. It looks like it isn't. Maybe it's because I installed Ubuntu in portuguese and so my default repositories are [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) ...

Anyway it's working now...

---

