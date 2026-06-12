---
title: "Ubuntu installer sees empty partition table"
date: 2009-02-23
forum: Installation &amp; Upgrades
---

### Post by EpsilonDelta on 2009-02-23
I recently reinstalled win xp, so I needed to restore the boot menu with the live cd to be able to dualboot again. I followed to how-to, and it failed.
So I decided to also reinstall ubuntu with the live cd. However, the installer sees only an empty partition table, and the only option I have is to create a new partition table. gparted shows my hd as unallocated space.
Did reinstalling windows mess up my partitions?
I can still access all partitions through the live cd, so I made a backup of my linux files. But is there any way to reinstall ubuntu without formatting the entire hd?
Here's the output from sudo fdisk -lu

omitting empty partition (5)

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x006d006d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   263465999   131732968+   7  HPFS/NTFS
/dev/sda2       263466000   625121279   180827640    f  W95 Ext'd (LBA)
/dev/sda3       314568828   625121279   155276226    7  HPFS/NTFS
/dev/sda5       263466126   312367859    24450867   83  Linux
/dev/sda6       312367923   314568764     1100421   82  Linux swap / Solaris

---

### Post by taurus on 2009-02-23
When you get to the partition screen, pick the Manual option and mount /dev/sda5 to / (root filesystem) and format it.  You don't have to do anything with /dev/sda6 (swap partition) since the installer knows how to handle it.

Remember, you need to give a mount point for /dev/sda5, /, or the installer will complain about no root filesystem defined.

---

### Post by caljohnsmith on 2009-02-23
> **EpsilonDelta said:**
> 
Here's the output from sudo fdisk -lu
```

[COLOR="Red"]omitting empty partition (5)[/COLOR]

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x006d006d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   263465999   131732968+   7  HPFS/NTFS
[COLOR="Red"]/dev/sda2       263466000   625121279[/COLOR]   180827640    f  W95 Ext'd (LBA)
[COLOR="Red"]/dev/sda3       314568828   625121279[/COLOR]   155276226    7  HPFS/NTFS
/dev/sda5       263466126   312367859    24450867   83  Linux
/dev/sda6       312367923   314568764     1100421   82  Linux swap / Solaris
```
Any time fdisk reports "omitting empty partition (X)", unfortunately that is a sure sign that your partition table is corrupt; that would explain why the installer can not recognize your partitions. As shown highlighted above in red, your sda3 primary partition is inside of your sda2 extended partition; thus sda3 should either be a logical partition, or your sda2 extended partition should be resized so it does not contain sda3. Unfortunately having your partition table corrupted sometimes happens when you reinstall Windows, because the Windows partitioner can use slightly different rules than the standard most Linux partition programs use; thus Windows can't adequately deal with a drive that's been partitioned with linux tools, and Windows ends up corrupting the partition table. If you would like help fixing your partition table, how about posting:
```
sudo sfdisk -d /dev/sda
sudo mount /dev/sda3 /mnt && ls -l /mnt
```
And also, do you have any preference whether sda3 is a logical or primary partition? If it does not have Windows installed to it, I would recommend making it a logical partition, because that usually gives you maximum flexibility when repartitioning.

---

### Post by EpsilonDelta on 2009-02-24
> sudo sfdisk -d /dev/sda
```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=263465937, Id= 7, bootable
/dev/sda2 : start=263466000, size=361655280, Id= f
/dev/sda3 : start=314568828, size=310552452, Id= 7
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=263466126, size= 48901734, Id=83
/dev/sda6 : start=312367923, size=  2200842, Id=82

```
>  sudo mount /dev/sda3 /mnt && ls -l /mnt
```
total 96
drwxrwxrwx 1 root root 28672 2009-01-29 13:55 a3a1a4ba37747b3f21be619a
drwxrwxrwx 1 root root  4096 2009-01-08 13:13 art
drwxrwxrwx 1 root root     0 2009-02-02 17:50 fraps
drwxrwxrwx 1 root root  8192 2009-02-15 19:47 games
drwxrwxrwx 1 root root  8192 2009-01-29 18:47 install
drwxrwxrwx 1 root root 20480 2009-02-16 11:40 music
drwxrwxrwx 1 root root  4096 2009-02-09 19:37 programming
drwxrwxrwx 1 root root     0 2009-01-29 13:54 RECYCLER
drwxrwxrwx 1 root root  4096 2008-12-23 11:17 shared_doeke
drwxrwxrwx 1 root root  4096 2008-03-17 20:30 System Volume Information
drwxrwxrwx 1 root root 12288 2009-02-20 19:32 torrents
drwxrwxrwx 1 root root     0 2009-02-08 13:29 ubuntu_backup
drwxrwxrwx 1 root root  4096 2008-08-01 13:23 websites

```
> And also, do you have any preference whether sda3 is a logical or primary partition?
No I don't, as you can see it's just data, windows is on sda1.
Is there any way I can save at least my windows partitions?

---

### Post by caljohnsmith on 2009-02-24
> **EpsilonDelta said:**
> 
No I don't, as you can see it's just data, windows is on sda1.
Is there any way I can save at least my windows partitions?
The partition table problem that the Windows installer caused is simple and not serious; fortunately it should not be a big deal for us to fix your partition table so you won't lose any of your partitions. How about downloading the attached "partition_table.txt" file to your Ubuntu Live CD desktop, and then do:
```
sudo sfdisk --no-reread -f /dev/sda < ~/Desktop/partition_table.txt
```
And please post the output. Then reboot your Live CD (it is important to reboot), and please post the output of:
```
sudo fdisk -lu
sudo parted /dev/sda print
sudo grub
grub> root (hd0,4)
grub> setup (hd0)
grub> quit
```
And we can work from there.

