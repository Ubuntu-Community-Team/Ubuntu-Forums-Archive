---
title: "Install from Knoppix"
date: 2005-01-28
forum: Installation &amp; Upgrades
---

### Post by ecc6 on 2005-01-28
I recently tried to install Ubuntu and ran into the problem where my partition table is not recognized (reported [here](http://ubuntuforums.org/showthread.php?t=8883&referrerid=4137) ). So I thought I'd try the install from Knoppix instructions given [here](http://www.ubuntulinux.org/wiki/InstallFromKnoppixHowto/view?searchterm=knoppix). Well, that didn't work either. I followed the instructions up to the point where I ran debootstrap. It downloaded eveything fine but as it was installing the packages it quit with this error:

Errors were encountered while processing:
 /var/cache/apt/archives/console-common_0.7.47ubuntu4_all.deb
 /var/cache/apt/archives/evms_2.3.4-1ubuntu2_i386.deb
 /var/cache/apt/archives/mailx_1%3a8.1.2-0.20040524cvs-1_i386.deb
 /var/cache/apt/archives/module-init-tools_3.1-pre2-2ubuntu3_i386.deb
 /var/cache/apt/archives/postfix_2.1.3-1ubuntu17_i386.deb
 /var/cache/apt/archives/postfix-tls_2.1.3-1ubuntu17_i386.deb
W: Failure while installing base packages.  This will be re-attempted up to five times.
I: Configuring the base system...
mv: cannot stat `/mnt/ubuntu/usr/sbin/sendmail': No such file or directory

It seems to me that sendmail is not supposed to be donwloaded and installed. Maybe postfix depends on it. Whatever the case, I can't get past this error. Anybody know anything about debootstrap or how to fix this? I'd really like to install ubuntu but this is the second method that has failed me. Thanks.

---

