---
title: "kdocker doesn't work with prism?"
date: 2008-09-18
forum: General Help
---

### Post by moore.bryan on 2008-09-18
i just installed prism and a few of its google components to play with... then i realized prism seems to ignore kdocker:
```
kdocker prism-google-docs
``` doesn't give me anything. any ideas?

---

### Post by bigcrunch on 2009-05-20
> **moore.bryan said:**
> i just installed prism and a few of its google components to play with... then i realized prism seems to ignore kdocker:
```
kdocker prism-google-docs
``` doesn't give me anything. any ideas?

Hi, I had the same problem but I solved with this trick:

```
prism-google-mail&pause 1;kdocker -b -f& 
```

---

### Post by moore.bryan on 2009-05-20
i thought this thread was dead! interesting solution... is this from startup or just run in term?

---

