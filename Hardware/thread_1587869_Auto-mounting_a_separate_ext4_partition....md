---
title: "Auto-mounting a separate ext4 partition..."
date: 2010-10-04
forum: Hardware
---

### Post by Baldrick_NZ on 2010-10-04
Hi guys,

I've recently reclaimed precious HDD space where windows used to reside. I've formatted it to EXT4, labelled it, and can see it using Nautilus once I've booted up. I'm using the new partition for music and video.

The problem is when I start RhythmBox, no music loads until I actually mount the partition.

So, how can I get the partition to mount automatically upon start-up in the same way my external drive mounts?

Thanks in advance...

---

### Post by sisco311 on 2010-10-04
[thread=283131]How to fstab[/thread].

You have to create an fstab entry for the partition. You can use a pysdm or edit the file manually. 

The fstab entry should look like this:
```
LABEL=**label-of-the-partition** /media/mount-point ext4 relatime 0 2
```

---

### Post by Baldrick_NZ on 2010-10-04
> **sisco311 said:**
> [thread=283131]How to fstab[/thread].

You have to create an fstab entry for the partition. You can use a pysdm or edit the file manually. 

The fstab entry should look like this:
```
LABEL=**label-of-the-partition** /media/mount-point ext4 relatime 0 2
```

Tried pysdm, but it only lists sda5 & 6, neither are useful. The partition I'd like to automount is sda1 - but pysdm doesn't list this partition, even with a refresh.

---

### Post by ajgreeny on 2010-10-04
Does the partition show in ```
sudo fdisk -l
``` output?  If it does then simply make a mountpoint with ```
sudo mkdir /mnt/sda1
``` and then add the line manually to /etc/fstab with gksudo gedit /etc/fstab ```
UUID=longalphanumeric /mnt/sda1 ext4 defaults,relatime 0 2
```  You can get the UUID from ```
sudo blkid
``` and personally I prefer the UUID to a label, which you may not have even given to the partition.

---

### Post by Baldrick_NZ on 2010-10-05
> **ajgreeny said:**
> Does the partition show in ```
sudo fdisk -l
``` output?  If it does then simply make a mountpoint with ```
sudo mkdir /mnt/sda1
``` and then add the line manually to /etc/fstab with gksudo gedit /etc/fstab ```
UUID=longalphanumeric /mnt/sda1 ext4 defaults,relatime 0 2
```  You can get the UUID from ```
sudo blkid
``` and personally I prefer the UUID to a label, which you may not have even given to the partition.

So I did all that and now my puter won't start!!

I've loaded the liveCD, and tried to remove the offending line, but it won't let me because I don't have the 'permissions' to do it.

So, how, in terminal from the liveCD can I get into the etc /fstab file to change it?

Or is there another way?

Cheers.

---

### Post by Baldrick_NZ on 2010-10-05
bump...

---

### Post by drs305 on 2010-10-05
You can mount the partition from a LiveCD terminal:
```
sudo mount /dev/sd**XY** /mnt
gksudo gedit /mnt/etc/fstab
```

---

### Post by dtfinch on 2010-10-05
When it appears frozen during boot, try pressing the 's' key.

When mountall can't find a device in /etc/fstab during boot, it sits and waits for the device to magically appear somehow. Pressing 's' tells it to stop waiting. If that works, you can add a "nobootwait" mount option to the fstab entry to prevent it from stalling on subsequent boots when it can't find the device.

---

### Post by Baldrick_NZ on 2010-10-05
> **dtfinch said:**
> When it appears frozen during boot, try pressing the 's' key.

When mountall can't find a device in /etc/fstab during boot, it sits and waits for the device to magically appear somehow. Pressing 's' tells it to stop waiting. If that works, you can add a "nobootwait" mount option to the fstab entry to prevent it from stalling on subsequent boots when it can't find the device.

Thanks for that, the 's' button worked!

---

### Post by Baldrick_NZ on 2010-10-06
> **ajgreeny said:**
> Does the partition show in ```
sudo fdisk -l
``` output?  If it does then simply make a mountpoint with ```
sudo mkdir /mnt/sda1
``` and then add the line manually to /etc/fstab with gksudo gedit /etc/fstab ```
UUID=longalphanumeric /mnt/sda1 ext4 defaults,relatime 0 2
```  You can get the UUID from ```
sudo blkid
``` and personally I prefer the UUID to a label, which you may not have even given to the partition.

Thanks for all your help, which is much appreciated.

Neither this post or the one above helped.

Just to clarify what I'm wanting to achieve..

I have my main partition on sda5, with the swap on sda6. I have a newly formatted ext4 partition on sda1. Sda1 has been claimed as "Baldrick's Music". 
Currently, when I reboot, and go to 'Places' I find that partition. I click on it, and it mounts. The partition icon also shows on the desktop.
RhythmBox loads and then subsequently plays.

What I'm trying to achieve is to make sda1 automatically mount upon boot, so that RhythmBox can load without any further intervention.

