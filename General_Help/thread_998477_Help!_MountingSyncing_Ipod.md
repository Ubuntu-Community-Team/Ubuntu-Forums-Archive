---
title: "Help! Mounting/Syncing Ipod"
date: 2008-11-30
forum: General Help
---

### Post by s3n5ai on 2008-11-30
Greetings,

I'm trying to mount and sync my 30gb ipod video off the guide: [http://ubuntuforums.org/showthread.php?t=103071](http://ubuntuforums.org/showthread.php?t=103071)

When I plug in my ipod and try to mount /dev/sdb2 it mounts "Apple iPod Music Player" and my mount point /mnt/ipod is not mounted. But if I try to mount /mnt/ipod Player, I get the message "mount: /dev/sdb2 is already mounted or /mnt/ipod is busy. mount: according to mtab, /dev/sdb2 is already mounted on /mnt/ipod.

If I go to /mnt/ipod the folder is not empty as if something is mounted, yet on my tool bar it shows /mnt/ipod as not mounted. Also no desktop icons appear like when something is mounted and there are no other mounted volumes in Places.

When I open gtkpod, no ipods are listed nor detected when I click Load iPods. 

This is what the terminal outputs when dmesg is run:


[ 5071.345973] scsi 10:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 5071.349951] sd 10:0:0:0: [sdb] 58605120 512-byte hardware sectors (30006 MB)
[ 5071.353195] sd 10:0:0:0: [sdb] Write Protect is off
[ 5071.353198] sd 10:0:0:0: [sdb] Mode Sense: 68 00 00 08
[ 5071.353200] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[ 5071.360934] sd 10:0:0:0: [sdb] 58605120 512-byte hardware sectors (30006 MB)
[ 5071.364176] sd 10:0:0:0: [sdb] Write Protect is off
[ 5071.364178] sd 10:0:0:0: [sdb] Mode Sense: 68 00 00 08
[ 5071.364179] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[ 5071.364182]  sdb: sdb1 sdb2
[ 5071.380795] sd 10:0:0:0: [sdb] Attached SCSI removable disk
[ 5071.380818] sd 10:0:0:0: Attached scsi generic sg2 type 0
[ 5108.608539] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!


Here is my /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=01a37f88-b69b-4383-bba2-b905d85d0a94 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=da46bd3a-d0ec-4310-b191-8eba2f139c7a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb2 /mnt/ipod vfat nosuid,noauto,nodev,rw,umask=077,gid=1000,uid=1000,user,defaults,noatime,iocharset=utf8 0 0


And here is my /etc/mtab:

/dev/sda2 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-21-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
gvfs-fuse-daemon /home/s3n5ai/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=s3n5ai 0 0
/dev/sdb2 /mnt/ipod vfat rw,noexec,nosuid,nodev,noatime,umask=077,gid=1000,uid=1000,iocharset=utf8 0 0

Also for some reason in my /media folder, an IPOD folder is created and mounted i believe. Everytime I plug in my ipod it creates another IPOD folder with an underscore at the end. So in my /media folder I have for some reason "IPOD", "IPOD_", "IPOD__", "IPOD___"  and so on...

---

