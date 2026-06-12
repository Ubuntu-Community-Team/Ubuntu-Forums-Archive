---
title: "[SOLVED] Can't install updates in Hardy..."
date: 2008-07-12
forum: General Help
---

### Post by Jordinho on 2008-07-12
When I try to install openoffice.org (which is in my update manager) I get this message:

```
E: /var/cache/apt/archives/openoffice.org-help-en-us_1%3a2.4.1-1ubuntu2_all.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/openoffice/help/en/scalc.idx/POSITIONS')
```

What exactly does that mean?

---

### Post by rraj.be on 2008-07-13
Try this
```
apt-get clean 
```

then try re installation

I think you haven't downloaded the package completely

---

### Post by Jordinho on 2008-07-13
Worked. Thanks!

---

