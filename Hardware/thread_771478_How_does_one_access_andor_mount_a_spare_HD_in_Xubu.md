---
title: "How does one access and/or mount a spare HD in Xubuntu?"
date: 2008-04-27
forum: Hardware
---

### Post by celticninja on 2008-04-27
Well i have a spare HD and i formatted it to ext3, but cant mount it in GParted. And upon reading different forum post typed in the sudo fdisk -l command and it produced this:

[I]Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c34de

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd1fa51f2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       10011    80413326   83  Linux[/I]

and i tried *sudo mount /dev/sdb and /dev/sdv1* but it came up with:

can't find /dev/sdb1 in /etc/fstab or /etc/mtab

---

### Post by chewearn on 2008-04-28
What do you get for the following commands:
```
mount -l
```
```
cat /etc/fstab
```

---

### Post by celticninja on 2008-04-28
**mount -l:**

```
[I]/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro) []
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev[/I]
```


**cat /etc/fstab:**


```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4209be6b-b03e-43d5-b862-a533c6d39195 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=29835988-43cd-481f-829b-a419598e85f8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0


```

---

### Post by chewearn on 2008-04-28
Right-click on a desktop panel
Select "Add new item"
Type "Places" in the search box
Select Places applet
Click "Add" button

A "Places" applet will now be added on the panel.  If you click on it, your additional harddisk should be listed.
Click on the harddisk entry, select the pop-up menu "Mount".
To unmount, right-click on your harddisk entry, and select "Unmount".

---

### Post by celticninja on 2008-04-28
Well i did that, and it just has the same options as the default Places

---

### Post by sisco311 on 2008-04-28
To mount manually the partition:
```
sudo mount -t ext3 -o defaults /dev/sdb1 /mnt
```

The partition will be mounted in the /mnt directory.


To mount the partition at boot time:
Edit the fstab:
```
sudo mousepad /etc/fstab
```and add this line at the end of the file:
> /dev/sdb1    **<mount-point>**    ext3    relatime,defaults    0    2Replace <mount-point> with an empty,existing directory from your file system.
example1:
```
sudo mkdir /media/my-data
```--->
> /dev/sdb1    **/media/my-data**    ext3    relatime,defaults    0    2example2:
```
mkdir /home/<your-username-here>/data
```--->
> /dev/sdb1    **/home/<you-username-here>/data**    ext3    relatime,defaults    0    2Mount the partition:
```
sudo mount -a
```To get write permission change the owner and group[ of the partition:

```
sudo chown -R <your-username>:<your-username> <mount-point>
```For example:
```
sudo chown -R celticninja:celticninja /home/celticninja/data
```

---

### Post by celticninja on 2008-04-28
Thanks, i will probably just keep that command to manually mount it, bc i don't always need to use it, basically its just for back-up :)

---

