---
title: "Partition option during install"
date: 2009-10-15
forum: Installation &amp; Upgrades
---

### Post by emma_peel on 2009-10-15
Hello.

The first time I have installed Ubuntu, I found an option during the guided partition process which gives me choice between :
- 2 partitions, 1 for / and 1 for swap
- 3 partitions, the 2 previous plus 1 for /home
- even more partitions, with /var and /temp partitions

I have to reinstall Ubuntu from scratch and I no longer see this option. This option is not documented in the installation process. I did not find it in the installation process from the CD.

Is this option still available ? How can I use it again, if this option is somehow hidden ?

Thank you for the feedback !

---

### Post by earthpigg on 2009-10-15
***manually partition*** is what you are looking for.

given your post, im pretty sure it isn't to much or to complicated for you.

small (20gb max) partition with the 'mountpoint' of / and give it the bootable flag. ext3 or 4, take your pick.
swap partition of 1-2gb.
rest with the 'mountpoint' of /home. again, ext3 or 4, take your pick.

if you want /var, /temp, etc on their own partitions... go for it. but this is becoming less and less common, more and more depreciated. the advantages are miniscule, and it ends up using more hard drive space than needed.

---

### Post by emma_peel on 2009-10-15
Thank's for the answer.

I know that we can do it manually ... the option I remember gives directly a proposition.

Anyway, if I don't find it again, I will go for a manual partition definition.

---

### Post by louieb on 2009-10-15
Don't recall seeing the option to automatically create anything other that a / (root) and swap partition. Unless its a part of the LVM option which I have not used. 

Have see post saying Open Suse or Fedora installer has the option to create a /home partition - and wondering why Ubuntu/Debian did not offer the same.  Perhaps you were looking at the install for one of those distributions. 

LoL - got my curriosity up too.

---

### Post by emma_peel on 2009-10-16
Find it in the doc :

[https://help.ubuntu.com/9.04/installation-guide/i386/module-details.html#di-partition](https://help.ubuntu.com/9.04/installation-guide/i386/module-details.html#di-partition)

> Next, you will be able to choose from the schemes listed in the table below. All schemes have their pros and cons, some of which are discussed in Appendix C, Partitioning for Ubuntu. If you are unsure, choose the first one. Bear in mind that guided partitioning needs a certain minimal amount of free space to operate with. If you don't give it at least about 1GB of space (depends on chosen scheme), guided partitioning will fail.

Partitioning scheme	Minimum space	Created partitions
All files in one partition	600MB	/, swap
Separate /home partition	500MB	/, /home, swap
Separate /home, /usr, /var and /tmp partitions	1GB	/, /home, /usr, /var, /tmp, swap

But the installer does not ask which one to use ...

---

### Post by earthpigg on 2009-10-16
aha! debian-installer.... the installer used in super old versions of ubuntu, and the one used on the alternate installation cd.

take a look here, this is what you are looking for:
[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

---

