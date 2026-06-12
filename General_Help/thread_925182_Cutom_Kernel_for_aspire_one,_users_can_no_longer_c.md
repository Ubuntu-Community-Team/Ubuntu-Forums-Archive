---
title: "Cutom Kernel for aspire one, users can no longer compile"
date: 2008-09-20
forum: General Help
---

### Post by Syco54645 on 2008-09-20
Hello,

I am a kernel hacker for the oneLinux project.  I have made great progress in slimming down the kernel so that the Acer Aspire One will boot faster.  The only problem that I am having is that once users install the deb files for the headers and images that they can no longer compile.  It gives an error about kernelpath.  I cannot reproduce this since it works fine for me.  I am using the old method to compile (the make-kpkg).  I will point the users of my kernel here so that they can offer their input and try to help with the problem.  Any help is greatly appreciated.

Thanks

-Syco54645

someone has pated the error in irc for me.  it is
make[1]: Entering Directory '/usr/src/linux-headers-2.6.27-rc6-v.8aao'
/usr/src/linux-headers-2.6.27-rc6-v.8aao/arch/x86/Makefile:41: /usr/src/linux-headers-2.6.27-rc6-v.8aao/arch/x86/Makefile_32.cpu: No such file or directory

---

### Post by wrigleyj on 2008-09-23
I captured the output from installing both the linux-image and linux-headers packages and paste them here. It looks like a broken symlink in the linux-image package that should perhaps be in the linux-headers package? (I'm not too familiar with Ubuntu kernel packagin).

Script started on Tue 23 Sep 2008 11:07:33 AM BST
joe@theone:/media/CRUZERMINI$ sudo dpkg -i oneLinux/linux*
Selecting previously deselected package linux-headers-2.6.27-rc6-v.8.2aao.
(Reading database ... 111991 files and directories currently installed.)
Unpacking linux-headers-2.6.27-rc6-v.8.2aao (from .../linux-headers-2.6.27-rc6-v.8.2aao_2.6.27-rc6-v.8.2aao-10.00.Custom_i386.deb) ...
Selecting previously deselected package linux-image-2.6.27-rc6-v.8.2aao.
Unpacking linux-image-2.6.27-rc6-v.8.2aao (from .../linux-image-2.6.27-rc6-v.8.2aao_2.6.27-rc6-v.8.2aao-10.00.Custom_i386.deb) ...
Done.
Setting up linux-headers-2.6.27-rc6-v.8.2aao (2.6.27-rc6-v.8.2aao-10.00.Custom) ...

Setting up linux-image-2.6.27-rc6-v.8.2aao (2.6.27-rc6-v.8.2aao-10.00.Custom) ...

 Hmm. There is a symbolic link /lib/modules/2.6.27-rc6-v.8.2aao/build
 However, I can not read it: No such file or directory
 Therefore, I am deleting /lib/modules/2.6.27-rc6-v.8.2aao/build


 Hmm. The package shipped with a symbolic link /lib/modules/2.6.27-rc6-v.8.2aao/source
 However, I can not read the target: No such file or directory
 Therefore, I am deleting /lib/modules/2.6.27-rc6-v.8.2aao/source

Running depmod.
Finding valid ramdisk creators.
Using mkinitramfs-kpkg to build the ramdisk.
Running postinst hook script update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-rc6-v.8.2aao
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

joe@theone:~$ exit
Script done on Tue 23 Sep 2008 11:12:55 AM BST

---

### Post by wrigleyj on 2008-09-23
I just had a look at the old kernel and note the following:

# ls /lib/modules/2.6.24-19-generic/build -lh
lrwxrwxrwx 1 root root 40 2008-09-22 16:49 /lib/modules/2.6.24-19-generic/build -> /usr/src/linux-headers-2.6.24-19-generic
# dpkg-query -S /lib/modules/2.6.24-19-generic/build
linux-headers-2.6.24-19-generic: /lib/modules/2.6.24-19-generic/build

Which would imply that the build symlink should only be part of the linux-headers*aao package (which it is) and not the linux-image*aao package.

---

