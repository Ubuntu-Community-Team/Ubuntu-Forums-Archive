---
title: "Install 9.04 alt CD to LVM no GRUB install"
date: 2009-08-29
forum: Installation &amp; Upgrades
---

### Post by poonla on 2009-08-29
I built a new system with a new empty 1 TB hard drive.  I installed Windows Vista in a 200GB primary partition and left the rest of the disk unused. I  installed Ubuntu several different ways into the remaining space on the disk, but I can't get it the way I want it.

What I want is a GRUB dual boot setup with Ubuntu installed into an LVM in the remaining 800GB empty space.  

There's a guided partitioning option to install Ubuntu into an LVM using the entire disk, but I don't want to do that because I want to keep my Vista system in the first partition.  There is no guided option to install Ubuntu into an LVM in the remaining space.  

I set expert mode (F6 from initial install splash screen) to get the most control over the install and tried manually partitioning. I created a 10 GB swap partition at the end of the unallocated disk space, then created a LVM physical volume group in the empty space. I created a logical volume for root / and another logical volume for /home.  

The install proceeded successfully, then I got to the option to install LILO.  Since I want GRUB and not LILO, I skipped the LILO step and told the installer not to install a boot loader.  I finished the install, but there was never an option to install GRUB.  So now I have Ubuntu installed into an LVM extended partition with no way to boot it.  Windows boots normally.  

How can I get GRUB installed so I can dual boot Vista or Ubuntu?   

Thanks for any help.  I'm not a Linux newbie, but I'm not very familiar with the Ubuntu installation process.

---

### Post by poonla on 2009-08-30
Solved.  

I started over.  This time I created primary partition #2 as a bootable ext3 partition for /boot, then I created an LVM PV in an extended partition in the remaining space on the disk.  I created an LV for swap, for root, and for home.   

This time when I got to the boot loader part of the install script, I had the option of installing LILO or GRUB.  I chose GRUB, installed it into the mbr, and it worked.  Now I can dual boot either Vista or Ubuntu.

Evidently, you must have /boot mounted in a primary bootable partition in order for GRUB to be presented by the installer as a possible boot loader.

---

### Post by poonla on 2009-08-30
I think it would be useful to have the required partitioning information documented for those who want to set up non-default configurations that aren't automatically handled by the installer.  I searched, and it is possible that I simply missed it, but the minimum required partitions that have to be set up in order to get GRUB set up in a manual LVM or LVM+Encrypted install don't appear to be explained anywhere. And there is no guided partitioning installation that addresses the situation that I had, even though I believe it is not an uncommon one.  

Of course if one is really an "expert", then the Expert installation method using the alternate CD should pose no hurdles.  In reality, the level of expertise varies considerably from person to person, yet the Expert installation method is the only way for someone, experienced or not, to set up a non-automated or less common configuration.

A useful addition to the alternate CD installation would be a guided partitioning option to install Ubuntu using LVM into free space on the disk.  Currently the only choice is to install LVM onto the entire disk, which of course would wipe out any other installed operating systems or data.  Likewise, a guided partitioning option to install LVM and encrypted systems into free space on the disk would be useful.  

Is there some place I can make these suggestions to the distribution builders?

---

