---
title: "[SOLVED] Problem with synaptic"
date: 2008-10-13
forum: General Help
---

### Post by N4zgu1 on 2008-10-13
When I try to install a program with the Terminal or Syanptic I got this message:


```
E: The package index files are corrupted. No Filename: field for package libsnack2.
```

---

### Post by Pro-reason on 2008-10-14
Try this:

```

sudo apt-get -f remove libsnack2

```

What’s the output?

---

