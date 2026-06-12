---
title: "Synaptic"
date: 2008-11-26
forum: General Help
---

### Post by djframes on 2008-11-26
Synaptic shows this error every time I try to install Wacom tools or Xsane:

E: /var/cache/apt/archives/xsane-common_0.995-6_all.deb: trying to overwrite `/usr/share/doc/xsane-common/html/sane-problems-doc.html', which is also in package xsane-doc

Fix Broken packages does nothing any ideas?

---

### Post by taurus on 2008-11-26
Close down synaptic.  Then, open a terminal and try to fix the broken package with

```
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
```

---

### Post by djframes on 2008-11-27
Thank you, Taurus - This seems to work although Synaptic still reports the same error when I try to install Wacom Tools. At the bottom it says no broken installations but says one to install or upgrade even though all seem installed.

---

### Post by djframes on 2008-11-27
Sorry, no it didn't fix it I misread the message at the bottom. Still one broken- Xsane.  Reinstall throws up the original error.

---

