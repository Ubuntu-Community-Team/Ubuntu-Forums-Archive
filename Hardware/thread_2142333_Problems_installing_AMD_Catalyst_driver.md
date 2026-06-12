---
title: "Problems installing AMD Catalyst driver"
date: 2013-05-05
forum: Hardware
---

### Post by jrohde on 2013-05-05
Hi

I have a AMD Radeon HD 7800 graphics card in the pc that I have installed Ubuntu 13.04 64 bit on. I want to install the proprietary driver, but I am gettig the message: 

**One or more tools required for installation cannot be found on the system. Install the required tools before installing the fglrx driver.**

I have installed the Linux headers. What other tools could they be talking about?

Regards
JRohde

---

### Post by Yellow Pasque on 2013-05-05
```
sudo apt-get install build-essential cdbs dh-make dkms execstack dh-modaliases linux-headers-generic fakeroot
```
Source: [http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)

---

