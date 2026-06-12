---
title: "ubuntu 9.04 with kde3.5"
date: 2009-07-07
forum: Installation &amp; Upgrades
---

### Post by mkrahmeh on 2009-07-07
gurus
the kubuntu 9.04 comes with kde 4 by default, can i use ubuntu 9.04 with kde 3.5 desktop ?
thx

---

### Post by meindian523 on 2009-07-07
I don't think so.I installed kubuntu-desktop meta package and got KDE4.2.2.How I long for KDE4-.....

edit:and did I mention KDE4.2.2 totally sucks and is so full of bloat you ought to invent a new word beyond obese for it?

---

### Post by mkrahmeh on 2009-07-07
> **meindian523 said:**
> I don't think so.I installed kubuntu-desktop meta package and got KDE4.2.2.How I long for KDE4-.....

edit:and did I mention KDE4.2.2 totally sucks and is so full of bloat you ought to invent a new word beyond obese for it?

+1

anyway, should've looked around before posting, coz the good news is that you can install kde3.5 on 8.10 and above..
[*http://apt.pearsoncomputing.net/install.html*]("http://apt.pearsoncomputing.net/install.html")

am working on it at the moment, i'll let you know if it works

---

### Post by meindian523 on 2009-07-07
yeah,that should work out.PPA's satisfy those who are not happy with "progress" on the DEs,or any other package for that matter.

---

### Post by mkrahmeh on 2009-07-07
as a conjecture, the package kubuntu-desktop-kde3 refers to kde3, and the package kubuntu-desktop refers to kde4, dont know if its safe to remove the kubuntu-desktop package after installing kubuntu-desktop-kde3, there might be some shared libs or so..what do you think ?

---

### Post by mkrahmeh on 2009-07-07
its working fine, i also uninstalled (but without purging) the kubuntu-desktop package, but when i choose kdm session at the login screen, kde4 is still there !!

---

### Post by meindian523 on 2009-07-07
you probably need to purge the files.Shared libs will be reinstalled,because nobody's expecting you to try KDE4+ first and then try KDE3.They can't depend on the libs being there,so I should say you can purge the kubuntu-desktop package.

---

