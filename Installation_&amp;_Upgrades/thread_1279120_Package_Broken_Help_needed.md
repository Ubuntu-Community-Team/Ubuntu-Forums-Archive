---
title: "Package Broken Help needed"
date: 2009-09-30
forum: Installation &amp; Upgrades
---

### Post by gratcliffe on 2009-09-30
E: linux-restricted-modules-2.6.28-15-server: subprocess post-removal script returned error exit status 1

The above is the error I get when trying to remove the listed packed. As a result I cannot remove or install anything using synaptic, or thru terminal either.

output from terminal is below

gary@gary-desktop:~$ cd  /var/cache/apt/archives/
gary@gary-desktop:/var/cache/apt/archives$ ls linux-restricted-modules-2.6.28*linux-restricted-modules-2.6.28-15-server_2.6.28-15.20_i386.deb
gary@gary-desktop:/var/cache/apt/archives$ sudo dpkg -r Linux-restricted-modules-2.6.28-15-server
[sudo] password for gary: 
dpkg: status database area is locked by another process
gary@gary-desktop:/var/cache/apt/archives$ sudo dpkg -r Linux-restricted-modules-2.6.28-15-server
(Reading database ... 313759 files and directories currently installed.)
Removing linux-restricted-modules-2.6.28-15-server ...
rmdir: failed to remove `/lib/modules/2.6.28-15-server/volatile/': No such file or directory
FATAL: Could not open '/boot/System.map-2.6.28-15-server': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.28-15-server
Cannot find /lib/modules/2.6.28-15-server
update-initramfs: failed for /boot/initrd.img-2.6.28-15-server
dpkg: error processing linux-restricted-modules-2.6.28-15-server (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-restricted-modules-2.6.28-15-server
gary@gary-desktop:/var/cache/apt/archives$ 


I am fairly new to ubuntu, so my knowledge is limited.  Any help is appreciated.

---

### Post by mikewhatever on 2009-09-30
Try the [How to fix broken package]("https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages") guide.

---

### Post by gratcliffe on 2009-09-30
Thanks tried this but no cigar, the package is still stuck in Mark for removal

---

### Post by mikewhatever on 2009-09-30
Try closing Synaptic and then deleting the broken file:

sudo rm /var/cache/apt/archives/linux-restricted-modules-2.6.28-15-server*.

---

### Post by gratcliffe on 2009-09-30
No joy.
output below

gary@gary-desktop:~$ sudo rm /var/cache/apt/archives/linux-restricted-modules-2.6.28-15-server*
[sudo] password for gary: 
rm: cannot remove `/var/cache/apt/archives/linux-restricted-modules-2.6.28-15-server*': No such file or directory
gary@gary-desktop:~$ cd  /var/cache/apt/archives/gary@gary-desktop:/var/cache/apt/archives$ sudo rm linux-restricted-modules-2.6.28-15-server*
rm: cannot remove `linux-restricted-modules-2.6.28-15-server*': No such file or directory
gary@gary-desktop:/var/cache/apt/archives$ sudo rm linux-restricted-modules-2.6.28-15-server
rm: cannot remove `linux-restricted-modules-2.6.28-15-server': No such file or directory
gary@gary-desktop:/var/cache/apt/archives$ ls
lock  partial
gary@gary-desktop:/var/cache/apt/archives$ dir
lock  partial
gary@gary-desktop:/var/cache/apt/archives$

---

