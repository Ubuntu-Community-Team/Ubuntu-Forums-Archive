---
title: "Installing ATI drivers on Ubuntu 9.04 x64"
date: 2009-08-18
forum: Installation &amp; Upgrades
---

### Post by Shugge on 2009-08-18
Hi,

I'm relatively new to Ubuntu. I'm runnig Ubuntu 9.04 x64 on my corei7 system.

What I want to do is installing the ati catalyst driver 9.8 manually.

I found this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

I've followed the guide step by step, but when I type the second terminal command this is what I get:

erik@erik-desktop:~$ sh ati-driver-installer-9-8-x86.x86_64.run --buildpkg Ubuntu/jaunty
sh: Can't open ati-driver-installer-9-8-x86.x86_64.run

Does anyone know what I'm doing wrong?

---

### Post by jaywhy13 on 2009-08-18
Is the file executable?
chmod a+x ati....run

---

### Post by markbuntu on 2009-08-18
First, you need to make that file executable which you can do by right clicking on t and choosing properties/permission and checking the little Execute box.

Second, you need to run the installer as root

sudo sh /.ati-driver-installer.......


If you have an older driver installed you really need to remove it before installing a new one.

---

