---
title: "ATI Radeon HD 6870 Driver fails to install default-policy.sh does not support version"
date: 2011-04-09
forum: Hardware
---

### Post by Guardian-Mage on 2011-04-09
I'm running Ubuntu 11.04 Beta, with everything updated completely. I'm using Ubuntu Classic, because Unity fails to run, supposedly because of my video card. The drivers for the Radeon HD 6870 series is apparently lacking, but I found a [post]("http://gamblis.com/2011/03/25/ati-radeon-hd6870-driver-11-2-for-ubuntu/") stating the newest version has full support for Ubuntu Natty Narwhal. That post is slightly old, so i grabbed 11.3 for Ubuntu x86 off the ATI website. 

When I run the installation program, I receive the following error:

```
> ./ati-driver-installer-11-3-x86.x86_64.run 
Created directory fglrx-install.uREFoO
Verifying archive integrity... All good.
Uncompressing ATI Catalyst(TM) Proprietary Driver-8.831.2.........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
=====================================================================
 ATI Technologies Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.38-8-generic-pae:; make sure that the version is being
correctly set by --iscurrentdistro

=====================================================================
 ATI Technologies Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.38-8-generic-pae:; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.uREFoO
> 

```

I would love to get the latest ATI drivers working so that I can try out Unity!

---

### Post by Yellow Pasque on 2011-04-09
Use the ones included with Natty (available in repo as fglrx). They're newer than the Catalyst 11-3 you tried to install. Details: [http://www.phoronix.com/scan.php?page=news_item&px=OTI3MQ](http://www.phoronix.com/scan.php?page=news_item&px=OTI3MQ)

BTW, if you ever want to install Catalyst downloaded from AMD site, don't just run the installer like that (makes uninstall messy). Build packages like: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually)

---

