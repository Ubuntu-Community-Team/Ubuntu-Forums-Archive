---
title: "NTFS Mounting Problem"
date: 2008-10-15
forum: Hardware
---

### Post by Dengeki on 2008-10-15
I've just recently converted to Ubuntu from Windows and I made a back-up of my pictures, music, and some of my games onto a back-up 160GB hard drive that is formated as an NTFS. At first, I thought I could access it without any terminal coding, but after following [this guide](http://www.obharath.net/blog/2005/10/05/reading-files-from-windows-partitionntfs-on-ubuntu-linux/), it keeps telling me that the volume doesn't exist

---

### Post by Rocket2DMn on 2008-10-15
Can you please post the output of the following commands:
```
sudo fdisk -l
cat /etc/fstab
sudo blkid
mount
```
Also, can you please specify if the drive is internal or external?

---

### Post by Dengeki on 2008-10-15
```
dengeki@dengeki-desktop:~$ sudo fdisk -l
[sudo] password for dengeki: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe49fe49f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156288321    7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a020b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       23564   189277798+  83  Linux
/dev/sdb2           23565       24321     6080602+   5  Extended
/dev/sdb5           23565       24321     6080571   82  Linux swap / Solaris
dengeki@dengeki-desktop:~$ sudo mkdir /media/windows
mkdir: cannot create directory `/media/windows': File exists
dengeki@dengeki-desktop:~$ sudo mount /dev/sda1 /media/windows/ -t ntfs -o nls=utf8,unmask=0222
ntfs-3g: Failed to access volume '/dev/sda1': No such file or directory
Please type '/sbin/mount.ntfs --help' for more information.
dengeki@dengeki-desktop:~$ 
```

---

### Post by Rocket2DMn on 2008-10-15
Can you include the rest of the output of the other commands I listed in post 2 as well?  And it's umask, not unmask :)  Although it shouldn't matter, I tend to use "ntfs-3g" and use the -t option before the device
```
sudo mount -t ntfs-3g /dev/sda1 /media/windows -o nls=utf8,umask=0222
```
There are more complex mount options as well, like uid=1000.  My fstab has options 
```
auto,users,uid=1000,gid=100,locale=en_US.utf8,dmask=027,fmask=137
```

---

### Post by Dengeki on 2008-10-15
The only problem I'm having is 'why does it say no such directory when its just right there?' Could it be that when I browse for it in /dev, I can't find it, but I can find sba, but not sba1

---

### Post by Rocket2DMn on 2008-10-15
> **Dengeki said:**
> The only problem I'm having is 'why does it say no such directory when its just right there?'

I don't know, please post the requested information and we will try to add an fstab entry.

---

### Post by Dengeki on 2008-10-15
This is the output for 'sudo fdisk -l'
```
dengeki@dengeki-desktop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe49fe49f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156288321    7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a020b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       23564   189277798+  83  Linux
/dev/sdb2           23565       24321     6080602+   5  Extended
/dev/sdb5           23565       24321     6080571   82  Linux swap / Solaris

```

This is the output for 'cat /ect/fstab'
```
dengeki@dengeki-desktop:~$ sudo cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=fa53751c-7d52-4065-bf3d-26b7cb9b2321 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=ddc42095-7286-4fe6-9378-314d0910fb03 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

This is the output for 'sudo blkid
```
dengeki@dengeki-desktop:~$ sudo blkid
/dev/sdb1: UUID="fa53751c-7d52-4065-bf3d-26b7cb9b2321" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="ddc42095-7286-4fe6-9378-314d0910fb03"
```

This is the output for 'mount'
```
dengeki@dengeki-desktop:~$ sudo mount
/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/dengeki/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dengeki)
```

---

### Post by Rocket2DMn on 2008-10-15
Since the sda1 partition isn't appearing in the blkid command, it seems like something may be wrong with the drive (possibly at the hardware level).  I don't know why fdisk picked it up but nothing else did, I have never seen that behavior before.  If this is a dual boot setup, I suggest rebooting into Windows, running chkdsk, and defragging the hard drive.  You said you converted, so if that means Windows is gone, you should plug the drive into a windows computer and use chkdsk and defrag on it from there since Ubuntu cannot perform these actions on a NTFS formatted drive (unfortunately).

Also, you might try booting into a LiveCD and seeing if you can mount the drive from there (or at least see if blkid returns anything for it).  If it does, then it would seem something is strangely wrong with your Ubuntu install.

---

