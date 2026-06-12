---
title: "No desktop effects on Dell D620 under Lucid"
date: 2010-06-01
forum: Hardware
---

### Post by d620_user on 2010-06-01
I can't seem to get desktop effects working on my Dell D620 laptop.

I don't think it has the NVidia chip, just the basic Intel graphics, so I'm wondering if it's even possible to get this stuff working.

Can someone help or at least get me pointed  in the right direction on how to solve this issue?

---

### Post by Yellow Pasque on 2010-06-01
To start, post output of these commands:
```
compiz --replace
LIBGL_DEBUG=verbose glxinfo
```

---

