---
title: "ext4 Partition not working"
date: 2016-05-27
forum: Hardware
---

### Post by reut2 on 2016-05-27
I have a partition which I have used for a while.  I recently changed the partition sizes on the disk because my Windows7 Partition was full and need more space.  Now the ext4  partition is not working.  When it is *mounted* it appears to have no files, and nothing on it (see screen dump of Gparted below), but when I comment out the line in fstab then Gparted shows that is is about half full. When I try to unmount it to run fsck message says it is not mounted, but fsck says it is in use. 

 I did run ```
fsck.ext4 -f -c -v /dev/sdc5
``` when it was commented out in fastab and it was *clean*. and showed the file count etc.

Some perhaps useful information:[INDENT]> root@reuven-Ubuntu:/home/reuven# ```
fdisk /dev/sdc5
```
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0xab07caa1.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help):



[ATTACH=CONFIG]269317[/ATTACH][ATTACH=CONFIG]269316[/ATTACH]
[B]
Current fstab:[/B]
> # <file system>                 <mount point>   <type>      <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=6aed7472-b49c-43e5-8a79-14fc2054409b     /               ext4    errors=remount-ro     0       1
# /home was on /dev/sda6 during installation
UUID=1114e5de-4c5f-4101-be00-ac2f044a9de0     /home           ext4    defaults                0       2
# /home/a7 was on /dev/sda7 during installation
UUID=6C315A26408A8CB1                 /home/a7        ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda5 during installation
UUID=b7b7ca3e-ce8d-4918-925e-e3e72f29c603 none                swap    sw                  0       0
# swap was on /dev/sdb6 during installation
UUID=93558e88-551e-4629-b457-25f75827170e none                swap    sw                      0       0

#Windows got more room
UUID=EEC099CFC0999F01            /home/Windows7    ntfs-3g auto,user,uid=1001,gid=1001,permissions 0 2    

#UUID=CDC4-53E2                    /home/MyDocsOld    vfat    defaults,umask=007,gid=46 0       0
# This is what I cam up with
#/home/MyDocsOld/My\ Documents    /home/reuven/My\ Documents    none    bind

#This is a copy of mtab line    
/home/Nordman1/My\040Documents /home/reuven/My\040Documents none rw,bind 0 0
# this line added for new PATA drive
/dev/sda1                /home/Nordman1        vfat    defaults,umask=007,gid=46 0       0

#Drive not working, trying again,still not  working, ran FSCK trying again
/dev/sdc5                home/NewDrive           ext4    defaults                0       2
[/INDENT]

---

### Post by oldfred on 2016-05-27
Better to mount by UUID, I have drive order change when I plug in flash drive & reboot.
I had skipped a port. So flash drive was sdf when plugged in, but on reboot flash drive became sdb and every other drive moved up a letter.

Post this:
sudo parted -l

 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdc5 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdc5
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdc5

---

### Post by reut2 on 2016-05-27
```
root@reuven-Ubuntu:/home/reuven# sudo parted -l
```
Model: ATA SAMSUNG SV1533D (scsi)
Disk /dev/sda: 15.3GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  15.3GB  15.3GB  primary  fat32        boot, lba


Model: ATA WDC WD2500KS-00M (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 2      1049kB  80.8GB  80.8GB  primary   ext4            boot
 1      80.8GB  250GB   169GB   extended
 7      80.8GB  164GB   83.0GB  logical   ntfs
 6      164GB   248GB   84.6GB  logical   ext4
 5      248GB   250GB   1572MB  logical   linux-swap(v1)


Model: ATA WDC WD800AAJS-60 (scsi)
Disk /dev/sdc: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  106MB   105MB   primary   ntfs            boot
 2      106MB   56.8GB  56.7GB  primary   ntfs
 3      56.8GB  80.0GB  23.2GB  extended
 5      56.8GB  78.5GB  21.7GB  logical   ext4
 6      78.5GB  80.0GB  1513MB  logical   linux-swap(v1)


Model: ATA SAMSUNG HD080HJ/ (scsi)
Disk /dev/sdd: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  32.5GB  32.5GB  primary   ntfs            boot
 2      32.5GB  80.0GB  47.5GB  extended
 5      32.5GB  60.0GB  27.5GB  logical   ext4
 7      60.0GB  78.4GB  18.5GB  logical   ext3
 6      78.4GB  80.0GB  1571MB  logical   linux-swap(v1)

---

### Post by reut2 on 2016-05-27
```
reuven@reuven-Ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sdc5
[sudo] password for reuven: 
                                                                               
       18627 inodes used (1.41%, out of 1324512)
          48 non-contiguous files (0.3%)
           1 non-contiguous directory (0.0%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 18556/21
     3691828 blocks used (69.60%, out of 5304576)
           0 bad blocks
           2 large files

       15876 regular files
        2700 directories
           0 character device files
           0 block device files
           0 fifos
           0 links
          37 symbolic links (37 fast symbolic links)
           5 sockets
------------
       18618 files
```

---

### Post by oldfred on 2016-05-27
So can you see files now? 
It shows 18,618.

---

### Post by reut2 on 2016-05-27
Yes, I know that there is data on the disk, and it is somehow readable.  I did this by commenting out the fstab line for this partition, rebooting and running fsck. (The other (ntfs) partition on this disk works fine too.  )

So in the process of working this through I realized i had a mistake in my fstab line (I was missing a /.  It now reads:
> /dev/sdc5                /home/NewDrive           ext4    defaults                0       2

SO now it does mount, I can save files and delete them, but it shows zero items. and  fdisk returns:
> reuven@reuven-Ubuntu:~$ sudo fdisk /dev/sdc5
[sudo] password for reuven: 
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0xfccc1294.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help): 



---

### Post by oldfred on 2016-05-27
If you have backups, then I might try the write.

If not, try testdisk and see what it says. And if deeper search shows files, back them up.

       Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

