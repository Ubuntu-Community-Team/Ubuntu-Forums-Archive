---
title: "mkinitramfs not creating proper initrd after update to newer kernel"
date: 2009-05-20
forum: Installation &amp; Upgrades
---

### Post by djBo on 2009-05-20
Hi list,

My system:
AMD Athlon 64 X2 6400+/4Gb RAM
ATI Radeon 3870 PCIe (using ati fglrx)
sata boot disk
sata storage disks
Ubuntu 8.10 running 2.6.27-11-generic

My issue:
For some reason, after I have done a kernel upgrade, mkinitramfs will not create a proper initrd that boots my system even though nothing has changed before/after the upgrade. In this case I am trying to upgrade to 2.6.27.14-generic.

I have had this with the previous kernel update too, and had not made a backup copy of the working initrd image. I had reinstalled my system to overcome the problem... I know... silly.

This time round I had made a backup, and have been using the 2.6.27-11 kernel still. I had to boot from the cd in order to fix my grub menu, which it also had nicely overwritten too after the update.

The weird thing is, when I try to create a new initrd image for the current running kernel by hand, I am faced again with a non working initrd image (not finding/booting my hdd)...

The command I use to create the image:
mkinitramfs -o /boot/initrd.img-2.6.27.14-generic-new 2.6.27.14-generic

When booting, I simply edit the command line to rename the initrd image to boot it.

I hope someone can shed some light on my issue as to why this is not working as expected.

Thanks in advance for any assistance.
Bo

---

### Post by HeadHunter00 on 2010-08-15
Run this command and tell me if it starts working again
```
sudo apt-get remove realpath bootcd-i386 bootcd bootcd-mkinitramfs fdutils realpath bootcd-i386 bootcd bootcd-mkinitramfs bootcd-backup fdutils bootcd-i386 bootcd bootcd-mkinitramfs bootcd-backup bootcd-i386 bootcd libaio1 seabios bridge-utils qemu-kvm vgabios qemu-common kernel-package bootcd-mkinitramfs bootcd-i386 bootcd-mkinitramfs bootcd-i386 bootcd bootcd-mkinitramfs cryptsetup realpath bootcd-i386 bootcd fdutils bootcd-i386 bootcd bootcd-i386 bootcd
```

---

