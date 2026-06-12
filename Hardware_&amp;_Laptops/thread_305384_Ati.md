---
title: "Ati"
date: 2006-11-23
forum: Hardware &amp; Laptops
---

### Post by mad_alfred on 2006-11-23
Hi!

I just downloaded the new ati drivers for my mobility radeon X1400.
i tried to install thm with the command sudo sh driver-name.run but i reeived the following error.

Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.29.6.............................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager
-e ==================================================
./ati-installer.sh: 176: Syntax error: Bad substitution
Removing temporary directory: fglrx-install

what does it mean??

..i thought of a corrupt file so i downloaded them again but nothing changes.

please help!

---

### Post by cantormath on 2006-11-23
ati drivers for linux are only recommended if nothing else works...

---

### Post by mad_alfred on 2006-11-23
ok... I tried install these cause the xorg-fglrx drivers for 3d acceleration but nothing helps: sudo dpkg-reconfigure xserver-xorg and i select fglrx drivers but see  no 3d acceleration...

---

### Post by daradib on 2006-11-23
Disable composite extensions to add 3D support for fglrx driver. Note: Aiglx will not work since it requires composite extensions, so use XGL and Beryl instead.

To disable Composite extensions, add the following lines to the end of /etc/X11/xorg.conf file:

Section "Extensions"
        Option "Composite" "false"
EndSection

You will get 3D, DRI, and OpenGL support.

---

