---
title: "setting path to other version of program"
date: 2008-10-14
forum: General Help
---

### Post by falkenberg_cph on 2008-10-14
Hi
I have 2 version of Prolog installed on my system. Unfortunately one of them is a version without chr, and i would really like to uninstall this version. I can't so instead i want to make Ubuntu point to the newest version, so that whenever i write "pl" in terminal the newest Prolog version is started.

How do i go about doing that?
The paths are like this:
:/usr/local/lib/pl-5.6.59$
:/usr/local/lib/pl-5.6.61$

Thank you
Carsten

---

### Post by justleen on 2008-10-14
i'd create an alias in my .bashrc
```

cd
gedit .bashrc
#add a line:
alias pl='/usr/local/lib/pl-5.6.61/pl'
#save and close

```

---

