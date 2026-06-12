---
title: "[SOLVED] Grub Error 17 on boot"
date: 2008-12-22
forum: Installation &amp; Upgrades
---

### Post by Game_boy on 2008-12-22
My disk is this:

/dev/sda1 - Vista
/dev/sda2 - Swap
/dev/sda3 - Ubuntu 8.10 in unknown condition, formerly Fedora 10

Basically, I installed 8.10 to the Fedora partition. The installer crashed around 94% with a GRUB error, and now I get GRUB error 17 on boot and cannot access any OS. I don't know if Ubuntu is intact, but I can access the files in /dev/sda1 and /dev/sda3 using the LiveCD. My attempts to repair GRUB (grub-install, sudo grub, super grub disk, etc.) have all failed with errors.

What should I do? I want to restore GRUB so I can access Ubuntu and Vista.

---

### Post by Game_boy on 2008-12-22
Anyone?

The main problem seems to be that, despite me having /boot/grub/stage1 on /dev/sda3 and being able to visit it in file browsers and everything, GRUB cannot find it when I use:

*find /boot/grub/stage1*

It returns:

*Error 15: file not found*

Also, 

*root (anything I can think of) *
*setup (hd0) *

returns that it isn't a block device.

---

### Post by pennacook on 2008-12-22
might want to look at the fix that was posted:
[http://ubuntuforums.org/showthread.php?t=379012]("http://ubuntuforums.org/showthread.php?t=379012")

---

### Post by caljohnsmith on 2008-12-22
Having the Ubuntu installer fail at 94% is unfortunately a known bug, but the good news is that it can usually be circumvented by clicking the "advanced" button near the end of the installation process, and specify to have Grub installed to /dev/sda if sda is the drive you are installing Ubuntu to (most likely). How about giving that a shot and let me know how it goes.

---

### Post by Game_boy on 2008-12-22
> **pennacook said:**
> might want to look at the fix that was posted:
[http://ubuntuforums.org/showthread.php?t=379012]("http://ubuntuforums.org/showthread.php?t=379012")

That problem was because they have two harddrives. I have one. I have used their method and I don't have an hd1, so that isn't the problem.

[QUOTE=caljohnsmith]Having the Ubuntu installer fail at 94% is unfortunately a known bug, but the good news is that it can usually be circumvented by clicking the "advanced" button near the end of the installation process, and specify to have Grub installed to /dev/sda if sda is the drive you are installing Ubuntu to (most likely). How about giving that a shot and let me know how it goes.[/QUOTE]

I've just tried that and it gave the same error message. Since it looks like it is just using grub-install, I imagine it's getting the same errors as when I try that from the command line.

---

### Post by caljohnsmith on 2008-12-22
OK, another method that has worked for people to get around that 94% install error is to format the Ubuntu partition to use ext2 rather than ext3 as the file system. If that works, it is really simple to upgrade the file system to ext3 after Ubuntu is installed by doing:
```
sudo tune2fs -j /dev/sdXY
```
Replace sdXY with your Ubuntu partition of course. After that, I believe the only thing you will need to do is edit your /etc/fstab so that the Ubuntu partition is mounted with "ext3" instead of "ext2". If you need help with that let me know. Otherwise let me know how it goes.

---

### Post by Game_boy on 2008-12-22
> **caljohnsmith said:**
> OK, another method that has worked for people to get around that 94% install error is to format the Ubuntu partition to use ext2 rather than ext3 as the file system. If that works, it is really simple to upgrade the file system to ext3 after Ubuntu is installed by doing:
```
sudo tune2fs -j /dev/sdXY
```
Replace sdXY with your Ubuntu partition of course. After that, I believe the only thing you will need to do is edit your /etc/fstab so that the Ubuntu partition is mounted with "ext3" instead of "ext2". If you need help with that let me know. Otherwise let me know how it goes.

Same error, unfortunately.

---

### Post by caljohnsmith on 2008-12-22
OK, how about instead installing Ubuntu without Grub, and then I can help you install Grub afterwards if you want. If you click the "advanced" button again during the install, you can choose to omit Grub there. If that works, post the output of:
```
sudo fdisk -lu
```
After you finish the installation, and please identify your partitions.

---

### Post by Game_boy on 2008-12-22
Is it enough to give you the output from the LiveCD? I'd like to install GRUB from the LiveCD too.

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbb3d7c05

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   234754047   117376000    7  HPFS/NTFS
/dev/sda2       234757845   235159469      200812+  82  Linux swap / Solaris
/dev/sda3       235159470   312576704    38708617+  8e  Linux LVM

```

/dev/sda1 - Windows Vista
/dev/sda2 - Swap
/dev/sda3 - Ubuntu 8.10

---

### Post by caljohnsmith on 2008-12-22
OK, from your Live CD, try the following, and please copy/paste your terminal session so I can see the output of all the commands:
```
sudo mount /dev/sda3 /mnt
sudo grub-install --root-directory=/mnt --recheck /dev/sda
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt
apt-get install grub
update-grub
cat /boot/grub/menu.lst
exit
```
If you get an error from any of the commands, stop immediately and don't do the rest of them. Let me know how it goes.

---

### Post by meierfra. on 2008-12-23
Could you post the output of

```
sudo  vol_id /dev/sda3
```

I think that the installer forgot to change the type of the Ubuntu partition from LVM to 83, and that is causing all the problems. 

Is it correct that /dev/sda2 used to be the boot partition for Fedora? 200MB seems to small for a Swap partition. 

You can follow caljohnsmith's advise and in addition change the type of /dev/sda3 to 83. This should let you boot into Ubuntu. But you still will have a  Swap partition which is too small.


So I suggest to reinstall again  but first use the Partition Editor (gparted) on the LiveCD to deleted  your swap  and your Ubuntu partition. Then install Ubuntu onto the unallocated space.

---

### Post by Game_boy on 2008-12-23
> **meierfra. said:**
> Could you post the output of

```
sudo  vol_id /dev/sda3
```
So I suggest to reinstall again  but first use the Partition Editor (gparted) on the LiveCD to deleted  your swap  and your Ubuntu partition. Then install Ubuntu onto the unallocated space.

This worked. The problem must have been the Ubuntu and swap partitions as you said, because deleting them and reinstalling to the free space worked perfectly. Thanks very much, and also thanks to caljohnsmith whose method may also have worked.

---

