---
title: "Can't access fat32 partition"
date: 2008-09-16
forum: General Help
---

### Post by tommyG999 on 2008-09-16
Hey, I'm new at Ubuntu been messing around with it for a few hours now..got 2 say I'm loving it!! The problem I'm experiencing right now Is that I can't access my fat32 partition..can only see the ntfs partition.

fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes

255 heads, 63 sectors/track, 9729 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x13a5d34b



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS

/dev/sda2            1913        9728    62782020    f  W95 Ext'd (LBA)

/dev/sda5            1913        3824    15358108+  83  Linux

/dev/sda6            3825        4334     4096543+  82  Linux swap / Solaris

/dev/sda7            4335        9728    43327273+   c  W95 FAT32 (LBA)





Any help will be greatly appreciated!!

---

### Post by iaculallad on 2008-09-16
Open your terminal (Applications->Accessories->Terminal):

Create a directory mount point for your FAT32 partition:

```
sudo mkdir /media/FAT32
```

Open your /etc/fstab file for editing:

```
gksudo gedit /etc/fstab
```

And try to paste the line of text below on the last part of the file (Use copy and paste):

> /dev/sda7 /media/FAT32 vfat iocharset=utf8,umask=000 0 0

Save and close the file. While on your terminal, try to execute:

```
sudo mount -a
```

---

### Post by tommyG999 on 2008-09-16
> **iaculallad said:**
> Open your terminal (Applications->Accessories->Terminal):

Create a directory mount point for your FAT32 partition:

```
sudo mkdir /media/FAT32
```

Open your /etc/fstab file for editing:

```
gksudo gedit /etc/fstab
```

And try to paste the line of text below on the last part of the file (Use copy and paste):



Save and close the file. While on your terminal, try to execute:

```
sudo mount -a
```
thanks for speedy reply but I still can't see it.


here is what's in the fstab...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=b16b2aa7-8c67-4075-85d1-d74e1e2b8f1f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=43BA-F5AB  /share          vfat    utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=e92d50b1-72e3-4f6c-8cef-b155bf2ba824 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda7 /media/FAT32 vfat iocharset=utf8,umask=000 0 0

---

### Post by iaculallad on 2008-09-16
Don't forget executing:

```
sudo mount -a
```

After that, navigate Places->Computer and locate your FAT32 drive. Try looking at your desktop too as the command above executes mount on the devices included in your fstab file.

---

### Post by tommyG999 on 2008-09-16
executed 'sudo mount -a' but still can't find the drive on the Desktop nor in Computer..
should I restart the computer??

---

### Post by tommyG999 on 2008-09-17
plz help..

---

### Post by blueturtl on 2008-09-17
Better check that the case of the letters matches in both fstab and the actual directory.

Aka if fstab says: /media/FAT32 then the actual directory can't be /media/fat32

See if that helps.

---

### Post by tommyG999 on 2008-09-17
still not working.

fdisk shows this: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13a5d34b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            1913        9728    62782020    f  W95 Ext'd (LBA)
/dev/sda5            1913        3824    15358108+  83  Linux
/dev/sda6            3825        4334     4096543+  82  Linux swap / Solaris
/dev/sda7            4335        9728    43327273+   c  W95 FAT32 (LBA)


fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=b16b2aa7-8c67-4075-85d1-d74e1e2b8f1f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=43BA-F5AB  /share          vfat    utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=e92d50b1-72e3-4f6c-8cef-b155bf2ba824 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda7 /media/FAT32 vfat iocharset=utf8,umask=000 0 0 

tried changing 'media' with 'share' but that didn't help...

---

### Post by drs305 on 2008-09-17
After you run "sudo mount -a", run "mount". If your FAT32 partition was mounted, it should include a line something like: 
/dev/sda/7 on /media/FAT32 type vfat .....

---

