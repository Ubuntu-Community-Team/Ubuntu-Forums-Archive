---
title: "[SOLVED] A Beginner with a missing drive"
date: 2008-06-13
forum: Hardware
---

### Post by wearekosh on 2008-06-13
Can someone help me find a SATA drive on my ASUS P5K Motherboard
I am dual boot UBUNTU / XP 
In XP I see the 3 drives plugged into the SATA ports 2 3 & 4 - C: D: & E: 
In UBUNTU I see only sda1 & sdb1 in /media
I seem to be missing E: drive :( that has all my stored data on....

:confused: Speak slowly - I'm a NeWbE to Linux :):lolflag:

Thanks

---

### Post by aquavitae on 2008-06-13
Can you open a terminal (its in the menus) a post the output of the following commands:
```
sudo fdisk -l
cat /etc/mtab

```

---

### Post by wearekosh on 2008-06-13
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04600460

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17593   141315741    7  HPFS/NTFS
/dev/sda2           30340       30401      498015   82  Linux swap / Solaris
/dev/sda3           17594       30339   102382245   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04b104b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30400   244187968+   7  HPFS/NTFS

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x34301248

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       24321   195358401    7  HPFS/NTFS


----

/dev/sda3 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
/dev/sda1 /media/sda1 fuseblk rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096 0 0
/dev/sdb1 /media/sdb1 fuseblk rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096 0 0
securityfs /sys/kernel/security securityfs rw 0 0


--------

---

### Post by aquavitae on 2008-06-13
When you say you can't find it, do you mean its not listed under Places?  What happens if you type ```
gnome-mount -d /dev/sdc1
```

---

### Post by wearekosh on 2008-06-13
8-[ I seem to have a new disk in my 'Places' menu :) 
and on my desk top too......Which seem to be the drive i am looking for.! :) 

Will it stay there if i reboot?

(shutdown)
doesn't seem to be there - IS GONE.. :(
How can i make mount on boot..

thanks

---

### Post by Coppy on 2008-06-13
edit the /etc/fstab using your favourite editor. 

first
create a folder in either /mnt or /media.

Then
add line to fstab something like this:
/dev/sda1 /media/<folder name> ntfs-3g defaults,locale=en_AU.UTF-8 0 0

---

### Post by wearekosh on 2008-06-13
:confused:
/dev/sda1 /media/<folder name> ntfs-3g defaults,locale=en_AU.UTF-8 0 0
not what i'm looking for i think as the first bit seems a bit wrong

maybe
/dev/sdc1 /media/disk ntfs-3g defaults,locale=en_AU.UTF-8 0 0
or
maybe i could ask for a second openion 

thanks

---

### Post by wearekosh on 2008-06-13
Found the answer out there - (somewhere else)

after the
gnome-mount -d /dev/sdc1
I unmounted the disk
installed ntfs-config from add/remove menu
ran it
detected it and I selected it and gave it a name
all better now - I have access and it is there after a restart :)

thanks for the help aquavitae :popcorn:

---

