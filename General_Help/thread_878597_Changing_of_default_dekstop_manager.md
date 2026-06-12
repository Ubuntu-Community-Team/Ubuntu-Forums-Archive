---
title: "Changing of default dekstop manager"
date: 2008-08-03
forum: General Help
---

### Post by SandyM on 2008-08-03
Hello ! I was using GNOME dekstop and loving every bit of it but then I just got attracted by the hype created by new KDE 4.1 and decided to try it.

THE ONLY BLUNDER I did was that , when asked about my default Desktop Manager I checked KDM instead of GDM . Now I am facing the consequences as many old terminal commands are not working with KDM. 

Now I want to resort to GDM but doesn't know how.I even downloaded an application 'Startup Manager' but it is not working as well.

PLEASE HELP !!!!!! as I desperately want GDM back.

---

### Post by billgoldberg on 2008-08-03
Use this command

```
sudo dpkg-reconfigure gdm
```

Then a box will appear asking if you want to use gdm or kdm.

---

