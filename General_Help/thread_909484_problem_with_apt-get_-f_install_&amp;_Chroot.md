---
title: "problem with apt-get -f install &amp; Chroot"
date: 2008-09-03
forum: General Help
---

### Post by a.dehqan on 2008-09-03
In The name of God
Hello

I'll be Thankfull if you guide me :
I have a harddisk from ,for example, system 1  ,That debian is installed on it.
I added it on another system (for example system 2) ,and We used ubuntu live cd to boot system 2 .
I want to install some packages on debian ,therefore i used chroot .
Now When i use command "apt-get -f install" it gives me these errors :

```
ubuntu:/# apt-get -f install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 172 not upgraded.
5 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up linux-image-2.6.18-6-486 (2.6.18.dfsg.1-22etch2) ...
Running depmod.
Finding valid ramdisk creators.
Using mkinitramfs-kpkg to build the ramdisk.
The link /initrd.img is a dangling linkto /boot/initrd.img-2.6.18-4-486
The link /vmlinuz is a dangling linkto /boot/vmlinuz-2.6.18-4-486
Running postinst hook script /sbin/update-grub.
You shouldn't call /sbin/update-grub. Please call /usr/sbin/update-grub instead!

Searching for GRUB installation directory ... 
No GRUB directory found.
 To create a template run 'mkdir /boot/grub' first.
 To install grub, install it manually or try the 'grub-install' command.
 ### Warning, grub-install is used to change your MBR. ###

User postinst hook script [/sbin/update-grub] exited with value 1
dpkg: error processing linux-image-2.6.18-6-486 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-2.6-486:
 linux-image-2.6-486 depends on linux-image-2.6.18-6-486; however:
  Package linux-image-2.6.18-6-486 is not configured yet.
dpkg: error processing linux-image-2.6-486 (--configure):
 dependency problems - leaving unconfigured
Setting up nvidia-kernel-common (20051028+1) ...

dpkg: dependency problems prevent configuration of nvidia-kernel-legacy-2.6.18-6-486:
 nvidia-kernel-legacy-2.6.18-6-486 depends on linux-image-2.6.18-6-486; however:
  Package linux-image-2.6.18-6-486 is not configured yet.
dpkg: error processing nvidia-kernel-legacy-2.6.18-6-486 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nvidia-kernel-legacy-2.6-486:
 nvidia-kernel-legacy-2.6-486 depends on nvidia-kernel-legacy-2.6.18-6-486; however:
  Package nvidia-kernel-legacy-2.6.18-6-486 is not configured yet.
 nvidia-kernel-legacy-2.6-486 depends on linux-image-2.6-486; however:
  Package linux-image-2.6-486 is not configured yet.
dpkg: error processing nvidia-kernel-legacy-2.6-486 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.18-6-486
 linux-image-2.6-486
 nvidia-kernel-legacy-2.6.18-6-486
 nvidia-kernel-legacy-2.6-486
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

regards dehqan

---

### Post by a.dehqan on 2008-09-05
In The Name Of God
Hello


Before above error that is commented , it gave me this error:

```
ubuntu:/# apt-get -f install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 172 not upgraded.
5 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up linux-image-2.6.18-6-486 (2.6.18.dfsg.1-22etch2) ...
sh: /dev/null: Permission denied
sh: /dev/null: Permission denied
Running depmod.
Finding valid ramdisk creators.
sh: /dev/null: Permission denied
sh: /dev/null: Permission denied
Failed to find suitable ramdisk generation tool for kernel version 
2.6.18-6-486 on running kernel 2.6.24-19-generic in mkinitramfs-kpkg mkinitrd.yaird
dpkg: error processing linux-image-2.6.18-6-486 (--configure):
 subprocess post-installation script returned error exit status 9
dpkg: dependency problems prevent configuration of linux-image-2.6-486:
 linux-image-2.6-486 depends on linux-image-2.6.18-6-486; however:
  Package linux-image-2.6.18-6-486 is not configured yet.
dpkg: error processing linux-image-2.6-486 (--configure):
 dependency problems - leaving unconfigured
Setting up nvidia-kernel-common (20051028+1) ...
/var/lib/dpkg/info/nvidia-kernel-common.postinst: line 27: /dev/null: Permission denied
/var/lib/dpkg/info/nvidia-kernel-common.postinst: line 34: /dev/null: Permission denied
dpkg: error processing nvidia-kernel-common (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of nvidia-kernel-legacy-2.6.18-6-486:
 nvidia-kernel-legacy-2.6.18-6-486 depends on nvidia-kernel-common (>= 20050829); however:
  Package nvidia-kernel-common is not configured yet.
 nvidia-kernel-legacy-2.6.18-6-486 depends on linux-image-2.6.18-6-486; however:
  Package linux-image-2.6.18-6-486 is not configured yet.
dpkg: error processing nvidia-kernel-legacy-2.6.18-6-486 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nvidia-kernel-legacy-2.6-486:
 nvidia-kernel-legacy-2.6-486 depends on nvidia-kernel-legacy-2.6.18-6-486; however:
  Package nvidia-kernel-legacy-2.6.18-6-486 is not configured yet.
 nvidia-kernel-legacy-2.6-486 depends on linux-image-2.6-486; however:
  Package linux-image-2.6-486 is not configured yet.
dpkg: error processing nvidia-kernel-legacy-2.6-486 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.18-6-486
 linux-image-2.6-486
 nvidia-kernel-common
 nvidia-kernel-legacy-2.6.18-6-486
 nvidia-kernel-legacy-2.6-486
E: Sub-process /usr/bin/dpkg returned an error code (1)
ubuntu:/# ls -ld /dev/null
crwxrwxrwx 1 root root 1, 3 2008-08-16 20:42 /dev/null
```

I fixed the problem with this command :"mount --bind /dev /media/disk/dev".


but now, if i want to do so "mount --bind /boot /media/disk/boot " to fix the problem it gives an error cause of that version of live cd grub files do not match debian files version .

regards dehqan

---

### Post by a.dehqan on 2008-09-08
In The name Of God
hello

The problem fixed when i mounted boot partition .

reagrs dehqan

---

