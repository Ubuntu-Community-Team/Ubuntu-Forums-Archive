---
title: "Karmic: madwifi missing"
date: 2009-10-30
forum: Hardware
---

### Post by jshayden on 2009-10-30
Does anyone know how to install the madwifi driver in Karmic?  My Atheros chip (AR5212) does not yet work with the ath5k/ath9k drivers.  I have the "linux-backports-karmic" package installed; this included the madwifi driver in Jaunty.

```
$ sudo apt-get install linux-backports-modules-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-backports-modules-2.6.31-14-generic-pae is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
```

```
$ sudo modprobe ath_pci
FATAL: Module ath_pci not found.
```


Any ideas?

Thanks!

---

### Post by jshayden on 2009-10-30
I've tried compiling madwifi from source, also, with the following result:

```
$ sudo make
cd: 1: can't cd to /lib/modules/2.6.31-14-generic-pae/build
Makefile.inc:66: *** /lib/modules/2.6.31-14-generic-pae/build is missing, please set KERNELPATH.  Stop.
```

---

### Post by drpjkurian on 2009-11-01
> **jshayden said:**
> I've tried compiling madwifi from source, also, with the following result:

```
$ sudo make
cd: 1: can't cd to /lib/modules/2.6.31-14-generic-pae/build
Makefile.inc:66: *** /lib/modules/2.6.31-14-generic-pae/build is missing, please set KERNELPATH.  Stop.
```

Hi Jshayden

Please visit my thread 
[http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)
It might help you.

With regards
Dr Kurian

---

