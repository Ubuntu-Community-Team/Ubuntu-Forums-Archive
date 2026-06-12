---
title: "Edit PATH"
date: 2009-08-10
forum: Installation &amp; Upgrades
---

### Post by MauserM98 on 2009-08-10
How do I edit Path?
I put a complex command inside a textfile that is executable and I wan't this file to work regardless of whom the user might be (root, me , someone).
I put the file in /usr/sbin since $PATH gave me that option but I guess that is not an ideal place.

Thanx in advance

---

### Post by slakkie on 2009-08-10
Per user basis:

edit your shellrc (eg .bashrc/.zshrc):

export PATH=$PATH:/path/to/dir

---

