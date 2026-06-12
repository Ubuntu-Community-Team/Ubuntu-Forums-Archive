---
title: "Missing /dev/sda1 device. First partition mounts to /dev/sda2"
date: 2008-09-16
forum: General Help
---

### Post by Rianthas on 2008-09-16
Here's an output of fdisk /dev/sda, /etc/fstab/, and /etc/mtab

```
The number of cylinders for this disk is set to 24321.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x07eec164

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1       24068   193326178+  83  Linux
/dev/sda3           24069       24321     2032222+  82  Linux swap / Solaris
```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    relatime,errors=remount-ro 0       1
/dev/sda3       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

```
/dev/sda2 / ext3 rw,relatime,errors=remount-ro 0 0
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
none /proc/fs/vmblock/mountPoint vmblock rw 0 0
gvfs-fuse-daemon /home/chris/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=chris 0 0

```

I'm completely blown away by this. Originally, I had three partitions. The first was an NTFS partition that had my Windows install. I kept it just to transfer over files, then I used Gparted to delete the Windows partition and expand the ext3 partition Ubuntu is on. After that point is when I noticed this problem.

I'm a college student majoring in network administration and was going to run this by one of the professors that teaches a class on Linux administration and server virtualization (and maintains the Microsoft Exchange and ORACLE servers for the college) with VMWare, but figured I'd post this here first to see if anyone has ideas.

Oh, and fsck returns no errors.

---

### Post by bingoUV on 2008-09-16
Why do you need a /dev/sda1 device? If I understand you correctly, you yourself deleted it. Are you missing any data? 

Do you expect gparted to rename /dev/sda2 to /dev/sda1 after deleting /dev/sda1? It doesn't do that.

---

### Post by Rianthas on 2008-09-16
It's seriously that simple? ](*,)

---

### Post by Rianthas on 2008-09-16
Yeah. I understand it now. Gparted isn't going to update the /dev block devices.

---

