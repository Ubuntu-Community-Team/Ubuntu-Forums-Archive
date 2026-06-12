---
title: "Issues with external drive mounting"
date: 2009-10-25
forum: Hardware
---

### Post by TeeRev on 2009-10-25
Hello, 

I've been having a hard time trying to set a partition on an external drive to be able to have read/write access.  I have been reading through the forums and it seems like a fairly common problem, but while I was trying to change some of the mount options by right clicking the drive, properties, volume, and then expanding the section under mount options.  In there I made a mistake and put something into the mount options that must not have been allowed, but now I can't get back to that screen to just set it back to how it was.  I'm not really finding any answers on how to go about resetting this so I'm asking if anyone can help.

Here is some info about my system:

Ubuntu 9.04

output from sudo fdisk -l:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc329c329

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6688    53721328+  83  Linux
/dev/sda2            6689        7296     4883760    5  Extended
/dev/sda5            6689        7296     4883728+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90d590d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2613    20988891    7  HPFS/NTFS
/dev/sdb2            2614        6437    30716280    7  HPFS/NTFS
/dev/sdb3            6438       11536    40957717+  83  Linux




and from fstab:

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=424be993-8e79-4ac6-a650-664d237e301c /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=fef19dd4-4f65-4dbe-b5f8-373729527914 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
//192.168.0.1/        /media/sharename  smbfs   credentials=/root/.smbcredentials,dmask=777,fmask=777   0       0




and from mtab:

/dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.28-16-generic/volatile tmpfs rw,mode=755 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/trev/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=trev 0 0
/dev/sdb2 /media/Windows\0407 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sdb1 /media/BOOT fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0




The volume that I am trying to make available is /dev/sdb3.  Thanks

---

