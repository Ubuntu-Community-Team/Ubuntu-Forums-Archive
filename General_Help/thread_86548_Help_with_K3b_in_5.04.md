---
title: "Help with K3b in 5.04"
date: 2005-11-05
forum: General Help
---

### Post by EvilBill on 2005-11-05
I have K3b installed.
I learned how to find it.

Now it says that I need "cdrdao package" in order for it to work.:???: 

 I cannot find this. Does anyone know where it is, or how I can get this K3b to work. I just want to be able to burn the 5.10 iso so I can upgrade.

---

### Post by Remmelas on 2005-11-05
easier to upgrade by editing /etc/apt/sources.list and changing all references to hoary to breezy
then sudo apt-get dist-upgrade
not sure why you aren't seeing the cdrdao package though, apt-cache search cdrdao finds it right off for me(but i'm already on breezy).

---

