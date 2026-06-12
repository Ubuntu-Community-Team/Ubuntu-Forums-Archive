---
title: "Why installing meta nvidia-470 remove r8169 driver?"
date: 2023-04-18
forum: Hardware
---

### Post by dufresnep on 2023-04-18
After installing metapackage nvidia-470 (for GTX 660 aka GK106) my Internet was gone.
lspci -k was not showing a driver anymore for ethernet.

Looking through /lib/modules/5.19.0-38-generic/kernel/net/  ... well was it realtek... not finding it anymore...
but r8169 was gone for current version... but there for previous versions of the kernel.

I am on Ubuntu 22.04.

By reading [https://askubuntu.com/questions/1052971/r8168-r8169-realtek-driver-module-troubles](https://askubuntu.com/questions/1052971/r8168-r8169-realtek-driver-module-troubles) I installed r8168-dkms (and blacklisted r8169 but I should probably undo that) and now my Internet is working.

But my question is why installing nvidia diriver did uninstall r8169?

Just found [https://askubuntu.com/questions/1387231/ethernet-disappears-after-nvidia-driver-installation](https://askubuntu.com/questions/1387231/ethernet-disappears-after-nvidia-driver-installation) that shows that this happens to others.

---

### Post by dufresnep on 2023-04-18
BTW why:
root@bismark:/home/paul# find /lib/modules -name r8169* -print
/lib/modules/5.19.0-38-generic/kernel/drivers/net/ethernet/realtek/r8169.ko
/lib/modules/5.19.0-35-generic/kernel/drivers/net/ethernet/realtek/r8169.ko
root@bismark:/home/paul# find /lib/modules -name r816* -print
root@bismark:/home/paul# 

would expect r816* to be more general than r8169* and so retruns more results.

root@bismark:/home/paul# ls -lh /lib/modules/5.19.0-38-generic/kernel/drivers/net/ethernet/realtek/
total 592K
-rw-r--r-- 1 root root 123K mar 17 16:56 8139cp.ko
-rw-r--r-- 1 root root 133K mar 17 16:56 8139too.ko
-rw-r--r-- 1 root root  67K mar 17 16:56 atp.ko
-rw-r--r-- 1 root root 263K mar 17 16:56 r8169.ko
root@bismark:/home/paul# 

I am surprised that r8169.ko is there... thought it was not there after installing nvidia driver...

---

