---
title: "Software sources error... help"
date: 2009-07-23
forum: Installation &amp; Upgrades
---

### Post by goldenboy1 on 2009-07-23
This is what I got when I tried to enable multiuniverse.  I am a newbe so only know how to open the terminal and will need specific steps to type to fix this..



E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report

Cheers,  Chris

---

### Post by Sub101 on 2009-07-23
Have you run: 

```
dpkg --configure -a
```

as it asks?

---

### Post by wojox on 2009-07-23
Open Terminal:

```
sudo dpkg --configure -a
```

---

### Post by goldenboy1 on 2009-07-23
Thanks the sudo one worked!

---

