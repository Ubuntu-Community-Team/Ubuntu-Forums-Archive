---
title: "Opera 10 BETA 3 installation"
date: 2009-08-19
forum: Installation &amp; Upgrades
---

### Post by AbraKdabra on 2009-08-19
Hi! I downloaded the Opera 10 Beta 3 .deb package (opera_10.00.4537.gcc3.qt3_i386.deb), and when I try to install it, the installation stop and throws an error telling me that it needs the libqt3c102-mt dependency. When I go to Synaptic that library is already installed.

Thanks for your help.

---

### Post by finalsayan on 2009-08-19
I have the same problem, but still no solution

---

### Post by ibutho on 2009-08-19
Have you tried using gdebi? It should resolve any dependencies for you. Try
```
sudo gdebi opera_10.00.4537.gcc3.qt3_i386.deb
```

---

### Post by AbraKdabra on 2009-08-19
> mauro@mauroubuntu:~/Escritorio$ sudo gdebi opera_10.00.4537.gcc3.qt3_i386.deb
[sudo] password for mauro:
Reading package lists: Done/non-free Packages: 95   95  ckages: 95
Reading state information: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done
Este paquete no es instalable (This packet is not stable)
La dependencia no se puede satisfacer: libqt3c102-mt (>= 3:3.2.1) (Dependency cannot be satisfied: libqt3c102-mt (>= 3:3.2.1))

mauro@mauroubuntu:~/Escritorio$

English traductions are between ( ) at the end of the messages, I use spanish version.

---

### Post by ibutho on 2009-08-19
What version of Ubuntu are you running? I have libqt3-mt 3.3.8 on Linux Mint 7 (based on Ubuntu 9.04) and opera installs without any problems.

---

### Post by AbraKdabra on 2009-08-19
Sorry about that, I'm using Ubuntu 9.04.

---

### Post by fullmetal_alchemist on 2009-08-19
> **AbraKdabra said:**
> Hi! I downloaded the Opera 10 Beta 3 .deb package (opera_10.00.4537.gcc3.qt3_i386.deb), and when I try to install it, the installation stop and throws an error telling me that it needs the libqt3c102-mt dependency. When I go to Synaptic that library is already installed.

Thanks for your help.

That version is compiled against very old libraries that are not available in ubuntu any more. You need this version [opera_10.00.4537.gcc4.qt4_i386.deb]("ftp://ftp.opera.com/pub/opera/linux/1000b3/beta3/en/i386/opera_10.00.4537.gcc4.qt4_i386.deb").

---

### Post by AbraKdabra on 2009-08-19
Thank you fullmetal_alchemist!! It worked perfect :D

---

