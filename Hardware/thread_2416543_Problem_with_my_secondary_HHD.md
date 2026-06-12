---
title: "Problem with my secondary HHD"
date: 2019-04-11
forum: Hardware
---

### Post by keramidas on 2019-04-11
Hello, i run ubuntu 18.04.2 on my desktop. Ubuntu is installed on a 120GB SSD and i have a secondary 500GB HDD for storage. 
I installed two of my steam games on the secondary drive but the don`t start and upon restarting steam they don`t apeear installed at all. I think the secondary HHD in not correctly ''recognised'' by the system?[ATTACH=CONFIG]283003[/ATTACH]

---

### Post by TheFu on 2019-04-11
Please post the command AND output from **df -hT** and **sudo fdisk -l** using "code tags" so everything lines up. See my sig for code tag help.

---

### Post by keramidas on 2019-04-12
Thank you for your interest. I don`t understand what code tags are. Is this helpful?

```

stelios@stelios-desktop:~$ xman
Warning: Cannot convert string "-*-helvetica-medium-r-*-*-*-120-*-*-*-*-*-*" to type FontStruct
df -hT
Warning: Cannot convert string "-*-courier-medium-r-*-*-*-120-*-*-*-*-*-*" to type FontStruct
Warning: Cannot convert string "-*-courier-bold-r-*-*-*-120-*-*-*-*-*-*" to type FontStruct
Warning: Cannot convert string "-*-courier-medium-o-*-*-*-120-*-*-*-*-*-*" to type FontStruct
Warning: Cannot convert string "-*-symbol-*-*-*-*-*-120-*-*-*-*-*-*" to type FontStruct
stelios@stelios-desktop:~$ df -hT
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  3,9G     0  3,9G   0% /dev
tmpfs          tmpfs     795M  1,9M  793M   1% /run
/dev/sdb1      ext4      110G   16G   89G  15% /
tmpfs          tmpfs     3,9G   25M  3,9G   1% /dev/shm
tmpfs          tmpfs     5,0M  4,0K  5,0M   1% /run/lock
tmpfs          tmpfs     3,9G     0  3,9G   0% /sys/fs/cgroup

/dev/sda2      ext4      458G   15G  420G   4% /mnt/e937f956-c4ca-4e16-91f2-397cc7ce4b1d
tmpfs          tmpfs     795M   16K  795M   1% /run/user/121
tmpfs          tmpfs     795M   28K  795M   1% /run/user/1000

stelios@stelios-desktop:~$ sudo fdisk -l
[sudo] password for stelios: 
Disk /dev/loop0: 3,7 MiB, 3846144 bytes, 7512 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
```

---

### Post by TheFu on 2019-04-12
Without code tags, it is too hard to read. It should line up here just like it lined up in the terminal. I can't be certain, but looks like the 2nd HDD is being mounted using a GUI.  That isn't ideal.  Modify the fstab file to mount the partition.  A guide to accomplish that: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Basically, you need to add 1 line to the file. Do not touch any other lines.  Use the **sudoedit /etc/fstab** command from a terminal to modify it.

Also, all the "loop" device output above isn't needed. It just clutters stuff up, so if you do edit to add the code tags, as requested, please remove all the lines and stanzas with "loop" devices.  They are almost never desired or need to be seen - like 99.99999% of the time, they are just clutter.

---

### Post by oldfred on 2019-04-12
Added code tags, easy to add in Forum's advanced editor with # icon.
       How to use Code tags, # in advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)

Also removed loop devices as they are all snaps, and just noise in mounting.
       exclude snaps
lsblk -af |grep -sv loop 
            df | egrep -v /dev/loop 
    

You seem to be mounting with UUID.
Better to mount with label or specific mount point.

Another post with info on editing fstab. 
       
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting.
After any edits of fstab, be sure to run this. It should just return (it has correctly remounted everything), but if errors you must fix before rebooting.
      
 sudo mount -a

---

### Post by TheFu on 2019-04-12
How did
```
/dev/sda2      ext4      458G   15G  420G   4% /mnt/e937f956-c4ca-4e16-91f2-397cc7ce4b1d
```
get mounted?  Normally, when a GUI is used, it would be under /media/{userid}/.....  I've never known any human to manually mount storage into that location using the UUID as the directory and don't know any GUI tools which would do it either.  

oldfred, looks like the most important **fdisk** output was lost in the simplification.  Was looking for all specific partitions inside sda and sdb. If there was only had 1 partition for Linux and data, fine.  There might be a UEFI or /boot partition too, which aren't too important.  I don't recall the partitions.  Would be best to see that data to be certain, but if the OP is confident, just modify the fstab for the 1 partition and use a descriptive mount point is my advice.

---

### Post by oldfred on 2019-04-12
Sorry if it deleted too much. Too many loop devices.
I cannot undo, so could user post this which will show partitions, but not loop mounts, not sure how to do fdisk without loops other than just deleting them:
       lsblk -af |grep -sv loop
sudo fdisk -l # but delete or not copy loop devices.

---

### Post by TheFu on 2019-04-12
I hate loop devices.   Until I love them. ;)  Things were easier before snaps.

```
sudo fdisk -l /dev/sd[a-z] 

```would work too, unless someone is using NVMe devices.

---

### Post by keramidas on 2019-04-12
Sorry for the delay, i think we are on different timezones.
 I am a newbie, so i don`t feel brave enough to play around with fstab. Does this help?


stelios@stelios-desktop:~$ sudo fdisk -l /dev/sd[a-z]
[sudo] password for stelios: 
Disk /dev/sda: 465,8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x68da33f1

Device     Boot  Start       End   Sectors   Size Id Type
/dev/sda1         2048    206847    204800   100M  7 HPFS/NTFS/exFAT
/dev/sda2       206848 976771071 976564224 465,7G 83 Linux


Disk /dev/sdb: 111,8 GiB, 120034123776 bytes, 234441648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x8795c5e7

Device     Boot Start       End   Sectors   Size Id Type
/dev/sdb1        2048 234440703 234438656 111,8G 83 Linux

---

### Post by TheFu on 2019-04-12
If you won't modify the fstab, I don't see how we can help.  The fstab is how storage gets mounted at boot.  There is 1 other method, but it is more complicated.

Good luck to you.

---

### Post by oldos2er on 2019-04-12
> **keramidas said:**
> I am a newbie, so i don`t feel brave enough to play around with fstab.

Make a backup copy before modifying fstab, for example ```
sudo cp /etc/fstab /etc/fstab.backup
```

---

