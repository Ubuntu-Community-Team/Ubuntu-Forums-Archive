---
title: "yahoo messenger not working"
date: 2008-07-12
forum: General Help
---

### Post by sacsha30 on 2008-07-12
Hi all

I am facing problem installing yahoo messenger. When I try to install it says:

[COLOR="Red"]Unpacking ymessenger (from .../ymessenger_1.0.4_1_i386.deb) ...
dpkg: dependency problems prevent configuration of ymessenger:
 ymessenger depends on libglib1.2 (>= 1.2.0); however:
  Package libglib1.2 is not installed.
 ymessenger depends on libssl0.9.6; however:
  Package libssl0.9.6 is not installed.
 ymessenger depends on xlibs (>> 3.3.6); however:
  Package xlibs is not installed.
dpkg: error processing ymessenger (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ymessenger[/COLOR]

and when I try to install these libraries, it says no such library or cant be installed.

Please suggest.

Regards
Sac

---

### Post by dracayr on 2008-07-12
try using aptitude instead of apt-get

dracayr

---

### Post by jonlemur on 2008-07-12
Try ```
sudo apt-get install libglib-2.0-0 libssl0.9.8
```
Or search for them in synaptic.  I don't know about xlibs.  Maybe the xlibs-static-dev?

---

### Post by ubanchaos on 2008-07-12
dude just just use pidgin instant messenger...it works with alot of different instant messenger

---

### Post by dexter.deepak on 2008-07-12
have you enabled all your repositories (main,universe,etc.)? you need to enable the repositories in order to install the missing dependencies.

even i would sugggest you ...its better to go for pidgin

---

