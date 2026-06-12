---
title: "Error when updating Ubuntu Jaunty"
date: 2009-10-02
forum: Installation &amp; Upgrades
---

### Post by airmid on 2009-10-02
Hi,

Will doing an update I ran into the following error:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

So I ran the suggested command and received the following:

lori@lori-laptop:~$ sudo dpkg --configure -a[sudo] password for lori: 
Setting up initramfs-tools (0.92bubuntu29) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-image-2.6.28-15-generic (2.6.28-15.52) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.28-15-generic
cpio: ./etc/modprobe.d/oss-compat: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.28-15-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.28-15-generic (--configure):
 subprocess post-installation script returned error exit status 2
Setting up linux-image-2.6.28-15-server (2.6.28-15.52) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.28-15-server
cpio: ./etc/modprobe.d/oss-compat: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.28-15-server
Failed to create initrd image.
dpkg: error processing linux-image-2.6.28-15-server (--configure):
 subprocess post-installation script returned error exit status 2
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.28-15-server
cpio: ./etc/modprobe.d/oss-compat: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.28-15-server
dpkg: subprocess post-installation script returned error exit status 1

I then looked at the following:

lori@lori-laptop:~$ ls -l /etc/modprobe.d/oss-compat
lrwxrwxrwx 1 root root 21 2009-08-29 19:22 /etc/modprobe.d/oss-compat -> /lib/oss-compat/linux
lori@lori-laptop:~$ ls /lib/oss-compat/linux
ls: cannot access /lib/oss-compat/linux: No such file or directory

How can I fix this? I cannot use Synpatic Manager or do any updates or installs.

Thanks!!

---

### Post by cLos420 on 2009-10-02
I'm not having the same problem. Instead the download is taking forever from the Update Manager.
800 b/s yea, that slow. Probably everyone is downloading it at the same time. Are there any mirrors?

---

### Post by Partyboi2 on 2009-10-02
> **cLos420 said:**
> I'm not having the same problem. Instead the download is taking forever from the Update Manager.
800 b/s yea, that slow. Probably everyone is downloading it at the same time. Are there any mirrors?
The servers seem to be a little slow at the moment, if you want to try another server you can go to Software Sources (System>Admin>Software Sources) and under the first tab change the download server to something else.

---

### Post by airmid on 2009-10-02
O.K. I "fixed" the issue by simply removed the /etc/modprode.d/oss-compat which was linked to nothing. I then ran sudo dpkg --configure -a and it completed successfully. 

I can now use dpkg and apt and Synapatic Manager.

---

