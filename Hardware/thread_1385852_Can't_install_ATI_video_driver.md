---
title: "Can't install ATI video driver"
date: 2010-01-20
forum: Hardware
---

### Post by Eirinjas on 2010-01-20
Tried installing it in Ubuntu 9.10, failed to install, and I have no idea what to do with what it's telling me:


jason@jason-desktop:~$ '/home/jason/Downloads/ati-driver-installer-9-3-x86.x86_64.run' 
Created directory fglrx-install.zztuH3
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.593...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.31-17-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.zztuH3
jason@jason-desktop:~$

---

### Post by Yellow Pasque on 2010-01-20
Catalyst 9-3 won't install in Karmic (or Jaunty). The X server is too new. Just use the open=source ati driver (pre-installed).

---

### Post by Eirinjas on 2010-01-20
Okay, how do I set that up?  I think I lost something, because OpenArena ran when I first installed, and now it's not.  Neither is Urban Terror.  I think it might have to do with my trying to install those drivers.  ATI catalyst control center HALF-installed.  It's in my applications-other list, but it complains about missing files.  How do I uninstall that?  Sorry, this is only my second day using a Linux system.

---

### Post by Yellow Pasque on 2010-01-20
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

---

