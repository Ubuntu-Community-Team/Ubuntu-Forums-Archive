---
title: "[SOLVED] No Intrepid Updates"
date: 2008-11-03
forum: General Help
---

### Post by Kevbert on 2008-11-03
I've been using Intrepid since the Alpha releases and have 2.6.27-7 pre-release on my PC (updates up to 28/10/08). Have there been any newly released updates since then ?  I'm getting all the development emails but have not downloaded any updates since 28/10/08.

---

### Post by tuxxy on 2008-11-03
There was updates on the 30th im sure for final release speicfically linux headers, have you checked for updates using update manager > check

---

### Post by Kevbert on 2008-11-03
Hi Tuxxy. I've used the equivalent from the command line:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
This occurs both in Kubuntu and Ubuntu.

---

### Post by Kevbert on 2008-11-04
Resolved the problem by installing the full release of Intrepid instead of trying to update the RC/Beta version. Immediately I had seven new updates. There must be a problem updating to the full release. I've looked at the package revisions between pre and full release and nothing is immediately obvious.

---

