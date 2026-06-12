---
title: "Kernel Upgrade: Fail? (What does this message mean?)"
date: 2009-06-23
forum: Installation &amp; Upgrades
---

### Post by AlexsAntidote on 2009-06-23
I just attempted to upgrade the the latest kernel using the following commands:

```
wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630-generic_2.6.30-020630_i386.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630_2.6.30-020630_all.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-image-2.6.30-020630-generic_2.6.30-020630_i386.deb
sudo dpkg -i linux-headers-2.6.30-020630-generic_2.6.30-020630_i386.deb linux-headers-2.6.30-020630_2.6.30-020630_all.deb linux-image-2.6.30-020630-generic_2.6.30-020630_i386.deb

```

Everything appeared to be OK, but right at the end I got the following [FAIL] messages:
```
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.30-020630-generic                                                                                      
 *  nvidia (180.44)...                                                          nvidia (180.44): Installing module.
..........(bad exit status: 10)
  Build failed.  Installation skipped.
                                                                         [fail]
run-parts: executing /etc/kernel/postinst.d/nvidia-common

Setting up linux-headers-2.6.30-020630-generic (2.6.30-020630) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.30-020630-generic                                                                                      
 *  nvidia (180.44)...                                                          nvidia (180.44): Installing module.
..........(bad exit status: 10)
  Build failed.  Installation skipped.
                                                                         [fail]
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common

```
(If you want you can just see the attached screenshot)

Any idea what this means or how to correct/fix it?

---

### Post by AlexsAntidote on 2009-06-23
Nevermind. I just followed the guide here: [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

It worked much better. I still had an issue with the NVIDIA driver, so I had to reinstall it using the following:
```
sudo apt-get remove --purge nvidia-common
cd /usr/src
sudo dpkg -i linux*2.6.30*.deb
sudo apt-get install nvidia-common
```

Thanks Master_Kernel for the help.

---

