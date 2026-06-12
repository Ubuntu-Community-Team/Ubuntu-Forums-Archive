---
title: "installing VMWareWorkStation?????"
date: 2009-02-05
forum: Installation &amp; Upgrades
---

### Post by Will4 on 2009-02-05
hi you'all

i don't know how to install VMWWS at my PC, it has something like this inside a file,

> embrace.nfo       keygen
install VMWare  VMware-Workstation-6.5.0-118166.i386.bundle

how do i install the 'bundle' package? what command am i supose to use?

thanks to everyone, 

much appreciation.;)

---

### Post by Partyboi2 on 2009-02-05
Open a terminal (Applications>Accessories>Terminal) and install a few packages you need to get the VMware workstation installed
```
sudo apt-get install build-essential linux-kernel-headers linux-kernel-devel
```Then change directory to where the 
VMware-Workstation-6.5.0-118166.i386.bundle is. So for example if it is located on your Desktop
```
cd ~/Desktop
``` Once you are in the correct directory type
```
gksudo bash ./VMware-Workstation-6.5.0-118166.i386.bundle 
```

---

### Post by binbash on 2009-02-05
sh VMware-Workstation-6.5.0-118166.i386.bundle (add sudo if you need root access)

---

### Post by Will4 on 2009-02-05
Thank you Partyboi,i appreciate your help. I got it!! its a pitty that we don't have the [SOLVED] button, 

Thanks again.

---

