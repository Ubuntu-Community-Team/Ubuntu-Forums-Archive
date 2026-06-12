---
title: "I want to install Banshee!!"
date: 2008-09-30
forum: General Help
---

### Post by iampriteshdesai on 2008-09-30
Hi!
I tried to install Banshee 1.2 and sucessfully added the repositorys but when I try to Apply changes. I get the error:
banshee-1:
  Depends: libboo2.0-cil (>=0.8.1.2865) but 0.8.0.2730-5 is to be installed
  Depends: libpango1.0-0 (>=1.20.5) but 1.20.1-1 is to be installed
What to do?

---

### Post by Ryadt on 2008-09-30
> **iampriteshdesai said:**
> Hi!
I tried to install Banshee 1.2 and sucessfully added the repositorys but when I try to Apply changes. I get the error:
banshee-1:
  Depends: libboo2.0-cil (>=0.8.1.2865) but 0.8.0.2730-5 is to be installed
  Depends: libpango1.0-0 (>=1.20.5) but 1.20.1-1 is to be installed
What to do?

Try to see if you have got backports update enabled. Go in the repositories (System > Administration > Software sources). Under the update tab uncheck the 'Unsupported updates (hardy-backports)'.

Then do```
sudo apt-get update
```

Try to reinstall after that.

---

### Post by zvacet on 2008-09-30
It looks like the Banshee 1.2 is Interpid package,so that is the reason you can not install it.

---

### Post by Nepherte on 2008-09-30
[https://edge.launchpad.net/~banshee-team/+archive](https://edge.launchpad.net/~banshee-team/+archive)

---

