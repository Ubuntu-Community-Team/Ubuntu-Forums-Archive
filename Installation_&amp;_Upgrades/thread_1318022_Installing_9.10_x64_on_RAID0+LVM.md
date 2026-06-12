---
title: "Installing 9.10 x64 on RAID0+LVM"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by rihad on 2009-11-07
Hello, first of all, I've been able to set up multibooting WinXP/Kubuntu/FreeBSD from RAID0 (ICH9R) before with Kubuntu 8.10/GRUB legacy. But 9.10/GRUB2 is whole another beast. 
First off, the installer always croaks at the "setting up GRUB" stage, so I again rerun the setup from scratch but this time I uncheck the "Install GRUB boot loader" checkbox and try to set it up manually. Here's my setup:
> 
# fdisk -l /dev/mapper/isw_dacdafdfg_RAHID

Disk /dev/mapper/isw_dacdafdfg_RAHID: 320.1 GB, 320079134720 bytes
255 heads, 63 sectors/track, 38914 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8d248d24

                          Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_dacdafdfg_RAHID1   *           1        3039    24410736    7  HPFS/NTFS
/dev/mapper/isw_dacdafdfg_RAHID2            3040        3047       64260   83  Linux
/dev/mapper/isw_dacdafdfg_RAHID3            3048       38304   283201852+  8e  Linux LVM
/dev/mapper/isw_dacdafdfg_RAHID4           38305       38914     4899825   a5  FreeBSD
# chroot /target
# ls -l /boot/grub/
total 0
# grub-install /dev/mapper/isw_dacdafdfg_RAHID
grub-probe: error: no mapping exists for `isw_dacdafdfg_RAHID2'
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
#

Please note that above GRUB assumes correctly that isw_dacdafdfg_RAHID2 is a Linux ext2 boot partition.
> 
# grub-install --modules=ext2 /dev/mapper/isw_dacdafdfg_RAHID
grub-probe: error: no mapping exists for `isw_dacdafdfg_RAHID2'
grub-probe: error: no mapping exists for `isw_dacdafdfg_RAHID2'
grub-probe: error: no mapping exists for `isw_dacdafdfg_RAHID2'
You attempted a cross-disk install, but the filesystem containing /boot/grub does not support UUIDs.

After this stage, the system is unbootable. Please help, I've no idea what else GRUB wants from me, its online documentation is enormous, and I don't know where to look. Shouldn't simple software as GRUB2 be as simple as 1-2-3 to setup? :-(

---

### Post by rihad on 2009-11-07
Anyone, please?

---

### Post by rihad on 2009-11-07
Alright, I've figured it out. It's a known bug in GRUB 2 that it doesn't work correctly with Intel or Nvidia fake RAID. Going back to "Grub legacy" and using an appropriate howto solved the problem for me.

---

### Post by eekie on 2009-11-15
I have the problem only with the 32 bits version.
Good you provide me with the appropriate link to the how to to solve this problem?

---

