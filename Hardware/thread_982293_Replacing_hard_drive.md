---
title: "Replacing hard drive"
date: 2008-11-14
forum: Hardware
---

### Post by mad_cyclist on 2008-11-14
I have kubuntu 8.04 running on a vista dual boot hp desktop. As well as the sata boot drive, I have 2 extra ide hard drives which are hda and hdb (not visible to vista). They are formatted with ext3 and the partitions are hda1 and hdb1. I bought a new larger hard drive to replace hdb. I removed hdb and replaced it with the new drive. Then I got gtparted to format it as ext3. I'm now trying to mount it but it gives me a generic mounting error 32. Any ideas? I thought maybe I should have unmounted the previous hdb first before switching off the machine and swapping out the physical disk because I am also getting an error saying there is already a device at hdb. Any ideas?

Cheers

Dave
:guitar:

---

### Post by taurus on 2008-11-14
What are the outputs of these commands from a terminal?

```
sudo fdisk -l
cat /etc/fstab
sudo blkid
df -h
```

---

### Post by mad_cyclist on 2008-11-14
sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaa095750

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       26023   209024558+   7  HPFS/NTFS
/dev/sda2           28573       30146    12635410    7  HPFS/NTFS
/dev/sda3           30146       30402     2057216    7  HPFS/NTFS
/dev/sda4           26024       28572    20474842+  83  Linux

Partition table entries are not in disk order

Disk /dev/hda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       30515   245111706   83  Linux

Disk /dev/hdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000b43a

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       60801   488384001   83  Linux

Disk /dev/sdb: 1028 MB, 1028653056 bytes
16 heads, 32 sectors/track, 3924 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0xbf339e6f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3924     1004528    b  W95 FAT32




-----------------------------------------------------------------------------------
cat /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda4
UUID=5c3a9b17-6528-431b-bb9e-56b6c6e632dd / ext3 nouser,relatime,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/hda1
UUID=f204888e-b266-40b4-9d1c-2f9582e43046 /media/hda1 ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
# /dev/hdb1
# /dev/sda1
UUID=11DB3C8B5E2F1049 /media/sda1 ntfs defaults,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
# /dev/sda2
UUID=0254EA8A6934B6D9 /media/sda2 ntfs defaults,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
# /dev/sda3
UUID=34E055ABE05573D8 /media/sda3 ntfs defaults,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
/dev/scd0 /media/cdrom0 udf,iso9660 user,utf8,atime,noauto,rw,dev,exec,suid 0 0
<device> /media/hdb1 auto nouser,atime,noauto,rw,nodev,noexec,nosuid 0 0
<device> /media/hdb1 auto nouser,atime,noauto,rw,nodev,noexec,nosuid 0 0
UUID=f204888e-b266-40b4-9d1c-2f9582e43046 /media/hdb1 ext3 nouser,loop,atime,noauto,rw,nodev,noexec,nosuid 0 0
UUID=f204888e-b266-40b4-9d1c-2f9582e43046 <mount\040point> ext3 nouser,atime,noauto,rw,nodev,noexec,nosuid 0 0
UUID=f204888e-b266-40b4-9d1c-2f9582e43046 /media/hdb1 ext3 nouser,atime,noauto,rw,nodev,noexec,nosuid 0 0
/dev/hda1 /media/hda1 auto nouser,atime,noauto,rw,nodev,noexec,nosuid 0 0
/dev/scd0 /media/cdrom0 auto nouser,atime,noauto,rw,nodev,noexec,nosuid 0 0
/dev/scd0 /media/cdrom auto nouser,atime,noauto,rw,nodev,noexec,nosuid 0 0
/dev/scd0 /media/cdrom0 auto nouser,atime,noauto,rw,nodev,noexec,nosuid 0 0
/dev/hdb1 /media/hdb1 auto nouser,noauto,atime,rw,nodev,noexec,nosuid 0 0


----------------------------------------------------------------------------------------------------
sudo blkid

/dev/sda1: UUID="11DB3C8B5E2F1049" TYPE="ntfs"
/dev/sda2: UUID="0254EA8A6934B6D9" LABEL="HP_RECOVERY" TYPE="ntfs"
/dev/sda3: UUID="34E055ABE05573D8" LABEL="OS_TOOLS" TYPE="ntfs"
/dev/sda4: UUID="5c3a9b17-6528-431b-bb9e-56b6c6e632dd" SEC_TYPE="ext2" TYPE="ext3"
/dev/hda1: UUID="f204888e-b266-40b4-9d1c-2f9582e43046" SEC_TYPE="ext2" TYPE="ext3"
/dev/hdb1: UUID="ce195365-fbfc-4670-9bc5-3f747d4c4478" SEC_TYPE="ext2" TYPE="ext3"
/dev/sdb1: UUID="A052-A4F1" TYPE="vfat"



------------------------------------------------------------------------------------------------
df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda4              20G  6.6G   12G  36% /
varrun                950M  160K  950M   1% /var/run
varlock               950M     0  950M   0% /var/lock
udev                  950M   72K  950M   1% /dev
devshm                950M     0  950M   0% /dev/shm
lrm                   950M   39M  911M   5% /lib/modules/2.6.24-21-generic/volatile
/dev/hda1             231G  226G  4.3G  99% /media/hda1
/dev/sda1             200G  196G  3.7G  99% /media/sda1
/dev/sda2              13G  4.2G  7.9G  35% /media/sda2
/dev/sda3             2.0G  202M  1.8G  11% /media/sda3
/dev/sdb1             980M  279M  701M  29% /media/disk



