---
title: "Newbie, help with dpkg command"
date: 2008-11-01
forum: General Help
---

### Post by nbtrap on 2008-11-01
If I want to uninstall a program not part of the repositories (i.e. I can't just use apt-get remove or synaptic), I would use dpkg -r or dpkg --purge.

My question is, say I've installed packages x, y & z to run program P, and now I want to uninstall P.  If I use dpkg --purge P, I'll get a message saying that x, y and/or z depend on P.  Is there a command that removes a package as well as all packages that depend on it, without uninstalling each package individually (since the lists can get pretty big)?  If not, is there a way to find out the names of all the packages installed together with P?

---

