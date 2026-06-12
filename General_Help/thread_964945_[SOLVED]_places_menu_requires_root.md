---
title: "[SOLVED] places menu requires root"
date: 2008-10-31
forum: General Help
---

### Post by lordcap90 on 2008-10-31
I just upgraded to Intrepid from hardy. Everything seems to be working fine, except that to open a folder from the places menu, a password prompt comes up. anyway to disable this because i don't need root for most file operations :).

---

### Post by lordcap90 on 2008-11-02
is there a conf file i have to edit.

---

### Post by lordcap90 on 2008-11-04
Fixed it, for future reference, I went to Places > Computer, right clicked on Filesystem, selected Properties, went to the Open With tab and found out that it was set to gksudo instead of Open Folder.

---

