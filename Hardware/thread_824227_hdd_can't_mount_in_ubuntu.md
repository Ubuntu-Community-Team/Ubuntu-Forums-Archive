---
title: "hdd can't mount in ubuntu"
date: 2008-06-09
forum: Hardware
---

### Post by barrett_1 on 2008-06-09
Ok, so this is my first post.  Hope y'all can help me.  I just recently installed Ubuntu on a dual-hdd computer.  I previously had windows installed and I didn't uninstall it, but rather had ubuntu share a drive with it.  How can I access my windows files in ubuntu? Thanks.

---

### Post by Rocket2DMn on 2008-06-09
Can you please post the output of
```
sudo fdisk -l
cat /etc/fstab
sudo blkid
mount
```

---

### Post by barrett_1 on 2008-06-10
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9ad99ad9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16708   134206978+   7  HPFS/NTFS
/dev/sda2           16709       24321    61151422+   f  W95 Ext'd (LBA)
/dev/sda5           16709       24321    61151391    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x55054103

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9352    75119908+  83  Linux
/dev/sdb2            9353        9729     3028252+   5  Extended
/dev/sdb5            9353        9729     3028221   82  Linux swap / Solaris

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00002d33

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19457   156288321    b  W95 FAT32
barrett@barrett-Wino:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=c56c0336-5949-420c-b20a-4f6840b4bba9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=a74f89ba-4523-43cf-9271-bb53bb4a7cdf none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
barrett@barrett-Wino:~$ sudo blkid
/dev/sda1: UUID="40D8D7D7D8D7C974" TYPE="ntfs" 
/dev/sda5: UUID="A22463C124639757" LABEL="My Media" TYPE="ntfs" 
/dev/sdb1: UUID="c56c0336-5949-420c-b20a-4f6840b4bba9" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="a74f89ba-4523-43cf-9271-bb53bb4a7cdf" 
/dev/sdc1: LABEL="SEA_DISC" UUID="0000-0000" TYPE="vfat" 
barrett@barrett-Wino:~$ mount
/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-18-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/barrett/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=barrett)
/dev/sdc1 on /media/SEA_DISC type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

---

### Post by Rocket2DMn on 2008-06-10
I'm a little confused about your sda drive (with windows).  It looks like you have a few partitions on it (windows + a media partition inside an extended partition?)  We will add both, you can remove one if it doesn't work.
Open /etc/fstab for editing
```
gksudo gedit /etc/fstab
```
Add the lines
```
UUID=40D8D7D7D8D7C974 /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0
UUID=A22463C124639757 /media/my_media ntfs-3g defaults,locale=en_US.utf8 0 0
```
Save and close. Now create the mount points:
```
sudo mkdir /media/windows /media/my_media
```
Now try and mount the partitions:
```
sudo mount -a
```
Post the output of that last command if it shows anything.  
If all goes well you should be able to access your partitions from /media/windows and /media/my_data

---

### Post by barrett_1 on 2008-06-10
Thanks for helping.  Here was the output to the last code:

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/windows -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/windows ntfs-3g force 0 0
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda5': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda5 /media/my_media -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda5 /media/my_media ntfs-3g force 0 0

---

### Post by Rocket2DMn on 2008-06-10
OK, it looks like windows didn't have a clean shutdown which is why the drives aren't mounting.  If you HIBERNATED your windows boot, do not force the mount.  First I would suggest rebooting into windows and then doing a clean shutdown.  After that, reboot into linux.  If the drives don't mount at boot or after running
```
sudo mount -a
```
try forcing them to mount with
```
mount -t ntfs-3g /dev/sda1 /media/windows -o force
mount -t ntfs-3g /dev/sda5 /media/my_media -o force
```
Post back with your results.

---

