---
title: "Can't create a working grub file"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by eekie on 2009-11-04
I wanted to install ubuntu 9.10 on striping disks on three computers in my local network. Two computers provided with MSI K9N2 SLI platinum mobo's (nvidia chipsets) gave no problems. The third however provided with MSI 790X-GD70 mobo (AMD chipset) is unwilling to start up ubuntu. Ubuntu 9.04 the previous distribution that I used on this computer worked fine.
Creating partitions (ext4, swap) and installing run fine. I installed the bootloader in the mbr of the devmapper and alternately in the mbr of a sata disk. Bootloader on the devmapper yields error 17, bootloader on the alternate disk (changed the boot sequence in the bios) gives the boot menu, but the files are not found. I checked the kernel version in vmlinuz and initrd with the ones in the boot directory (did this with help of fedora on the same raid array in this computer). I also checked the harddisk number with the harddisk number of windows and fedora. It all corresponds.
In order to use the other operating systems I had to deploy supergrub. Even supergrub does not see ubuntu.
Why does the new ubuntu distribution not get along with my new mobo?

---

### Post by EJeanmaire on 2009-11-04
> **eekie said:**
> I wanted to install ubuntu 9.10 on striping disks on three computers in my local network. Two computers provided with MSI K9N2 SLI platinum mobo's (nvidia chipsets) gave no problems. The third however provided with MSI 790X-GD70 mobo (AMD chipset) is unwilling to start up ubuntu. Ubuntu 9.04 the previous distribution that I used on this computer worked fine.
Creating partitions (ext4, swap) and installing run fine. I installed the bootloader in the mbr of the devmapper and alternately in the mbr of a sata disk. Bootloader on the devmapper yields error 17, bootloader on the alternate disk (changed the boot sequence in the bios) gives the boot menu, but the files are not found. I checked the kernel version in vmlinuz and initrd with the ones in the boot directory (did this with help of fedora on the same raid array in this computer). I also checked the harddisk number with the harddisk number of windows and fedora. It all corresponds.
In order to use the other operating systems I had to deploy supergrub. Even supergrub does not see ubuntu.
Why does the new ubuntu distribution not get along with my new mobo?

Not sure about the super-grub, but 9.10 uses Grub2... you should have tried to chroot into your ubuntu install and type 'update-grub2'  which would try to map out and generate a grub.cfg file for boot choices for you.  Worth a shot.

---

### Post by eekie on 2009-11-05
Hello EJanmaire,
I don't think it has got anything to do with grub2. I have flawlessly installed Ubuntu 9.10 on three machines of almost identical setup. The only difference is the chipsets.

---

### Post by eekie on 2009-11-05
Hello EJanmaire,
I don't think it has got anything to do with grub2. I have flawlessly installed Ubuntu 9.10 on three machines of almost identical setup. The only difference is the chipsets.

---

### Post by hexxamillion on 2009-11-06
Super-Grub will not work with Ubuntu 9.10 because it uses Grub2. However, there is an [Alpha version of Super Grub 2]("http://www.supergrubdisk.org/forum/index.php?topic=343.0") that you could try.  

See if that will help get your boot menu back. Or try a solution similar to this and just modify it if you are not dual booting with Windows:

1. Load a live CD/ or LIVE USB
2. Find where the linux partition is installed i.e.(/dev/sda4)
$ fdisk -l
3. Make a directory to mount the real root partition on
$ sudo mkdir realroot
4. Mount the linux partition in the real root folder so you can access the boot loader
$ sudo mount /dev/<partition> realroot
5. Use grub-install to redirect the real boot loader to the windows boot partition (the first part of the disk sector)
$ grub-install --root-directory=realroot /dev/sda

---

### Post by eekie on 2009-11-06
Hello Hexxamillion !
Supergrub 2 did the trick! The other solution did not work, because the sudo fdisk -l command does not produce the raid partitions.
Still I am puzzled why I could not find the bootloader on this very computer.
Anyway I am sending this reply in Ubuntu 9.10

Thanks

---

