---
title: "My files are missing"
date: 2015-11-17
forum: Hardware
---

### Post by shabba2 on 2015-11-17
*I'm a linux noob*

I recently switched over to Ubuntu from Windows 7.  I have two drives in my computer, a SSD I use for my OS/Programs/Etc and a HDD that I use for storage.  When I originally installed ubuntu (14 LTS) on my SSD as the primary operating system I could still go in my HDD and access all my files.  Well the other day I ran another distro from a USB (Kali, I know I know) and now I can't find my files on my HDD and it is renamed Kali showing 3.2gb of space with 300gbs of unallocated space.  


I realize I probably did something I shouldn't have but I did it and now I would like to try to fix it.  So is there any chance I can recover my files or am I SOL?

Thanks

---

### Post by Bashing-om on 2015-11-17
shabba2; Ouch !

Bad things can happen - that my friend is why we maintain our backups.

Look and see what is now :
From an ubuntu operating system what returns from terminal command:
```

sudo fdisk -lu
sudo parted -l

```

If the partition really has been over-ridden there are tools that "might" recover:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
Are some guides .

[INDENT][INDENT][INDENT]hope this helps
[/INDENT][/INDENT][/INDENT]

---

### Post by shabba2 on 2015-11-17
Yea I guess I was foolish not to have a backup but I thought they would be safe on another drive as long as I didn't install in OS or format it.  Anyways I ran the commands you gave me and here are my results, but honestly I'm not sure what it all means.  Any help would be greatly appreciated.  The drive in question is the 320gb  - SDB in terminal.  

```

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 240.1 GB, 240057409536 bytes
255 heads, 63 sectors/track, 29185 cylinders, total 468862128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   468862127   234431063+  ee  GPT

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0a9a1b1a

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/mapper/sda3_crypt: 239.3 GB, 239260925952 bytes
255 heads, 63 sectors/track, 29088 cylinders, total 467306496 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/sda3_crypt doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-root: 230.8 GB, 230787383296 bytes
255 heads, 63 sectors/track, 28058 cylinders, total 450756608 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-swap_1: 8472 MB, 8472494080 bytes
255 heads, 63 sectors/track, 1030 cylinders, total 16547840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-swap_1 doesn't contain a valid partition table

Disk /dev/sdc: 16.0 GB, 16016998400 bytes
255 heads, 63 sectors/track, 1947 cylinders, total 31283200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cdb82

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048    31283199    15640576    7  HPFS/NTFS/exFAT


```

```

Model: ATA KINGSTON SV300S3 (scsi)
Disk /dev/sda: 240GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size   File system  Name  Flags
 1      1049kB  538MB  537MB  fat32              boot
 2      538MB   794MB  256MB  ext2
 3      794MB   240GB  239GB


Model: ATA WDC WD3200BEKT-6 (scsi)
Disk /dev/sdb: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End  Size  Type  File system  Flags


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 8472MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  8472MB  8472MB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 231GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  231GB  231GB  ext4


Error: /dev/mapper/sda3_crypt: unrecognised disk label 

```

---

### Post by Bashing-om on 2015-11-17
shabba2; Yuk !

Looks like encryption . I have no experience with that level of complexity and do not know how to cope with it.

Others here can much better advise . 

[INDENT][INDENT]exit, stage left
[/INDENT][/INDENT]

---

### Post by shabba2 on 2015-11-17
I have encryption on my SSD through ubuntu if that matters.  Thanks for your help though.

---

### Post by oldfred on 2015-11-18
Was your data on sdb in the LVM encrypted partition. Or did you do a full drive LVM with encryption installl on sdb and overwrite all your data?

If just mounting encryption, if you can boot from sda, you then do not need live installer:
       Includes chroot:
[https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory)
[http://ubuntuforums.org/showthread.php?t=2028865](http://ubuntuforums.org/showthread.php?t=2028865)
[http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/)

If you overwrote data you may recover some with photorec, but I have used it and it ended up being weeks as I had many similar files to compare, update and rename. And I had a backup to compared files to, but it was a bit older. It only recovers files by file extensions. And you have to have another drive large enough to hold all your data that it recovers.

      
 [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

---

### Post by shabba2 on 2015-11-18
I'm sorry but I'm not really sure what you mean in the first sentence as far as LVM.  The data on sdb shouldn't have been encrypted and I didn't think I actually installed anything on sdb as I was just running it from a USB and choose the "live" option on the menu.  Although now that drive is called "kali live" and it shows about 3gb of data which I'm guessing is the Kali distro.

How can you guys tell me drive is encrypted in the coding above?

Gonna go through those links you posted and see what I can come up with.  Is there anything I shouldn't do that might mess this up even more?

In reading some of those threads they appear to be related to an encrypted home folder but yet my home folder shouldn't have been on my HDD so therefore it shouldn't be encrypted right?

---

### Post by oldfred on 2015-11-18
LVM default install is always full drive unless you manually change that which I have not done but understand it is not as easy as changing partitions in standard install.
And full drive encryption always uses LVM as opposed to encryption of /home only.

It looks like sdb is lvm with the /mapper and this:
> Disk /dev/mapper/sda3_crypt: 239.3 GB, 239260925952 bytes

---

