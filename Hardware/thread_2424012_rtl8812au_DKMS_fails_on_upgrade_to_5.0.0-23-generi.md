---
title: "rtl8812au DKMS fails on upgrade to 5.0.0-23-generic (18.04.2 LTS)"
date: 2019-08-01
forum: Hardware
---

### Post by donb-z on 2019-08-01
Auto upgrading to 5.0.0-23-generic and ensuring dkms autoinstalled all appropriate kernels resulted in a 4x module installed in the 5x module library tree. On reboot, the rtl8812au driver failed to install, of course, because of exec error. Attempting to manually induce a DKMS build of the rtl8812au driver resulted in a compilation error. 

Can be reproduced simply by updating to the 5x kernel (the default), then attempting to build rtl8812au with `dkms install`. 

I'd love to get this back online, so any help is appreciated. Thanks!
D

---

### Post by jeremy31 on 2019-08-01
You are better off using source code from github as the rtl8812au-dkms package changelog shows no update to support the version 5 kernel yet
```
sudo apt install git build-essential dkms
git clone https://github.com/abperiasamy/rtl8812AU_8821AU_linux.git
cd rtl8812AU_8821AU_linux
sudo make -f Makefile.dkms install
```
Reboot

---

### Post by donb-z on 2019-08-01
Thanks, Jeremy. That was definitely the best route to take in this situation.

---

