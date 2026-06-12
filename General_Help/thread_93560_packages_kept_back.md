---
title: "packages kept back"
date: 2005-11-22
forum: General Help
---

### Post by Zelut on 2005-11-22
I'm trying to upgrade my server-only install via apt-get and its telling me that the newly released kernel upgrade is 'being held back' or 'two packages not upgraded'.  I've tried apt-get -f install but that doesn't 'fix' it.

Can someone tell me how to fix this via the prompt as I don't have gnome, synaptec or 'smart upgrade'.

Thanks in advance.

---

### Post by kalin on 2005-11-22
Try using "apt-get dist-upgrade". Be careful what it asks you though, it probably needs to remove some packages in order to upgrade properly.

---

