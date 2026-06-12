---
title: "Adding Second Hard Drive Error"
date: 2008-02-22
forum: Hardware &amp; Laptops
---

### Post by DeadSteve on 2008-02-22
Can someone with more knowledge than I, tell me why this isn't working?

**_Drive Information:_**
  *-disk:1
       description: SCSI Disk
       product: ST340015A
       vendor: ATA
       physical id: 1
       bus info: scsi@0:0.1.0
       logical name: /dev/sdb
       version: 3.01
       serial: 5LAD569F
       size: 37GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5

I wonder why the description says it is a SCSI when it is an EIDE drive? :confused:

**_Terminal Capture:_**
root@UBUNTU-01:~# mkdir /mnt/storage
root@UBUNTU-01:~# mount -t ext3 /dev/sdb /mnt/storage
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


Thanks,
DeadSteve

---

### Post by banewman on 2008-02-22
Is it an ext3 filesystem on the drive or a windows ntfs?
Try  -  mount -v /dev/sdb /mnt/storage
:)

---

### Post by DeadSteve on 2008-02-22
Yes, it is formated as ext3.  I tried your suggestion and got this...

**_Terminal Capture_**
root@UBUNTU-01:~# mount -v /dev/sdb /mnt/storage
mount: you didn't specify a filesystem type for /dev/sdb
       I will try all types mentioned in /etc/filesystems or /proc/filesystems
Trying fuseblk
mount: you must specify the filesystem type

I was able to mount it by adding a one to the local name (/dev/sdb1), but it doesn't show up as a mounted drive, but a mounted folder.  When I do a sudo lshw -C disk the local name is just /dev/sdb, but it won't let you mount it using that local name.

Thanks,
DeadSteve

---

### Post by taurus on 2008-02-22
Can you post the outputs of these commands from a terminal?

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by DeadSteve on 2008-02-22
I think I may have it mounted as a folder, but am going to reboot the system with an update fstab to see if it works.

Here is the information you requested.

_**Terminal Capture**_
**root@UBUNTU-01:~# sudo fdisk -l**

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xad5a9104

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4666    37479613+  83  Linux
/dev/sda2            4667        4865     1598467+   5  Extended
/dev/sda5            4667        4865     1598436   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xabedabed

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4865    39078081   83  Linux


**root@UBUNTU-01:~# cat /etc/fstab**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=40c4d807-d109-4f5c-915c-fd08b7b04447 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=4271d721-d042-42bd-a73c-38edd2a2c33b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sdb1       /mnt/storage    ext3    defaults        0       2


**root@UBUNTU-01:~# df -h**
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              36G   32G  1.9G  95% /
varrun                268M   88K  268M   1% /var/run
varlock               268M     0  268M   0% /var/lock
udev                  268M   80K  268M   1% /dev
devshm                268M     0  268M   0% /dev/shm
lrm                   268M   34M  234M  13% /lib/modules/2.6.22-14-generic/volatile
/dev/sdb1              37G  177M   35G   1% /mnt/storage


Thanks,
DeadSteve

---

### Post by DeadSteve on 2008-02-22
Well, it worked, but should I have used /media/storage vs. /mnt/storage?  It still doesn't show it as a hard drive, but as a folder named storage under the mnt folder.

Thanks,
DeadSteve

---

### Post by taurus on 2008-02-22
You cannot access /dev/sdb1 directory.  Instead, you access /mnt/storage.  If you want to have a little icon on your desktop, then you should mount it to /media/storage instead of /mnt/storage.

---

### Post by DeadSteve on 2008-02-22
OK, thanks for all the help.  So is my current setup correct? 

Thanks,
DeadSteve

---

### Post by taurus on 2008-02-22
It looks good.  And if you need to be able to write to /mnt/storage, assuming you still plan to mount it to /mnt/storage, you can change the ownership of /mnt/storage from root to your login name.  

_Assuming_ your login name is **steve**, do

```
sudo chown -R **steve**:**steve** /mnt/storage
ls -la /mnt
```

---

### Post by DeadSteve on 2008-02-22
Awesome.  Worked perfectly.  Thanks again for all your help.

Thanks,
DeadSteve

---

