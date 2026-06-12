---
title: "AMD: Catalyst Omega Driver still shows old version"
date: 2014-12-14
forum: Hardware
---

### Post by micha2358 on 2014-12-14
Hi there,
 
I installed the new Catalyst Omega driver 14.12 with
#sudo dpkg -i --force-overwrite fglrx*.deb
according to this guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide)

I run on Utopic, so I created .deb-packages with
#sudo ./fglrx-14.501.1003/amd-driver-installer-14.501.1003-x86.x86_64.run --buildpkg Ubuntu/utopic

The installation was successful, but fglrxinfo and CCC still show old version from Catalyst 14.08 (14.201.1006.1002)

Only the 2D driver (shown in Catalyst) seems to be updated.

Previously, I had the proprietary system drivers installed, so at first I tried to purge fglrx* and other stuff recommended to remove previously, but no success...
But even though, the --force-overwrite command should overwrite all old stuff!?
What is my mistake? How can I install the driver properly, so that fglrxinfo shows version 14.501.1003?

---

