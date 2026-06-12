---
title: "[SOLVED] NTFS no more found"
date: 2007-07-02
forum: Hardware &amp; Laptops
---

### Post by unconcrete on 2007-07-02
Hi all, 
I am a Edgy Eft user and I've reinstalled grub in my Linux partition to use gfxboot in a dual boot system:(. Now I've lost my ntfs partition. 
Only the FAT and Linux partitions remain on my hard drive. 
A similar problem happened when I had Ubuntu Dapper Drake and I followed the manual step by step in this way:
1) sudo mkdir /media/pippo # ntfs
sudo mkdir /media/pluto # vfat
2) sudo gedit /etc/fstab
Add two lines:
devices            mount point      o.s.
/dev/sda1          /media/pippo     ntfs       nls=utf8,umask=0222       0       0
/dev/sda2          /media/pluto     vfat       defaults,umask=0000       0       0
Save fstab
sudo mount -a
This time I can't mount the ntfs partition. I don't know my mistake. Maybe it depends on a difference between the Dapper fstab 
and the Edgy one. Or, applying to Edgy, the Dapper fstab rules Iìve created an erroneous fstab. Can I recover the ntfs partition?

Please help.

---------------------------------------------------------CURRENT EDGY FSTAB----------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                                0  0  
# /dev/sda6
UUID=a6515639-89a1-4753-a488-94309cc1ec80  /              ext3         defaults,errors=remount-ro              0  1  
# /dev/sda1
UUID=E4C0300AC02FE212                      /media/pippo   ntfs         defaults,nls=utf8,umask=0222,gid=46     0  0  
# /dev/sda2
UUID=1006-16B2                             /media/pluto   vfat         defaults,utf8,umask=0000,gid=46         0  0  
# /dev/sda3
# UUID=c0ec6d7e-f4b4-40d5-ab11-a04b99ec3392 /media/sda3     ext3    defaults        0       2
# /dev/sda5
UUID=9206b41a-6f52-477e-8394-bdfadc71329e  none           swap         sw                                      0  0  
/dev/hdd                                   /media/cdrom0  udf,iso9660  user,noauto                             0  0  
/dev/hdc                                   /media/cdrom1  udf,iso9660  user,noauto                             0  0  
/dev/sda2                                  /media/pluto   vfat         defaults                                0  0  
/dev/sda1                                  /media/pippo   ntfs         nls=iso8859-1,users,umask=0222,user,ro  0  0  
/dev/sda5                                  /media/sda5    swap         defaults                                0  0  
------------------------------------      MOUNT ERRORS-------------------------------------------------------------
armonica@persik-desktop:~$ sudo mount -a
Password:
mount: special device /dev/disk/by-uuid/E4C0300AC02FE212 does not exist
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
----------------------------------------------DMSG OUTPUT ----------------------------------------------------------
armonica@persik-desktop:~$ dmesg | tail
[17180099.296000] NTFS-fs error (device sda1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17180099.296000] NTFS-fs error (device sda1): ntfs_fill_super(): Not an NTFS volume.
[17180216.748000] NTFS-fs warning (device sda1): is_boot_sector_ntfs(): Invalid boot sector checksum.
[17180216.748000] NTFS-fs error (device sda1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17180216.748000] NTFS-fs error (device sda1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17180216.748000] NTFS-fs error (device sda1): ntfs_fill_super(): Not an NTFS volume.
[17180247.524000] NTFS-fs warning (device sda1): is_boot_sector_ntfs(): Invalid boot sector checksum.
[17180247.524000] NTFS-fs error (device sda1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17180247.524000] NTFS-fs error (device sda1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17180247.524000] NTFS-fs error (device sda1): ntfs_fill_super(): Not an NTFS volume.
---------------------------------------------------------------------------------------------------

Thanks in advance,

unconcrete

](*,)

---

### Post by romer3r on 2007-11-22
How do you solve, I have the same problem after i install gfxboot

Regards.

---

