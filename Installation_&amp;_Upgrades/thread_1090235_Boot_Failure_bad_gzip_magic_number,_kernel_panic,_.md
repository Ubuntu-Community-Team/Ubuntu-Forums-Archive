---
title: "Boot Failure: bad gzip magic number, kernel panic, initrd.img-2.6.27-7-generic empty"
date: 2009-03-08
forum: Installation &amp; Upgrades
---

### Post by leifw on 2009-03-08
When I boot, after I select Ubuntu 8.10 from the GRUB menu, the kernel fails with a message like:

ACPI: Aborted because bad gzip magic number
Kernel Panic - not syncing: VFS: Unable to mount root filesystem on unknown block (0,0).

I looked around and saw that there had been problems with GRUB's menu and initrd.  Mine didn't appear to have that problem, but my initrd.img-2.6.27-7-generic is empty, i.e. zero bytes long.  That seems like it's probably bad.

Can anyone confirm that that is bad?  Can anyone tell me how I can download a good copy of that file?

Thanks,

Leif

---

### Post by scragar on 2009-03-08
That's your kernel image, one of the other images should work(grub does list multiple kernels, right?), once that's loaded reinstall the kernel:
```
sudo apt-get install linux-headers-2.6.27-11-generic linux-image-2.6.27-11-generic
```
That should be the latest kernel at the time of writing.

---

### Post by wbloos on 2009-03-25
Hi, 

me too.
I've had this problem before, and i reinstalled ubuntu. That got rid of the problem.
But a few weeks later it returned.
I could still boot from a different kernel and form windows which is on another partition on the same disk.
I tried the solution mentioned above, but apt says that the kernel is already installed.
So i removed the packages first and then installed them, which seems to have trigged a few things.
I'm still not sure if it solved the problem... alea iacta est.

Here's what happened:
==========================
username@username-laptop:~$ sudo apt-get install linux-headers-2.6.27-11-generic linux-image-2.6.27-11-generic
[sudo] password for username: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.27-11-generic is already the newest version.
linux-image-2.6.27-11-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
username@username-laptop:~$ sudo apt-get remove linux-headers-2.6.27-11-generic linux-image-2.6.27-11-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-generic linux-headers-2.6.27-11-generic linux-headers-generic
  linux-image-2.6.27-11-generic linux-image-generic
  linux-restricted-modules-2.6.27-11-generic linux-restricted-modules-generic
0 upgraded, 0 newly installed, 7 to remove and 0 not upgraded.
After this operation, 105MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 137094 files and directories currently installed.)
Removing linux-generic ...
Removing linux-headers-generic ...
Removing linux-headers-2.6.27-11-generic ...
Removing linux-restricted-modules-generic ...
Removing linux-restricted-modules-2.6.27-11-generic ...
update-initramfs: Generating /boot/initrd.img-2.6.27-11-generic
Removing linux-image-generic ...
Removing linux-image-2.6.27-11-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms
Uninstalling: nvidia 177.82 (2.6.27-11-generic) (i686)

-------- Uninstall Beginning --------
Module:  nvidia
Version: 177.82
Kernel:  2.6.27-11-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

nvidia.ko:
 - Uninstallation
   - Deleting from: /lib/modules/2.6.27-11-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.
depmod....

DKMS: uninstall Completed.
run-parts: executing /etc/kernel/prerm.d/last-good-boot
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

The link /vmlinuz is a damaged link
Removing symbolic link vmlinuz 
 you may need to re-run your boot loader[grub]
The link /initrd.img is a damaged link
Removing symbolic link initrd.img 
 you may need to re-run your boot loader[grub]
username@username-laptop:~$ sudo apt-get install linux-headers-2.6.27-11-generic linux-image-2.6.27-11-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  fdutils linux-doc-2.6.27 linux-source-2.6.27
The following NEW packages will be installed:
  linux-headers-2.6.27-11-generic linux-image-2.6.27-11-generic
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/24.1MB of archives.
After this operation, 102MB of additional disk space will be used.
Selecting previously deselected package linux-image-2.6.27-11-generic.
(Reading database ... 128325 files and directories currently installed.)
Unpacking linux-image-2.6.27-11-generic (from .../linux-image-2.6.27-11-generic_2.6.27-11.27_i386.deb) ...
Done.

Selecting previously deselected package linux-headers-2.6.27-11-generic.
Unpacking linux-headers-2.6.27-11-generic (from .../linux-headers-2.6.27-11-generic_2.6.27-11.27_i386.deb) ...
Setting up linux-image-2.6.27-11-generic (2.6.27-11.27) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.27-11-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-11-generic
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.27-11-generic                                                                                           
 *  nvidia (177.82)...                                                                                                                                           nvidia (177.82): Installing module.
......
run-parts: executing /etc/kernel/postinst.d/nvidia-common

Setting up linux-headers-2.6.27-11-generic (2.6.27-11.27) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.27-11-generic                                                                                           
 *  nvidia (177.82)...                                                                                                                                           nvidia (177.82): Already installed on this kernel.
                                                                                                                                                          [ OK ]
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common

username@username-laptop:~$ 
=================================================

---

### Post by wbloos on 2009-03-25
yes, it worked.
Thanks a lot.

This is quite a problem though.
I can imagine that users run away from ubuntu for this kind of behavior... it appears to render your computer useless.

Is the problem known?
Is the cause of the problem known?
Is there any work in progress to fix this?

Cheers,

wbloos.

---

### Post by scragar on 2009-03-25
That was my problem with the command, I should have specified --reinstall
```
sudo apt-get --reinstall install linux-headers-2.6.27-11-generic linux-image-2.6.27-11-generic
```
And that would work.

---

### Post by wbloos on 2009-04-02
and again.
this time: ACPI: Aborted because of crc error.

Booted on old kernel en reinstaled new kernel. Fine.

This is terrible. I hope that it's just me who has to reinstall his kernel every two weeks, and that my database server will be spared.
New users will be back on windows in no time.

---

### Post by scragar on 2009-04-02
I have no idea why you are having problems, it's working fine for me.

Could you upload kern.log.1.gz from /var/log that will have far more information on the error(replace 1 with one high every time you've rebooted after reinstalling the kernel).
I'm curious to know why you are having such problems with something that realy shouldn't be an issue at all...

---

### Post by wbloos on 2009-04-02
here it is, replaced my name with "username".
thanks so much for looking into this.

wbloos

---

