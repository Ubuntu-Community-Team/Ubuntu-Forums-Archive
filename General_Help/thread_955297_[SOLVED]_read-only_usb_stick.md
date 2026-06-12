---
title: "[SOLVED] read-only usb stick ???"
date: 2008-10-22
forum: General Help
---

### Post by Mzwo on 2008-10-22
hi all,

quick question: hardy refuses to copy stuff onto my usb stick, claiming it to be a read-only file system (tried for the first time today). works fine under windows, read AND write. i can't remember ever having specified the stick to be read only. 

what to do?

many thanks,
Mzwo

PS: Filesystem on the stick: FAT

---

### Post by skippy2222 on 2008-10-22
I'm having same issue with a external HD..... nightmare....

---

### Post by northern lights on 2008-10-22
What filesystem are the stick, and the external drive respectively, formatted as?

What distributions are you using?

---

### Post by skippy2222 on 2008-10-22
fat32 disk, ful details of my issue here

[http://ubuntuforums.org/showthread.php?t=955279](http://ubuntuforums.org/showthread.php?t=955279)

---

### Post by Stefanie on 2008-10-22
have you tried ```
sudo chown -R [username]:[username] /media/[disk]
sudo chmod 755 /media/[disk]
```
?

---

### Post by geirha on 2008-10-22
It sounds like it is mounted as root, without giving users write access. Does /etc/fstab have an entry for it?

When it is mounted, can you run ```
mount
``` in a terminal and post the output? Also, the output of ```
ls -ld /media/disk
``` would be helpful, but replace /media/disk with the actualy mount point.

---

### Post by northern lights on 2008-10-22
Your fstab should contain an entry along the lines of```
/dev/sdXX       /media/fat32       vfat       users,gid=users,umask=0002,utf8=true 0 0

```it gives ownership to root and read/write access to all users.
Thereupon you can set permissions to /media/fat32 (or your respective mountpoint) regularly.

If you don't understand what I'm suggesting, please post the output of```
cat /etc/fstab/
```and specify the mountpoint.

---

### Post by skippy2222 on 2008-10-22
> **Stefanie said:**
> have you tried ```
sudo chown -R [username]:[username] /media/[disk]
sudo chmod 755 /media/[disk]
```
?

hi, 
still ave same error, some more background.

on my hardy installation I have it set to auto login on my username, so I tried 

sudo chown -R ed:ed /media/STOREX

then 
 
sudo chmod 755 /media/STOREX

after that the folders were locked and error generated was Error removing file: Read-only file system

so i tried the same again with root as the username, same error

---

### Post by skippy2222 on 2008-10-22
[QUOTE=northern lights;6011031]Your fstab should contain an entry along the lines of```
/dev/sdXX       /media/fat32       vfat       users,gid=users,umask=0002,utf8=true 0 0

```

my drive is called STOREX so I tried adding: 

# media drive
/dev/sdb1       /media/STOREX       vfat       users,gid=users,umask=0002,utf8=true 0 0

n I get a cannot mount drive error saying mount point /media/STOREX does not exist

---

### Post by northern lights on 2008-10-22
> **skippy2222 said:**
> I get a cannot mount drive error saying mount point /media/STOREX does not exist
Create it. Either via a file manager or by running```
mkdir /media/STOREX
```You can put anywhere you like, actually.

/media/
/mnt/
/mount/
/whatever-you-prefer/STOREX

---

### Post by skippy2222 on 2008-10-22
ok,

I havethe entry in fstab, I restart the machine, open the drive and every folder is locked, attempting to copy a folder from Desktop to drive generates a read only filesystem error.

here is my fstab 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=b1e275e8-c478-43cb-8c7f-c7ca37de8dea /               ext3    relatime,errors=remount-ro 0       1
# /dev/hda4
UUID=2a0282e9-43e1-43e5-8548-d08a8a0ec8f2 /home           ext3    relatime        0       2
# /dev/hda2
UUID=43e0e1b6-ebe9-454d-a790-cc318763c183 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# media drive
/dev/sdb1       /media/STOREX       vfat       users,gid=users,umask=0002,utf8=true 0 0


username ed

trying mount at the prompt gives: 

mount
/dev/hda3 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-21-generic/volatile type tmpfs (rw)
/dev/hda4 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/ed/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ed)
/dev/sda1 on /media/DATA type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sdb1 on /media/STOREX type vfat (rw,noexec,nosuid,nodev,gid=100,umask=0002,utf8=true)

---

### Post by Mzwo on 2008-10-22
> **geirha said:**
> It sounds like it is mounted as root, without giving users write access. Does /etc/fstab have an entry for it?

When it is mounted, can you run ```
mount
``` in a terminal and post the output? Also, the output of ```
ls -ld /media/disk
``` would be helpful, but replace /media/disk with the actualy mount point.

hiya,

miraculously, it just started working. anyways, 
```
mount
```

gave me:


/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro) proc on /proc type proc (rw,noexec,nosuid,nodev) /sys on /sys type sysfs (rw,noexec,nosuid,nodev) varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620) lrm on /lib/modules/2.6.24-21-rt/volatile type tmpfs (rw) securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

```
ls -ld /media/disk
```

yielded:

drwx------ 8 mzwo root 16384 1970-01-01 01:00 /media/disk

not sure if the mount point is correct, though. how do i go about finding that out?

thanks,
Mzwo

---

### Post by northern lights on 2008-10-22
@Skippy:

Now you should be able to change permissions of /media/STOREX/ though.

