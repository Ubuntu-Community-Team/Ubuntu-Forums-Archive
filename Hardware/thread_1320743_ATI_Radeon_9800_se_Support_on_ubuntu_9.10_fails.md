---
title: "ATI Radeon 9800 se Support on ubuntu 9.10 fails"
date: 2009-11-09
forum: Hardware
---

### Post by epanda on 2009-11-09
Hi,


I am using an ATI Radeon 9800 se with HDMI connection.

I have two choices :

1/ First one is to install the free driver of Xorg and my screen has a good display but I CANNOT use special 3D effect with compiz or others 3D application.

2/ Install the last official driver of ATI for this card but it's the reverse. 
3D Special Effects with compiz are running well but the dsplay is bad. Somme pixel are not refreshed.



I have spend 3 days to test with modifications of xorg.conf or not without any success.

Can you help me please ?

NB : 

I have tried the last ati driver 9.3 and it fails during install decompression.



Created directory fglrx-install.oZga7E
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.593...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.31-14-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.oZga7E

---

### Post by DRF on 2010-02-02
The opensource drivers do support 3D effects (compiz etc) please make sure that the opensource driver is loading correctly. There is an issue some people have experienced with the radeon driver not loading correctly (see: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/468413](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/468413) ).

So you may want to try:
sudo rmmod radeon
sudo modprobe radeon
sudo /etc/init.d/gdm restart

There are more comprehensive work arounds mentioned on the bug report that don't require copying the above 3 lines into a terminal every time you boot up but this should help diagnose if it's an issue with loading the driver.

Daniel

---

