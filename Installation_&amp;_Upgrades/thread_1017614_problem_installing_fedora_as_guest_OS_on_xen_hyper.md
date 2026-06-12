---
title: "problem installing fedora as guest OS on xen hypervisor with Ubuntu 8.04 as host"
date: 2008-12-21
forum: Installation &amp; Upgrades
---

### Post by bharat.bvrit on 2008-12-21
after installing xen sever  and for creating Fedora7 image i gave the following command,

xen-create-image --hostname=fedora7 --size=2Gb --swap=256Mb --ide --ip=100.100.60.8 --netmask=255.255.255.0 --gateway=100.100.60.1 --force --dir=/home/xen --memory=64Mb --arch=amd64 --kernel=/boot/vmlinuz-2.6.24-22-xen  --initrd=/boot/initrd.img-2.6.24-22-xen --install-method=debootstrap --dist=fedora-core-7  --mirror = [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/)

then the installation terminated giving,

Installation method: debootstrap
Done
System installation failed.  Aborting
Logfile produced at:
	 /var/log/xen-tools/fedora7.log


**Also the log produced at /var/log/xen-tools/fedora7.log is **
General Information
--------------------
Hostname       :  fedora7
Distribution   :  fedora-core-7
Partitions     :  swap            256Mb (swap)
                  /               2Gb   (ext3)
Image type     :  sparse
Memory size    :  64Mb
Kernel path    :  /boot/vmlinuz-2.6.24-22-xen
Initrd path    :  /boot/initrd.img-2.6.24-22-xen

Networking Information
----------------------
IP Address 1   : 100.100.60.8 [MAC: 00:16:3E:26:49:7C]
Netmask        : 255.255.255.0
Broadcast      : 100.100.60.255
Gateway        : 100.100.60.1

Creating partition image: /home/xen/domains/fedora7/swap.img
0+0 records in
0+0 records out
0 bytes (0 B) copied, 2.6214e-05 s, 0.0 kB/s
Done

Creating swap on /home/xen/domains/fedora7/swap.img
Setting up swapspace version 1, size = 268431 kB
no label, UUID=249c5706-eb93-4c98-bf54-7fb3a11132a3
Done

Creating partition image: /home/xen/domains/fedora7/disk.img
0+0 records in
0+0 records out
0 bytes (0 B) copied, 1.1844e-05 s, 0.0 kB/s
Done

Creating ext3 filesystem on /home/xen/domains/fedora7/disk.img
mke2fs 1.40.8 (13-Mar-2008)
/home/xen/domains/fedora7/disk.img is mounted; will not make a filesystem here!
Done
Installation method: debootstrap
Falling back to default debootstrap command
[B]
Copying files from host to image.
Copying files from /var/cache/apt/archives -> /tmp/mVG9JX7B5R/var/cache/apt/archives
Done
Done
E: No such script: /usr/share/debootstrap/scripts/fedora-core-7

Copying files from new installation to host.
Copying files from /tmp/mVG9JX7B5R/var/cache/apt/archives -> /var/cache/apt/archives
Done
Done
The installation of the new system has failed.

The system is missing the common file: /bin/ls
Done
[/B]



the xen kernel i installed is **vmlinuz-2.6.24-22-xen**

What should i do..please help me out urgently
thanx.....

---

### Post by tapas_mishra on 2009-11-16
Has any one been able to solve this problem even I am getting the same issue

---

