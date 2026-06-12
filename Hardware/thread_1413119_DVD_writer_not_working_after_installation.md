---
title: "DVD writer not working after installation"
date: 2010-02-22
forum: Hardware
---

### Post by Abhinav K Sahdev on 2010-02-22
I installed ubuntu9.10 through the dvdrw drive but after installation the drive did not read nor showed any cd in it.But i could still write on disks for some time. after a few days it would'ntwrite either. .It worked in 9.04. It just keeps on spinning. same problem with another External Dvd writer.
Kindly see to my problem.
Here's what my fstab reads.

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=63ba256c-f261-4019-bbdb-33c7dd120106 /               ext4    errors=remount-ro 0       1
# /windows was on /dev/sda3 during installation
UUID=7FF5-9354  /windows        vfat    defaults,umask=007,gid=46 0       1
# swap was on /dev/sda6 during installation
UUID=d40aca35-0134-4c39-b7df-975361425c1d none            swap    sw              0       0

---

