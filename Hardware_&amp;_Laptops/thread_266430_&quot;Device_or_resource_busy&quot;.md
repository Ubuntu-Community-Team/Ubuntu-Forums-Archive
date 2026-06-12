---
title: "&quot;Device or resource busy&quot;"
date: 2006-09-27
forum: Hardware &amp; Laptops
---

### Post by SgtPepperKSU on 2006-09-27
Hi all.
I've [already posted]("http://ubuntuforums.org/showthread.php?t=265724") this under Desktop Support, but thought maybe hardware folks might be better equipped.
I am trying to create a raid1 partition using mdadm, but am getting "Device or resource busy" when (as far as I can tell) nothing is using either partition.  Any help on finding out why they are "busy" would be greatly appreciated.

Some info:
```
[FONT="Courier New"]**:~$ sudo mdadm --verbose --create /dev/md0 --level raid1 --raid-devices=2 /dev/hda3 /dev/hdb1**
mdadm: Cannot open /dev/hda3: Device or resource busy
mdadm: Cannot open /dev/hdb1: Device or resource busy
mdadm: create aborted
**:~$ sudo fdisk -l /dev/hdb**

Disk /dev/hdb: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        4863    39062016   fd  Linux raid autodetect
**:~$ sudo fdisk -l /dev/hda**

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9637    77409171   83  Linux
/dev/hda2           14501       14593      747022+   5  Extended
/dev/hda3            9638       14500    39062047+  fd  Linux raid autodetect
/dev/hda5           14501       14593      746991   82  Linux swap / Solaris

Partition table entries are not in disk order
**:~$ cat /etc/fstab**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
**:~$ cat /etc/mtab**
/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
lrm /lib/modules/2.6.15-27-686/volatile tmpfs rw 0 0
**:~$ sudo /usr/sbin/lsof /dev/hdb1**
**:~$ sudo /usr/sbin/lsof /dev/hda3**
**:~$ sudo /usr/sbin/lsof /dev/md0**
**:~$ sudo /usr/sbin/lsof | grep hdb1**
**:~$ sudo /usr/sbin/lsof | grep hda3**
**:~$ sudo /usr/sbin/lsof | grep md0**
md0_raid1  2054       root  cwd       DIR        3,1    4096          2 /
md0_raid1  2054       root  rtd       DIR        3,1    4096          2 /
md0_raid1  2054       root  txt   unknown                               /proc/2054/exe
**:~$ sudo /usr/sbin/lsof | grep md1**
md1_raid1  3734       root  cwd       DIR        3,1    4096          2 /
md1_raid1  3734       root  rtd       DIR        3,1    4096          2 /
md1_raid1  3734       root  txt   unknown                               /proc/3734/exe
**:~$ sudo /usr/sbin/lsof | grep md2**
**:~$ cat /etc/raidtab**
cat: /etc/raidtab: No such file or directory
**:~$ cat /proc/mdstat**
Personalities : [raid1]
md1 : active raid1 dm-3[1] dm-2[0]
      39061952 blocks [2/2] [UU]

md0 : active raid1 hda3[0] hdb1[1]
      39061952 blocks [2/2] [UU]

unused devices: <none>
**:~$ sudo mdadm --verbose --create /dev/md0 --level raid1 --raid-devices=2 /dev/hda3 /dev/hdb1**
mdadm: Cannot open /dev/hda3: Device or resource busy
mdadm: Cannot open /dev/hdb1: Device or resource busy
mdadm: create aborted
**:~$**[/FONT]
```

---

### Post by fmasi on 2006-09-28
I have the same message as you but becouse of another problem i postem my problem in [http://www.ubuntuforums.org/showthread.php?p=1555467#post1555467](http://www.ubuntuforums.org/showthread.php?p=1555467#post1555467)

anny whay in you case aparently /dev/md0 and /dev/md1 are in use as you can see in 
> :~$ cat /proc/mdstat
Personalities : [raid1]
md1 : active raid1 dm-3[1] dm-2[0]
      39061952 blocks [2/2] [UU]

md0 : active raid1 hda3[0] hdb1[1]
      39061952 blocks [2/2] [UU]

unused devices: <none>

you should stop them whith mdadm --stop /dev/md0 and the same for md1

maby you will have to clean the md superblock whith the --zero-superblock check it out in the man page.

Hope that it can help you fix your problem.:cool:

---

### Post by SgtPepperKSU on 2006-09-28
Yes, sorry, I forgot to reply here. :oops: That's exactly what I did to get it working.  Seeing that there was no raidtab blinded me to the fact that there were raid devices already there (why, I don't know).

Thanks!

---

