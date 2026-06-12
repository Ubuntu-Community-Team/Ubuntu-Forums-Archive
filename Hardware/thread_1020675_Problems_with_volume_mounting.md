---
title: "Problems with volume mounting"
date: 2008-12-24
forum: Hardware
---

### Post by Jguy on 2008-12-24
Well, I've so far been able to solve my own problems, but this one has troubled me. Last night I installed Ubuntu on this machine with a total of 4 Hard Drive inside the computer, and an external.

Everything worked flawlessly, this made me happy. I've used Ubuuntu before, but not without Windows, so this is all new to me. 

As of right now, last night I was able to mount this volume, '/dev/sde' which is the USB external I have hooked up (into the same port as before). Ubuntu mounted it fine, no issues with permissions, I was able to read, write, delete and modify the volume to my hearts content.

When I turned my PC on today, it does not want to mount. Here's what I've done:
* the USB device is on. I know this because it mounts on my Laptop, an Acer also running Ubuntu.
* I have attempted to double click on the volume in 'Computer' only to get the dreaded error message "Unable to mount volume - You are not privileged enough to mount this volume'
* I have opened a terminal, by running fdisk, I come up with this: 
```
jguy@jguy-desktop:~$ sudo fdisk -l

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x73557355

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       17495   140528556   83  Linux
/dev/sdb2           17496       18241     5992245    5  Extended
/dev/sdb5           17496       18241     5992213+  82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a0f81

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       32636   262148638+  83  Linux

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

Disk /dev/sde: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xacdd9b22

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       77825   625129281    7  HPFS/NTFS
```

(again, /dev/sde/ is the drive in question)

Okay, not enough priviledges, I'll just issue a sudo mount from the terminal:
```
jguy@jguy-desktop:~$ sudo mount /dev/sde
mount: can't find /dev/sde in /etc/fstab or /etc/mtab
jguy@jguy-desktop:~$ sudo mount /dev/sde1
fuse: failed to access mountpoint /media/My Stuff: No such file or directory
jguy@jguy-desktop:~$ sudo mount -afuse: failed to access mountpoint /media/My Stuff: No such file or directory
jguy@jguy-desktop:~$ 
```

Ooooookay. It's plugged in. The partition tables are valid, what the heck am I missing. So then I read somewhere to check in fstab
```
jguy@jguy-desktop:~$ gksudo gedit /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
#Entry for /dev/sdb1 :
UUID=5c3f8cd5-c0a1-43a3-ad0b-601e52194c48	/	ext3	relatime,errors=remount-ro	0	1
#Entry for /dev/sde1 :
UUID=FACC62B1CC626839	/media/My\040Stuff	ntfs-3g	defaults	0	0
/dev/sdc1	/media/My_Stuff	ext2	defaults	0	2
#Entry for /dev/sdb5 :
UUID=a6536fa6-f1c7-4672-baef-95edf26e9db5	none	swap	sw	0	0
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0
```

Hm. It's there....what about mtab...

```
jguy@jguy-desktop:~$ gksudo gedit /etc/mtab
/dev/sdb1 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.27-9-generic/volatile tmpfs rw,mode=755 0 0
/dev/sdc1 /media/My_Stuff ext2 rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/jguy/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=jguy 0 0
```

Hm, doesn't seem to be there....should it be in both places, or just fstab?

It is external, Ubuntu did shut down properly when it was working, ntfs-3g is installed, I don't quite understand why if I try to mount it I get 'that I'm not privileged enough' and if I try to mount it with sudo it'll tell me it doesn't exist, when I can see it in GParted, fdisk and 'Computer'.

Any ideas?

---

### Post by taurus on 2008-12-24
```
sudo mkdir /media/sde1
sudo mount -t ntfs-3g /dev/sde1 /media/sde1
df -h
```

---

