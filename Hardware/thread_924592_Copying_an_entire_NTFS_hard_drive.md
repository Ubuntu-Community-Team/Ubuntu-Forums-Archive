---
title: "Copying an entire NTFS hard drive"
date: 2008-09-19
forum: Hardware
---

### Post by JackPrice on 2008-09-19
Recently, I started getting the dreaded Blue Screen of Death on my dekstop running Vista. I'm pretty sure it's due to bad drivers, but I can't fix it.

I put the hard drive from my laptop in my desktop, attaching it with various bits of elastic band. On this hard drive I was dual booting Ubuntu 8.04 with Vista; I'm currently running said Ubuntu on my PC from laptop hard drive.

What I want to do is copy my entire desktop hard drive to my external hard drive before I reinstall Vista on it, so that if I need any of the data on it I can get it.

Recap:

-Running Ubuntu 8.04 off laptop hard drive (HDD 1)
-Have desktop hard drive (HDD2) and external hard drive (HDD3) plugged in and detected
-Want to copy HDD2 (160GB) to HDD3 (500GB)

HOWEVER, because HDD2 is NTFS it won't mount - I get "Unable to mount the volume." and I can't copy it to my external drive.

Any solutions?

Thanks.

---

### Post by Bucky Ball on 2008-09-19
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

[http://www.cyberciti.biz/faq/mounting-windows-partition-onto-ubuntu-linux/](http://www.cyberciti.biz/faq/mounting-windows-partition-onto-ubuntu-linux/)

---

### Post by IntuitiveNipple on 2008-09-19
The easy way is to copy the entire file-system to a file (or empty partition) on the back-up drive.

For example, if the drive /dev/sdc has a partition (/dev/sdc1) with an NTFS file-system containing Windows it can be copied to the file Windows-NTFS.img on the back-up device mounted on /media/back-up/ like this:
```

dd if=/dev/sdc1 of=/media/back-up/Windows-NTFS.img

```
That back-up can later be mounted using the loop file-system:
```

sudo mkdir -p /media/Windows.bak
sudo losetup /dev/loop0 /media/back-up/Windows-NTFS.img
sudo mount /dev/loop0 /media/Windows.bak

```

---

### Post by JackPrice on 2008-09-19
I'm sorry, I'm lost. I tried following the instructions in the second link provided by  Bucky Ball:

```
jack@jack-ubuntu:~$ sudo fdisk -l
[sudo] password for jack: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4a2d6be5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1019     8185086   27  Unknown
/dev/sda2   *        1020       10258    74212267+   6  FAT16
/dev/sda3           10259       14865    36999319+   7  HPFS/NTFS
/dev/sda4           14866       19457    36885240    5  Extended
/dev/sda5           14866       19263    35326903+  83  Linux
/dev/sda6           19264       19457     1558273+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008571d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    c  W95 FAT32 (LBA)
jack@jack-ubuntu:~$ sudo mkdir -p /media/c
jack@jack-ubuntu:~$ sudo mount -t ntfs -o nls=utf8,umask=0222 /dev/sdb1 /media/c$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/c -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/c ntfs-3g force 0 0
jack@jack-ubuntu:~$ mount -t ntfs-3g /dev/sdb1 /media/c -o force
mount: only root can do that

```

---

