---
title: "FStab Problems...."
date: 2008-09-12
forum: General Help
---

### Post by robelliott2125 on 2008-09-12
Gah!

Seems only I can seriously mess up my system.

Right, I freshly reinstalled Hardy about a month or so ago, and I have finally gotten to the end of my tether with the fact that none of my drives automount.

For some reason, my Fstab is the old fstab from when I ran Gutsy, and Hardy didn't reinstall / recreate the file.

Each time I've been needing a file etc, i've had to click on the drive under places, which then mounts and allows the drive to be RW from.

I had someone start helping me, and have now made my Music and Storage drives unreadable / non-mountable.

So, here I am, pleading for someone to help me, preferably with something so simple (like a way to just reinstall the fstab easily), or how I can easily re-write it without a headache.

I'm seriously a linux n00b and am slowly growing tired of the problems I cause myself (The thought of 'boxing the PC back up and selling it due to being too stupid for linux' comes to mind).

Hope someone can help.

Thanks guys and gals!

---

### Post by Vivaldi Gloria on 2008-09-12
Open a terminal and give the commands:

```
cat /etc/fstab
sudo fdisk -l
ls /dev/disk/* -lah

```

Copy and paste the results here. Please put your code between [noparse]```
 
```[/noparse] tags.

---

### Post by robelliott2125 on 2008-09-13
> **Vivaldi Gloria said:**
> Open a terminal and give the commands:

```
cat /etc/fstab
sudo fdisk -l
ls /dev/disk/* -lah

```

Copy and paste the results here. Please put your code between [noparse]```
 
```[/noparse] tags.

Hi Gloria,

Here it is:

```
robert@robert-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=5cf872e3-5930-47b0-a6c7-1606dd41e0d0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=527CCD3E7CCD1D9B /dev/Music      ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdc1
UUID=622C2D6F2C2D3F81 /dev/Storage    ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=C08C3B748C3B63D6 /dev/Uploads    ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=146682b2-b0d9-4518-846b-4c8bfdc5b082 /home           ext3    relatime        0       2
# /dev/sda4
UUID=F458313C5830FEC4 /windows        ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda1
UUID=ec365d95-1f87-411c-b04e-90c6394bbd26 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
robert@robert-desktop:~$ sudo fdisk -l
sudo: unable to resolve host robert-desktop
[sudo] password for robert: 

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00076399

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         127     1020096   82  Linux swap / Solaris
/dev/sda2             128        1402    10241437+  83  Linux
/dev/sda3            1403        2551     9229342+  83  Linux
/dev/sda4   *        2552        4865    18587205    7  HPFS/NTFS

Disk /dev/sdb: 13.6 GB, 13601193984 bytes
255 heads, 63 sectors/track, 1653 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa665ba42

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         836     6715138+   7  HPFS/NTFS
/dev/sdb2             837        1653     6562552+   f  W95 Ext'd (LBA)
/dev/sdb5             837        1653     6562521    7  HPFS/NTFS

Disk /dev/sdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x467367f2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        4865    39078081    7  HPFS/NTFS
robert@robert-desktop:~$ ls /dev/disk* -lah
total 0
drwxr-xr-x  6 root root 120 2008-09-13 14:00 .
drwxr-xr-x 14 root root 14K 2008-09-13 13:01 ..
drwxr-xr-x  2 root root 480 2008-09-13 14:00 by-id
drwxr-xr-x  2 root root 100 2008-09-13 14:00 by-label
drwxr-xr-x  2 root root 280 2008-09-13 14:00 by-path
drwxr-xr-x  2 root root 180 2008-09-13 14:00 by-uuid

```

Hope this is clear to you guys, I was told to just reinstall last night, but I really can't be bothered to do that (Again).

---

### Post by Vivaldi Gloria on 2008-09-13
You missed a / in the last command. Please repost the output of:

```
ls /dev/disk/* -lah
```

I'm getting out now. I'll come back in a few hours and I'll look then.

---

### Post by robelliott2125 on 2008-09-13
Ah yes.  Thank you for pointing that out.

Here it is again...

