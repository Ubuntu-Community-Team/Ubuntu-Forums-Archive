---
title: "in terminal how do you fix?"
date: 2008-09-02
forum: General Help
---

### Post by sourlemonhead on 2008-09-02
gabrielle@gabrielle-desktop:~$ sudo apt-get update
E: Type 'fishmanic20' is not known on line 56 in source list /etc/apt/sources.list

---

### Post by signifer123 on 2008-09-02
```
sudo vim /etc/apt/sources.list +56
```

Add a # to the beggining of the line that starts with fishmanic20 (Press Insert, Home, Shift + 3, Escape, :, w, q, Enter)


Or use whatever editor you prefer, it just is complaining because that line(56) is setup wrong.

---

### Post by oldos2er on 2008-09-02
> **sourlemonhead said:**
> gabrielle@gabrielle-desktop:~$ sudo apt-get update
E: Type 'fishmanic20' is not known on line 56 in source list /etc/apt/sources.list

 gedit is more newbie-friendly than vim. Use "gksudo gedit /etc/apt/sources.list" and fix line 56.

---

### Post by sourlemonhead on 2008-09-02
okay that seem to do the trick thanks for the help:)

---

