---
title: "monitor: 'input not supported' after installing fglrx"
date: 2016-08-16
forum: Hardware
---

### Post by fkkroundabout on 2016-08-16
recently switched graphics card to a HD 6790. had to use a DVI to VGA adapter, the OS didn't have any problems using the open source driver. but once i install the proprietary driver it doesn't boot to the desktop whatsoever, i just get a blank screen with the monitor's firmware saying 'input not supported'.  

i did run 'amdconfig --initial' after install 

if i run fglrxinfo i get: 'unable to open display (null)' 

i am aware i can uninstall and go back to the open source, but from past experience with a 6670, the performance is better with fglrx than radeon, so i want to get it working. 

regardless of whether i install using 'additional drivers' or apt-get or using .deb files from the AMD website, they are all the same versions of the software, and the result is the same.   i'm on ubuntu 14.04.5, and will be testing a fresh install on a separate partition soon 

all questions welcome

---

### Post by deadflowr on 2016-08-16
Is this from a fresh 14.04.5 installation disk?
If it is, then it uses the same kernel and xserver package used in 16.04, in which case the fglrx driver is unusable.
So that might be where the problem lies.

Unfortunately, since the driver still exists for users running earlier 14.04 releases (14.04 and 14.04.1, those are still supported for the fglrx driver) it would probably still show up in apt-get and the additional drivers.
fwiw.

---

### Post by fkkroundabout on 2016-08-16
thank you for the info. do you know if this is the same for  12.04.5 ?

---

### Post by fkkroundabout on 2016-08-16
checked out benchmarks. the radeon open source driver is more inefficient, but not by alot. might just leave it, instead. figured out manual resolution with xrandr  

[https://www.phoronix.com/scan.php?page=article&item=ubuntu-1604-amd&num=1](https://www.phoronix.com/scan.php?page=article&item=ubuntu-1604-amd&num=1)

---

### Post by mastablasta on 2016-08-17
or you can install 14.04.1 and then add fglrx. but first check which kernel you have.

but first - can you maybe boot with one of the boot options (like nomodeset): [SIZE=2]https://help.ubuntu.com/community/BootOptions
[/SIZE]

---