```

robert@robert-desktop:~$ ls /dev/disk/* -lah
/dev/disk/by-id:
total 0
drwxr-xr-x 2 root root 480 2008-09-13 14:00 .
drwxr-xr-x 6 root root 120 2008-09-13 14:00 ..
lrwxrwxrwx 1 root root   9 2008-09-13 14:00 ata-WDC_WD136AA_WD-WM6780363654 -> ../../sdb
lrwxrwxrwx 1 root root  10 2008-09-13 14:00 ata-WDC_WD136AA_WD-WM6780363654-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  10 2008-09-13 14:00 ata-WDC_WD136AA_WD-WM6780363654-part2 -> ../../sdb2
lrwxrwxrwx 1 root root  10 2008-09-13 14:00 ata-WDC_WD136AA_WD-WM6780363654-part5 -> ../../sdb5
lrwxrwxrwx 1 root root   9 2008-09-13 14:00 ata-WDC_WD400EB-11CPF0_WD-WMAAT5145220 -> ../../sda
lrwxrwxrwx 1 root root  10 2008-09-13 14:00 ata-WDC_WD400EB-11CPF0_WD-WMAAT5145220-part1 -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-09-13 14:00 ata-WDC_WD400EB-11CPF0_WD-WMAAT5145220-part2 -> ../../sda2
lrwxrwxrwx 1 root root  10 2008-09-13 14:00 ata-WDC_WD400EB-11CPF0_WD-WMAAT5145220-part3 -> ../../sda3
lrwxrwxrwx 1 root root  10 2008-09-13 14:00 ata-WDC_WD400EB-11CPF0_WD-WMAAT5145220-part4 -> ../../sda4
lrwxrwxrwx 1 root root   9 2008-09-13 14:00 ata-WDC_WD400EB-11CPF0_WD-WMAATL738805 -> ../../sdc
lrwxrwxrwx 1 root root  10 2008-09-13 14:00 ata-WDC_WD400EB-11CPF0_WD-WMAATL738805-part1 -> ../../sdc1
lrwxrwxrwx 1 root root   9 2008-09-13 14:00 scsi-1ATA_WDC_WD136AA_WD-WM6780363654 -> ../../sdb
lrwxrwxrwx 1 root root  10 2008-09-13 14:00 scsi-1ATA_WDC_WD136AA_WD-WM6780363654-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  10 2008-09-13 14:00 scsi-1ATA_WDC_WD136AA_WD-WM6780363654-part2 -> ../../sdb2
lrwxrwxrwx 1 root root  10 2008-09-13 14:00 scsi-1ATA_WDC_WD136AA_WD-WM6780363654-part5 -> ../../sdb5
lrwxrwxrwx 1 root root   9 2008-09-13 14:00 scsi-1ATA_WDC_WD400EB-11CPF0_WD-WMAAT5145220 -> ../../sda
lrwxrwxrwx 1 root root  10 2008-09-13 14:00 scsi-1ATA_WDC_WD400EB-11CPF0_WD-WMAAT5145220-part1 -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-09-13 14:00 scsi-1ATA_WDC_WD400EB-11CPF0_WD-WMAAT5145220-part2 -> ../../sda2
lrwxrwxrwx 1 root root  10 2008-09-13 14:00 scsi-1ATA_WDC_WD400EB-11CPF0_WD-WMAAT5145220-part3 -> ../../sda3
lrwxrwxrwx 1 root root  10 2008-09-13 14:00 scsi-1ATA_WDC_WD400EB-11CPF0_WD-WMAAT5145220-part4 -> ../../sda4
lrwxrwxrwx 1 root root   9 2008-09-13 14:00 scsi-1ATA_WDC_WD400EB-11CPF0_WD-WMAATL738805 -> ../../sdc
lrwxrwxrwx 1 root root  10 2008-09-13 14:00 scsi-1ATA_WDC_WD400EB-11CPF0_WD-WMAATL738805-part1 -> ../../sdc1

/dev/disk/by-label:
total 0
drwxr-xr-x 2 root root 100 2008-09-13 14:00 .
drwxr-xr-x 6 root root 120 2008-09-13 14:00 ..
lrwxrwxrwx 1 root root  10 2008-09-13 14:00 Backup -> ../../sdb1
lrwxrwxrwx 1 root root  10 2008-09-13 14:00 Music -> ../../sdb5
lrwxrwxrwx 1 root root  10 2008-09-13 14:00 Storage -> ../../sdc1

/dev/disk/by-path:
total 0
drwxr-xr-x 2 root root 280 2008-09-13 14:00 .
drwxr-xr-x 6 root root 120 2008-09-13 14:00 ..
lrwxrwxrwx 1 root root   9 2008-09-13 14:00 pci-0000:00:1f.1-scsi-0:0:0:0 -> ../../sda
lrwxrwxrwx 1 root root  10 2008-09-13 14:00 pci-0000:00:1f.1-scsi-0:0:0:0-part1 -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-09-13 14:00 pci-0000:00:1f.1-scsi-0:0:0:0-part2 -> ../../sda2
lrwxrwxrwx 1 root root  10 2008-09-13 14:00 pci-0000:00:1f.1-scsi-0:0:0:0-part3 -> ../../sda3
lrwxrwxrwx 1 root root  10 2008-09-13 14:00 pci-0000:00:1f.1-scsi-0:0:0:0-part4 -> ../../sda4
lrwxrwxrwx 1 root root   9 2008-09-13 14:00 pci-0000:00:1f.1-scsi-0:0:1:0 -> ../../sdb
lrwxrwxrwx 1 root root  10 2008-09-13 14:00 pci-0000:00:1f.1-scsi-0:0:1:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  10 2008-09-13 14:00 pci-0000:00:1f.1-scsi-0:0:1:0-part2 -> ../../sdb2
lrwxrwxrwx 1 root root  10 2008-09-13 14:00 pci-0000:00:1f.1-scsi-0:0:1:0-part5 -> ../../sdb5
lrwxrwxrwx 1 root root  10 2008-09-13 14:00 pci-0000:00:1f.1-scsi-1:0:0:0 -> ../../scd0
lrwxrwxrwx 1 root root   9 2008-09-13 14:00 pci-0000:00:1f.1-scsi-1:0:1:0 -> ../../sdc
lrwxrwxrwx 1 root root  10 2008-09-13 14:00 pci-0000:00:1f.1-scsi-1:0:1:0-part1 -> ../../sdc1

/dev/disk/by-uuid:
total 0
drwxr-xr-x 2 root root 180 2008-09-13 14:00 .
drwxr-xr-x 6 root root 120 2008-09-13 14:00 ..
lrwxrwxrwx 1 root root  10 2008-09-13 14:00 146682b2-b0d9-4518-846b-4c8bfdc5b082 -> ../../sda3
lrwxrwxrwx 1 root root  10 2008-09-13 14:00 527CCD3E7CCD1D9B -> ../../sdb5
lrwxrwxrwx 1 root root  10 2008-09-13 14:00 5cf872e3-5930-47b0-a6c7-1606dd41e0d0 -> ../../sda2
lrwxrwxrwx 1 root root  10 2008-09-13 14:00 622C2D6F2C2D3F81 -> ../../sdc1
lrwxrwxrwx 1 root root  10 2008-09-13 14:00 78484FEB484FA6AA -> ../../sdb1
lrwxrwxrwx 1 root root  10 2008-09-13 14:00 ec365d95-1f87-411c-b04e-90c6394bbd26 -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-09-13 14:00 F458313C5830FEC4 -> ../../sda4

```

