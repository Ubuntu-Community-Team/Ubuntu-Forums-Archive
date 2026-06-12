---
title: "Vmware"
date: 2008-11-13
forum: General Help
---

### Post by Mathurin1968 on 2008-11-13
Vmware keeps asking me for the directory of c header files that match my kernel?  Any ideas?

and thanks!

---

### Post by snova on 2008-11-13
Try installing the linux-headers-generic package.

---

### Post by linux_tech on 2008-11-13
After downloading vmware, run these-
```
sudo aptitude install build-essential linux-headers-generic
```
```
cp /media/cdrom/VMwareTools-*.tar.gz /tmp/
```
```
cd /tmp/
```
```
tar xf VMwareTools-*.tar.gz
```
```
cd vmware-tools-distrib/
```
```
sudo ./vmware-install.pl
```

---

### Post by Mathurin1968 on 2008-11-13
ahhh the darn thing came back and said were already the newest version.

---

