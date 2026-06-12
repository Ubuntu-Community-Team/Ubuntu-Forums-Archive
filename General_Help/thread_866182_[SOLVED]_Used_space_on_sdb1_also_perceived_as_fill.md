---
title: "[SOLVED] Used space on /sdb1 also perceived as filling /sda1"
date: 2008-07-21
forum: General Help
---

### Post by dppowell on 2008-07-21
I've got a notebook with two 120GB disks.  Hardy runs on the first disk, and the second serves as a backup target (after an earlier, abortive attempt to boot OEM Vista from it).

df falsely reports that /sda1 is 94% full:

```
dave@gewgaw:/media/sdb1$ df -m
Filesystem           1M-blocks      Used Available Use% Mounted on
/dev/sda1               108915     96515      6912  94% /
varrun                    1512         1      1512   1% /var/run
varlock                   1512         0      1512   0% /var/lock
udev                      1512         1      1512   1% /dev
devshm                    1512         1      1512   1% /dev/shm
lrm                       1512        44      1468   3% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon        108915     96515      6912  94% /home/dave/.gvfs
/dev/scd0                 4268      4268         0 100% /media/cdrom0

```

But there are only 21 GB of files there:

```
dave@gewgaw:~$ du -sh
21G	.

```

Here's my fstab:

```
dave@gewgaw:/media/sdb1$ more /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=860f3898-ce5b-44f6-a6b5-6c3bd8b5389d /               ext3    relatime,error
s=remount-ro 0       1
# /dev/sda5
UUID=b4382d7e-9501-464c-b53c-992dfb5c89ae none            swap    sw            
  0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#Added by diskmounter utility
/dev/sdb1 /media/sdb1 ntfs ro,user,fmask=0111,dmask=0000 0 0

```

The Gnome disk usage analyzer showed that 71 GB worth of backups on /sdb1 were somehow being perceived as used space on my main drive.  I'm guessing that this is some kind of fstab or other mounting-related misconfiguration.

I discovered the problem when I tried to create a 20 GB VirtualBox disk and the operation failed.  Does anyone know how to fix this?

---

### Post by Potatoj316 on 2008-07-21
I had the same problem a while ago I think its this line thats the problem

gvfs-fuse-daemon        108915     96515      6912  94% /home/dave/.gvfs

In disk usage analyser look around for an option that lets you tell it what to search through when checking the filesystem.  You probably have 2 entries / and /home/dave/.gvfs.  Take the second one out and it should work.

---

### Post by dppowell on 2008-07-21
Thanks for that.  I changed the Gnome disk analyzer prefs so it would only scan /dev/sda1 and not the gvfs-fuse-daemon virtual device, but the output is the same.  Perhaps I misunderstood your suggestion?

---

### Post by rogier.de.groot on 2008-07-21
To me this looks like /media/sdb1 isn't even mounted. Could you please list the output of the following commands:
mount
du -sh /media/sdb1
sudo fdisk -l /dev/sda
sudo fdisk -l /dev/sdb

---

### Post by dppowell on 2008-07-21
Absolutely, thanks for your interest:

```
dave@gewgaw:~$ du -sh /media/sdb1
71G	/media/sdb1
dave@gewgaw:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc5fcbd5f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris
dave@gewgaw:~$ sudo fdisk -l /dev/sdb

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb9e65ff6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241   83  Linux

```

---

### Post by rogier.de.groot on 2008-07-21
You forgot the output of the "mount" command. Please post it.
Also, why does /etc/fstab say /dev/sdb1 is a NTFS partition, while fdisk thinks it's a linux partition?

---

### Post by dppowell on 2008-07-21
Apologies, I missed the 'mount' command in your first post:

```
dave@gewgaw:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/dave/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dave)
/dev/scd0 on /media/cdrom0 type udf (ro,nosuid,nodev,utf8,user=dave)

```

I'm not sure about the discrepancy between the fstab and fdisk.  I'm sure the fstab entry is a relic from my attempt to put a bootable Vista installation on /sdb1.  When I couldn't get that working correctly, I just decided to use it for backups.

---

### Post by rogier.de.groot on 2008-07-21
Hmm... weird, I think that gvfs-fuse-daemon thing just always shows up. There should be a mount entry for the /dev/sdb1 partition. Could you try something like:
sudo mount /dev/sdb1 /media/sdb1
and see what happens? if it works repost the outputs of "mount" and "df -h".

---

### Post by dppowell on 2008-07-21
It mounted successfully.  Here's the requested output:

```
dave@gewgaw:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/dave/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dave)
/dev/scd0 on /media/cdrom0 type udf (ro,nosuid,nodev,utf8,user=dave)
/dev/sdb1 on /media/sdb1 type ext3 (rw)

dave@gewgaw:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             107G   95G  6.8G  94% /
varrun                1.5G  232K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G   60K  1.5G   1% /dev
devshm                1.5G   24K  1.5G   1% /dev/shm
lrm                   1.5G   44M  1.5G   3% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon      107G   95G  6.8G  94% /home/dave/.gvfs
/dev/scd0             4.2G  4.2G     0 100% /media/cdrom0
/dev/sdb1             111G  188M  106G   1% /media/sdb1

```

So, the backup I'd thought was going to /dev/sdb1 was actually just going to the /media/sdb1 directory on /sda1?

How is it that I can't see that with a du -sh?  (as shown in original post)

---

### Post by rogier.de.groot on 2008-07-21
Yes, it looks like you were backing up to a the directory /media/sdb1 instead of the second harddrive. You can add a line (replacing the old NTFS one) to /etc/fstab to automatically mount /dev/sdb1 at boot time.
As to the "du -sh" question, it looks like you're executing it in your user's home directory, and /media/sdb1 isn't in your user's home directory.
That /home/dave/.gvfs entry seems normal; mine reports the same thing even though there's nothing mounted on it. Bit weird, but probably normal.

---

### Post by dppowell on 2008-07-21
Thanks for the help and for indulging my ignorance!

---

