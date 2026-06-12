---
title: "Problem with gdebi-kde on Kubuntu 8.04"
date: 2008-10-11
forum: General Help
---

### Post by matrix14 on 2008-10-11
Dear guys,

I just installed Kubuntu 8.04 on two of my PC's. The installation fully success and my new Kubuntu seem runing well.
Just few hours I run it and tested, then I try to install new package, GPL EDA and its dependencies. But what's going on???
After some dependencies I installed but then gdebi-kde causes error: my PC seem run too busy with high CPU and memory usage then gdebi-kde stop unexpectedly. In such circumstance, the package fail to install.

I am not sure that GPL EDA or its dependencies just caused the error.

I try to find what really cause is, I go to folder /usr/bin then I try to view gdebi-kde.py with use kate and I found something strength like:

```
data="/usr/share/python/gdebi"
```

Such code seem point to a missing directory, 'cause when I locate in /usr/share just not found. I don't really understand whether that is a cause of such error or maybe any other causes which triggered such error.

Such error also occurred to another one of my PC's wich also installed with Kubuntu 8.04; such error occurred even when I try to install different program with off course have different dependencies.

Perhaps you guys can help to solve this problem or inform what should I do. 

Thank you.

---