Temporarily unmount the device```
umount /dev/sdb1
```
Then change ownership```
sudo chown -R root:users /media/STOREX
```Then set permissions```
sudo chmod 774 /meida/STOREX
```

Remount. Now what?

---

### Post by skippy2222 on 2008-10-22
mount output

mount
/dev/hda3 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-21-generic/volatile type tmpfs (rw)
/dev/hda4 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/ed/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ed)
/dev/sda1 on /media/DATA type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sdb1 on /media/STOREX type vfat (rw,noexec,nosuid,nodev,gid=100,umask=0002,utf8=true)


/media/STOREX$ ls -ld /media/STOREX
drwxrwxr-x 8 ed users 32768 1970-01-01 01:00 /media/STOREX

any attempt to write to the HD generates a read only filesystem error

---

### Post by geirha on 2008-10-22
> **Mzwo said:**
> 
/dev/sdb1 on [COLOR="Blue"]/media/disk[/COLOR] type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

This says it's mounted at /media/disk, so that's correct.

> **Mzwo said:**
> 
d[COLOR="Red"]rwx[/COLOR]------ 8 [COLOR="Red"]mzwo[/COLOR] root 16384 1970-01-01 01:00 /media/disk

And the user mzwo has read, write and execute permissions to it.

Not sure why it wouldn't work like that before, but if you have several users logged in at the same time, they will sort of "fight" for mounting the drive, and the one who wins gets the write permissions. Could that be the case?

---

### Post by skippy2222 on 2008-10-22
> **northern lights said:**
> @Skippy:

Now you should be able to change permissions of /media/STOREX/ though.

Temporarily unmount the device```
umount /dev/sdb1
```
Then change ownership```
sudo chown -R root:users /media/STOREX
```Then set permissions```
sudo chmod 774 /meida/STOREX
```

Remount. Now what?

bizarre......

mount: special device /dev/sdb1 does not exist

---

### Post by geirha on 2008-10-22
> **skippy2222 said:**
> 
/dev/sdb1 on /media/STOREX type vfat (rw,noexec,nosuid,nodev,gid=100,umask=0002,utf8=true)


/media/STOREX$ ls -ld /media/STOREX
drwxrwxr-x 8 ed users 32768 1970-01-01 01:00 /media/STOREX

any attempt to write to the HD generates a read only filesystem error

According to that, you should have write permissions for it now, so it's odd that you'd get such an error. Could you also post the output of ```
touch /media/STOREX/testfile
```

Some usb-drives has a physical switch on them, that will enable/disable write-access, you don't have anything like that on yours?

Also run ```
dmesg
``` and see if there's any error messages related to /dev/sdb1

---

### Post by Mzwo on 2008-10-22
> **geirha said:**
> .

Not sure why it wouldn't work like that before, but if you have several users logged in at the same time, they will sort of "fight" for mounting the drive, and the one who wins gets the write permissions. Could that be the case?


no user fights. i'm the only one. suppose i'll file the case under "bizarre" and forget about it.

thanks for your help!

Mzwo

---

### Post by skippy2222 on 2008-10-22
results 

touch: cannot touch `/media/STOREX/testfile': Permission denied


[   51.922929] eth0: no IPv6 routers present
[  130.225349] FAT: Filesystem panic (dev sdb1)
[  130.225356]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  130.225359]     File system has been set read-only
[  131.084000] FAT: Filesystem panic (dev sdb1)
[  131.084006]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  270.401350] FAT: Filesystem panic (dev sdb1)
[  270.401357]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  270.401360]     File system has been set read-only
[  951.151638] FAT: Filesystem panic (dev sdb1)
[  951.151652]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 1075.329917] FAT: Filesystem panic (dev sdb1)
[ 1075.329927]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 1099.267539] FAT: Filesystem panic (dev sdb1)
[ 1099.267547]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 1131.813580] FAT: Filesystem panic (dev sdb1)
[ 1131.813587]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 1153.578111] FAT: Filesystem panic (dev sdb1)
[ 1153.578120]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 1180.411399] FAT: Filesystem panic (dev sdb1)
[ 1180.411411]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 1720.103018] usb 3-7: USB disconnect, address 5

---

### Post by geirha on 2008-10-22
Looks like an error with the filesystem. Mount it in windows and run scandisk/chkdsk on it.

---

### Post by skippy2222 on 2008-10-22
there is my problem I have no windows anymore, can I resize the ubuntu partitions and hack off 20GB for a windows restore session? if so how do I do it?

---

### Post by northern lights on 2008-10-22
> **skippy2222 said:**
> [  130.225349] FAT: Filesystem panic (dev sdb1)
[  130.225356]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  130.225359]     File system has been set read-only

Running```
sudo dosfsck -av /dev/sdb1
```should fix your filesystem errors.

---

### Post by skippy2222 on 2008-10-22
superb, its copying across.


thank you for your time and patience, much appreciated.

---

### Post by northern lights on 2008-10-22
Sorted. Glad we could help.

As an aside:
> **geirha said:**
> Mount it in windows and run scandisk/chkdsk on it.
*dosfsck* is the Linux alternative to just that.

---

### Post by Mzwo on 2008-10-22
...  i consider this solved, then. :-)

Mzwo

---

### Post by northern lights on 2008-10-22
> **Mzwo said:**
> ...  i consider this solved, then. :-)
Seems to be for both of you...

---

### Post by skippy2222 on 2008-10-23
yep, fully working, thank you very much

---

