---
title: "Installing from linux on attached drive"
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by turtles on 2009-05-18
I searched for a how to only found this out of date one:
[https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/linux-upgrade.html](https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/linux-upgrade.html)

I have the drive attached via a USB to ATA adaptor.

There is an old Ubuntu install on the drive that will not boot (waited too long for updates).

Here is what I had to do so far:

Mounted the drive in Gentoo

mount point is /mnt/osx/
The drives showed up as /dev/sda1 for boot and /dev/sda3 for / on my Gentoo laptop.

```
mount -t auto /dev/sda3 /mnt/osx/
```
```
mount -t auto /dev/sda1 /mnt/osx/boot/
```
```
cd /mnt/osx/
```
```
mkdir work 
```
```
 cd work 
```
```
wget http://mirrors.kernel.org/ubuntu/pool/main/d/debootstrap/debootstrap_1.0.13~jaunty1_all.deb 
```

The next 3 instructions on the outdated guide modified to this:
```
ar -x debootstrap_0.X.X_all.deb
cd ..
zcat work/data.tar.gz | tar xv

```

I had to edit line 16 and remove the forward slash.
```
nano debootstrap-1.0.13/debootstrap
```
(Use CNTRL / to locate line 16)
Edit /sbin/
to be sbin/

Remove all of the the hozed system dirs like bin,sbin,usr,etc etc...
Save /home /var and /root as well as any others you want.
Or move them all to a back up.
This was hasty but it had old symlinks that broke bash
Use with caution check your working dir first.
```
 rm -rf lib 
``` then do the same for bin and sbin
Next I run the command to install the base system over the old system:
```
usr/sbin/debootstrap --arch ARCH jaunty /mnt/osx/
```
ARCH is your arch (usr/sbin/debootstrap --arch i386 jaunty /mnt/osx/) In my case
It ends with:
> W: Failure while configuring base packages.  This will be attempted 5 times.
I: Configuring udev...
W: Failure while configuring base packages.  This will be attempted 5 times.

I did not get a working copy of nano and a few other things so I am copying over mine:
```
cp -avx /lib/libncurses* lib/ && cp /bin/nano bin/nano
```
Next I am going bind my working system to the base of the new system:
```
mount -t proc none /mnt/osx/proc
mount -o bind /dev /mnt/osx/dev/
```
And mount the new Ubuntu system:
```
chroot /mnt/osx/ /bin/bash
```
I get some errors like
>  id: cannot find name for group ID 11

but I can see I am in by the bash history for the old root user.
i will update this as i progress.
Any tips or links to an updated guide would be great thanks!

---

### Post by turtles on 2009-05-19
Well now I get the following error:
```
chroot) $dpkg --configure -a
dpkg: dependency problems prevent configuration of initramfs-tools:
 initramfs-tools depends on klibc-utils (>= 1.5.9-1); however:
  Package klibc-utils is not installed.
 initramfs-tools depends on busybox-initramfs; however:
  Package busybox-initramfs is not installed.
 initramfs-tools depends on cpio; however:
  Package cpio is not installed.
 initramfs-tools depends on module-init-tools; however:
  Package module-init-tools is not installed.
 initramfs-tools depends on findutils (>= 4.2.24); however:
  Package findutils is not installed.
dpkg: error processing initramfs-tools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of udev:
 udev depends on libc6 (>= 2.8); however:
  Package libc6 is not installed.
 udev depends on libselinux1 (>= 2.0.59); however:
  Package libselinux1 is not installed.
 udev depends on libvolume-id1; however:
  Package libvolume-id1 is not installed.
 udev depends on module-init-tools (>= 3.2.1-0ubuntu3); however:
  Package module-init-tools is not installed.
 udev depends on initramfs-tools (>= 0.40ubuntu30); however:
  Package initramfs-tools is not configured yet.
 udev depends on procps; however:
  Package procps is not installed.
 udev depends on adduser; however:
  Package adduser is not installed.
dpkg: error processing udev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 initramfs-tools
 udev
(chroot) $                                  
```

What a mess.
Is is possible to isntall Ubuntu from Gentoo on a host system?

---

### Post by turtles on 2009-05-19
bump

---

### Post by turtles on 2009-05-20
So I take it no one whom hangs out here installs Ubuntu from another linux distro on to a spare hard drive?

---

### Post by PippoFranco on 2009-05-20
I have installed a new version of Ubuntu on a spare USB drive with no problem.

Boot form a live CD,
plug the spare disk,
unmount the disk (leave it on),
start the usual install,
at the partitioning manually select the spare disk,
at the and you will have a bootable disk.

To boot from the new system plug the disk, select from the bios prompt to boot from the USB disk.

Here you are ready. If you boot from the hard disk you will boot the original system unchanged

Franco

---

