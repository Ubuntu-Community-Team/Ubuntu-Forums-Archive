---
title: "Cant install ati propietary drivers"
date: 2010-08-11
forum: Hardware
---

### Post by rado3105 on 2010-08-11
after putting this command:
sudo sh /home/r-c/Plocha/ati-driver-installer-9-3-x86.x86_64.run

shows me this:

Created directory fglrx-install.SHMZt4
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.593...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.32-23-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.SHMZt4



Ubuntu 9.10

---

### Post by Fludizz on 2010-08-11
Are you sure your system is installed as a 64bit system? You seem to be trying to install the 64bit ATi driver on a generic kernel rather then a 64bit kernel. The ATi driver explicitly wants a AMD64 kernel if you install the 64bit driver...

---

### Post by odinfromvalhalla on 2010-08-11
execute in a terminal:

uname -r 

to get the kernel version you are running

---

### Post by TBABill on 2010-08-11
Isn't fglrx already in Synaptic to install?

---

### Post by rado3105 on 2010-08-11
I chose 32 bit ati driver but allways it download just 64bit. Yes I have generic kernel.

---

### Post by rado3105 on 2010-08-11
fglrx is ati propietary driver?

---

### Post by Yellow Pasque on 2010-08-11
You're trying to install a version of the driver too old for Lucid (probably because your card is no longer supported by recent drivers and the AMD/ATI site offered you the old version).

See this to clean your install: [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver)

Don't try to install the proprietary fglrx/Catalyst again.

---

