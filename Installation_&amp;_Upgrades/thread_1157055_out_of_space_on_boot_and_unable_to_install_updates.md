---
title: "out of space on /boot and unable to install updates"
date: 2009-05-12
forum: Installation &amp; Upgrades
---

### Post by kartik_vad on 2009-05-12
When I try to install any updates from the Update Manager, it asks me to run dpkg --configure -a. So I do that, but as part of the process, gzip complains there's no space left:

root@enlightenment:/boot# dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu39.3) ...
update-initramfs: deferring update (trigger activated)

dpkg: dependency problems prevent configuration of openoffice.org-style-human:
 openoffice.org-style-human depends on openoffice.org-common (= 1:2.4.1-1ubuntu2.1); however:
  Version of openoffice.org-common on system is 1:2.4.1-1ubuntu2.
dpkg: error processing openoffice.org-style-human (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (= 1:2.4.1-1ubuntu2.1); however:
  Version of openoffice.org-core on system is 1:2.4.1-1ubuntu2.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 1:2.4.1-1ubuntu2.1); however:
  Version of openoffice.org-core on system is 1:2.4.1-1ubuntu2.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-crystal:
 openoffice.org-style-crystal depends on openoffice.org-common (= 1:2.4.1-1ubuntu2.1); however:
  Version of openoffice.org-common on system is 1:2.4.1-1ubuntu2.
dpkg: error processing openoffice.org-style-crystal (--configure):
 dependency problems - leaving unconfigured
Setting up linux-ubuntu-modules-2.6.24-23-generic (2.6.24-23.37) ...
update-initramfs: Generating /boot/initrd.img-2.6.24-23-generic

dpkg: dependency problems prevent configuration of openoffice.org-calc:
 openoffice.org-calc depends on openoffice.org-base-core (= 1:2.4.1-1ubuntu2.1); however:
  Version of openoffice.org-base-core on system is 1:2.4.1-1ubuntu2.
 openoffice.org-calc depends on openoffice.org-core (= 1:2.4.1-1ubuntu2.1); however:
  Version of openoffice.org-core on system is 1:2.4.1-1ubuntu2.
dpkg: error processing openoffice.org-calc (--configure):
 dependency problems - leaving unconfigured
Setting up linux-ubuntu-modules-2.6.24-21-generic (2.6.24-21.33) ...
update-initramfs: Generating /boot/initrd.img-2.6.24-21-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-21-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-21-generic (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of openoffice.org-common:
 openoffice.org-common depends on openoffice.org-style-human | openoffice.org-style-tango | openoffice.org-style-crystal | openoffice.org-style-andromeda; however:
  Package openoffice.org-style-human is not configured yet.
  Package openoffice.org-style-tango is not installed.
  Package openoffice.org-style-crystal is not configured yet.
  Package openoffice.org-style-andromeda is not installed.
dpkg: error processing openoffice.org-common (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-23-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-23-generic
dpkg: subprocess post-installation script returned error exit status 1


Sure enough, there's no space left on /boot (only 5.9MB). I found some initrd*.bak files there that moved to /, but that's still not enough:

root@enlightenment:/boot# ls -lhA 
total 33M
-rw-r--r-- 1 root root 413K 2008-08-21 10:16 abi-2.6.24-19-generic
-rw-r--r-- 1 root root 413K 2008-10-22 08:42 abi-2.6.24-21-generic
-rw-r--r-- 1 root root 413K 2009-01-26 10:00 abi-2.6.24-23-generic
-rw-r--r-- 1 root root  79K 2008-08-21 10:16 config-2.6.24-19-generic
-rw-r--r-- 1 root root  79K 2008-10-22 08:42 config-2.6.24-21-generic
-rw-r--r-- 1 root root  79K 2009-01-26 10:00 config-2.6.24-23-generic
drwxr-xr-x 2 root root 1.0K 2009-05-12 19:33 grub
-rw-r--r-- 1 root root 7.6M 2008-10-12 17:31 initrd.img-2.6.24-19-generic
-rw-r--r-- 1 root root 7.6M 2009-05-12 19:33 initrd.img-2.6.24-21-generic
-rw-r--r-- 1 root root 7.6M 2009-05-12 19:35 initrd.img-2.6.24-23-generic
drwx------ 2 root root  12K 2008-10-05 18:20 lost+found
-rw-r--r-- 1 root root 101K 2007-09-28 15:36 memtest86+.bin
-rw-r--r-- 1 root root 884K 2008-08-21 10:16 System.map-2.6.24-19-generic
-rw-r--r-- 1 root root 885K 2008-10-22 08:42 System.map-2.6.24-21-generic
-rw-r--r-- 1 root root 885K 2009-01-26 10:00 System.map-2.6.24-23-generic
-rw-r--r-- 1 root root 1.9M 2008-08-21 10:16 vmlinuz-2.6.24-19-generic
-rw-r--r-- 1 root root 1.9M 2008-10-22 08:42 vmlinuz-2.6.24-21-generic
-rw-r--r-- 1 root root 1.9M 2009-01-26 10:00 vmlinuz-2.6.24-23-generic


Which of these can I safely delete? Do I really need three versions of vmlinuz and initrd? Can I move one set of these to / and symlink them from /boot, if that helps?

---

### Post by Partyboi2 on 2009-05-12
Hi, you can open up Synaptic and do a search for "linux-image" and uninstall the ones you know longer need but make sure you keep the latest one.

---

### Post by kartik_vad on 2009-06-27
Sorry for the late reply. I tried to do that, but synaptic doesn't run, asking me to run:
dpkg --configure -a

apt-get -f install also gives the same error. So now I'm in a catch 22 situation. What do I do? Go to the dpkg layer directly bypassing apt?

---

### Post by presence1960 on 2009-06-27
you need to get / more space. try gparted. shrink a partition next to / and then extend / using that space. Take a look at your partitions and see if you can do that.

---

### Post by drs305 on 2009-06-27
There is the link to a guide I wrote about recovering lost disk space, analyzing why you ran out, and how to fix it, in my signature line.

For this particular issue, you can run "uname -r" which will show your current kernel version. Remember that one and then open nautilus:
```

gksudo nautilus /boot

```
Delete one of the older ones - *vmlinuz-2.6.24-19-generic* would probably be a safe bet unless that is the one you are using. Use SHIFT-DELETE to delete the file, otherwise it will be moved to root's trash but still take up space in the partition. You can also delete the associated system map and initrd files.

That should then give you enough breathing room to open synaptic and remove some of the other older kernels ("linux-image-2.6.24-XXX"). Example: linux-image-2.6.24-19-generic.  Keep the one you are using plus one other. If removed via Synaptic your grub menu will be automatically trimmed - removing kernel options that no longer are on your system.

---

