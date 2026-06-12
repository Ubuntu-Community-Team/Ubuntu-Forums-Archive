---
title: "Partitions constantly being renamed"
date: 2008-07-18
forum: General Help
---

### Post by vigleik on 2008-07-18
I have several partitions on my hard drive, usually called things like sda2. The other day the partitions were suddenly renamed to things like disk-6. That causes me all sorts of trouble, for example Amarok can no longer find my music, which moved from sda2 to disk-6.

So I fixed my problems, only to find that the next time I rebooted the partitions were back to the old names. Now the names have switched again, with my music now on disk-4! There seems to be no system to the madness.

I run 8.04 with the kde4 remix, I have no idea if kde is somehow responsible. A while ago I ran some sort of script to have my partitions automatically mounted, I can't remember exactly what I did.

Oh, and I also formatted my other hard drive (sdb) a while ago and every time I boot I get some sort of error message about not being able to activate swap.

I don't really care what ubuntu calls my partitions, as long as the names don't change from day to day. Does anyone have a clue as to why this is happening, or how to stop it?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                    0  0
# /dev/sdb6
UUID=55f3b7e4-ef4d-4585-bffe-8e7ab3421a84  /               ext3         relatime,errors=remount-ro  0  1
# /dev/sda2
UUID=49d38668-bbb1-4afb-8a52-89e3aeeaea3c  none            swap         sw                          0  0
# /dev/sdb4
UUID=a40faaae-1f0f-453c-9d82-3c75993f477f  none            swap         sw                          0  0
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8       0  0
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8    0  0
/dev/sda2                                  /media/sda2     ext3         errors=remount-ro           0  0
/dev/sda3                                  /media/sda3     ext3         errors=remount-ro           0  0
/dev/sda4                                  /media/sda4     swap         sw                          0  0
/dev/sda5                                  /media/sda5     ext3         errors=remount-ro           0  0
/dev/sda6                                  /media/sda6     ext3         errors=remount-ro           0  0
/dev/sda7                                  /media/sda7     ext3         errors=remount-ro           0  0
/dev/sdb1                                  /media/sdb1     ext3         errors=remount-ro           0  0

---

### Post by Bachstelze on 2008-07-18
Details, please... Where do you see those disk-* names ?

---

### Post by vigleik on 2008-07-18
Both the sda's and disk-* names are present in /media/, sometimes the sda's are automounted, sometimes they simply don't exist in /dev/. Here's my current mtab:

/dev/sdb6 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-19-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/dev/sdb3 /media/disk ext3 rw,nosuid,nodev,uhelper=hal 0 0
/dev/sdb5 /media/disk-1 ext3 rw,nosuid,nodev,uhelper=hal 0 0
/dev/sdb7 /media/disk-2 ext3 rw,nosuid,nodev,uhelper=hal 0 0
/dev/sda1 /media/disk-3 ext3 rw,nosuid,nodev,uhelper=hal 0 0
/dev/sdb2 /media/disk-4 ext3 rw,nosuid,nodev,uhelper=hal 0 0

---

