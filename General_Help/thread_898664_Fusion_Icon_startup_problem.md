---
title: "Fusion Icon startup problem"
date: 2008-08-23
forum: General Help
---

### Post by biszkopt on 2008-08-23
Hi, i have a little problem: i installed fusion icon, and add it to startup but when system turns on fusion-icon comes up but there is no desktop effects, and every time computer restart i have to manually right-click on fusion icon and set Select Window Manager -> Compiz. What is strange that this option is shown as enabled but before i click on it there is no desktop effects. Please help!

---

### Post by wishyjr on 2008-08-25
ive got this problem too. But i think that it's compiz that isn't starting on startup. 

Is there a way to add compiz (or a specific related process/program etc.) into the startup programs list?

---

### Post by wishyjr on 2008-08-25
Solution!

In order to use Compiz as your default window manager, all you have to do is go to System &#8594; Preferences &#8594; Sessions &#8594; Startup Programs. Then add ```
compiz --replace
```

Wishy.

---

