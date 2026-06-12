---
title: "DKMS tree problem"
date: 2008-12-03
forum: Installation &amp; Upgrades
---

### Post by micnguyen on 2008-12-03
I got this problem:
=================================================================
mic@mUBUNTU:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libprojectm-dev
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up kvm-source (1:72+dfsg-1ubuntu6) ...

Error! DKMS tree already contains: kvm-72
You cannot add the same module/version combo more than once.
dpkg: error processing kvm-source (--configure):
 subprocess post-installation script returned error exit status 3
Errors were encountered while processing:
 kvm-source
E: Sub-process /usr/bin/dpkg returned an error code (1)
================================================================

how can i fix it? thanks

---

### Post by skajotde on 2008-12-12
I have the same problem with kvm. 

Where can I find additional info ? Message from dpkg little informative what exactly goes wrong.

---

### Post by skajotde on 2008-12-12
I had virtualbox on core 2 duo. When i wanted try kvm dpkg crash with above message and i cant logging in gdm (no keyboard resposne in gdm, console works) but

apt-get remove kvm doesnt work
dpkg --configure -a nothing change.

---

### Post by pIII on 2010-01-10
same here, using:

```
linux-headers-2.6.31-9-rt
linux-image-2.6.31-9-rt 
```

i get:

```
run-parts: executing /etc/kernel/header_postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.31-9-rt                                        *  vboxdrv (3.0.8)...                                                                          [ OK ] 
 *  vboxnetadp (3.0.8)...                                                                       [ OK ] 
 *  vboxnetflt (3.0.8)...                                                                       [ OK ] 

Configurando virtualbox-ose-source (3.0.8-dfsg-1ubuntu1) ...
Adding modules to DKMS build system

Error! DKMS tree already contains: vboxdrv-3.0.8
You cannot add the same module/version combo more than once.
dpkg: error al procesar virtualbox-ose-source (--configure):
```

please someone give us a hint on how to fix this..

---

### Post by pIII on 2010-01-31
nada

---

### Post by barbolani on 2011-06-21
At least in Natty, I did the following and solved the problem:

1- sudo apt-get purge virtualbox-ose-dkms
2- Clear all the old stuff in /var/lib/dkms from older VBox versions (I had modules for vboxdrv, etc)
3- sudo apt-get install virtualbox-ose-dkms. You'll get the error
4- sudo dkms install -m virtualbox-ose-dksm -v 4.0.4

And now my VirtualBox works.

---

