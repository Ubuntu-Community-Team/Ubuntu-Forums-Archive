---
title: "Drive won't &quot;unmount&quot;"
date: 2010-04-13
forum: Hardware
---

### Post by ftPeter on 2010-04-13
Hi,

I'm looking for some help.  I'm trying to resize a partition but I'm having a problem where parted believes that the partition is mounted, even though it is not.

Does anyone know a work around or fix that will get me going?

Here is what parted is saying:
```
(parted) select /dev/sdb                                                  
Using /dev/sdb
(parted) print 
Model: ATA Hitachi HDS72202 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 2      32.3kB  2000GB  2000GB  extended                    
 5      126GB   245GB   119GB   logical   ext3              
 6      1995GB  2000GB  5075MB  logical   linux-swap        

(parted) move 5 32.3kb 1994gb
Error: Partition /dev/sdb5 is being used. You must unmount it before you modify it with Parted.
(parted)   
```

Here is why I'm pretty sure it's not mounted:
```
peter@robotron-linux:~$ umount /dev/sdb5
umount: /dev/sdb5 is not mounted (according to mtab)
peter@robotron-linux:~$ more /etc/mtab
/dev/sda5 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.27-17-generic/volatile tmpfs rw,mode=755 0 0
securityfs /sys/kernel/security securityfs rw 0 0
none /proc/fs/vmblock/mountPoint vmblock rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/peter/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=peter 0 0
peter@robotron-linux:~$ 
```

---

### Post by pastalavista on 2010-04-13
The drive is mounted or you couldn't be running from it. It's the "root" filesystem that all other drives are mounted inside of. You need to resize working  partitions from a live CD.

---

### Post by r_s on 2010-04-13
Are you using NTFS config tool?

---

### Post by ftPeter on 2010-04-13
> **r_s said:**
> Are you using NTFS config tool?

No, I'm not running NTFS anywhere.

Also, it's a secondary drive, so I'm not running from it.  /dev/sda is my root/boot/swap.

---

### Post by pastalavista on 2010-04-13
> **ftPeter said:**
> No, I'm not running NTFS anywhere.

Also, it's a secondary drive, so I'm not running from it.  /dev/sda is my root/boot/swap.
In that case, unless it's mounted in your home directory, you need to use sudo before you use parted, mount/umount commands.

---

### Post by ftPeter on 2010-04-13
I got the livecd.  That worked.  I'll just chalk this up to weirdness.

Thanks for your replies.

---

