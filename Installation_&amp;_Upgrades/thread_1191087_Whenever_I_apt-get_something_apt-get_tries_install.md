---
title: "Whenever I apt-get something apt-get tries installing my kernel"
date: 2009-06-18
forum: Installation &amp; Upgrades
---

### Post by tsft on 2009-06-18
I've installed a new kernel manually - but I got something wrong - the kernel installation itself passed - and I am running this new kernel, but a few things went wrong :

1. I'm using old nVidia graphic card - and when I tried installing it's drivers (as ubuntu offered) - they failed, even though I don't need them.
2. Whenever I try apt-get'ting something apt-get continues from the failed kernel installation. I installed the new kernel from here - [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile), using the old fashined Debian way.
Just to note -the package gets installated - but whenever it finishes that it continues and tries to reinstalled the faulty kernel installation, here's what I get (this is the 2nd time I apt-get libusb-dev and thus 'twas already installed)
```

sudo apt-get install libusb-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libusb-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 15 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.30-some-string-here (2.6.30-some-string-here-10.00.Custom) ...
Running depmod.
Finding valid ramdisk creators.
Using mkinitramfs-kpkg to build the ramdisk.
initrd.img(/boot/initrd.img-2.6.30-some-string-here
) points to /boot/initrd.img-2.6.30-some-string-here
 (/boot/initrd.img-2.6.30-some-string-here) -- doing nothing at /var/lib/dpkg/info/linux-image-2.6.30-some-string-here.postinst line 588.
vmlinuz(/boot/vmlinuz-2.6.30-some-string-here
) points to /boot/vmlinuz-2.6.30-some-string-here
 (/boot/vmlinuz-2.6.30-some-string-here) -- doing nothing at /var/lib/dpkg/info/linux-image-2.6.30-some-string-here.postinst line 588.
Running postinst hook script update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.30-some-string-here
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
run-parts: executing /etc/kernel/postinst.d/nvidia-common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 20
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.30-some-string-here.postinst line 1186.
dpkg: error processing linux-image-2.6.30-some-string-here (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.30-some-string-here
E: Sub-process /usr/bin/dpkg returned an error code (1)

```My questions are - 
1. How do I remove those nVidia drivers faulty installation from my Ubuntu (9.04) machine ? 
2. How do I stop apt-get from trying to install the faulty kernel ?


Thanks in advance.

---

### Post by AlphaLexman on 2009-06-18
I don't know if it is related or not, but this morning I updated my kernel (kubuntu-jj) and on reboot I could not get into X.  I got alot of Nvidia errors, don't recall them now, but I did a reboot to a previous kernel, down loaded the newest Nvidia drivers for my system from [www.nvidia.com](www.nvidia.com), rebooted again to console and followed the directions from the script. Rebooted again and everything was fine.

---

### Post by tsft on 2009-06-18
Nope. It doesn't matter.
I just removed the old drivers (thanks Synaptic!) but the kernel installation keeps going 
on for everything I apt-get 
any ideas ? anyone ? How would anyone remove a faulty kernel installation ?

---

### Post by tsft on 2009-06-19
Anyone ? PLease ?

---

