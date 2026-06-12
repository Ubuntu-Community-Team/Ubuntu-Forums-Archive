---
title: "installing Driver"
date: 2006-01-04
forum: Hardware &amp; Laptops
---

### Post by dsjas297 on 2006-01-04
RaLink just released their Linux driver for the chipset my wireless adapter has.
I begin to install it according to their instructions until this happens:

```

sudo make all
Password:
make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/home/jasdeep/RT61_Linux_STA_Drv1.0.3.0_200512230/Module modules
make: *** /lib/modules/2.6.12-9-386/build: No such file or directory.  Stop.
make: *** [all] Error 2

```

What should I do to solve this problem?

Help is direly needed (I only have internet acceess on my Windows boot!) and greatly appreciated.

---

### Post by phillyboy on 2006-01-04
You need to install the kernel headers for your specific kernel (2.6.12-9-386). Since you only have internet access in Windows, you can download the specific package from the one of the Ubuntu archives in Windows, and then install it in Ubuntu using 'dpkg -i <package>' (assuming you can already set up access to your Windows drives in Linux). 

[This package]("http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.12/linux-headers-2.6.12-9-386_2.6.12-9.23_i386.deb") should be the one your a looking for, and [here]("http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.12/") is the general directory where some kernel-related things lie.

---

