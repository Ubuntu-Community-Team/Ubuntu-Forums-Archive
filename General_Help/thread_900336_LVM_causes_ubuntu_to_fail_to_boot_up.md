---
title: "LVM causes ubuntu to fail to boot up"
date: 2008-08-25
forum: General Help
---

### Post by petervn1 on 2008-08-25
I've been having issues trying to configure my two 500G SATA drives with LVM on Hardy Heron (generic kernel to support the dual core intel chipset). It seems that no matter what, ubuntu fails to boot and instead displays the busybox initramfs command prompt upon rebooting the machine. Unless I wipe out the lvm2 disk type off the partition previously configured with the LVM, ubuntu would not boot. Not sure what is missing. Here is what I did:
- Pre-requisites:
   Ubuntu: hardy heron, 2.6.24-19-generic #1 SMP. Two 500G SATA drives and one SATA DVD-RW burner.
   /dev/sda <- 500G
    /dev/sda1 <- bootable volume
    /dev/sda2 <- swap
   /dev/sdb  <- 500G

- installed the lvm: apt-get install lvm2

- using fdisk created the following partitions
   /dev/sda3 <- primary partition, 50G
   /dev/sda4 <- extended partition
     /dev/sda5 <- logical volume 540G
   /dev/sdb1 <- primary partition, 50G
   /dev/sdb4 <- extended partition
     /dev/sdb5 < logical volume, 550G

- Re-read the partition table:
  partprobe

- added the physical volumes:
   pvcreate /dev/sda3  <- primary partition 50G
   pvcreate /dev/sda5  <- a logical volume within an extended partition, 440G
   pvcreate /dev/sdb1
   pvcreate /dev/sdb5

- created two LVM groups:
   vgcreate vg1 /dev/sda3 /dev/sdb1
   vgcreate vg2 /dev/sda5 /dev/sdb5

- created two logical volumes:
   lvcreate --corelog -m 1 -n mirroredvol vg1 -l 50G /dev/sda3 /dev/sdb1
   lvcreate -L 440G -n datavol vg2 

** No errors so far, everything is looking good, the device-mapper appears to function properly and I can see the mirrored devices in gparted.

I've verified that the volumes are mountable; everything is working as it should. But... as soon as I reboot, I can see that the kernel fails to recognize the LVM partitions, and, what is very bizzar, could not mount the /dev/sda1 volume, could not boot up and displays the busybox initramfs prompt. The only way I was able to get out of this predicament was to load the ubuntu for LiveCD and wipe out the LVM partitions. As soon as I do that, the system is operational again.

---

### Post by petervn1 on 2008-08-27
After researching the problem, I've found the solution. 
Apparently, the evms installed on my ubuntu machine was interferring with LVM. First, I found a lot of error messages in the boot log:

device-mapper: table: 245:1: linear: dm-linear: device lookup failed 

Following the intstructions in the article [http://ubuntuforums.org/showthread.php?t=587450](http://ubuntuforums.org/showthread.php?t=587450) I uninstalled the evms:

sudo aptitude remove evms

Once the emvs and all related packages were removed, I had no issues installing and configuring the LVM partitions on my ubuntu box.

---