Thanks

Dave

---

### Post by taurus on 2008-11-14
> **mad_cyclist said:**
> 
cat /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda4
UUID=5c3a9b17-6528-431b-bb9e-56b6c6e632dd / ext3 nouser,relatime,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/hda1
UUID=f204888e-b266-40b4-9d1c-2f9582e43046 /media/hda1 ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
# /dev/hdb1
# /dev/sda1
UUID=11DB3C8B5E2F1049 /media/sda1 ntfs defaults,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
# /dev/sda2
UUID=0254EA8A6934B6D9 /media/sda2 ntfs defaults,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
# /dev/sda3
UUID=34E055ABE05573D8 /media/sda3 ntfs defaults,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
/dev/scd0 /media/cdrom0 udf,iso9660 user,utf8,atime,noauto,rw,dev,exec,suid 0 0
[B][COLOR="Blue"]<device> /media/hdb1 auto nouser,atime,noauto,rw,nodev,noexec,nosuid 0 0
<device> /media/hdb1 auto nouser,atime,noauto,rw,nodev,noexec,nosuid 0 0[/COLOR][/B]
[COLOR="Red"]UUID=f204888e-b266-40b4-9d1c-2f9582e43046 /media/hdb1 ext3 nouser,loop,atime,noauto,rw,nodev,noexec,nosuid 0 0[/COLOR]
**[COLOR="Blue"]UUID=f204888e-b266-40b4-9d1c-2f9582e43046 <mount\040point> ext3 nouser,atime,noauto,rw,nodev,noexec,nosuid 0 0[/COLOR]**
[COLOR="Red"]UUID=f204888e-b266-40b4-9d1c-2f9582e43046 /media/hdb1 ext3 nouser,atime,noauto,rw,nodev,noexec,nosuid 0 0[/COLOR]
/dev/hda1 /media/hda1 auto nouser,atime,noauto,rw,nodev,noexec,nosuid 0 0
/dev/scd0 /media/cdrom0 auto nouser,atime,noauto,rw,nodev,noexec,nosuid 0 0
/dev/scd0 /media/cdrom auto nouser,atime,noauto,rw,nodev,noexec,nosuid 0 0
/dev/scd0 /media/cdrom0 auto nouser,atime,noauto,rw,nodev,noexec,nosuid 0 0
/dev/hdb1 /media/hdb1 auto nouser,noauto,atime,rw,nodev,noexec,nosuid 0 0


Not sure why you have those three lines (in blue) in your /etc/fstab.  Also, you have your CD/DVD mounted to /media/cdrom & /media/cdrom0 (two lines).  

Let's see if you can mount /dev/hdb1 by hand from a terminal.  Run

```
sudo mount -t ext3 /dev/hdb1 /media/hdb1
df -h
```

p.s.  Two lines in red are for the same device, /dev/hdb1!  How did you create your /etc/fstab anyway?

---

### Post by mad_cyclist on 2008-11-14
sudo mount -t ext3 /dev/hdb1 /media/hdb1
df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda4              20G  6.6G   12G  36% /
varrun                950M  160K  950M   1% /var/run
varlock               950M     0  950M   0% /var/lock
udev                  950M   72K  950M   1% /dev
devshm                950M     0  950M   0% /dev/shm
lrm                   950M   39M  911M   5% /lib/modules/2.6.24-21-generic/volatile
/dev/hda1             231G  226G  4.3G  99% /media/hda1
/dev/sda1             200G  196G  3.7G  99% /media/sda1
/dev/sda2              13G  4.2G  7.9G  35% /media/sda2
/dev/sda3             2.0G  202M  1.8G  11% /media/sda3
/dev/sdb1             980M  279M  701M  29% /media/disk
/dev/hdb1             463G  199M  439G   1% /media/hdb1


Thanks a lot that seems to have worked. :)
As for where the /etc/fstab came from I have no idea. It must have been created during install. Do I need to amend it in ant way?

Cheers

Dave

---

### Post by taurus on 2008-11-14
If it were me, I would definitely clean up /etc/fstab.  So, if you decide to do that, make a backup copy of it first.

```
sudo mv /etc/fstab /etc/fstab.original
```
Then, fire up a gedit editor.

```
gksudo gedit /etc/fstab
```
You should see a blank screen at this point.  Now, paste the following lines to it.

```

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda4
UUID=5c3a9b17-6528-431b-bb9e-56b6c6e632dd / ext3 nouser,relatime,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/hda1
UUID=f204888e-b266-40b4-9d1c-2f9582e43046 /media/hda1 ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
# /dev/hdb1
UUID=ce195365-fbfc-4670-9bc5-3f747d4c4478 /media/hdb1 ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
# /dev/sda1
UUID=11DB3C8B5E2F1049 /media/sda1 ntfs defaults,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
# /dev/sda2
UUID=0254EA8A6934B6D9 /media/sda2 ntfs defaults,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
# /dev/sda3
UUID=34E055ABE05573D8 /media/sda3 ntfs defaults,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
/dev/scd0 /media/cdrom0 udf,iso9660 user,utf8,atime,noauto,rw,dev,exec,suid 0 0
/dev/scd0 /media/cdrom auto nouser,atime,noauto,rw,nodev,noexec,nosuid 0 0

```
Save it and reboot.  Hopefully, everything mounts where they should be.

---

### Post by mad_cyclist on 2008-11-14
Thanks I'll try that tomorrow.

Cheers for all your help and have a good weekend

---

