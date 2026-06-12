---
title: "Not the owner of my second hard drive"
date: 2008-12-23
forum: Installation &amp; Upgrades
---

### Post by Evil Ninja on 2008-12-23
I'm having a problem (hopefully my last one) with my second hard drive. It says I am not the owner is the hard drive, so I can't do anything with it. I can't make folders, put files in it, etc. Any help how how to change it so I can "own" the drive again?

---

### Post by Idefix82 on 2008-12-23
What is the name of the drive? What is the output if you open the terminal and type in
```
ls /media
```

To change ownership you use the chown command, but if you answer the above questions I can tell you the exact command.

---

### Post by Evil Ninja on 2008-12-23
> **Idefix82 said:**
> What is the name of the drive? What is the output if you open the terminal and type in
```
ls /media
```

To change ownership you use the chown command, but if you answer the above questions I can tell you the exact command.

```
marcastorck@marcslaptop:~$ ls /media
cdrom  cdrom0  mynewdrive

```

Hm. The drive I need to own is "mynewdrive", but I don't know why it's showing two cdrom's.

---

### Post by Idefix82 on 2008-12-23
To change ownership do
```
sudo chown -R $USER:$USER /media/mynewdrive
```

I hope it's just data and no linux software on this drive? Otherwise the software might stop working if you change its ownership.

---

### Post by logos34 on 2008-12-23
> **Evil Ninja said:**
> ```
marcastorck@marcslaptop:~$ ls /media
cdrom  cdrom0  mynewdrive

```

Hm. The drive I need to own is "mynewdrive", but I don't know why it's showing two cdrom's.

cdrom might just be a link

> ls [COLOR="Red"]-l[/COLOR] /media

try

sudo chown -R username /media/mynewdrive

where username = yours

---

### Post by Evil Ninja on 2008-12-23
> **Idefix82 said:**
> To change ownership do
```
sudo chown -R $USER:$USER /media/mynewdrive
```

I hope it's just data and no linux software on this drive? Otherwise the software might stop working if you change its ownership.

Nope. Just an empty drive.

> **logos34 said:**
> cdrom might just be a link



try

sudo chown -R username /media/mynewdrive

where username = yours


It didn't seem to work, unless I need to restart the computer.

---

### Post by taurus on 2008-12-23
What filesystem is your second harddrive?

Post

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by Evil Ninja on 2008-12-23
> **taurus said:**
> What filesystem is your second harddrive?

Post

```
sudo fdisk -l
cat /etc/fstab
df -h
```

```
marcastorck@marcslaptop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x45ff45fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18728   150432628+  83  Linux
/dev/sda2           18729       19457     5855692+   5  Extended
/dev/sda5           18729       19457     5855661   82  Linux swap / Solaris
c
Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xce8d5882

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux
marcastorck@marcslaptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a1619353-edf1-4902-9b5a-01e4ad54925e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=b14ee239-4488-4d59-95c9-9660337f26dd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1    /media/mynewdrive   ext3    defaults     0        2
marcastorck@marcslaptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             142G  3.3G  131G   3% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  212K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  2.8M  1.5G   1% /dev
tmpfs                 1.5G  884K  1.5G   1% /dev/shm
lrm                   1.5G  2.4M  1.5G   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sdb1             147G  188M  140G   1% /media/mynewdrive

```

---

### Post by taurus on 2008-12-23
Try

```
sudo chown -R marcastorck:marcastorck /media/mynewdrive
ls -la /media
```
You should now be the proud owner of /media/mynewdrive so you can write to it anytime you want.

---

### Post by Evil Ninja on 2008-12-23
> **taurus said:**
> Try

```
sudo chown -R marcastorck:marcastorck /media/mynewdrive
ls -la /media
```
You should now be the proud owner of /media/mynewdrive so you can write to it anytime you want.

Indeed I am. Thanks a lot. :)

---

### Post by thexaspect on 2008-12-29
Hi there, I'm having the exact same problem as the original poster, but the solutions that worked for him are not working for me. And one other, I completely reinstalled Hardy in the hopes that picking up the new drive from the beginning would work out better, and it didnt. For whatever reason, chown and chmod have not worked. I'll let the code speak:

```
x@serverbox:~$ sudo chown -R x:x /media/space
chown: changing ownership of `/media/space': Operation not permitted
x@serverbox:~$ sudo chown -R $USER:$USER /media/space
chown: changing ownership of `/media/space': Operation not permitted
x@serverbox:~$ sudo chown -R x /media/space
chown: changing ownership of `/media/space': Operation not permitted
x@serverbox:~$ sudo chown -R x /media/space
chown: changing ownership of `/media/space': Operation not permitted
x@serverbox:~$ 
x@serverbox:~$ ls -la /media
total 32
drwxr-xr-x  5 root root     4096 2008-07-02 06:16 .
drwxr-xr-x 21 root root     4096 2008-12-29 01:49 ..
lrwxrwxrwx  1 root root        6 2008-12-29 01:39 cdrom -> cdrom0
drwxr-xr-x  2 root root     4096 2008-12-29 01:39 cdrom0
lrwxrwxrwx  1 root root        7 2008-12-29 01:39 floppy -> floppy0
drwxr-xr-x  2 root root     4096 2008-12-29 01:39 floppy0
drwxrwx---  2 root plugdev 16384 1969-12-31 19:00 space
x@serverbox:~$ 

```

