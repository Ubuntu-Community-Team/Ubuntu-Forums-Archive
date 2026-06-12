---
title: "Generic kernel install"
date: 2009-10-08
forum: Installation &amp; Upgrades
---

### Post by g-raf on 2009-10-08
I'm using the ubuntu studio rt kernel and can't upgrade or install anything because of a bug: [https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/440589](https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/440589)

I need to install the generic kernel to fix this problem. How can i install the generic kernel and boot it up?

---

### Post by g-raf on 2009-10-09
I've tried to install the linux-generic package through synaptic and in the terminal, but it always starts trying to update openoffice.org-emailmerge and then freezes. I can't update or install anything. Is there any way out of this?

---

### Post by g-raf on 2009-10-10
bump

---

### Post by g-raf on 2009-10-13
Please help. At this point, my rt kernel is freezing quite often and i need to install the generic kernel and update the system. I'm afraid if i find no way to install the generic kernel without the installer jumping to "openoffice.org-emailmerge" updates, i will need to reinstall ubuntu studio from disk.

---

### Post by sousana on 2009-10-21
try downloading deb packages from here for example: [http://www.ramoonus.nl/2009/03/24/linux-kernel-2629-installation-guide-for-ubuntu-and-debian-linux/](http://www.ramoonus.nl/2009/03/24/linux-kernel-2629-installation-guide-for-ubuntu-and-debian-linux/)
then in terminal go to folder with the packages and install them with
sudo dpkg -i linux-headers-2.6.29-020629_2.6.29-020629_all.deb 
sudo dpkg -i linux-headers-2.6.29-020629-generic_2.6.29-020629_i386.deb 
sudo dpkg -i linux-image-2.6.29-020629-generic_2.6.29-020629_i386.deb 
this worked for me, dpkg installed only the kernel. hope it helps ;)

---

### Post by g-raf on 2009-10-27
This worked perfectly, problem done fixed. Thanks alot.

---

