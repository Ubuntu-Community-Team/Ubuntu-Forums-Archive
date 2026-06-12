---
title: "Problem upgrading"
date: 2009-01-16
forum: Installation &amp; Upgrades
---

### Post by Kakistos on 2009-01-16
When I recently upgraded Ubuntu there were some errors. It said to run "dpkg --configure -a".  Which I did.  I've tried this several times, and it always fails.  

This is the terminal output:

chris@chris-desktop:~$ sudo dpkg --configure -a
[sudo] password for chris: 
Setting up linux-image-2.6.24-23-generic (2.6.24-23.46) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-23-generic
Could not find postinst hook script [update-grub].
Looked in: '/bin', '/sbin', '/usr/bin', '/usr/sbin'
dpkg: error processing linux-image-2.6.24-23-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-23-generic:
 linux-restricted-modules-2.6.24-23-generic depends on linux-image-2.6.24-23-generic; however:
  Package linux-image-2.6.24-23-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-23-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-23-generic:
 linux-ubuntu-modules-2.6.24-23-generic depends on linux-image-2.6.24-23-generic; however:
  Package linux-image-2.6.24-23-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-23-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-23-generic; however:
  Package linux-image-2.6.24-23-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-23-generic; however:
  Package linux-ubuntu-modules-2.6.24-23-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-23-generic; however:
  Package linux-restricted-modules-2.6.24-23-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.23.25); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.23.25); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-23-generic
 linux-restricted-modules-2.6.24-23-generic
 linux-ubuntu-modules-2.6.24-23-generic
 linux-image-generic
 linux-restricted-modules-generic
 linux-generic

Any ideas what's going wrong?

C

---

### Post by utnubuuser on 2009-01-16
Hi -- Maybe try disabling the restricted repos in System>>Administration>>Synaptic Package Manager>>Settings>>Repositories>>Universe and Multiverse, doing your upgrade, or running "sudo dpkg --configure -a".  Alternately, make sure your repos are enabled.

PS Seems there's always problems when going through the upgrade path.  I usually make room on the hard disk, install the new version, and in the process import all the settings and documents.  -- I've read that this method tends to give better results.

---

### Post by Kakistos on 2009-01-17
Cheers for the reply.  I've tried that and it didn't work.  I'm going to try upgrading to 8.10 and see if that works any better.

C

---