and also my fdisk and fstab:
```
x@serverbox:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000874f8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60044   482303398+  83  Linux
/dev/sda2           60045       60801     6080602+   5  Extended
/dev/sda5           60045       60801     6080571   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00081ee8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    b  W95 FAT32
x@serverbox:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=087f9062-e632-4ba0-ae0f-23a6c0e0432d /               ext2    relatime,errors=remount-ro 0       1
# /dev/sdb1
UUID=4958-25ED  /media/space    vfat    utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=d1b5ada6-f3bd-407a-b932-a6d11dc6bab7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
x@serverbox:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             453G  2.0G  428G   1% /
varrun               1014M  104K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   52K 1014M   1% /dev
devshm               1014M   48K 1014M   1% /dev/shm
lrm                  1014M   38M  976M   4% /lib/modules/2.6.24-19-generic/volatile
/dev/sdb1             932G   16K  932G   1% /media/space
gvfs-fuse-daemon      453G  2.0G  428G   1% /home/x/.gvfs
x@serverbox:~$ 

```

Any help would be GREATLY appreciated because otherwise I've got this shiny new 1TB paperweight sitting on my desk....

---

### Post by taurus on 2008-12-29
> **thexaspect said:**
> Hi there, I'm having the exact same problem as the original poster, but the solutions that worked for him are not working for me. And one other, I completely reinstalled Hardy in the hopes that picking up the new drive from the beginning would work out better, and it didnt. For whatever reason, chown and chmod have not worked. I'll let the code speak:

```
x@serverbox:~$ sudo chown -R x:x /media/space
chown: changing ownership of `/media/space': Operation not permitted
x@serverbox:~$ sudo chown -R $USER:$USER /media/space
chown: changing ownership of `/media/space': Operation not permitted
x@serverbox:~$ sudo chown -R x /media/space
chown: changing ownership of `/media/space': Operation not permitted
x@serverbox:~$ sudo chown -R x /media/space
chown: changing ownership of `/media/space': Operation not permitted
x@serverbox:~$ 
x@serverbox:~$ ls -la /media
total 32
drwxr-xr-x  5 root root     4096 2008-07-02 06:16 .
drwxr-xr-x 21 root root     4096 2008-12-29 01:49 ..
lrwxrwxrwx  1 root root        6 2008-12-29 01:39 cdrom -> cdrom0
drwxr-xr-x  2 root root     4096 2008-12-29 01:39 cdrom0
lrwxrwxrwx  1 root root        7 2008-12-29 01:39 floppy -> floppy0
drwxr-xr-x  2 root root     4096 2008-12-29 01:39 floppy0
drwxrwx---  2 root plugdev 16384 1969-12-31 19:00 space
x@serverbox:~$ 

```

and also my fdisk and fstab:
```
x@serverbox:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000874f8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60044   482303398+  83  Linux
/dev/sda2           60045       60801     6080602+   5  Extended
/dev/sda5           60045       60801     6080571   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00081ee8

   Device Boot      Start         End      Blocks   Id  System
**[COLOR="Red"]/dev/sdb1               1      121601   976760001    b  W95 FAT32[/COLOR]**
x@serverbox:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=087f9062-e632-4ba0-ae0f-23a6c0e0432d /               ext2    relatime,errors=remount-ro 0       1
# /dev/sdb1
UUID=4958-25ED  /media/space    vfat    utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=d1b5ada6-f3bd-407a-b932-a6d11dc6bab7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
x@serverbox:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             453G  2.0G  428G   1% /
varrun               1014M  104K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   52K 1014M   1% /dev
devshm               1014M   48K 1014M   1% /dev/shm
lrm                  1014M   38M  976M   4% /lib/modules/2.6.24-19-generic/volatile
/dev/sdb1             932G   16K  932G   1% /media/space
gvfs-fuse-daemon      453G  2.0G  428G   1% /home/x/.gvfs
x@serverbox:~$ 

```

Any help would be GREATLY appreciated because otherwise I've got this shiny new 1TB paperweight sitting on my desk....

The reason chmod & chown don't work for you because you are using fat32/vfat filesystem while the OP uses ext3.  

So, do you want to leave that new harddrive as fat32/vfat or do you want to reformat it to ext3 filesystem?

---

### Post by thexaspect on 2008-12-29
Nope, I can reformat no problem, didn't even realize that would be an issue, I'll let you know how it works out =D

---

### Post by thexaspect on 2008-12-29
you, sir, are a genius

---

