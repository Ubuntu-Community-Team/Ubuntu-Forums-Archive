---
title: "DKPG problem and w760i connection"
date: 2008-08-10
forum: General Help
---

### Post by Aslund on 2008-08-10
Hey all

Got two problems here, not sure if they are realted. After a system update I started to get this message: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
So I can't install or update my system anymore, have tried to do what the commad says but with out luck. 
There other thing is my newly bought w760i, when I put it to my laptop, it is possible for me to see the phone as camera, but do not seem I can enter it as a storage drive and add files to it's M2 card.

Thanks for your time and help

Regards

Sebastian Aslund

---

### Post by WRDN on 2008-08-10
Regarding the dpkg error, try clearing the cache, then running the command again.

Run:

```
sudo apt-get clean
```

This will remove all downloaded files in /var/cache

Now run:

```
dpkg --configure -a
```

---

### Post by Aslund on 2008-08-10
The problem is still there, here is the info I get when I run it: 

aslund@LordAslund:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu39.2) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-image-2.6.24-20-generic (2.6.24-20.38) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-20-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-20-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.24-20-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-20-generic; however:
  Package linux-image-2.6.24-20-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-20-generic:
 linux-ubuntu-modules-2.6.24-20-generic depends on linux-image-2.6.24-20-generic; however:
  Package linux-image-2.6.24-20-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-20-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.20.22); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-20-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-20-generic
dpkg: subprocess post-installation script returned error exit status 1

---

### Post by joffa82 on 2008-08-12
I'm having the same or similar issue to you after just updating my system. I can't even open synaptic now.

```

geoff@geoff-laptop:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu39.2) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.26
Cannot find /lib/modules/2.6.26
update-initramfs: failed for /boot/initrd.img-2.6.26
dpkg: subprocess post-installation script returned error exit status 1
geoff@geoff-laptop:~$ sudo apt-get clean
geoff@geoff-laptop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
geoff@geoff-laptop:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu39.2) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.26
Cannot find /lib/modules/2.6.26
update-initramfs: failed for /boot/initrd.img-2.6.26
dpkg: subprocess post-installation script returned error exit status 1
geoff@geoff-laptop:~$ 

```

I'm still learning my way around linux so i'm a bit stumped what to do.

---

### Post by esteban09 on 2008-10-10
Hi,

I got the same problem too... 
After digging around I found out the command 'update-initramfs -u' was failing, while
installing 'initramfs-tools_0.85eubuntu39.2_all.deb'.

Executing 'update-initramfs -c -k all' works fine, so everything with the packet was
ok, but the command 'update-initramfs -u' on the commandline failed too.

It turned out that 'update-initramfs -u' is reading the kernel versions, for which
the initrd should be updated from filenames in '/var/lib/initramfs-tools' and there
was besides the file for the actually installed kernel, also a file '2.6.26'.
You have to delete this file and the command 'dpkg --configure -a' works fine.

regards,
esteban

---

### Post by GonZo on 2009-07-02
Show [this]("http://ubuntuforums.org/showthread.php?p=7549944#post7549944") thread to know everything about w760i and ubuntu

---

