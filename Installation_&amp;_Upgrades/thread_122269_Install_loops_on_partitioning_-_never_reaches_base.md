---
title: "Install loops on partitioning - never reaches base install"
date: 2006-01-27
forum: Installation &amp; Upgrades
---

### Post by treblemaker on 2006-01-27
I have a Dell Dimension 4100, 1GHz P-3, with two 80 GB IDE drives.  For historical reasons (ie it's been that way a long time and I never bothered to fix it), the master (hd0) appears as hdb and the slave (hd1) appears as hda.
I have windows XP and Knoppix installed on partitions in hdb with grub installed in the MBR.  hdb is the first boot drive, and both windows and Knoppix boot up just fine.
The partition map looks like this:
```

   Device Boot  Size  Id  System                 Comment
   -------------------------------------------------------------
/dev/hdb1   *   6 GB   7  HPFS/NTFS             # windows system
/dev/hdb2     256 KB  83  Linux                 # linux /boot
/dev/hdb3              f  W95 Ext'd (LBA)     
/dev/hdb5      21 GB   7  HPFS/NTFS             # windows stuff
/dev/hdb6       1 GB   7  HPFS/NTFS             # windows stuff
/dev/hdb7       2 GB   c  W95 FAT32 (LBA)       # windows stuff
/dev/hdb8      34 GB   7  HPFS/NTFS             # windows stuff
/dev/hdb9       1 GB  82  Linux swap / Solaris  
/dev/hdb10      4 GB  83  Linux                 # knoppix
/dev/hdb11      4 GB  83  Linux                 # ubuntu (planned)
/dev/hdb12      4 GB  83  Linux                 # suse (planned)

```
When I get to the partitioning phase, I select manual partitioning.  I changed hdb2 to mount as "/boot" and changed hdb11 to mount as "/"

Here's the problem: After I save the partitioning and exit back to the main install menu, I select the next step, which is to install the base packages.   However, instead, I am immediately returned to the partitioning menu.  There is no error message or explanation given as to why I am back in the partitioning.   The error log shows only the following, repeating for each attempt to proceed with the installation:

...
File descriptor 3 left open
File descriptor 4 left open
File descriptor 5 left open
File descriptor 6 left open
No matching physical volumes found
File descriptor 3 left open
File descriptor 4 left open
File descriptor 5 left open
File descriptor 6 left open
No volume groups found
Reading all physical volumes. This may take a while...

I have previously used this same CD to install to a blank disk [Edited to add:  on this same computer], and also, while booted into knoppix, I confirmed the MD5 sums against /md5sum.txt.

How can I discover why the installer returns to the partitioning tool instead of continuing with the installation?

Thanks and Best Regards,

---

