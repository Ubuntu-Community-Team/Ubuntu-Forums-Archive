---
title: "Uninstalling Kubuntu and Xubuntu"
date: 2008-11-22
forum: General Help
---

### Post by rmcellig on 2008-11-22
I am running Ubuntu 8.10. I decided to try out Xubuntu and Kubuntu. I installed them both, tried them out and would now like to completely uninstall them.

How do I do this?

---

### Post by taurus on 2008-11-22
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by beno1990 on 2008-11-22
Just repartition the partitions each distro is installed to and then remove them from your /boot/grub/menu.lst options.

**NOTE:** Editing your GRUB options is dangerous
**NOTE 2:** Ensure you don't repartition the drive/partition which GRUB is installed to.

(This assumes you're uninstalling completely different OS installations, not just the desktop environments)

---

