---
title: "HDD drive formatted to ntfs"
date: 2020-08-26
forum: Hardware
---

### Post by mcsheffrey on 2020-08-26
Just purchased a used dell i7 8th generation intel with a 256GB ssd and 1TB HDD (came with WIN 10 installed on the SSD)  it had the BIOS configured with IRS, has to change bios to AHCI, then installed ubuntu 20.04., overwriting the WINDOWS 10. Everything seems to have work ok, except the HDD is in NTFS format. Can I or should I re-format it to ext4, there is nothing currently on  it. Welcome any suggestions.

---

### Post by oldfred on 2020-08-26
You cannot run most fixes to NTFS from Linux.
It will need chkdsk and defrag.
If not dual booting at minimum you need a Windows repair flash drive to do maintenance.

But if no data, best to convert to ext4. But you then have to mount partition(s) with fstab and give yourself ownership & permissions if regularly using it.

I like to have another small install of Ubuntu on every drive, so make an ESP as first partition. And then a 25GB / (root) partition. And I have data partition(s), and space for data copy. Which is not really a backup as just a current copy, so deleted files or changed files cannot be recovered like from my backups on other devices.

---

### Post by mcsheffrey on 2020-08-26
Unmounted the partition and deleted it, formated as ext4, chown ed and  chgrp ed it after reboot ubuntu doesnt see it, went into gparted and it shows  as unmounted, but doesnt allow me to mount it. How would I add this to /etc/fstab, is it done manually like vi or is there a safer way thru a utility.

---

### Post by Yellow Pasque on 2020-08-26
Can you give output of:
```
sudo fdisk -l
sudo blkid
```

---

### Post by mcsheffrey on 2020-08-26
here it is:
```
mcsheffrey@mcsheffrey-G7-7588:/media/mcsheffrey$ sudo fdisk -l
[sudo] password for mcsheffrey: 
Disk /dev/loop0: 56.27 MiB, 58998784 bytes, 115232 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop1: 28.92 MiB, 30306304 bytes, 59192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop2: 96.64 MiB, 101318656 bytes, 197888 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop3: 161.42 MiB, 169254912 bytes, 330576 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop4: 143.53 MiB, 150491136 bytes, 293928 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop5: 54.98 MiB, 57626624 bytes, 112552 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop6: 49.8 MiB, 52203520 bytes, 101960 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop7: 55.33 MiB, 58007552 bytes, 113296 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/nvme0n1: 238.49 GiB, 256060514304 bytes, 500118192 sectors
Disk model: BC501 NVMe SK hynix 256GB               
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: B315CC7F-F35B-4803-9968-A45E25BB53A0


Device           Start       End   Sectors  Size Type
/dev/nvme0n1p1    2048   1050623   1048576  512M EFI System
/dev/nvme0n1p2 1050624 500117503 499066880  238G Linux filesystem




Disk /dev/sda: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: ST1000LM035-1RK1
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 4E81384D-8402-4A16-A4C9-83E95002AF93


Device      Start        End    Sectors   Size Type
/dev/sda1    2048     264191     262144   128M Microsoft reserved
/dev/sda2  264192 1953523711 1953259520 931.4G Linux filesystem




Disk /dev/loop8: 255.58 MiB, 267980800 bytes, 523400 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop9: 62.9 MiB, 65105920 bytes, 127160 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop10: 29.91 MiB, 31342592 bytes, 61216 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop11: 29.9 MiB, 31334400 bytes, 61200 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop12: 290.45 MiB, 304545792 bytes, 594816 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
mcsheffrey@mcsheffrey-G7-7588:/media/mcsheffrey$ sudo blkid
/dev/nvme0n1p2: UUID="cd7c8593-e964-4eda-a9b6-1f1eabf13ae2" TYPE="ext4" PARTUUID="39b0bd36-e97a-4280-bd7d-5a9e0e0684a8"
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/nvme0n1p1: UUID="EBF8-6043" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="5062bde0-ceee-4c9f-ac29-8b6b522c8af3"
/dev/sda2: LABEL="DATA" UUID="edc88173-1328-440a-af7b-e2beaaee29ca" TYPE="ext4" PARTLABEL="basic data partition" PARTUUID="53d0df6e-b29c-4404-9398-22ae0ef190f9"
/dev/loop8: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
/dev/loop10: TYPE="squashfs"
/dev/loop11: TYPE="squashfs"
/dev/loop12: TYPE="squashfs"
/dev/sda1: PARTLABEL="Microsoft reserved partition" PARTUUID="33a40607-7376-4e45-9bf7-fef0703d7be7"
mcsheffrey@mcsheffrey-G7-7588:/media/mcsheffrey$
```

