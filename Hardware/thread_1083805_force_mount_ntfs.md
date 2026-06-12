---
title: "force mount ntfs"
date: 2009-03-01
forum: Hardware
---

### Post by skykaptain on 2009-03-01
Hello,

XP some how became corrupted and now when I try to reinstall it, it wants to reformat. I cannot get into my Ubuntu 8.10 partition because Grub will not come up after Post so I am using a 8.04 Live CD. I would like to know how I can force mount my XP partition and my external back up so I can transfer some files.

I have tried to use the NTFS config tool but when I try to mount the disks it says they are being used my XP and/or they were not properly dismounted. Also it says I am not privileged to mound them either.

Thanks.

---

### Post by taurus on 2009-03-01
```
sudo mkdir /media/windows
sudo mount -t ntfs-3g /dev/sda1 /media/windows -o force
df -h
```
_Assuming_ /dev/sda1 is where windows is.

---

### Post by skykaptain on 2009-03-01
Ok, I did that and this is what I got back:
```
ubuntu@ubuntu:~$ sudo mkdir /media/windows
ubuntu@ubuntu:~$ sudo mount -t ntfs-3g /dev/sda1 /media/windows -o force
ntfs_attr_pread: ntfs_pread failed: Input/output error
Failed to read $MFTMirr: Input/output error
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.
ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 1.5G   13M  1.5G   1% /lib/modules/2.6.24-19-generic/volatile
tmpfs                 1.5G   13M  1.5G   1% /lib/modules/2.6.24-19-generic/volatile
varrun                1.5G  108K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G   76K  1.5G   1% /dev
devshm                1.5G   12K  1.5G   1% /dev/shm
tmpfs                 1.5G   16K  1.5G   1% /tmp
gvfs-fuse-daemon      1.5G  119M  1.4G   9% /home/ubuntu/.gvfs
/dev/sda5              30G  4.2G   24G  15% /media/disk

```

---

### Post by taurus on 2009-03-01
Looks to me like you need to use TestDisk, [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk), to pick your ntfs partition.

---

### Post by vanadium on 2009-03-01
Are we sure /dev/sda1 is the ntfs partition? Find the device name of your ntfs partition in the output of "sudo fdisk -l" or "sudo blkid"

---

### Post by skykaptain on 2009-03-01
I installed TestDisk and it said it needed to be ran as root. Running fdisk gave:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38e438e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       56890   456968893+   7  HPFS/NTFS
/dev/sda2           56891       60801    31415107+   5  Extended
/dev/sda5           56891       60801    31415076   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfe81fe81

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      121601   976760001    7  HPFS/NTFS

```

Where sda1 is the windows partition and sdb1 is the back up disk. Sda5 is my 8.10 partition that I cannot boot into because Grub does not appear after booting My back up disk is mounted and I can read and write from it.

---

