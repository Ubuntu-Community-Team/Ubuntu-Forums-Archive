---
title: "windows partitions not mounted after installing hardy using Wubi"
date: 2009-01-02
forum: Installation &amp; Upgrades
---

### Post by abhinav.p on 2009-01-02
can anyone tel me how to mount the hard disk partitions in windows in hardy installed using Wubi.the output of some commands are:



harsha@harsha-laptop:~$ mount
/host/ubuntu/disks/root.disk on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
/host/ubuntu/disks/boot on /boot type none (rw,bind)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/harsha/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=harsha)


harsha@harsha-laptop:~$ sudo fdisk -l
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            1913        7295    43238947+   f  W95 Ext'd (LBA)
/dev/sda5            1913        4462    20482843+   e  W95 FAT16 (LBA)
/dev/sda6            4463        7295    22756041    e  W95 FAT16 (LBA)





harsha@harsha-laptop:~$ ls /media
cdrom cdrom0

---

### Post by albinootje on 2009-01-02
> **abhinav.p said:**
> can anyone tel me how to mount the hard disk partitions in windows in hardy installed using Wubi.


See here : [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

For example, just for testing, try this in a terminal :
```

sudo mkdir /media/sda5
sudo mount /dev/sda5 /media/sda5 -o umask=000

```
After that check the /media/sda5/ directory with your filemanager.

For making it permanent, see the link above.

---

### Post by hyperdude111 on 2009-01-02
if you go to filesystem in wubi and press ctrl-h you should see a folder called "host"

When you go in that folder you will see it is the windows partition

---

### Post by abhinav.p on 2009-01-02
output forommands suggested:
harsha@harsha-laptop:~$ sudo mkdir /media/sda5
harsha@harsha-laptop:~$ sudo mount /dev/sda5 /media/sda5 -o umask=000
mount: you must specify the filesystem type




also host folder no boubt has a windows folder.but it still does not show my 45 GB hard disk there.

---

### Post by albinootje on 2009-01-02
> **abhinav.p said:**
> output forommands suggested:
harsha@harsha-laptop:~$ sudo mkdir /media/sda5
harsha@harsha-laptop:~$ sudo mount /dev/sda5 /media/sda5 -o umask=000
mount: you must specify the filesystem type


I was already a bit surprised to see FAT16 labeled partitions in your "fdisk -l" output.

Can you try this :
```

sudo mkdir /media/sda1
sudo mount /dev/sda1 /media/sda1 -t ntfs-3g -o umask=000,force
sudo mkdir /media/sda5
sudo mount /dev/sda5 /media/sda5 -t vfat -o umask=000
sudo mkdir /media/sda6
sudo mount /dev/sda6 /media/sda6 -t vfat -o umask=000

```
And post any errors.

---

### Post by abhinav.p on 2009-01-02
> **albinootje said:**
> I was already a bit surprised to see FAT16 labeled partitions in your "fdisk -l" output.

Can you try this :
```

sudo mkdir /media/sda1
sudo mount /dev/sda1 /media/sda1 -t ntfs-3g -o umask=000,force
sudo mkdir /media/sda5
sudo mount /dev/sda5 /media/sda5 -t vfat -o umask=000
sudo mkdir /media/sda6
sudo mount /dev/sda6 /media/sda6 -t vfat -o umask=000

```
And post any errors.

putput for suggested commands:
mount: wrong fs type, bad option, bad superblock on /dev/sda6,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

