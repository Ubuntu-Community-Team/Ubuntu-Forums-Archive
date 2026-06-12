---
title: "[SOLVED] Firefox Profile manager not working - intrepid"
date: 2008-11-26
forum: General Help
---

### Post by suffer1989 on 2008-11-26
Hey, whenever i type ```
firefox -profilemanager
``` into terminal, it only launches a new firefox window. how do i get the profilemanager to work ?

Im using Firefox 3.04

---

### Post by suffer1989 on 2008-11-26
Figiured it out : i need to use 
```
firefox -no-remote -P
```

---

### Post by sstusick on 2008-11-26
Please mark the thread as solved if you have *solved* the problem. 

Glad you figured it out!

---

### Post by poebae on 2008-11-26
As with all things Linux, it's case-sensitive

```
firefox -ProfileManager
```

should work.

Firstly make sure that Firefox is not running, and that there are no firefox processes running in System Monitor.

---

### Post by praveensleeps on 2010-05-23
hey Thanks it works !
May i know why  firefox -ProfileManager  doesnt work for profiles in Lucid Lynx ?

---

