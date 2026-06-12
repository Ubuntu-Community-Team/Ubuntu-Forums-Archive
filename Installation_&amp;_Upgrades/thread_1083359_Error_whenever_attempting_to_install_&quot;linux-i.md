---
title: "Error whenever attempting to install &quot;linux-image-2.6.27-11-generic&quot;"
date: 2009-02-28
forum: Installation &amp; Upgrades
---

### Post by Xqtftqx on 2009-02-28
Hello, im new on the forum.
Ive been using versions of linux for a long time now, and i decided to try out ubuntu for once, and it has worked perfectly until now.

Whenever i try to upgrade, install, or remove any package, it attempts to install "linux-image-2.6.27-11-generic".

The command "sudo apt-get autoremove" gives the following:
```

Reading package lists...
Building dependency tree...
Reading state information...
0 upgraded, 0 newly installed, 0 to remove and 75 not upgraded.
7 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.27-11-generic (2.6.27-11.27) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.27-11-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-11-generic
Found kernel: /boot/vmlinuz-2.6.27-9-generic
Found kernel: /boot/vmlinuz-2.6.24-22-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.27-11-generic       [80G 
 *  nvidia (177.82)...       [80G nvidia (177.82): Already installed on this kernel.

[74G[ OK ]
 *  vboxdrv (2.0.4)...       [80G vboxdrv (2.0.4): Already installed on this kernel.

[74G[ OK ]
run-parts: executing /etc/kernel/postinst.d/nvidia-common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.27-11-generic.postinst line 1002.
dpkg: error processing linux-image-2.6.27-11-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.27-11-generic:
 linux-restricted-modules-2.6.27-11-generic depends on linux-image-2.6.27-11-generic; however:
  Package linux-image-2.6.27-11-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.27-11-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.27-11-generic; however:
  Package linux-image-2.6.27-11-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.27-11-generic; however:
  Package linux-restricted-modules-2.6.27-11-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.27.11.14); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.27.11.14); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-2.6.27-11-generic (2.6.27-11.27) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.27-11-generic       [80G 
 *  nvidia (177.82)...       [80G nvidia (177.82): Already installed on this kernel.

[74G[ OK ]
 *  vboxdrv (2.0.4)...       [80G vboxdrv (2.0.4): Already installed on this kernel.

[74G[ OK ]
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.27-11-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.27-11-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.27-11-generic; however:
  Package linux-headers-2.6.27-11-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.27-11-generic
 linux-restricted-modules-2.6.27-11-generic
 linux-image-generic
 linux-restricted-modules-generic
 linux-generic
 linux-headers-2.6.27-11-generic
 linux-headers-generic

```

It fails with an error code of 1.

For future help, thank you.
If anybody else needs anything else, just ask.

---

### Post by darco on 2009-03-01
oops, I misread your post......... are you trying to install 27.11 or another package?

darco

---

### Post by caljohnsmith on 2009-03-02
How about trying:
```
sudo apt-get purge linux-image-2.6.27-11-generic linux-restricted-modules-2.6.27-11-generic
sudo apt-get install linux-image-2.6.27-11-generic linux-restricted-modules-2.6.27-11-generic
```
And please post the output of both commands.

---

### Post by Xqtftqx on 2009-03-02
Whenever i try to install another package, it tries to install it and no it just wastes time.

First command:
```

xqtftqx@xqtftqx-laptop:~$ sudo apt-get purge linux-image-2.6.27-11-generic linux-restricted-modules-2.6.27-11-generic
[sudo] password for xqtftqx: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-generic* linux-image-2.6.27-11-generic* linux-image-generic*
  linux-restricted-modules-2.6.27-11-generic*
  linux-restricted-modules-generic*
0 upgraded, 0 newly installed, 5 to remove and 75 not upgraded.
7 not fully installed or removed.
After this operation, 96.7MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 155151 files and directories currently installed.)
Removing linux-generic ...
Removing linux-restricted-modules-generic ...
Removing linux-restricted-modules-2.6.27-11-generic ...
rmdir: failed to remove `/lib/modules/2.6.27-11-generic/volatile/': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.27-11-generic
Purging configuration files for linux-restricted-modules-2.6.27-11-generic ...
Removing linux-image-generic ...
Removing linux-image-2.6.27-11-generic ...
WARN: Proceeding with removing running kernel image.
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms
Uninstalling: vboxdrv 2.0.4 (2.6.27-11-generic) (i686)

-------- Uninstall Beginning --------
Module:  vboxdrv
Version: 2.0.4
Kernel:  2.6.27-11-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/2.6.27-11-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.
depmod....

