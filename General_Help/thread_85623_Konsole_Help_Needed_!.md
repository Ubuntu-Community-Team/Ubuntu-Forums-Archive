---
title: "Konsole Help Needed !"
date: 2005-11-03
forum: General Help
---

### Post by soib on 2005-11-03
New to Kubuntu 5.10 after Fedora. Managed to get Konsole to do "configure", But unable to get it to do "make" and "make install"  to install new programs, all help appreciated !

---

### Post by niko_ on 2005-11-03
what kind of errors you get after make?
if i understand you right, you want to install Konsole program? then just use: sudo apt-get install konsole

---

### Post by soib on 2005-11-03
thanks Niko, I have Konsole installed, But i want to install other KDE programs from "Source" , ive done it heaps in the Gedit console NP'
but it wont do it in konsole even as #root. yes ive used aept but the programs i wantto install are from Kde-apps.org .

---

### Post by GoldBuggie on 2005-11-03
Have you installed "build-essential"????
```

sudo apt-get install build-essential
```

---

### Post by dodger on 2005-11-03
[QUOTE=GoldBuggie]Have you installed "build-essential"????
```

sudo apt-get install build-essential
```[/QUOTE]

yep, I would also guess that that's what's causing your problem.

---

