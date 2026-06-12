---
title: "intel video drivers safe to install?"
date: 2013-03-22
forum: Hardware
---

### Post by bogdarnet on 2013-03-22
Was pleasantly surprised to find this website offering linux graphics drivers, having had mixed success with ppas I've tried so far, thought it might do the trick (mostly things work, but hoping for better opengl support, most 3d games not running well... even warzone, though it runs, gives lots of visual artifacts, on an old laptop with an intel 945gm video chip):

[https://01.org/linuxgraphics/](https://01.org/linuxgraphics/)

Unfortunately, though, when I downloaded their .deb installer for ubuntu 12.04 32-bits and tried to install it, software center gave me a warning, "This package is of bad quality" with details as such:

Lintian check results for intel-linux-graphics-installer_1.0_i386.deb:
Use of uninitialized value $ENV{"HOME"} in concatenation (.) or string at /usr/bin/lintian line 108.
E: intel-linux-graphics-installer: malformed-deb-archive found 4 members instead of 3

Running lintian on the deb at the command line gave further warnings as well:

W: intel-linux-graphics-installer: latest-debian-changelog-entry-changed-to-native
E: intel-linux-graphics-installer: malformed-deb-archive found 4 members instead of 3
W: intel-linux-graphics-installer: spelling-error-in-description allows to allows one to
W: intel-linux-graphics-installer: binary-without-manpage usr/bin/ilg-config-test
W: intel-linux-graphics-installer: binary-without-manpage usr/bin/intel-linux-graphics-installer
W: intel-linux-graphics-installer: script-not-executable usr/share/intel-linux-graphics-installer/scripts/yum-fetch-and-downgrade.sh

So, this is mostly unknown to me, is it something wrong with my system or with the file?

---

### Post by CatKiller on 2013-03-22
If it were mine, I wouldn't install that. Intel drivers are part of the kernel. You don't really want to be introducing low-quality code there.

---

### Post by Yellow Pasque on 2013-03-22
I would avoid that .deb like the plague. Using the xorg-edgers PPA is probably the safest way to try the latest graphics stack, but I wouldn't hold much hope for a lowly 945G to do serious gaming in Linux since the hardware only supports OpenGL 1.4.

---

### Post by ManamiVixen on 2013-03-22
The Intel driver from Intel's website is only for Chipsets older than the i915. You don't need it.

---

