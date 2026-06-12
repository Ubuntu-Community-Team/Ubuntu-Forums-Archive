---
title: "Trouble installing Looking Glass app"
date: 2009-01-25
forum: Installation &amp; Upgrades
---

### Post by Adali on 2009-01-25
Hi am have problems installing Looking Glass. I get the following output from the terminal:
sudo apt-get install lg3d-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lg3d-core is already the newest version.
The following packages were automatically installed and are no longer required:
  nvidia-71-modaliases menu syslinux python-opengl libqca2 libqimageblitz4
  cdparanoia pinentry-gtk2 libk3b3 vorbis-tools libgda3-common libotr2 clamav
  libkleo4 clamav-freshclam libdvdcss2 konqueror-nsplugins lockfile-progs
  libkipi-common libmimelib4 libflac++6 libboost-thread1.34.1
  libswt3.2-gtk-java libcarp-clan-perl clamav-base libexiv2-4
  libboost-date-time1.34.1 libclamav5 k3b-data guile-1.8-libs
  libakonadiprivate1 python-openssl xinput libkpgp4 libkonq5 libkdepim4
  libksieve4 deborphan kfind libgle3 gnupg-agent libxul0d fglrx-modaliases
  libdbus-qt-1-1c2 netpbm nvidia-173-modaliases libmozjs0d python-setuptools
  kdepimlibs5 nvidia-common mpg123 libkonq5-templates libmpg123-0 libnetpbm10
  libgda3-3 libswt3.2-gtk-gcj libqca2-plugin-ossl imagemagick exiv2
  libxul-common libswt3.2-gtk-jni nvidia-96-modaliases kdepimlibs-data
  libgdl-1-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up lg3d-core (1.0.0) ...
/usr/share/lg3d/bin/postinstall: line 10: /bin/arch: No such file or directory
/usr/share/lg3d/bin/../bin/add-lg-to-gdm: line 28: /bin/arch: No such file or directory
Success. LG has been added as a gdm session.
/usr/share/lg3d/bin/postinstall: line 43: cd: /usr/share/lg3d/bin/../lib/linux-/lg3d-x11/programs/Xserver: No such file or directory
chown: cannot access `Xorg': No such file or directory
chgrp: cannot access `Xorg': No such file or directory
chmod: cannot access `Xorg': No such file or directory
dpkg: error processing lg3d-core (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 lg3d-core
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Partyboi2 on 2009-01-25
Try  [[COLOR=Blue]this[/COLOR]]("http://www.go2linux.org/Looking-glass-on-debian-Etch") it worked for me.

---

### Post by Adali on 2009-01-27
Thanks Partyboi2. That was the info I need. I can now start Looking Glass although I'm a bit disappointed that this desktop environment has alot of problems running apps.But anyway, its was nice to try out a different desktop environment. I'm amazed by the degree of customization that Linux and Ubuntu provide.

---

### Post by Partyboi2 on 2009-01-27
> **Adali said:**
> Thanks Partyboi2. That was the info I need. I can now start Looking Glass although I'm a bit disappointed that this desktop environment has alot of problems running apps.But anyway, its was nice to try out a different desktop environment. I'm amazed by the degree of customization that Linux and Ubuntu provide.
The joys of open source :)

---

