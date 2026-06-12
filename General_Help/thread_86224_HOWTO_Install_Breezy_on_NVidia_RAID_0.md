---
title: "HOWTO Install Breezy on NVidia RAID 0"
date: 2005-11-04
forum: General Help
---

### Post by MiddleBrooker on 2005-11-04
Hi to all,
after some experience in Gentoo installation I'm writing this HOWTO from my Ubuntu System installed in a Shuttle XPC with TWO Serial ATA Disk in RAID 0 Configuration.
Normally Ubuntu was not able to detect correctly the RAID Stripe from the BIOS so I've used an alternative method to install my favourite distro in my system without leave out the RAID 0 settings (that I like very much :D ); now I'm happy to share my experience with all the members of the forum and I hope in some feedback or suggestion from user much more expert than me :smile:
PS: Sorry for my English!!
 
A special thanks to this [http://gentoo-wiki.com/HOWTO_Install_Gentoo_with_NVRAID_using_dmraid]("http://gentoo-wiki.com/HOWTO_Install_Gentoo_with_NVRAID_using_dmraid") HOWTO from the Gentoo Wiki.

OK, for install Ubuntu on our NVRAID 0 Stripe we need to:

1) Download the Gentoo LiveCD that is able to detect correctly the RAID 0 setup from the BIOS - Download it from here ---> [http://gentoo.osuosl.org/releases/]("http://gentoo.osuosl.org/releases/");

2) Preare an external USB disk or a normal IDE disk to install Ubuntu as the usual method;

My RAID disk have the first little partition as /boot and the second partition as / (ROOT).
```

#root@Mbrooker:~# ls /dev/mapper/
#control
#nvidia_bigjabae
#nvidia_bigjabae1
#nvidia_bigjabae2

```

We're going to install the basicall Ubuntu system into a normal USB or IDE disk and after that we'll copy all the installed system into our NVRAID Stripe (composed of both TWO SATA disks) by using the Gentoo LiveCD; after that we'll work on some system files to get GRUB - DMRAID etc... working correctly during the booting process.

I've installed Ubuntu as the usual method into the normal USB or IDE disk BUT REMEMBER TO DON'T INSTALL GRUB because this grub will not work with your RAID disk, after that I've made the boot with the Gentoo LiveCD and this command at the initial prompt:
```
#gentoo dodmraid
```

First of all be sure to have your internet connection working so run net-setup eth0 and follow the wizard to setup your ethernet card.
Now you should be able to see correctly your RAID partitons under /dev/mapper :
```
#ls /dev/mapper/
```

You should see something like: nvidia_bigjabaeX (nvraid) or sil_XXXXX, depend from your RAID controller.
We can partition the disk via the usual fdisk command:
```
#fdisk /dev/mapper/nvidia_bigjabae
```
[!!!] Please note that if you're partitioning for the first time you must reboot the system and re-run the Gentoo LiveCD for see the new partitions. [!!!]

After that we can mount both Ubuntu disk and the New RAID partition:
```

#mkdir /mnt/Ubuntu_IDE
#mkdir /mnt/Ubuntu_RAID
#mount /dev/hdX /mnt/Ubuntu_IDE
#mount /dev/mapper/nvidia_bigjabae2 /mnt/Ubuntu_RAID
#copy -r /mnt/Ubuntu_IDE/* /mnt/Ubuntu_RAID
#mount /dev/mapper/nvidia_bigjabae1 /mnt/Ubuntu_RAID/boot

```

Now we can remove the temporary IDE, USB and chroot the RAID Ubuntu, so start to tune it:
```
#chroot /mnt/Ubuntu_RAID /bin/bash
```