### Post by tommyG999 on 2008-09-18
looks like it's mounted but still can't see it

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
/dev/sda7 on /share type vfat (rw,utf8,umask=007,gid=46)
/dev/sda7 on /media/FAT32 type vfat (rw,iocharset=utf8,umask=000)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/xtn/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=xtn)
/dev/sda7 on /share/FAT32 type vfat (rw,iocharset=utf8,umask=000)
/dev/sda7 on /media type vfat (rw,iocharset=utf8,umask=000)

---

### Post by TeXtonyx on 2008-09-18
I think you should simplify this troubleshooting.  Make a copy of your fstab and name it something like fstabOrig.  Then make a new file for fstab, copy all the text from the original and paste it into gedit (I use gedit). Delete or comment out # every line in fstab which makes areference to /dev/sda7 in the new fstab. I think there may be something wrong with your fstab,  it looks redundant. So reboot, your Fat32 partition should not be mounted. (I play it safe and reboot, perhaps too cautiously.)
I've done this several times manually, recently. Let's try a different mount point.
sudo mkdir /mnt/share  which will make a directory for the mount.
sudo mount -t vfat /dev/sda7  /mnt/share  then cd /mnt/share change directory and
do an ls to see if you see the files belonging to the fat32 partition, are now showing up.
The point is to find out if the problem is in fstab, or somehow before that step. If you 
can see your fat32 files manually, then the problem is in your fstab entries.

---

### Post by TeXtonyx on 2008-09-18
# Entry for /dev/sda7 :
UUID=9b4248e1-e709-434b-a8c1-b921d9213d77 none swap sw 0 0
/dev/scd1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd0 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sda1 /media/WindowsXP ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdb7 /mnt/share vfat auto,users,rw 0 0
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
This is part of my fstab. I automatically mount my Windows XP partition which is on the first drive and automatically mount the fat32 partition which I decided to call share, on the second drive. Your entry would substitute your sda7 where I typed sdb7. I made a copy of the /share folder and pasted it on my desktop and renamed it to shared32. Anyway, you see why I thought your fstab held too many (conflicting?) entries. 
Good luck, Stephen

---

### Post by tommyG999 on 2008-09-19
It worked! Thanks a million!

---

### Post by baytuni on 2009-02-06
I think I have the proper directory permissions as:

```
bop@hal:/media$ ls -all
total 52
drwxr-xr-x  9 root root 4096 2009-02-06 13:21 .
drwxr-xr-x 20 root root 4096 2009-01-29 00:25 ..
drwxr-xr-x  2 root root 4096 2008-12-11 04:09 BOP
drwxrwxrwx  1 root root 8192 2009-02-05 18:49 BOP_
lrwxrwxrwx  1 root root    6 2008-12-04 04:48 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2008-12-04 04:48 cdrom0
drwxr-xr-x  2 root root 4096 2008-12-04 04:48 cdrom1
-rw-r--r--  1 root root   24 2009-02-04 14:45 .created_by_python-fstab
drwxr-xr-x  2 root root 4096 2009-02-02 15:07 disk
-rw-r--r--  1 root root   86 2009-02-06 13:21 .hal-mtab
-rw-------  1 root root    0 2009-02-06 13:21 .hal-mtab-lock
drwxr-xr-x  2 root root 4096 2008-12-08 17:53 windows
drwxrwxrwx  6 root root 8192 2009-02-06 13:39 winlin
bop@hal:/media$ 

```
Here winlin is my fat32 partition. and i still cannot send files to trash for this partition.Any more ideas?

---

### Post by drs305 on 2009-02-06
> **baytuni said:**
> Here winlin is my fat32 partition. and i still cannot send files to trash for this partition.Any more ideas?

Are you able to create/change files? If you mount /media/winlin with the following you should be able to create and delete files. Change the device to the correct designation (e.g. sda4, sdd2, etc) The command assumes you are user 1000 (check with the "id" command):
```

sudo mount /dev/sd[COLOR="Red"]XX[/COLOR] /media/winlin -t vfat -o uid=1000

```

Alternatively, you can open nautilus with admin powers. Be careful as you can delete anything, including system files.

```
gksudo nautilus /media/winlin
```

---