When I tried the above, Ubuntu launched on reboot, but I couldn't see 'Baldrick's Music' under Places, so couldn't even be mounted manually.

Cheers.

---

### Post by sisco311 on 2010-10-06
Please post the output of:
```
sudo blkid -c /dev/null
```
```
mount
```
and
```
cat /etc/fstab
```

---

### Post by Baldrick_NZ on 2010-10-06
sudo blkid -c /dev/null
```
baldrick@baldrick-desktop:~$ sudo blkid -c /dev/null
[sudo] password for baldrick: 
/dev/sda1: LABEL="Baldrick's Music" UUID="5b1cea5a-bc0c-4256-b887-41d323e42f8e" TYPE="ext4" 
/dev/sda5: UUID="38c1a200-1131-46a1-a9c4-d95e2f4c2706" TYPE="ext4" 
/dev/sda6: UUID="c05e9e5c-d35c-4eae-b4ed-6cc88923137c" TYPE="swap" 

```

mount

```
/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sda1 on /media/Baldrick's Music type ext4 (rw,nosuid,nodev,uhelper=udisks)

```

cat /etc/fstab

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=38c1a200-1131-46a1-a9c4-d95e2f4c2706 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=c05e9e5c-d35c-4eae-b4ed-6cc88923137c none            swap    sw              0       0

```

Hope this helps...

Thanks again.

---

### Post by sisco311 on 2010-10-06
[list=i]
[*]Edit the fstab file:
```
gksu gedit /etc/fstab
```
and paste the following entry at the end of the file:
```
UUID=5b1cea5a-bc0c-4256-b887-41d323e42f8e    /media/Baldrick\047s\040Music    ext4    relatime    0    2
```


[*]Unmount the partition:
```
sudo umount /dev/sda1
```


[*]Create the mount point:
```
sudo mkdir -p "/media/Baldrick's Music"
```


[*]Mount all filesystems mentioned in fstab:
```
sudo mount -a
```
[/list]

---

### Post by Baldrick_NZ on 2010-10-07
Perfect, Sisco, just what I wanted. Thanks!

---

### Post by ivanrd on 2011-01-02
Just to say thank you too. This thread helped me to solve my problems with mounting additional ext4 volume called "Data". Mine was at sda5.

---

### Post by th1 on 2012-02-23
can someone help me out:

**sudo blkid -c /dev/null**
```
/dev/sda1: LABEL="Main Data" UUID="9A58141A5813F3AB" TYPE="ntfs" 
/dev/sda2: UUID="2eedf535-3598-410d-84d2-e28ff2928add" TYPE="ext2" 
/dev/sda3: UUID="987cebe9-f1c7-4043-9fd0-e77b7e103833" TYPE="swap" 
/dev/sda5: UUID="16943a4c-9c9c-4b4e-9c21-5c4ad4e3f6c9" TYPE="ext4" 
/dev/sda6: UUID="2f9b4f20-6c23-4fa4-a04a-4d686ee0aa24" TYPE="ext4" 
/dev/sdb1: UUID="a9b9b337-de93-432b-8108-7b9c7bfac549" TYPE="ext4" 
/dev/sdc1: LABEL="Dados" UUID="F80C3EF20C3EAC0E" TYPE="ntfs" 
/dev/sdc5: LABEL="What?" UUID="78FC5CC3FC5C7CF6" TYPE="ntfs" 
```**mount**
```
/dev/sda5 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda2 on /boot type ext2 (rw)
/dev/sda6 on /home type ext4 (rw,commit=0)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/tiago/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=tiago)
/dev/sdc5 on /media/What? type fuseblk (rw,nosuid,nodev,allow_other,blksize=1024,default_permissions)

```**cat /etc/fstab**
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=16943a4c-9c9c-4b4e-9c21-5c4ad4e3f6c9 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda2 during installation
UUID=2eedf535-3598-410d-84d2-e28ff2928add /boot           ext2    defaults        0       2
# /home was on /dev/sda6 during installation
UUID=2f9b4f20-6c23-4fa4-a04a-4d686ee0aa24 /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=987cebe9-f1c7-4043-9fd0-e77b7e103833 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```I'd like to make:
**/dev/sdb1: UUID="a9b9b337-de93-432b-8108-7b9c7bfac549" TYPE="ext4" **

auto-mount, so I can place all the music there (its an internal 40GB HDD) I formated it as ext4 using gparted

my understanding is that I need to do this: (but I'm afraid it might not be quite it because I didn't named the drive 'MusicData' and I don't konw if I should use "0" and "2" for step 2)

1- gksu gedit /etc/fstab
2- UUID=**a9b9b337-de93-432b-8108-7b9c7bfac549**   /media/**MusicData**    ext4    relatime    [COLOR=DarkOrange]**?    ?**[/COLOR]
3- sudo umount /dev/sdb1
4- sudo mkdir -p "/media/MusicData"
5- sudo mount -a

---

