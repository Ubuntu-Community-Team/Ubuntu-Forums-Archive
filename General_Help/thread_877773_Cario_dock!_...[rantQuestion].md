---
title: "Cario dock! ...[rant/Question]"
date: 2008-08-02
forum: General Help
---

### Post by Kaneda187 on 2008-08-02
Okay I was looking around for a new dock cuz my friends got a mac book i was messing around with last night and above everything on it i like the dock the most! so i began to think ther must something like that on ubuntu and yes ther is loads of docks kiba probably being my fav( its fun flinging you icons round the desktop) i tried awn but i think its a bit boring then i came across cario dock! why would they(the people who developed it) release such an unstable dock? i installed it and thought Oh this looks nice....WRONG! then tried to change the themes the whole thing froze up! this is within less then three mins of use! C'mon guys you cant release something that UNstable then type stable after it.....Its NOT!!! dont kid yourself!! nice idea though!

am can anyone help me totally remove this cario thing off my laptop?? thanks in advance!

---

### Post by powerpleb on 2008-08-02
> **Kaneda187 said:**
> 
am can anyone help me totally remove this cario thing off my laptop?? thanks in advance!
How did you install it?

---

### Post by Kaneda187 on 2008-08-02
it comes in two files plugins and the dock its self they were both .deb files....

---

### Post by powerpleb on 2008-08-02
> **Kaneda187 said:**
> it comes in two files plugins and the dock its self they were both .deb files....

```
sudo dpkg -P cairo-dock cairo-dock-plugins
```
If that doesn't work do:```
sudo dpkg -l cairo*
```
and see what the packages are called

---

### Post by Kaneda187 on 2008-08-02
kaneda@kanedas-interface:~$ sudo dpkg -l *cairo*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ri  cairo-dock     1.6.1.2        A light and eye-candy dock to launch your pr
ii  cairo-dock-plu 1.6.1.2        A collection of official plug-ins and applet
un  libcairo       <none>         (no description available)
ii  libcairo-perl  1.043-1        Perl interface to the Cairo graphics library
un  libcairo0.5.1  <none>         (no description available)
un  libcairo0.6.0  <none>         (no description available)
un  libcairo0.9.0  <none>         (no description available)
un  libcairo1      <none>         (no description available)
ii  libcairo2      1.6.0-0ubuntu2 The Cairo 2D vector graphics library
un  libcairomm-1.0 <none>         (no description available)
ii  libcairomm-1.0 1.4.2-1        C++ wrappers for Cairo (shared libraries)
ii  libmono-cairo1 1.2.6+dfsg-6ub Mono Cairo library
ii  libmono-cairo2 1.2.6+dfsg-6ub Mono Cairo library
ii  python-cairo   1.4.0-2ubuntu2 Python bindings for the Cairo vector graphic
un  python2.3-cair <none>         (no description available)
un  python2.4-cair <none>         (no description available)
un  python2.5-cair <none>         (no description available)
kaneda@kanedas-interface:~$

---

### Post by powerpleb on 2008-08-02
The plugins are still installed...
Try this:
```
sudo dpkg -P cairo-dock-plug-ins cairo-dock

```

To-many-hyphens

---

### Post by Kaneda187 on 2008-08-02
kaneda@kanedas-interface:~$ sudo dpkg -l cairo*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
pn  cairo-dock     <none>         (no description available)
pn  cairo-dock-plu <none>         (no description available)


success!!!.....I think??

---

### Post by powerpleb on 2008-08-02
Yup, both are toast.

---

### Post by Kaneda187 on 2008-08-02
thanks dude!! :D

---

