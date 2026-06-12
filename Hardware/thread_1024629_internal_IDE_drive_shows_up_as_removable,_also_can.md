---
title: "internal IDE drive shows up as removable, also cant be renamed."
date: 2008-12-29
forum: Hardware
---

### Post by animaniac on 2008-12-29
I installed a new drive (sdb) and added it to fstab with the mountpoint /home/user/Pictures. It still shows up in Removable Media, and the icon for the drive shows up on the desktop. I want the system to treat the drive as it does my root and home partition and not my external media.


Also i cant rename it, i get the following:
> 
Item could not be renamed.

Sorry, could not rename "250.1 GB Media" to "Pictures": Operation not supported by backend

any tips on how these two annoyances can be solved?

edit: even though i changed the ownersip of the drive and all its contents to myself, still nothing.

---

### Post by taurus on 2008-12-29
What filesystem is that harddrive?  Can you post the outputs of these commands from a terminal?

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by animaniac on 2008-12-29
Here you go..

> user:~$ sudo fdisk -l
[sudo] password for user: 

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcb71cb71

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         436     3502138+  82  Linux swap / Solaris
/dev/sda2   *         437        2174    13960485   83  Linux
/dev/sda3            2175       10011    62950702+  83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0148e76d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux

Disk /dev/sdg: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12345678

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1       30515   245111706    c  W95 FAT32 (LBA)

> user:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=44377417-2bd5-4527-baf8-5610a34b3234 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=fbee422e-6e2f-4189-876d-d7070c29bbfd /home           ext3    relatime        0       2
# /dev/sda1
/dev/sda1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/sdb1
/dev/sdb1 /home/user/Pictures           ext3    relatime        0       3



> user:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              14G  4.0G  8.6G  32% /
tmpfs                 505M     0  505M   0% /lib/init/rw
varrun                505M  212K  505M   1% /var/run
varlock               505M     0  505M   0% /var/lock
udev                  505M  2.8M  502M   1% /dev
tmpfs                 505M  444K  505M   1% /dev/shm
lrm                   505M  2.0M  503M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sda3              60G   11G   46G  19% /home
/dev/sdb1             230G   29G  190G  13% /home/user/Pictures
/dev/sdg1             234G  158G   77G  68% /media/LACIE


---

### Post by taurus on 2008-12-29
What if you edit /etc/fstab and change the last line from this

```
/dev/sdb1 /home/user/Pictures ext3 relatime 0 3
```
to this.

```
/dev/sdb1 /home/user/Pictures ext3 defaults 0 2
```
Save it and reboot.

---

### Post by animaniac on 2008-12-30
still same problems, changing options to defaults did nothing.

---

### Post by Glendon on 2008-12-30
I'm having this problem as well. 

I added a second internal drive, added an entry in fstab, and I'm getting an icon on the desktop next to my external USB drives. 

Any suggestions?

---

### Post by Glendon on 2008-12-30
After some playing around I figured out how to make internal drives not show up as removable. 

I was mounting my new drive's fs to /media/here.

I tried mounting it to /mnt/here instead and now it's not on my desktop anymore.

Profit!

---

### Post by Glendon on 2008-12-31
If you want to rename the drive try this:

While mounted,

```
tune2fs -L <new-name> <device>
```

for example,

```
tune2fs -L my_new_hard_drive /dev/sdb1
```

Unmount

Recycle the power on the drive

Mount

---

