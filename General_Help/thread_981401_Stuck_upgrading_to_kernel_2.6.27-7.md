---
title: "Stuck upgrading to kernel 2.6.27-7"
date: 2008-11-13
forum: General Help
---

### Post by ewak on 2008-11-13
After removing old kernel packages with apt-get remove --purge I cannot upgrade to the latest kernel server package.
I've tried to locate the problem in aptitude and finally just purged linux-image-server-2.6.27-17 and tried to install the linux-server package.

I get the following output:

ldconfig deferred processing now taking place
Processing triggers for man-db ...
Setting up linux-image-2.6.24-21-server (2.6.24-21.43) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-21-server
Could not find postinst hook script [usr/sbin/update-grub].
Looked in: '/bin', '/sbin', '/usr/bin', '/usr/sbin'
dpkg: error processing linux-image-2.6.24-21-server (--configure):
 subprocess post-installation script returned error exit status 2
Setting up linux-image-2.6.27-7-server (2.6.27-7.16) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.27-7-server
Could not find postinst hook script [usr/sbin/update-grub].
Looked in: '/bin', '/sbin', '/usr/bin', '/usr/sbin'
dpkg: error processing linux-image-2.6.27-7-server (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-21-server:
 linux-ubuntu-modules-2.6.24-21-server depends on linux-image-2.6.24-21-server; however:
  Package linux-image-2.6.24-21-server is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-21-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-server:
 linux-image-server depends on linux-image-2.6.27-7-server; however:
  Package linux-image-2.6.27-7-server is not configured yet.
dpkg: error processing linux-image-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-image-server (= 2.6.27.7.11); however:
  Package linux-image-server is not configured yet.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because MaxReports is reached already
                No apport report written because MaxReports is reached already
                                                                              Errors were encountered while processing:
 linux-image-2.6.24-21-server
 linux-image-2.6.27-7-server
 linux-ubuntu-modules-2.6.24-21-server
 linux-image-server
 linux-server
E: Sub-process /usr/bin/dpkg returned an error code (1)



Any ideas how to solve this?

---

