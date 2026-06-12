---
title: "dpkg errors"
date: 2008-10-08
forum: General Help
---

### Post by kktaus on 2008-10-08
I've recently setup an environment on Unbuntu for Plone 3.0 that includes Python 2.4. I get the errors below when doing various things with apt-get like 'install python'. Is there some configuration that needs to be done as the message suggests? Thanks in advance.

dpkg: error processing python-setuptools (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-paste:
 python-paste depends on python-setuptools (>= 0.6b3-1); however:
  Package python-setuptools is not configured yet.
dpkg: error processing python-paste (--configure):inst
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-pastedeploy:
 python-pastedeploy depends on python-setuptools (>= 0.6b3-1); however:
  Package python-setuptools is not configured yet.
dpkg: error processing python-pastedeploy (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-pastescript:
 python-pastescript depends on python-paste (>= 1.6-1); however:
  Package python-paste is not configured yet.
 python-pastescript depends on python-pastedeploy (>= 1.3.1-2); however:
  Package python-pastedeploy is not configured yet.
 python-pastescript depends on python-setuptools (>= 0.6b3-1); however:
  Package python-setuptools is not configured yet.
dpkg: error processing python-pastescript (--configure):
 dependency problems - leaving unconfigured

Errors were encountered while processing:
 python-setuptools
 python-paste
 python-pastedeploy
 python-pastescript

-kkt

---

### Post by Pro-reason on 2008-10-09
Try getting rid of them and reloading the package list.

```
sudo apt-get -f remove python-setuptools python-paste python-pastescript python-pastedeploy
sudo apt-get update
sudo apt-get install python-setuptools

```

---

### Post by kktaus on 2008-10-09
It worked!! Thank you very much.

-kkt

---

