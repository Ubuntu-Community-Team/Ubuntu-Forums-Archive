---
title: "ATI drivers?"
date: 2005-07-02
forum: Hardware &amp; Laptops
---

### Post by nbx909 on 2005-07-02
Right now i am running Fedora Core 4 on my main machine but i recently installed ubuntu on a P3 machine for a server. I now want to switch my FC4 machine to ubuntu but before i do i would like to know if my ATI radeon 9600 pro video card would have 3d support. I know that ATI drivers suck for linux, i spent 5 days getting them to work in Fedora Core. So... are there drivers for my video card? and how do i install them?

---

### Post by jasmuz on 2005-07-02
[QUOTE=nbx909]Right now i am running Fedora Core 4 on my main machine but i recently installed ubuntu on a P3 machine for a server. I now want to switch my FC4 machine to ubuntu but before i do i would like to know if my ATI radeon 9600 pro video card would have 3d support. I know that ATI drivers suck for linux, i spent 5 days getting them to work in Fedora Core. So... are there drivers for my video card? and how do i install them?[/QUOTE]
 Installing the ATI drivers are relatively easy.

Read this: [http://www.ubuntulinux.org/wiki/BinaryDriverHowto](http://www.ubuntulinux.org/wiki/BinaryDriverHowto)

---

### Post by nbx909 on 2005-07-02
```
michael@mikelinux:~$ sudo apt-get install fglrx-driver Reading package lists... Done
Building dependency tree... Done
Package fglrx-driver is a virtual package provided by:
  xfree86-driver-fglrx 4.3.0-8.8.25-0ubuntu11
  xorg-driver-fglrx 6.8.0-8.8.25-0ubuntu11
You should explicitly select one to install.
E: Package fglrx-driver has no installation candidate
michael@mikelinux:~$ sudo apt-get install xfree86-driver-fglrx
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  xfree86-driver-fglrx: Depends: xserver-xfree86 (>= 4.3)
E: Broken packages
michael@mikelinux:~$
``` 
the link that you gave me appears to work with xfree drivers but the xfree drivers gave that error.

---

### Post by E-werd on 2005-07-03
Note: If you are using Xorg, chances are that XF86 drivers won't work.

Have you tried to "sudo apt-get install xorg-driver-fglrx"?

---

### Post by nbx909 on 2005-07-03
how do i tell what drivers i am useing?

---

