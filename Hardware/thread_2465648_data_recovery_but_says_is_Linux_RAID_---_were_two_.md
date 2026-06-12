---
title: "data recovery but says is Linux RAID --- were two in RAID 1, but one broke"
date: 2021-08-07
forum: Hardware
---

### Post by lsepolis123 on 2021-08-07
data recovery but says is Linux RAID --- were two HDDs 2 x 2TB in RAID 1, but one broke LEFT ONE --- How recover DATA... in Linux RAID?
[COLOR=#54FF54][FONT=monospace][B]
ubuntu-studio@ubuntu-studio[/B][/FONT][/COLOR][COLOR=#000000][FONT=monospace]:[/FONT][/COLOR][COLOR=#5454FF][FONT=monospace]**~**[/FONT][/COLOR][COLOR=#000000][FONT=monospace]$ sudo mkdir -p /media/nas1[/FONT][/COLOR]
[COLOR=#54FF54][FONT=monospace]**ubuntu-studio@ubuntu-studio**[/FONT][/COLOR][COLOR=#000000][FONT=monospace]:[/FONT][/COLOR][COLOR=#5454FF][FONT=monospace]**~**[/FONT][/COLOR][COLOR=#000000][FONT=monospace]$ sudo mount -t ext3 /dev/sdd4 /media/nas1[/FONT][/COLOR]
[FONT=monospace]mount: /media/nas1: wrong fs type, bad option, bad superblock on /dev/sdd4, missing codepage or helper program, or other error.[/FONT]
[COLOR=#54FF54][FONT=monospace]**ubuntu-studio@ubuntu-studio**[/FONT][/COLOR][COLOR=#000000][FONT=monospace]:[/FONT][/COLOR][COLOR=#5454FF][FONT=monospace]**~**[/FONT][/COLOR][COLOR=#000000][FONT=monospace]$ sudo mount -t ext4 /dev/sdd4 /media/nas1  [/FONT][/COLOR]
[FONT=monospace]mount: /media/nas1: wrong fs type, bad option, bad superblock on /dev/sdd4, missing codepage or helper program, or other error.[/FONT]
[COLOR=#54FF54][FONT=monospace]**ubuntu-studio@ubuntu-studio**[/FONT][/COLOR][COLOR=#000000][FONT=monospace]:[/FONT][/COLOR][COLOR=#5454FF][FONT=monospace]**~**[/FONT][/COLOR][COLOR=#000000][FONT=monospace]$ sudo mount -t ext2 /dev/sdd4 /media/nas1  [/FONT][/COLOR]
[FONT=monospace]mount: /media/nas1: wrong fs type, bad option, bad superblock on /dev/sdd4, missing codepage or helper program, or other error.[/FONT]
[COLOR=#54FF54][FONT=monospace]**ubuntu-studio@ubuntu-studio**[/FONT][/COLOR][COLOR=#000000][FONT=monospace]:[/FONT][/COLOR][COLOR=#5454FF][FONT=monospace]**~**[/FONT][/COLOR][COLOR=#000000][FONT=monospace]$ sudo mount -t exfat /dev/sdd4 /media/nas1   [/FONT][/COLOR]
[FONT=monospace]mount: /media/nas1: wrong fs type, bad option, bad superblock on /dev/sdd4, missing codepage or helper program, or other error.[/FONT]
[COLOR=#54FF54][FONT=monospace]**ubuntu-studio@ubuntu-studio**[/FONT][/COLOR][COLOR=#000000][FONT=monospace]:[/FONT][/COLOR][COLOR=#5454FF][FONT=monospace]**~**[/FONT][/COLOR][COLOR=#000000][FONT=monospace]$ sudo lsblk -f[/FONT][/COLOR]
[FONT=monospace]NAME   FSTYPE            FSVER  LABEL       UUID                               [/FONT][FONT=monospace]  FSAVAIL FSUSE% MOUNTPOINT[/FONT]
[FONT=monospace]loop0  squashfs          4.0                               [/FONT][FONT=monospace]                            0   100% /rofs[/FONT]
[FONT=monospace]sda                               [/FONT][FONT=monospace]                              [/FONT][FONT=monospace]                              [/FONT][FONT=monospace]   [/FONT]
[FONT=monospace]&#9500;&#9472;sda1                               [/FONT][FONT=monospace]                              [/FONT][FONT=monospace]                              [/FONT]
[FONT=monospace]&#9492;&#9472;sda2 ntfs                     Photos      5A5ED2EC5ED2BFC5                               [/FONT][FONT=monospace]      [/FONT]
[FONT=monospace]sdb                               [/FONT][FONT=monospace]                              [/FONT][FONT=monospace]                              [/FONT][FONT=monospace]   [/FONT]
[FONT=monospace]&#9500;&#9472;sdb1 vfat              FAT32              A8EE-195A                               [/FONT][FONT=monospace]             [/FONT]
[FONT=monospace]&#9500;&#9472;sdb2                               [/FONT][FONT=monospace]                              [/FONT][FONT=monospace]                              [/FONT]
[FONT=monospace]&#9500;&#9472;sdb3 ntfs                     System      F4E6F627E6F5E9AE                               [/FONT][FONT=monospace]      [/FONT]
[FONT=monospace]&#9492;&#9472;sdb4 ntfs                               [/FONT][FONT=monospace]  FC701D41701D03D4                               [/FONT][FONT=monospace]      [/FONT]
[FONT=monospace]sdc                               [/FONT][FONT=monospace]                              [/FONT][FONT=monospace]                              [/FONT][FONT=monospace]   [/FONT]
[FONT=monospace]&#9492;&#9472;sdc1 vfat              FAT32  UBUNTU-STUD 0D0B-1467                               [/FONT][FONT=monospace]228G     2% /cdrom[/FONT]
[FONT=monospace]sdd                               [/FONT][FONT=monospace]                              [/FONT][FONT=monospace]                              [/FONT][FONT=monospace]   [/FONT]
[FONT=monospace]&#9500;&#9472;sdd1 linux_raid_member 0.90.0             83c50fc9-7a7e-[/FONT][FONT=monospace]1883-e892-110c86771389                 [/FONT]
[FONT=monospace]&#9500;&#9472;sdd2 linux_raid_member 0.90.0             cacff1a5-bc3d-[/FONT][FONT=monospace]bc69-9b96-723e207b5106                 [/FONT]
[FONT=monospace]&#9500;&#9472;sdd3 linux_raid_member 0.90.0             a286820b-53b3-[/FONT][FONT=monospace]2b19-723f-1fb0e5891d50                 [/FONT]
[FONT=monospace]&#9492;&#9472;sdd4 linux_raid_member 1.2    3           43a65e83-5ade-81ba-[/FONT][FONT=monospace]6ecb-7cd77c98b2fa                 [/FONT]
[FONT=monospace]sr0                               [/FONT][FONT=monospace]                              [/FONT][FONT=monospace]                              [/FONT][FONT=monospace]   [/FONT]
[COLOR=#54FF54][FONT=monospace]**ubuntu-studio@ubuntu-studio**[/FONT][/COLOR][COLOR=#000000][FONT=monospace]:[/FONT][/COLOR][COLOR=#5454FF][FONT=monospace]**~**[/FONT][/COLOR][COLOR=#000000][FONT=monospace]$ sudo parted -l[/FONT][/COLOR][COLOR=#54FF54][FONT=monospace][B]
[/B][/FONT][/COLOR][COLOR=#54FF54][FONT=monospace]**ubuntu-studio@ubuntu-studio**[/FONT][/COLOR][COLOR=#000000][FONT=monospace]:[/FONT][/COLOR][COLOR=#5454FF][FONT=monospace]**~**[/FONT][/COLOR][COLOR=#000000][FONT=monospace]$ mdadm --stop /dev/sdd4[/FONT][/COLOR]
[FONT=monospace]mdadm: must be super-user to perform this action[/FONT]
[COLOR=#54FF54][FONT=monospace]**ubuntu-studio@ubuntu-studio**[/FONT][/COLOR][COLOR=#000000][FONT=monospace]:[/FONT][/COLOR][COLOR=#5454FF][FONT=monospace]**~**[/FONT][/COLOR][COLOR=#000000][FONT=monospace]$ sudo mdadm --stop /dev/sdd4[/FONT][/COLOR]
[FONT=monospace]mdadm: /dev/sdd4 does not appear to be an md device[/FONT]
[COLOR=#54FF54][FONT=monospace]**ubuntu-studio@ubuntu-studio**[/FONT][/COLOR][COLOR=#000000][FONT=monospace]:[/FONT][/COLOR][COLOR=#5454FF][FONT=monospace]**~**[/FONT][/COLOR][COLOR=#000000][FONT=monospace]$ history        [/FONT][/COLOR]
[FONT=monospace]   [/FONT][COLOR=#54FF54][FONT=monospace][B]

ubuntu-studio@ubuntu-studio[/B][/FONT][/COLOR][COLOR=#000000][FONT=monospace]:[/FONT][/COLOR][COLOR=#5454FF][FONT=monospace]**~**[/FONT][/COLOR][COLOR=#000000][FONT=monospace]$ !2[/FONT][/COLOR]
[FONT=monospace]sudo fdisk -l[/FONT]
[COLOR=#000000][FONT=monospace]**Disk /dev/loop0: 3.66 GiB, 3927035904 bytes, 7669992 sectors**[/FONT][/COLOR][COLOR=#000000][FONT=monospace][/FONT][/COLOR]
[FONT=monospace]Units: sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=monospace]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT]
[FONT=monospace]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT]


[COLOR=#000000][FONT=monospace]**Disk /dev/sda: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors**[/FONT][/COLOR][COLOR=#000000][FONT=monospace][/FONT][/COLOR]
[FONT=monospace]Disk model: ST1000DM003-1SB1[/FONT]
[FONT=monospace]Units: sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=monospace]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT]
[FONT=monospace]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/FONT]
[FONT=monospace]Disklabel type: gpt[/FONT]
[FONT=monospace]Disk identifier: 07967940-BBBF-45F2-AAF3-[/FONT][FONT=monospace]8D10EBDC4EDD[/FONT]

[COLOR=#000000][FONT=monospace]**Device**[/FONT][/COLOR][COLOR=#000000][FONT=monospace]     [/FONT][/COLOR][COLOR=#000000][FONT=monospace]**Start**[/FONT][/COLOR][COLOR=#000000][FONT=monospace] [/FONT][/COLOR][COLOR=#000000][FONT=monospace]**       End**[/FONT][/COLOR][COLOR=#000000][FONT=monospace] [/FONT][/COLOR][COLOR=#000000][FONT=monospace]**   Sectors**[/FONT][/COLOR][COLOR=#000000][FONT=monospace] [/FONT][/COLOR][COLOR=#000000][FONT=monospace]**  Size**[/FONT][/COLOR][COLOR=#000000][FONT=monospace] [/FONT][/COLOR][COLOR=#000000][FONT=monospace]**Type**[/FONT][/COLOR][COLOR=#000000][FONT=monospace][/FONT][/COLOR]
[FONT=monospace]/dev/sda1     34      32767      32734    16M Microsoft reserved[/FONT]
[FONT=monospace]/dev/sda2  32768 1953521663 1953488896 931.5G Microsoft basic data[/FONT]

[COLOR=#B21818][FONT=monospace]Partition 1 does not start on physical sector boundary.[/FONT][/COLOR][COLOR=#000000][FONT=monospace][/FONT][/COLOR]


[COLOR=#000000][FONT=monospace]**Disk /dev/sdb: 232.89 GiB, 250059350016 bytes, 488397168 sectors**[/FONT][/COLOR][COLOR=#000000][FONT=monospace][/FONT][/COLOR]
[FONT=monospace]Disk model: HP SSD S700 250G[/FONT]
[FONT=monospace]Units: sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=monospace]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT]
[FONT=monospace]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/FONT]
[FONT=monospace]Disklabel type: gpt[/FONT]
[FONT=monospace]Disk identifier: B37B5B9B-2EBB-47A3-93CD-[/FONT][FONT=monospace]B29453F2EDC5[/FONT]

[COLOR=#000000][FONT=monospace]**Device**[/FONT][/COLOR][COLOR=#000000][FONT=monospace]     [/FONT][/COLOR][COLOR=#000000][FONT=monospace]**    Start**[/FONT][/COLOR][COLOR=#000000][FONT=monospace] [/FONT][/COLOR][COLOR=#000000][FONT=monospace]**      End**[/FONT][/COLOR][COLOR=#000000][FONT=monospace] [/FONT][/COLOR][COLOR=#000000][FONT=monospace]**  Sectors**[/FONT][/COLOR][COLOR=#000000][FONT=monospace] [/FONT][/COLOR][COLOR=#000000][FONT=monospace]**  Size**[/FONT][/COLOR][COLOR=#000000][FONT=monospace] [/FONT][/COLOR][COLOR=#000000][FONT=monospace]**Type**[/FONT][/COLOR][COLOR=#000000][FONT=monospace][/FONT][/COLOR]
[FONT=monospace]/dev/sdb1       2048    206847    204800   100M EFI System[/FONT]
[FONT=monospace]/dev/sdb2     206848    239615     32768    16M Microsoft reserved[/FONT]
[FONT=monospace]/dev/sdb3     239616 487371479 487131864 232.3G Microsoft basic data[/FONT]
[FONT=monospace]/dev/sdb4  487372800 488394751   1021952   499M Windows recovery environment[/FONT]


[COLOR=#000000][FONT=monospace]**Disk /dev/sdc: 232.42 GiB, 249561088000 bytes, 487424000 sectors**[/FONT][/COLOR][COLOR=#000000][FONT=monospace][/FONT][/COLOR]
[FONT=monospace]Disk model: USB DISK         [/FONT]
[FONT=monospace]Units: sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=monospace]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT]
[FONT=monospace]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT]
[FONT=monospace]Disklabel type: dos[/FONT]
[FONT=monospace]Disk identifier: 0x033e678e[/FONT]

[COLOR=#000000][FONT=monospace]**Device**[/FONT][/COLOR][COLOR=#000000][FONT=monospace]     [/FONT][/COLOR][COLOR=#000000][FONT=monospace]**Boot**[/FONT][/COLOR][COLOR=#000000][FONT=monospace] [/FONT][/COLOR][COLOR=#000000][FONT=monospace]**Start**[/FONT][/COLOR][COLOR=#000000][FONT=monospace] [/FONT][/COLOR][COLOR=#000000][FONT=monospace]**      End**[/FONT][/COLOR][COLOR=#000000][FONT=monospace] [/FONT][/COLOR][COLOR=#000000][FONT=monospace]**  Sectors**[/FONT][/COLOR][COLOR=#000000][FONT=monospace] [/FONT][/COLOR][COLOR=#000000][FONT=monospace]**  Size**[/FONT][/COLOR][COLOR=#000000][FONT=monospace] [/FONT][/COLOR][COLOR=#000000][FONT=monospace]**Id**[/FONT][/COLOR][COLOR=#000000][FONT=monospace] [/FONT][/COLOR][COLOR=#000000][FONT=monospace]**Type**[/FONT][/COLOR][COLOR=#000000][FONT=monospace][/FONT][/COLOR]
[FONT=monospace]/dev/sdc1  *     2048 487423999 487421952 232.4G  c W95 FAT32 (LBA)[/FONT]


[COLOR=#000000][FONT=monospace]**Disk /dev/sdd: 1.82 TiB, 2000398934016 bytes, 3907029168 sectors**[/FONT][/COLOR][COLOR=#000000][FONT=monospace][/FONT][/COLOR]
[FONT=monospace]Disk model: Tech             [/FONT]
[FONT=monospace]Units: sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=monospace]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT]
[FONT=monospace]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/FONT]
[FONT=monospace]Disklabel type: gpt[/FONT]
[FONT=monospace]Disk identifier: 1553E3B2-225D-460F-8DF7-[/FONT][FONT=monospace]812B420472C5[/FONT]

[COLOR=#000000][FONT=monospace]**Device**[/FONT][/COLOR][COLOR=#000000][FONT=monospace]     [/FONT][/COLOR][COLOR=#000000][FONT=monospace]**  Start**[/FONT][/COLOR][COLOR=#000000][FONT=monospace] [/FONT][/COLOR][COLOR=#000000][FONT=monospace]**       End**[/FONT][/COLOR][COLOR=#000000][FONT=monospace] [/FONT][/COLOR][COLOR=#000000][FONT=monospace]**   Sectors**[/FONT][/COLOR][COLOR=#000000][FONT=monospace] [/FONT][/COLOR][COLOR=#000000][FONT=monospace]**   Size**[/FONT][/COLOR][COLOR=#000000][FONT=monospace] [/FONT][/COLOR][COLOR=#000000][FONT=monospace]**Type**[/FONT][/COLOR][COLOR=#000000][FONT=monospace][/FONT][/COLOR]
[FONT=monospace]/dev/sdd1   195312    2283203    2087892 1019.5M Linux RAID[/FONT]
[FONT=monospace]/dev/sdd2  2283204    4373046    2089843 1020.4M Linux RAID[/FONT]
[FONT=monospace]/dev/sdd3  4373047    5416015    1042969  509.3M Linux RAID[/FONT]
[FONT=monospace]/dev/sdd4  5416016 3906832031 3901416016    1.8T Linux RAID[/FONT]

[COLOR=#B21818][FONT=monospace]Partition 2 does not start on physical sector boundary.[/FONT][/COLOR][COLOR=#000000][FONT=monospace][/FONT][/COLOR]
[COLOR=#B21818][FONT=monospace]Partition 3 does not start on physical sector boundary.[/FONT][/COLOR][COLOR=#000000][FONT=monospace][/FONT][/COLOR]
[COLOR=#54FF54][FONT=monospace]**ubuntu-studio@ubuntu-studio**[/FONT][/COLOR][COLOR=#000000][FONT=monospace]:[/FONT][/COLOR][COLOR=#5454FF][FONT=monospace]**~**[/FONT][/COLOR][COLOR=#000000][FONT=monospace]$ sudo mdadm --stop /dev/sdd[/FONT][/COLOR]
[FONT=monospace]mdadm: /dev/sdd does not appear to be an md device[/FONT]
[COLOR=#54FF54][FONT=monospace]**ubuntu-studio@ubuntu-studio**[/FONT][/COLOR][COLOR=#000000][FONT=monospace]:[/FONT][/COLOR][COLOR=#5454FF][FONT=monospace]**~**[/FONT][/COLOR][COLOR=#000000][FONT=monospace]$ sudo mount -t 'Linux RAID' /dev/sdd4 /media/nas1     [/FONT][/COLOR]
[FONT=monospace]mount: /media/nas1: unknown filesystem type 'Linux RAID'.[/FONT]
[COLOR=#54FF54][FONT=monospace]**ubuntu-studio@ubuntu-studio**[/FONT][/COLOR][COLOR=#000000][FONT=monospace]:[/FONT][/COLOR][COLOR=#5454FF][FONT=monospace]**~**[/FONT][/COLOR][COLOR=#000000][FONT=monospace]$ history                                          [/FONT][/COLOR]
[FONT=monospace]   1  sudo fdisk[/FONT]
[FONT=monospace]   2  sudo fdisk -l[/FONT]
[FONT=monospace]   3  mkdir -p /media/nas1[/FONT]
[FONT=monospace]   4  sudo mkdir -p /media/nas1[/FONT]
[FONT=monospace]   5  sudo mount -t ext3 /dev/sdd4 /media/nas1[/FONT]
[FONT=monospace]   6  sudo mount -t ext4 /dev/sdd4 /media/nas1[/FONT]
[FONT=monospace]   7  sudo mount -t ext2 /dev/sdd4 /media/nas1[/FONT]
[FONT=monospace]   8  sudo mount -t exfat /dev/sdd4 /media/nas1[/FONT]
[FONT=monospace]   9  sudo lsblk -f[/FONT]
[FONT=monospace]  10  sudo parted -l[/FONT]
[FONT=monospace]  11  history[/FONT]
[FONT=monospace]  12  sudo mount -t vfat /dev/sdd4 /media/nas1[/FONT]
[FONT=monospace]  13  sudo mount -t auto /dev/sdd4 /media/nas1[/FONT]
[FONT=monospace]  14  mdadm --examine[/FONT]
[FONT=monospace]  15  sudo apt install mdadm[/FONT]
[FONT=monospace]  16  mdadm --examine[/FONT]
[FONT=monospace]  17  mdadm --stop /dev/sdd4[/FONT]
[FONT=monospace]  18  sudo mdadm --stop /dev/sdd4[/FONT]
[FONT=monospace]  19  history[/FONT]
[FONT=monospace]  20  sudo fdisk -l[/FONT]
[FONT=monospace]  21  sudo mdadm --stop /dev/sdd[/FONT]
[FONT=monospace]  22  sudo mount -t 'Linux RAID' /dev/sdd4 /media/nas1[/FONT]
[FONT=monospace]  23  history[/FONT]
[COLOR=#54FF54][FONT=monospace]**ubuntu-studio@ubuntu-studio**[/FONT][/COLOR][COLOR=#000000][FONT=monospace]:[/FONT][/COLOR][COLOR=#5454FF][FONT=monospace]**~**[/FONT][/COLOR][COLOR=#000000][FONT=monospace]$  [/FONT][/COLOR][FONT=monospace][/FONT]
[FONT=monospace]
[/FONT]

---

### Post by TheFu on 2021-08-07
Throwing commands at storage is a good way to cause corruption.

It looks like there are 4 partitions each is half a an mdadm RAID ... assuming RAID 1, which I wouldn't do. Could easily be parts to a RAID5, RAID10, or RAID6 setup.

First step is to learn the difference between partitions and whole disk devices. This matters.

/dev/sdd is the entire disk.  That should be used only for operations that work on the entire disk. That would be partitioning and SMART tests.  File systems and RAID should never be laid down directly onto a non-partitioned disks.

/dev/sdd[1-4] are the 4 partitions of whole disk sdd.  It is highly unlikely they are used together as RAID - cause that would be stupid.  

Next you'll need to work through an mdadm tutorial to understand how mdadm arrays are built, run, examined, and and stopped.  HDDs can't just be pulled from an array.  They must be "removed" using the mdadm command.  Then a new array can be created in a degraded mode with whatever the minimal number of parts is required for that type of array to be used.  Hopefully, we can get the array to tell us what it knows.  Looks like you were really close with the --examine, but you didn't tell it what to look at.

sudo mdadm -E /dev/sdd1
sudo mdadm -E /dev/sdd2
sudo mdadm -E /dev/sdd3
sudo mdadm -E /dev/sdd4

There is an answer here, which may be useful:
[https://unix.stackexchange.com/questions/300122/mount-a-single-hard-disk-that-was-part-of-raid-1](https://unix.stackexchange.com/questions/300122/mount-a-single-hard-disk-that-was-part-of-raid-1)

And the granddaddy of all mdadm documentation:
[https://tldp.org/HOWTO/html_single/Software-RAID-HOWTO/](https://tldp.org/HOWTO/html_single/Software-RAID-HOWTO/)

---

### Post by cryptearth on 2021-08-07
You could have a try with

sudo mdadm --assemble --scan --verbose

It you could give you some hints about what mdadm can get from those partitions.
Also that layout of the 4th hdd doesn't look quite right but rather re-used - maybe even multiple times. Two 1gb and one 500mb partitions - and two of them not lined up and the first not start somewhere usual like 2048 or so ... and 4th partition using v1.2 while the other three use 0.9? Some lines look rather weird. Also: As it's a raid1: Where'S the 2nd mirror?

---

### Post by rsteinmetz70112 on 2021-08-09
If sdd really is 4 partitions of Raid 1 the simple way to go about fixing it is

  1. Get another disk drive to replace the failed drive.
  2.Copy the partition table from /dev/sdd to the new drive. 
  3.Join the new drive to the raid arrays. 

It should  come back up and rebuild the array. There are a lot of tutorials for replacing a bad drive in an array.

mdadm commands generally require an md device typically /dev/mdx or /dev/md/x not /dev/sddx

If you have a RAID 1 array you can also try assembling and mounting the existing md devices. Check /dev/md/ for any existing md devices. If they are there you should be able to mount them, they will show degraded but may be accessible.
You can also try the mdadm command above to scan for and assemble the arrays. You will then need to mount them by their md device name.

---

