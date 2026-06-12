---
title: "mkinitramfs failure on pi zero 2"
date: 2021-11-17
forum: Hardware
---

### Post by bizzehdee on 2021-11-17
I am trying to do a apt upgrade after a first install on my raspberry pi zero 2, everything installs fine except for "linux-firmware, linux-image-raspi, linux-raspi and linux-image-5.13.0-1010-raspi" which fail due to mkinitramfs failing.

When i attempted to re-run dpkg --configure, i was able to get the following error log:

```
Setting up linux-firmware (1.201.1) ...
update-initramfs: Generating /boot/initrd.img-5.13.0-1008-raspi
Killed
E: mkinitramfs failure zstd -q -19 -T0 137
update-initramfs: failed for /boot/initrd.img-5.13.0-1008-raspi with 1.
dpkg: error processing package linux-firmware (--configure):
 installed linux-firmware package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 linux-firmware

```

Is there any way i can find out what the error is, and how i am supposed to resolve it?

Thank you

---

### Post by ahaswell on 2021-11-17
I have been struggling with the same problem today.
This is on a 32bit impish install
Here's the dump

```
ubuntu@ubuntu:~$ sudo apt upgrade --show-progress
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up linux-firmware (1.201.1) ...
update-initramfs: Generating /boot/initrd.img-5.13.0-1008-raspi
Killed
E: mkinitramfs failure zstd -q -19 -T0 137
update-initramfs: failed for /boot/initrd.img-5.13.0-1008-raspi with 1.
dpkg: error processing package linux-firmware (--configure):
 installed linux-firmware package post-installation script subprocess returned error exit status 1
Setting up linux-image-5.13.0-1010-raspi (5.13.0-1010.12) ...
dpkg: dependency problems prevent configuration of linux-image-raspi:
 linux-image-raspi depends on linux-firmware; however:
  Package linux-firmware is not configured yet.

dpkg: error processing package linux-image-raspi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-raspi:No apport report written because the error message indicates its a followup error from a previous failure.

 linux-raspi depends on linux-image-raspi (= 5.13.0.1010.16); however:
  Package linux-image-raspi is not configured yet.

dpkg: error processing package linux-raspi (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Processing triggers for linux-image-5.13.0-1010-raspi (5.13.0-1010.12) ...
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.13.0-1010-raspi
Killed
E: mkinitramfs failure zstd -q -19 -T0 137
update-initramfs: failed for /boot/initrd.img-5.13.0-1010-raspi with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-5.13.0-1010-raspi (--configure):
 installed linux-image-5.13.0-1010-raspi package post-installation script subprocess returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-firmware
 linux-image-raspi
 linux-raspi
 linux-image-5.13.0-1010-raspi
needrestart is being skipped since dpkg has failed
E: Sub-process /usr/bin/dpkg returned an error code (1)
ubuntu@ubuntu:~$
```

---

### Post by ahaswell on 2021-11-17
as noted elsewhere this is an out of memory error. I watched `top` as the memory went to zero and the pi hung.

The solution is to replace zstd with lz4 in
/etc/initramfs-tools/initramfs.conf
 
and rerun sudo apt upgrade

you can track the issue here:
[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1950214](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1950214)

---

### Post by bizzehdee on 2021-11-18
Thats incredible, thank you &#55357;&#56833;

---

