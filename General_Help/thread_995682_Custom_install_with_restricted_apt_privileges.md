---
title: "Custom install with restricted apt privileges"
date: 2008-11-28
forum: General Help
---

### Post by early_adopter on 2008-11-28
I'm looking for advice or pointers on making a custom Ubuntu install which could readily be applied to a number of PCs.

The users should have limited rights to use apt to install packages from a given repository (but not from any repository).  The given repository will contain a partial mirror of an Ubuntu release.

The intention here is that users be allowed to install "userspace" packages such as a browser or a media player but not "system level" packages such as web servers, window managers and such.

The distinction is artificial to some extent but I'm hoping to find a way to allow non-privileged users to install and try out packages for themselves.

---

### Post by inobe on 2008-11-28
administration>users and groups

much can be done within the user properties.

---

