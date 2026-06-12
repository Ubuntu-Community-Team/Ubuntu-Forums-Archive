---
title: "installing ndiswrapper disturbs the system"
date: 2008-08-23
forum: General Help
---

### Post by dexter.deepak on 2008-08-23
i installed ndiswrapper and am currently using it to access internet over my hardy system. since i have installed that thing, i am facing frequent standstills, slow program startups and computer hangups.
i later read that installing ndiswrapper for an unsupported card may bring the system to unstability.,,since my card is not their in the supported list, i guess this is the cause of my current problems.

so i need to know.. how to uninstall ndiswrapper, and make my system use its own drivers....actually i forced my system to use ndiswrapper drivers instead of its own drivers.

---

### Post by LateNiteTV on 2008-08-23
first you need to unload ndiswrapper:
```
modprobe -r ndiswrapper
```
then remove driver from system:
```
ndiswrapper -r DriverName
```
then in the ndiswrapper directory:
```
make uninstall
```

then remove loadndiswrapper in sbin and ndiswrapper in /usr/bin. remove ndiswrapper kernel module in:
```
/lib/modules/`uname -r`/misc
```

---

### Post by dexter.deepak on 2008-08-24
before trying this code, i would just like to confirm, will this method make the system use the inbuilt drivers for my card ? i am asking this as i would still like to run internet on my system after removing ndiswrapper.

---

### Post by LateNiteTV on 2008-08-24
no, it wont make your system use the "inbuilt drivers".
if you have to use ndiswrapper to use wireless, then there is no native driver for your card.

---

### Post by dexter.deepak on 2008-08-24
> **LateNiteTV said:**
> no, it wont make your system use the "inbuilt drivers".
if you have to use ndiswrapper to use wireless, then there is no native driver for your card.

actually this is not the case here. i had some in-built drivers, but since i was getting very slow internet speed (atleast 10 times slower than in windows), i tried to use the windows drivers. unluckily that too didnt help improve the speed and instead that made my system unstable.:(

---

### Post by LateNiteTV on 2008-08-24
what card are you using?

---

### Post by dexter.deepak on 2008-08-24
> **LateNiteTV said:**
> what card are you using?

its a "D-Link Wireless G DWA-510 desktop adapter" and i am in a WPA network.

---

