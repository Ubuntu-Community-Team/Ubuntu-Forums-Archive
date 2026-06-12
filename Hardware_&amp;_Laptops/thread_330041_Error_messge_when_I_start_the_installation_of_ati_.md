---
title: "Error messge when I start the installation of ati driver"
date: 2007-01-02
forum: Hardware &amp; Laptops
---

### Post by pierluc on 2007-01-02
When I start the installation of the driver it give me this messgae:

Detected configuration:
Architecture: i686 (32-bit)
X Server: Unknown X Window
cp: ne peut évaluer `x710/usr/X11R6/bin/*': Aucun fichier ou répertoire de ce type
find: install/usr/bin/fireglcontrolpanel: Aucun fichier ou répertoire de ce type

My OS is: Kubuntu Linux 6.10
My video card is a powercolor radeon 9550

I will describe what I have do:

I have type:
pierluc@pierluc:~/Desktop/ati$ sudo ./ati-driver-installer-8.32.5-x86.x86_64.run

It automaticly write:
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.32.5
........................................................
==================================================
ATI Technologies Linux Driver Installer/Packager
==================================================
Detected configuration:
Architecture: i686 (32-bit)
X Server: Unknown X Window
cp: ne peut évaluer `x710/usr/X11R6/bin/*': Aucun fichier ou répertoire de ce type
find: install/usr/bin/fireglcontrolpanel: Aucun fichier ou répertoire de ce type

After, the installation Window have open. After, I have clic on "cancel" Because I was afraid to create a bogue and I have close the Konsole window.

Why the driver installer give me the error message? Can I continue the installation if I have this message?

Tanks to answer my Ticket,
Pier Luc CR
Québec (Province of Québec), Canada
The January 2nd, 2007

** My first language is the Québec french ans is difficult for me to write in english but I think you will understand my question.

---

### Post by pierluc on 2007-01-10
up

---

### Post by EclipseAgent on 2007-01-16
Do you have /usr/lib or /usr/lib64 ? is QT 3.3 installed? 

If you have /usr/lib64 make symlink to /usr/lib

---

