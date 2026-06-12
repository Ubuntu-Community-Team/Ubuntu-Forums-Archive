---
title: "ATI driver install problem"
date: 2009-06-20
forum: Hardware
---

### Post by h2z on 2009-06-20
I can't seem to install the ATI driver, keep getting the same error "aticonfig: No supported adapters detected"

```

stefan@Ubuntu:~/Desktop$ sudo dpkg -i xorg-driver-fglrx_*.deb fglrx-kernel-source_*.deb fglrx-amdcccle_*.deb
[sudo] password for stefan: 
Selecting previously deselected package xorg-driver-fglrx.
(Reading database ... 119099 files and directories currently installed.)
Unpacking xorg-driver-fglrx (from xorg-driver-fglrx_8.620-0ubuntu1_i386.deb) ...
Selecting previously deselected package fglrx-kernel-source.
Unpacking fglrx-kernel-source (from fglrx-kernel-source_8.620-0ubuntu1_i386.deb) ...
Selecting previously deselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from fglrx-amdcccle_8.620-0ubuntu1_i386.deb) ...
Setting up fglrx-kernel-source (2:8.620-0ubuntu1) ...
Adding Module to DKMS build system
Doing initial module build
Installing initial module
Done.

Setting up xorg-driver-fglrx (2:8.620-0ubuntu1) ...
Installing new version of config file /etc/ati/atiogl.xml ...
Installing new version of config file /etc/ati/signature ...
Installing new version of config file /etc/ati/control ...
Installing new version of config file /etc/ati/amdpcsdb.default ...

Processing triggers for man-db ...
Setting up fglrx-amdcccle (2:8.620-0ubuntu1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
stefan@Ubuntu:~/Desktop$ sudo gedit /etc/X11/xorg.conf
stefan@Ubuntu:~/Desktop$ sudo aticonfig --initial -f
aticonfig: No supported adapters detected

```

---

### Post by wojox on 2009-06-20
Look here. A friend of mine had a similiar problem.

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_7.12_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_7.12_Driver_Manually)

---