DKMS: uninstall Completed.
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
/etc/kernel/prerm.d/last-good-boot: 3: /usr/sbin/kernel-helper: not found
run-parts: /etc/kernel/prerm.d/last-good-boot exited with return code 127
Failed to process /etc/kernel/prerm.d at /var/lib/dpkg/info/linux-image-2.6.27-11-generic.prerm line 267.
dpkg: error processing linux-image-2.6.27-11-generic (--purge):
 subprocess pre-removal script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.27-11-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

And the second:
```
 sudo apt-get install linux-image-2.6.27-11-generic linux-restricted-modules-2.6.27-11-generic
[sudo] password for xqtftqx: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-image-2.6.27-11-generic is already the newest version.
The following NEW packages will be installed:
  linux-restricted-modules-2.6.27-11-generic
0 upgraded, 1 newly installed, 0 to remove and 75 not upgraded.
3 not fully installed or removed.
Need to get 766kB of archives.
After this operation, 2224kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com intrepid-updates/restricted linux-restricted-modules-2.6.27-11-generic 2.6.27-11.16 [766kB]
Fetched 766kB in 2s (270kB/s)                                      
Selecting previously deselected package linux-restricted-modules-2.6.27-11-generic.
(Reading database ... 155085 files and directories currently installed.)
Unpacking linux-restricted-modules-2.6.27-11-generic (from .../linux-restricted-modules-2.6.27-11-generic_2.6.27-11.16_i386.deb) ...
Setting up linux-image-2.6.27-11-generic (2.6.27-11.27) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.27-11-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-11-generic
Found kernel: /boot/vmlinuz-2.6.27-9-generic
Found kernel: /boot/vmlinuz-2.6.24-22-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.27-11-generic          
 *  nvidia (177.82)...                                                          nvidia (177.82): Installing module.
......
 *  vboxdrv (2.0.4)...                                                          vboxdrv (2.0.4): Installing module.
......
run-parts: executing /etc/kernel/postinst.d/nvidia-common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.27-11-generic.postinst line 1002.
dpkg: error processing linux-image-2.6.27-11-generic (--configure):
 subprocess post-installation script returned error exit status 2
Setting up linux-headers-2.6.27-11-generic (2.6.27-11.27) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.27-11-generic          
 *  nvidia (177.82)...                                                          nvidia (177.82): Already installed on this kernel.
                                                                         [ OK ]
 *  vboxdrv (2.0.4)...                                                          vboxdrv (2.0.4): Already installed on this kernel.
                                                                         [ OK ]
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.27-11-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.27-11-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.27-11-generic; however:
  Package linux-headers-2.6.27-11-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.27-11-generic:
 linux-restricted-modules-2.6.27-11-generic depends on linux-image-2.6.27-11-generic; however:
  Package linux-image-2.6.27-11-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.27-11-generic (--configure):
 dependency problemNo apport report written because the error message indicates its a followup error from a previous failure.
                                             No apport report written because MaxReports is reached already
                           s - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.27-11-generic
 linux-headers-2.6.27-11-generic
 linux-headers-generic
 linux-restricted-modules-2.6.27-11-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Sorry for the late reply

---

### Post by caljohnsmith on 2009-03-02
It looks to me like the crux of the problem is your nvidia driver that gets installed into any new kernel:
[QUOTE=Xqtftqx]run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
[/QUOTE]
So that nvidia-common file returned an error 10. You could maybe try uninstalling/reinstalling your nvidia driver and see if that fixes the problem.

---

### Post by mnial on 2009-04-16
and if not?
any ideas on how-to reimstall linux-image-2.6.27-11-generic with all the dependencies?

---

### Post by abhiroopb on 2009-05-11
Similar problem here...

I started another thread...

[http://ubuntuforums.org/showthread.php?t=1156074](http://ubuntuforums.org/showthread.php?t=1156074)

But its the same thing, I'm trying to install 2.6.28-12

---

### Post by Coastalguy on 2009-11-23
I also get an error trying to install these 2 packages. My error seems to indicate it cannot make a backup link??

E: /var/cache/apt/archives/linux-image-2.6.24-19-generic_2.6.24-19.41_i386.deb: unable to make backup link of `./boot/vmlinuz-2.6.24-19-generic' before installing new version
E: /var/cache/apt/archives/linux-image-2.6.24-24-generic_2.6.24-24.61_i386.deb: unable to make backup link of `./boot/vmlinuz-2.6.24-24-generic' before installing new version

---

