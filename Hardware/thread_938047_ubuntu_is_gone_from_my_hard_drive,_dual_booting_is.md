---
title: "ubuntu is gone from my hard drive, dual booting issue"
date: 2008-10-04
forum: Hardware
---

### Post by ryologic on 2008-10-04
Hey Guys, I'm new to this posting thing so bear with me please.

I have windows xp dual booting with ubuntu 8.04 which I installed with Wubi.

Recently ubuntu stopped loading from the GRUB menu. Grub loaded fine and i had the option to boot to either winxp or ubuntu. Winxp boots fine, but ubuntu gets stuck at the splash screen with the loading bar.

I popped in a live cd to see if i could figure out the problem and found that  my ubuntu partition was not appearing in gnome.

in gparted, only two partitions are shown, one for windows and one recovery partition for windows. I know the ubuntu partition must exist in some manner, because the total size of my hard drive is 10 gigs smaller

I would like to get rid of ubuntu on my computer so i can get the 10 gigs back and do a clean install,  without hurting windows or the recovery partition.

I saw similar posts where the output to the following command was requested, so i thought it might be helpful.

```
 sudo fdisk -l
```

ubuntu@ubuntu:~$  sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8       19452   156191962+   7  HPFS/NTFS
ubuntu@ubuntu:~$

---