OK, now we are into the RAID Ubuntu system by the Gentoo LiveCD Kernel; the next part of the HOWTO will let you know how to install Grub and boot the system into your RAID disk.
We need a correctly compiled kernel, so download and build it.
Be sure to add STATICALLY (not as Module) into the kernel configuration all the necessary for your RAID controller and for the RAID support:
```

#
# SCSI device support
#
CONFIG_SCSI=y
# CONFIG_SCSI_PROC_FS is not set

#
# SCSI support type (disk, tape, CD-ROM)
#
CONFIG_BLK_DEV_SD=y
# CONFIG_CHR_DEV_ST is not set
# CONFIG_CHR_DEV_OSST is not set
# CONFIG_BLK_DEV_SR is not set
CONFIG_CHR_DEV_SG=y
# CONFIG_CHR_DEV_SCH is not set

#
# SCSI low-level drivers
#
CONFIG_SCSI_SATA=y
# CONFIG_SCSI_SATA_AHCI is not set
# CONFIG_SCSI_SATA_SVW is not set
# CONFIG_SCSI_ATA_PIIX is not set
CONFIG_SCSI_SATA_NV=y
# CONFIG_SCSI_SATA_PROMISE is not set
# CONFIG_SCSI_SATA_QSTOR is not set
# CONFIG_SCSI_SATA_SX4 is not set
# CONFIG_SCSI_SATA_SIL is not set
# CONFIG_SCSI_SATA_SIS is not set
# CONFIG_SCSI_SATA_ULI is not set
# CONFIG_SCSI_SATA_VIA is not set
# CONFIG_SCSI_SATA_VITESSE is not set

#
# Multi-device support (RAID and LVM)
#
CONFIG_MD=y
CONFIG_BLK_DEV_MD=y
# CONFIG_MD_LINEAR is not set
CONFIG_MD_RAID0=y
# CONFIG_MD_RAID1 is not set
# CONFIG_MD_RAID10 is not set
# CONFIG_MD_RAID5 is not set
# CONFIG_MD_RAID6 is not set
# CONFIG_MD_MULTIPATH is not set
# CONFIG_MD_FAULTY is not set
CONFIG_BLK_DEV_DM=y
CONFIG_DM_CRYPT=y
CONFIG_DM_SNAPSHOT=y
CONFIG_DM_MIRROR=y
CONFIG_DM_ZERO=y
CONFIG_DM_MULTIPATH=y
CONFIG_DM_MULTIPATH_EMC=y

```

Using the chrooted system you'll be able to install via apt-get all the necessary packages to build your kernel via dpkg-buildpackage.
To do this remember to set your internet connection via the Gentoo LiveCD.
After that install the kernel package and don't reboot the system.

Install Grub
```

#apt-get install grub

```

Now I've attached to this thread the dmraidinitrd script (from the gentoo Wiki) to create an image for boot correctly the system.
I've edited it because one link is missing and the package is no longer available (remove the .txt extension from it).
```

apt-get install libselinux1 libselinux1-dev
#wget http://tienstra4.flatnet.tudelft.nl/~gerte/gen2dmraid/linuxrc
#chmod +x dmraidinitrd
#./dmraidinitrd linuxrc initrd
#cp linuxrc /boot
#cp initrd /boot

```

Now make sure you have the kernel image into the /boot directory or the classic vmlinuz link, so lets go to grub configuration:
```

#vi /boot/grub/grub.conf

```

```

title Ubuntu
root (hd0,0)
kernel /vmlinuz-2.6.12 root=/dev/ram0 init=/linuxrc real_root=/dev/mapper/nvidia_bigjabae2
initrd (hd0,0)/initrd

```
[!!!]Remember to append the real_root option to specify your real root device from the device mapper[!!!]

We can install grub as reported in the Gentoo wiki page:
Do not run grub-install! It will not work properly, and will probably detect the sda1, etc. instead of your actual raid. Make also sure not to start grub inside of an chroot enviroment like you propably do if you install from the Gentoo LiveCD and do it like described in the installation manual of gentoo.org. It doesn't know about /dev/mapper so you would get some errors with grub. In this case just jump into another terminal with ALT+F2. Start grub and make sure that it's pointing to /dev/null as a device map.
```

#grub --device-map=/dev/null

```

```

grub> device (hd0,0) /dev/mapper/nvidia_bigjabae1
grub> device (hd0) /dev/mapper/nvidia_bigjabae
grub> root (hd0,0)
grub> setup (hd0)
grub> quit

```


FINISH!!!
You should be able to reboot and select the Ubuntu System installed into your RAID disk, it should be boot up correctly and you can enjoy your RAID 0 system.

Please send to me via this thread some feedbacks or opinions regarding this HOWOT I'll be very happy to have any other suggestion!
Regards,

MiddleBrooker

---

### Post by MiddleBrooker on 2005-11-04
Sorry for the double post, please remove this!
The good post is here [http://www.ubuntuforums.org/showthread.php?t=86219]("http://www.ubuntuforums.org/showthread.php?t=86219")

Thanks

---

