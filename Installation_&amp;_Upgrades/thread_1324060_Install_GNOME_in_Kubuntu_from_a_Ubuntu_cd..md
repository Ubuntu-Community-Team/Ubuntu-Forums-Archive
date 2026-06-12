---
title: "Install GNOME in Kubuntu from a Ubuntu cd."
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by kio_http on 2009-11-12
Is there any way to install ubuntu-desktop using the desktop cd of Ubuntu karmic. (To be installed to Kbuuntu Karmic)

---

### Post by aysiu on 2009-11-12
> **kio_http said:**
> Is there any way to install ubuntu-desktop using the desktop cd of Ubuntu karmic. (To be installed to Kbuuntu Karmic)
Yes. If you use the Ubuntu Karmic **Alternate** CD, you can add the CD-ROM as an apt source using either Synaptic Package Manager or [the terminal](http://www.psychocats.net/ubuntu/terminal) command ```
sudo apt-cdrom add
``` After that, you can install the *ubuntu-desktop* metapackage.

This will **not** work for the Ubuntu Desktop CD. It will work for only the Ubuntu Alternate CD.

---

### Post by kio_http on 2009-11-12
> **aysiu said:**
> 

This will **not** work for the Ubuntu Desktop CD. It will work for only the Ubuntu Alternate CD.

Thanks just needed to confirm this actually. Knew it would work with alternate because of .deb files.

I was just wondering if it was possible to copy out and intalled GNOME from the desktop live cd.

---

### Post by aysiu on 2009-11-12
> **kio_http said:**
> Thanks just needed to confirm this actually. Knew it would work with alternate because of .deb files.

I was just wondering if it was possible to copy out and intalled GNOME from the desktop live cd.
No. There are a few random .deb files on the Desktop CD but not for the Gnome desktop environment.

The Gnome on the live CD that "installs" actually is just a squashed image that gets copied over. A small handful of .deb files get added during the installation process sometimes for hardware drivers or for localization.

---

