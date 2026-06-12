---
title: "Installing a bare minimum system"
date: 2009-06-29
forum: Installation &amp; Upgrades
---

### Post by kristian on 2009-06-29
I'm wondering how to get rid of all the unneeded packages that always gets installed with ubuntu. I've set up a netboot installer with a preseed file but I can't seem to find a way to get rid of packages that gets pulled in as part of the base system.

Does anyone know how to choose which packages the base system should depend upon?

Sure I can remove the packages after the installation but it's quite the pain to do this for each server we install.

Thanks in advance.

---

### Post by Revolutionary101 on 2009-06-29
If you are looking for a bare minimum install, I suggest installing xubuntu instead of ubuntu.

---

### Post by mikewhatever on 2009-06-29
Try installing ubuntu-minimal metapackage. You'll end up with a CLI system of about 450 MB. I don't know if you can get leaner then that with Ubuntu by pulling packages from the repositories. If you want GUI, go ahead and install gdm, xorg and lxde.

---

### Post by kristian on 2009-06-30
Thanks for your replies. However I'm looking for something more along the lines of the debian potato installation of 8mb.

---

