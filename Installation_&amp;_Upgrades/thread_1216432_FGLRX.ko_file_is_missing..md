---
title: "FGLRX.ko file is missing."
date: 2009-07-18
forum: Installation &amp; Upgrades
---

### Post by Askar450 on 2009-07-18
Does anyone know why I am not getting a fglrx.ko file? I've gone to System > Administration > Hardware Driver then enabled fglrx but when I type in 
sudo dpkg-reconfigure -phigh linux-restricted-modules-`uname -r`
it says : 
update-initramfs: Generating /boot/initrd.img-2.6.28-13-generic
then I try :
sudo insmod /lib/modules/`uname -r`/volatile/fglrx.ko
I get an error message saying the file does not exist
what am I doing wrong? >.<

---

### Post by RaenirSalazar on 2009-08-03
I have the precisely same problem so far no go in IRC.

---

### Post by Ide on 2009-08-06
if i do a find / -name "fglrx.ko" i get this:
/lib/modules/2.6.28-14-generic/updates/dkms/fglrx.ko

when insmod that one i get :
insmod: error inserting '/lib/modules/2.6.28-14-generic/updates/dkms/fglrx.ko': -1 Operation not permitted

and im on t he 9.04 x64

Then i rolled back the installation by
sudo apt-get remove --purge fglrx*
and installed the ati.com version like described in: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
worked like  charm



(BTW: i use fglrx because of the open source makes my GPU run to 78°C. With the fglrx its now 56 degrees

---