Thank you,

---

### Post by vanadium on 2008-09-13
Your ntfs drives are being mounted with the "traditional" ntfs driver, which is a read-only driver. They should be mounted read/write if in your /etc/fstab, you replace all occurrences of ntfs with ntfs-3g. Hardy comes with the ntfs-3g driver installed and configured: no need to install that.

A second point you need to check: nfts drives will be mounted only if they are "clean", i.e. if they have properly been closed by Windows. ntfs volumes are closed only when you completely shut down Windows, not when you hibernate Windows. If an ntfs partition still does not mount read/write, load windows and have the partition checked using the Windows tools.

---

### Post by Vivaldi Gloria on 2008-09-13
**[COLOR="Red"]1)[/COLOR]** Give the following commands in a terminal:

```

sudo mkdir /mnt/disk1
sudo mkdir /mnt/disk2
sudo mkdir /mnt/disk3
sudo mkdir /mnt/disk4
sudo chown username:username /mnt/disk1
sudo chown username:username /mnt/disk2
sudo chown username:username /mnt/disk3
sudo chown username:username /mnt/disk4
```

Here replace "username" with your username and don't forget the : sign.

**[COLOR="Red"]2)[/COLOR]** Press ALT+F2 and start

```
gksudo gedit /etc/fstab
```

And change the lines to following:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=5cf872e3-5930-47b0-a6c7-1606dd41e0d0 /        ext3    relatime,errors=remount-ro  0       1
#
UUID=527CCD3E7CCD1D9B /mnt/disk1    ntfs-3g   auto,rw,users,uid=1000,gid=100,utf8,force  0       0
#
UUID=622C2D6F2C2D3F81 /mnt/disk2    ntfs-3g   auto,rw,users,uid=1000,gid=100,utf8,force  0       0
#
UUID=C08C3B748C3B63D6 /mnt/disk3    ntfs-3g   auto,rw,users,uid=1000,gid=100,utf8,force  0       0
#
UUID=F458313C5830FEC4 /mnt/disk4    ntfs-3g   auto,rw,users,uid=1000,gid=100,utf8,force  0       0
#
UUID=146682b2-b0d9-4518-846b-4c8bfdc5b082 /home        ext3    relatime        0       2
# 
UUID=ec365d95-1f87-411c-b04e-90c6394bbd26 none         swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

Save the file. Restart computer.

**[COLOR="Red"]3)[/COLOR]** Now your disks should be mounted in /mnt directory. Open file browser and click file system and go to /mnt and verify that the drives are mounted in /mnt/disk? (we can put a symlink to a more convenient place later on). If they are working OK (or not) then please let me know.

---