---

### Post by Yellow Pasque on 2020-08-26
(Reformatting so I can read better and got rid of loop device info):
```
Disk /dev/nvme0n1: 238.49 GiB, 256060514304 bytes, 500118192 sectors
Disk model: BC501 NVMe SK hynix 256GB
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: B315CC7F-F35B-4803-9968-A45E25BB53A0

Device Start End Sectors Size Type
/dev/nvme0n1p1 2048 1050623 1048576 512M EFI System
/dev/nvme0n1p2 1050624 500117503 499066880 238G Linux filesystem


Disk /dev/sda: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: ST1000LM035-1RK1
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 4E81384D-8402-4A16-A4C9-83E95002AF93

Device Start End Sectors Size Type
/dev/sda1 2048 264191 262144 128M Microsoft reserved
/dev/sda2 264192 1953523711 1953259520 931.4G Linux filesystem
```

```

/dev/nvme0n1p2: UUID="cd7c8593-e964-4eda-a9b6-1f1eabf13ae2" TYPE="ext4" PARTUUID="39b0bd36-e97a-4280-bd7d-5a9e0e0684a8"
/dev/nvme0n1p1: UUID="EBF8-6043" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="5062bde0-ceee-4c9f-ac29-8b6b522c8af3"
/dev/sda2: LABEL="DATA" UUID="edc88173-1328-440a-af7b-e2beaaee29ca" TYPE="ext4" PARTLABEL="basic data partition" PARTUUID="53d0df6e-b29c-4404-9398-22ae0ef190f9"
/dev/sda1: PARTLABEL="Microsoft reserved partition" PARTUUID="33a40607-7376-4e45-9bf7-fef0703d7be7"
```

---

### Post by oldfred on 2020-08-26
I do not like Disks as it may not use correct parameters. Better to use template/example and adjust for your specifics

[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to. And then link folders into /home.
I use noatime for SSD partitions and relatime for HDD partitions.

My entry:
```
# Entry for /dev/sdb4 on Asus AR:
UUID=a0c1c99f-0f09-4787-a7cc-9e15bb3b4aa5 /mnt/data ext4 relatime 0 2

```

---

### Post by mcsheffrey on 2020-08-26
Here's the entry I added to /etc/fstab
UUID=edc88173-1328-440a-af7b-e2beaaee29ca /mnt/DATA ext4 relatime 0 2
Re-booted and it still doesn't show up anywhere, nothing in "files" or under /media/.../..
Also when I look at it in GPARTED it show it as being mounted.
Did I miss to do something.
ooops its where I told it to mount, in /mnt/DATA
now is there a way to get this to show in in "files" , don't want to have to go to terminal every time I want to use it.

---

### Post by oldfred on 2020-08-27
If you want to directly show it in /home you have to mount it there.

I prefer to link folders into /home from my mount.

[http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

You do have to make sure you do not link a folder with the same name as a folder in /home that has data as then that data disappears. I always delete the default folders as soon as I install, so they are empty adn then link my data folders. That way I can have same data in multiple installs or do a new install and link same data. I have done that for every LTS version as I do a new install and multiple test installs of every new version.

---

### Post by mcsheffrey on 2020-08-27
I created a symbolic link to my home folder and everything looks good now. Problem solved. Thanks you very much for all your help.  Roy

---

