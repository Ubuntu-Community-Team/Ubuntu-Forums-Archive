---
title: "gksudo and sudo?"
date: 2008-09-22
forum: General Help
---

### Post by Monotoko on 2008-09-22
can someone explain the differance between those two please? never had any idea...

---

### Post by qstraza on 2008-09-22
well gksudo is not installed by default

---

### Post by hyper_ch on 2008-09-22
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

and gksudo is installed by default.

---

### Post by qstraza on 2008-09-22
well that explains why i dont have it.
I checked on ubuntu server and kubuntu... ;)

---

### Post by aysiu on 2008-09-22
Kubuntu uses *kdesu* instead of *gksudo*

---

### Post by qstraza on 2008-09-22
nice to know, i prefer text only... ;>

---

### Post by oldos2er on 2008-09-22
> **qstraza said:**
> well that explains why i dont have it.
I checked on ubuntu server and kubuntu... ;)

 Ubuntu server is CLI, so won't have any graphical apps; and as aysiu said, Kubuntu would need kdesu instead of the Gnome-specific command gksudo. This should answer your original question: [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

---

### Post by mb_webguy on 2008-09-22
> **Monotoko said:**
> can someone explain the differance between those two please? never had any idea...

In a nutshell, gksu (or gksudo, which in Ubuntu is an alias for gksu) or kdesu (if you're using KDE) are for GUI applications, while sudo is for command-line applications.  The link posted by hyper_ch and oldos2er does a very good job of explaining the two.

If you want a concrete and visible example, try running Firefox using sudo and then using gksu.  If you use sudo, it runs with root privileges, but with your profile (and consequentally refuses to start if you're already running Firefox).  If you run Firefox with gksu, however, it not only runs with root privileges, but runs AS root, with root's profile (as it should).

Conversely, you also don't want to run command-line applications using gksu.  While the applications may run as expected, since gksu is expecting a GUI application, your screen may occasionally do funky things, like not recovering completely from the dimming effect of the gksu prompt.

---

