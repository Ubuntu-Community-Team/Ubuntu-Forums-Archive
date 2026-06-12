---
title: "[SOLVED] Another busted fstab!"
date: 2008-11-10
forum: General Help
---

### Post by mixim on 2008-11-10
Hello, tried to use the pysdm gui for automounting my NTFS drive, only thing it resulted in was my main drive automounting in /media and therefore on the desk... where should this be mounted when configured as stock? Don't care about the automount ntfs at this moment.

[COLOR="DarkRed"][B]
How should I configure my sdb in fstab for normal behaviour[/B]? Completely remove all the sdb entries?[/COLOR]

**fdisk -l gives:**
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7a40316e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6528    52428800    7  HPFS/NTFS
/dev/sda2            6528       60802   435955712    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x73a6ebc1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9327    74919096   83  Linux
/dev/sdb2            9328        9729     3229065    5  Extended
/dev/sdb5            9328        9729     3229033+  82  Linux swap

```
[B]
fstab looks like this:[/B]
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sda1
UUID=e80540ff-2292-4206-a9eb-3bbf1dea8b27  /              ext3         relatime,errors=remount-ro  0  1  
# /dev/sda5
UUID=13f96180-496f-46ef-a3f8-f519d91d038a  none           swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/sdb5                                  /media/sdb5    swap         sw                          0  0  
/dev/sdb1                                  /media/sdb1    ext3         errors=remount-ro           0  0  
/dev/sda1                                  /media/sda1    ntfs         defaults                    0  0  

```

Will do it the backup way next time ! Thanks in advance!

---

### Post by mixim on 2008-11-14
Anybody got a thought on this?

---

### Post by tarps87 on 2008-11-14
can you post the output of this please
```
sudo blkid
```

It appears between fdisk and the fstab file the device names change, the blkid will show the devices uuid's which do not change

---

### Post by geirha on 2008-11-14
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sda1
UUID=e80540ff-2292-4206-a9eb-3bbf1dea8b27  /              ext3         relatime,errors=remount-ro  0  1  
# /dev/sda5
UUID=13f96180-496f-46ef-a3f8-f519d91d038a  none           swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
[COLOR="Red"]/dev/sdb5                                  /media/sdb5    swap         sw                          0  0  
/dev/sdb1                                  /media/sdb1    ext3         errors=remount-ro[/COLOR]           0  0  
[COLOR="Blue"]/dev/sda1                                  /media/sda1    ntfs         defaults                    0  0[/COLOR]  

```

The two lines marked in red is your swap and / partitions respectively, they are already mounted by the two lines starting with UUID=, so just remove those two red lines.

The blue line is your ntfs, but it's not how you want it. It is using the old ntfs filesystem driver which doesn't support writing.

Change it to something like this:
```
UUID=*abcd1234* /media/windows  ntfs-3g defaults,uid=*yourusername*,gid=admin,fmask=113,dmask=002 0  0
```

Replace the UUID with the correct uuid. The command **sudo blkid** will list the UUIDs of all filesystems. 

I replaced /media/sda1 with /media/windows, you can call it whatever you like, but make sure the mount-point exists ```
sudo mkdir /media/windows
```

The options field makes the filesystem owned by *yourusername* (replace it with your username) and the group admin. The fmask and dmask sets the permissions for the files and directories, and in this case they are set so that *yourusername* and the members of the group admin have read and write access, while everyone else only have read access.

---

### Post by drs305 on 2008-11-14
/media is the default location for devices, and the default is also for these devices to be shown on the desktop. If you do not wish a specific device to appear on the desktop, you can change the mount point to /mnt/mountpoint.name , for example */mnt/mydata*

---

### Post by The Cog on 2008-11-14
In the absence of the output from blkid, try this one. I have commented out the original root (/) UUID line and the original sdb1 line, and added a modified sdb1 line that mounts it as root:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sda1
#UUID=e80540ff-2292-4206-a9eb-3bbf1dea8b27  /              ext3         relatime,errors=remount-ro  0  1  
# /dev/sda5
UUID=13f96180-496f-46ef-a3f8-f519d91d038a  none           swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/sdb5                                  /media/sdb5    swap         sw                          0  0  
#/dev/sdb1                                  /media/sdb1    ext3         errors=remount-ro           0  0  
/dev/sdb1                                  /              ext3         relatime,errors=remount-ro  0  1  
/dev/sda1                                  /media/sda1    ntfs         defaults                    0  0

```

---

### Post by mixim on 2008-11-14
> **tarps87 said:**
> can you post the output of this please
```
sudo blkid
```


**Result of blkid:**
```
/dev/sda1: UUID="C8F49685F4967582" LABEL="OS" TYPE="ntfs" 
/dev/sda2: UUID="4EE0B04DE0B03CD1" LABEL="Filer" TYPE="ntfs" 
/dev/sdb1: UUID="e80540ff-2292-4206-a9eb-3bbf1dea8b27" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="13f96180-496f-46ef-a3f8-f519d91d038a" 
```

---

### Post by tarps87 on 2008-11-17
This should get it back to normal
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sda1
UUID=e80540ff-2292-4206-a9eb-3bbf1dea8b27  /              ext3         relatime,errors=remount-ro  0  1  
# /dev/sda5
UUID=13f96180-496f-46ef-a3f8-f519d91d038a  none           swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  

``` 

To add the NTFS shares first run these commands
```
mkdir /media/WinXP
mkdir /media/Filer
```
Now add these two lines
```

#/dev/sda1
UUID=C8F49685F4967582 /media/WinXP ntfs-3g auto,users,uid=1000,gid=100,dmask=027,fmask=137,utf8  0  0

#/dev/sda2
UUID=4EE0B04DE0B03CD1 /media/Filer ntfs-3g auto,users,uid=1000,gid=100,dmask=027,fmask=137,utf8  0  0

```

---

### Post by mixim on 2008-11-17
> **tarps87 said:**
> This should get it back to normal

Thanks geirha,tarps87 and the rest. Got it to work exactly this way yesterday!

[I]Tarps87:
You wrote "users" instead of a specific username, does this enable the shares for all users?[/I]

---

### Post by geirha on 2008-11-17
> **mixim said:**
> 
[I]Tarps87:
You wrote "users" instead of a specific username, does this enable the shares for all users?[/I]

From the mount(8)  (man 8 mount)
```

              users  Allow  every  user  to mount and unmount the file system.
                     This option implies the options noexec, nosuid, and nodev
                     (unless  overridden  by  subsequent  options,  as  in the
                     option line users,exec,dev,suid).

```

> **mixim said:**
> 
Were would be a suitable place to mount theese drives if I do not want ubuntu to recognize them as removable media?

Mounting them under /mnt/ instead of /media/ should make them not show up as drives in nautilus.

---

### Post by tarps87 on 2008-11-17
> **mixim said:**
> [I]Tarps87:
You wrote "users" instead of a specific username, does this enable the shares for all users?[/I]

users will allow any user to mount/unmout the device, they won't need to be sudo.
nouser will only permit root to mount the filesystem.

the uid and gid can be used to set access to the files on the drive, as it is set everyone should have access to it

uid=n, gid=n
Sets the user identifier, uid, and group identifier, gid, for all files on the filesystem.

---

### Post by tarps87 on 2008-11-17
Double post

---

### Post by mixim on 2008-11-17
Thanks for the info , yea figured the mnt plae out but great info on "users" from both of you!

thanks once again guys!

---

