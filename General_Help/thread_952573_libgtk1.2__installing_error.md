---
title: "libgtk1.2  installing error"
date: 2008-10-19
forum: General Help
---

### Post by namaster on 2008-10-19
sudo apt-get install libgtk1.2
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Any idea how to fix it? I have no idea what it means.

Also, is it after update 8.0.4.1 u get .21 and .19 kernel options in the boot menu while booting?

---

### Post by Ryadt on 2008-10-19
Try closing any other package manager you've got open, synaptic or update manager.
Then retry to install.

---

### Post by northern lights on 2008-10-19
You've got another application accessing /var/lib/dpkg/.

Make sure there's no instance of synaptic or update manager running. Also, aptitude, apt-get or dpkg would lock the directory if invoked from another shell or terminal instance.

---