---

### Post by EpsilonDelta on 2009-02-24
Thanks for helping me. I can now access my linux partitions from windows, and the boot menu is back. But booting from my ubuntu partition fails: "error 17, could not mount selected partition".
Here are all the outputs:

```
ubuntu@ubuntu:~$ sudo sfdisk --no-reread -f /dev/sda < ~/Desktop/partition_table.txt

Disk /dev/sda: 38913 cylinders, 255 heads, 63 sectors/track
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+  16399   16400- 131732968+   7  HPFS/NTFS
/dev/sda2      16400   38911   22512  180827640    f  W95 Ext'd (LBA)
/dev/sda3      19581+  38911   19331- 155276226    7  HPFS/NTFS
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5      16400+  19443    3044-  24450867   83  Linux
/dev/sda6      19444+  19580     137-   1100421   82  Linux swap / Solaris
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *        63 263465999  263465937   7  HPFS/NTFS
/dev/sda2     263466000 625121279  361655280   5  Extended
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty
/dev/sda5     263466126 312367859   48901734  83  Linux
/dev/sda6     312367923 314568764    2200842  82  Linux swap / Solaris
/dev/sda7     314568828 625121279  310552452   7  HPFS/NTFS
Successfully wrote the new partition table

Re-reading the partition table ...
BLKRRPART: Device or resource busy

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)

```
Reboot
```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x006d006d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   263465999   131732968+   7  HPFS/NTFS
/dev/sda2       263466000   625121279   180827640    5  Extended
/dev/sda5       263466126   312367859    24450867   83  Linux
/dev/sda6       312367923   314568764     1100421   82  Linux swap / Solaris
/dev/sda7       314568828   625121279   155276226    7  HPFS/NTFS
ubuntu@ubuntu:~$ sudo parted /dev/sda print
Model: ATA SAMSUNG HD321KJ (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system  Flags
 1      32.3kB  135GB  135GB   primary   ntfs         boot 
 2      135GB   320GB  185GB   extended                    
 5      135GB   160GB  25.0GB  logical   ext3              
 6      160GB   161GB  1127MB  logical   linux-swap        
 7      161GB   320GB  159GB   logical   ntfs 
```

```
grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,4)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.
```

---

### Post by caljohnsmith on 2009-02-24
It looks like your partition table is OK now, so hopefully you won't have to reinstall Windows again in the near future. How about doing the following:
```
sudo mount /dev/sda5 /mnt && gksudo gedit /mnt/boot/grub/menu.lst
```
Although I haven't seen your menu.lst, probably all the Ubuntu entries are using the wrong (hdX,Y) references; they should all be [COLOR="Blue"](hd0,4)[/COLOR]. If they do need to be changed to (hd0,4), be sure to also change the "#groot..." line:
```
# groot=[COLOR="Blue"](hd0,4)[/COLOR]
```
If you run into any problems, please post your entire menu.lst. Otherwise let me know if that works to boot Ubuntu or not.

---

### Post by EpsilonDelta on 2009-02-25
Thanks! I changed all root(hd0,5) to (hd0,4), and my ubuntu boots again. Again, thanks for all the help!

---

### Post by caljohnsmith on 2009-02-25
You're certainly welcome, and I'm really glad to hear you can boot both Ubuntu and Windows again; cheers and have fun with your dual-boot Windows/Ubuntu setup. :)

---

### Post by nghalion on 2009-09-22
Hello Everyone,

I have THE SAME EXACT PROBLEM. I installed WinXP (one of my biggest mistakes) after Ubuntu and this lead to the corrupted partition table. The only difference is that I want to restore the Primary partition having 'Windows'. What should my partition file look like?

Here's the outputs that I get for the following:
> **sudo sfdisk -d /dev/sda**```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=   690732, Id= b, bootable
/dev/sda2 : start=   690795, size= 48146805, Id=83
/dev/sda3 : start= 48837600, size=263739105, Id= 5
/dev/sda4 : start=303532173, size=  9044532, Id=82
/dev/sda5 : start= 48837726, size=205085664, Id=83
/dev/sda6 : start=253923453, size= 29302497, Id=83
/dev/sda7 : start=283226013, size= 20306097, Id= 7
```> **sudo mount /dev/sda7 /mnt && ls -l /mnt**```
total 2095148
drwxrwxrwx 1 root root       4096 2009-09-22 14:35 Documents and Settings
-rwxrwxrwx 1 root root 2145386496 2009-09-22 15:24 pagefile.sys
drwxrwxrwx 1 root root       8192 2009-09-22 14:58 Program Files
drwxrwxrwx 1 root root          0 2009-09-22 14:46 RECYCLER
drwxrwxrwx 1 root root       4096 2009-09-22 14:35 System Volume Information
drwxrwxrwx 1 root root          0 2009-09-22 14:58 Temp
drwxrwxrwx 1 root root      28672 2009-09-22 15:31 WINDOWS
```I would've tried creating my own partition table but I'm afraid I'll mess things up. Any help is greatly appreciated.

Thanks in advance.

---

### Post by nghalion on 2009-09-22
And Oh..the output for:

> **sudo fdisk -l**

omitting empty partition (5)

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000bb3d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          43      345366    b  W95 FAT32
/dev/sda2              44        3040    24073402+  83  Linux
/dev/sda3            3041       19457   131869552+   5  Extended
/dev/sda4           18895       19457     4522266   82  Linux swap / Solaris
/dev/sda5            3041       15806   102542832   83  Linux
/dev/sda6           15807       17630    14651248+  83  Linux
/dev/sda7           17631       18894    10153048+   7  HPFS/NTFS

Thanks again.

---

