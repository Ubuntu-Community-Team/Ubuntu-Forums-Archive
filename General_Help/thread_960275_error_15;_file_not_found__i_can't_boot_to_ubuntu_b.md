---
title: "error 15; file not found ? i can't boot to ubuntu but mac,xp"
date: 2008-10-27
forum: General Help
---

### Post by qywolala on 2008-10-27
i installed ubuntu, yesterday i install kde,(sudo apt-get install kde),but i found gnome menu is too long and i dont like kde environment,so i use synaptic to uninstall it(search linux-image,mark,apply),after reboot : **error 15 file not found** it seems i uninstalled kernel:
**this is file list in my boot directory**: ex2fs in windows xp
installed-version
xfs_stage1_5
menu.lst~
reiserfs_stage1_5
default
stage2
minix_stage1_5
menu.lst
device.map
e2fs_stage1_5
stage1
fat_stage1_5
jfs_stage1_5


[I]**this is my boot menu**:
ubuntu 8.04,kernel 2.26.24-21 generic
ubuntu 8.04,kernel 2.26.24-21(recovery mode)
ubuntu 8.04,kernel 2.26.24-16 generic
ubuntu 8.04,kernel 2.26.24-16(recovery mode)
other operatins system:
windows vista/xp loader[/I]


no matter i choose which entry expect "vista/xp loader",i got this error : error 15 file not found

[I]i tried fix grub like this:
press c 
find /boot/grub/stage1  :(hd0,5)
root (hd0,5)
setup (hd0,5) 
: checking if "boot/grub/stage1" exists :yes
: checking if "boot/grub/stage2" exists :yes
: checking if "boot/grub/e2fs_stage1_5" exists :yes
: running  "embed boot/grub/e2fs_stage1_5 (hd0,5)"  failed (this is not fatal)
:running  "install boot/grub/e2fs_stage1_5 (hd0,5)"  failed (this is not fatal)
check /boot/grub/stage2 p /boot/grub/menu.lst"  succeeded
[/I]

anyone can help me ?
Thanks in advance!

note : i tried ubuntu Live CD ,synaptic,search linux-image,mark,apply. reboot
but it does'nt help .....

---

### Post by qywolala on 2008-10-27
i've post it  here:
[http://ubuntuforums.org/showthread.php?t=960275]("http://ubuntuforums.org/showthread.php?t=960275")

---

### Post by caljohnsmith on 2008-10-27
OK, how about booting your Live CD, open a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu
sudo mount /dev/sda6 /mnt
cat /mnt/boot/grub/menu.lst
ls -l /mnt/boot

```
Where "-l" is a lowercase L, not a one. We can work from there. :)

---

### Post by bapoumba on 2008-10-27
Threads merged.

---

### Post by qywolala on 2008-10-28
> **caljohnsmith said:**
> OK, how about booting your Live CD, open a terminal (applications > accessories > terminal), a```

```nd post the output of:
```
sudo fdisk -lu
sudo mount /dev/sda6 /mnt
cat /mnt/boot/grub/menu.lst
ls -l /mnt/boot

```
Where "-l" is a lowercase L, not a one. We can work from there. :)


Great Thanks !  :)

sudo fdisk -lu
```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe24be24b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    40960079    20480008+   7  HPFS/NTFS
/dev/sda2        40960080    61447679    10243800   af  Unknown
/dev/sda3        61447680   156295439    47423880    5  Extended
/dev/sda5        61447743    78472799     8512528+   b  W95 FAT32
/dev/sda6        78472863    98960399    10243768+  83  Linux
/dev/sda7        98960463   102120479     1580008+  82  Linux swap / Solaris
/dev/sda8       102120543   119432879     8656168+   7  HPFS/NTFS
/dev/sda9       119432943   156295439    18431248+   b  W95 FAT32

```

sudo mount /dev/sda6 /mnt
cat /mnt/boot/grub/menu.lst

```
default         0
timeout         10

title           Ubuntu 8.04, kernel 2.6.24-21-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.24-21-generic root=UUID=9ed8ee87-9963-42c4-9870-de9710967656 ro quiet splash
initrd          /boot/initrd.img-2.6.24-21-generic
quiet

title           Ubuntu 8.04, kernel 2.6.24-21-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.24-21-generic root=UUID=9ed8ee87-9963-42c4-9870-de9710967656 ro single
initrd          /boot/initrd.img-2.6.24-21-generic

title           Ubuntu 8.04, kernel 2.6.24-16-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=9ed8ee87-9963-42c4-9870-de9710967656 ro quiet splash
initrd          /boot/initrd.img-2.6.24-16-generic
quiet

title           Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=9ed8ee87-9963-42c4-9870-de9710967656 ro single
initrd          /boot/initrd.img-2.6.24-16-generic

title           Ubuntu 8.04, memtest86+
root            (hd0,5)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows Vista/Longhorn (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda8
title           Windows NT/2000/XP (loader)
root            (hd0,7)
savedefault
makeactive
chainloader     +1

```

ls -l /mnt/boot

```
ubuntu@ubuntu:~$ ls -l /mnt/boot
total 112
drwxr-xr-x 2 root root   4096 2008-10-27 13:20 grub
-rw-r--r-- 1 root root 103204 2007-09-28 10:06 memtest86+.
```

---

### Post by caljohnsmith on 2008-10-28
It looks like the problem is you don't have any kernels installed anymore. :) Try the following from your Live CD to install the 2.6.24-21 kernel:
```
sudo mount /dev/sda6 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt /bin/bash
apt-get install linux-headers-2.6.24-21-generic linux-image-2.6.24-21-generic linux-restricted-modules-2.6.24-21-generic linux-ubuntu-modules-2.6.24-21-generic
exit
```
If any of the commands return an error, do not proceed with the rest of them, and post the output of the commands up to that point; otherwise, go ahead and reboot, and let me know what happens on start up when you choose the "Ubuntu 8.04, kernel 2.6.24-21-generic" entry in the Grub menu. :)

---

### Post by qywolala on 2008-11-01
thanks 
i do it as you told me, 
but when i reboot,i enter my username and password, i just can't see my desktop ...

i've reinstalled a fresh new 8.10 today.
thanks again!

---

