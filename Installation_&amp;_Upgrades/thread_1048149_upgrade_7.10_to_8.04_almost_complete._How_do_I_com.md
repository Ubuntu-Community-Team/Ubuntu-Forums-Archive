---
title: "upgrade 7.10 to 8.04 almost complete. How do I complete it?"
date: 2009-01-23
forum: Installation &amp; Upgrades
---

### Post by BramVanOosterhout on 2009-01-23
I did a remote upgrade of a server using 

[FONT="Arial"]ssh -X root@tinkerbell update-manager[/FONT]

There is a long story below, but the short version is:

I killed the Xterm at the step where do-release-upgrade asks to remve obsolete packages. And do-release-upgrade does not restart, because it thinks my system is up to date

My question is:
1. is there a way that I can start somewhere in do-release-upgrade so that I can let it run to a successful completion?

2. Can I manually do the clean up and do whatever would have been done by do-release-upgrade if I had not killed it?

[B]Now for the long story:
========================[/B]

I did a remote upgrade of a server using 

[FONT="Arial"]ssh -X root@tinkerbell update-manager[/FONT]


I know, it's not recommended, but the server is a long way away so I thought, nothing ventured nothing gained.

I used the instructions at
[http://www.howtoforge.com/upgrade-ubuntu-7.10-server-to-8.04-lts](http://www.howtoforge.com/upgrade-ubuntu-7.10-server-to-8.04-lts)

and it worked. After 12 hours I was at the 

> Remove obsolete packages?

18 packages are going to be removed.

 Continue [yN]  Details [d] 
 
 But the screen said: close your running applications. And like an idiot I did, for a moment forgetting that I was upgrading a remote machine.
 
 No harm done, [FONT="Arial"]tinkerbell[/FONT] was still running. and in / it said
 
> lrwxrwxrwx   1 root root    33 2009-01-23 09:51 initrd.img -> boot/initrd.img-2.6.24-23-generic
lrwxrwxrwx   1 root root    33 2009-01-18 08:26 initrd.img.old -> boot/initrd.img-2.6.22-16-generic
...
lrwxrwxrwx   1 root root    30 2009-01-23 09:51 vmlinuz -> boot/vmlinuz-2.6.24-23-generic
lrwxrwxrwx   1 root root    30 2009-01-18 08:26 vmlinuz.old -> boot/vmlinuz-2.6.22-16-generic

So it looked as if the new OS had been set up.

lsb_release confirmed that:
> 
root@tinkerbell:~# lsb_release -a
LSB Version:    core-2.0-ia32:core-3.0-ia32:core-3.1-ia32:core-3.2-ia32:core-2.0-noarch:core-3.0-noarch:core-3.1-noarch:core-3.2-noarch
Distributor ID: Ubuntu
Description:    Ubuntu 8.04.2
Release:        8.04
Codename:       hardy
root@tinkerbell:~#  

The grub menu list on the other hand still shows the old kernel. :

> ## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/hda4 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/hda4 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,3)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST



So I attempted a reboot and that worked fine, except that, as expected it booted into the old kernel
> root@tinkerbell:~# uname -a
Linux tinkerbell.bram.van-oosterhout.org 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i586 GNU/Linux
root@tinkerbell:~#

I tried to continue the upgrade, but 

[FONT="Arial"]ssh -X root@tinkerbell update-manager[/FONT]
says my system is up to date

and 
> root@tinkerbell:~# do-release-upgrade
Checking for a new ubuntu release
No new release found
root@tinkerbell:~# 

and 
> root@tinkerbell:~# apt-get -s dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@tinkerbell:~#  

So all these tools think the upgrade is complete 

I tried running update-grub

it realises that an update of the grub menu.lst is in order, but does not actually do it:
> root@tinkerbell:/# update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-23-generic
Found kernel: /boot/vmlinuz-2.6.22-16-generic
Found kernel: /boot/vmlinuz-2.6.22-14-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

root@tinkerbell:/# diff /boot/grub/menu.lst /boot/grub/menu.lst.090123
root@tinkerbell:/# ls -l /boot/grub/menu.lst
-rw-r--r-- 1 root root 4202 2009-01-23 20:57 /boot/grub/menu.lst
root@tinkerbell:/#   

My question is:
1. is there a way that I can start somewhere in do-release-upgrade so that I can let it run to a successful completion?

2. Can I manually do the clean up and do whatever would have been done by do-release-upgrade if I had not killed it?

---

### Post by Sef on 2009-01-23
>  2. Can I manually do the clean up and do whatever would have been done by do-release-upgrade if I had not killed it?

```
sudo apt-get autoclean
```

---

