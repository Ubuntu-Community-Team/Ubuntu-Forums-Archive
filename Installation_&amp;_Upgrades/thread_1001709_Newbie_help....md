---
title: "Newbie help..."
date: 2008-12-04
forum: Installation &amp; Upgrades
---

### Post by Newbie420 on 2008-12-04
Ok, as you see by the nick I chose, I'm a newbie. We all gotta learn somewhere, I'm currently in school for programming, and have dabbled with linux, but that dabbling is very limited. Any threads for us newb's to help us with the transition from Windows to Ubuntu. Ok so here's my issue..

I downloaded and installed the latest version of Apache, and I downloaded PHP 5. So here's my question, before I had installed the downloaded apache, I used 'apt-get install' but it wasn't apache, is was something like apache-dev or something. So now, I have two copies of Apache running. How can I distinguish the two copies, and remove the unwanted one?

Thanks guy/gals for any help.

---

### Post by pennacook on 2008-12-04
You should be able to discover what is installed by running:
```
dpkg -l |grep apache
```
Typically apache-dev is to make your own apache, not a separate apache install.

---

### Post by Newbie420 on 2008-12-04
> **pennacook said:**
> You should be able to discover what is installed by running:
```
dpkg -l |grep apache
```
Typically apache-dev is to make your own apache, not a separate apache install.

Thanks for that pennacook, It helped alot!

---

