---
title: "Using Metacity theme and Compiz-Fusion"
date: 2008-08-25
forum: General Help
---

### Post by noper2 on 2008-08-25
I was wondering if there is an easy way to use a metacity theme for window borders and the effects from compiz-fusion at the same time. Whenever I do "metacity --replace", all of my compiz effects go away. In particular, I'm trying to use the new ["Dust-0" theme]("http://www.geocities.com/kid_orig/themer/Dust-0.tar.gz").

---

### Post by sayakb on 2008-08-25
> **noper2 said:**
> I was wondering if there is an easy way to use a metacity theme for window borders and the effects from compiz-fusion at the same time. Whenever I do "metacity --replace", all of my compiz effects go away. In particular, I'm trying to use the new ["Dust-0" theme]("http://www.geocities.com/kid_orig/themer/Dust-0.tar.gz").

Instead of **metacity --replace**, do
```
gtk-window-decorator --replace
```

---

### Post by noper2 on 2008-08-25
Thanks! That was exactly what I was looking for.

---

