---
title: "Why did Ubuntu format my system drive this way?"
date: 2019-09-04
forum: Hardware
---

### Post by cscj01 on 2019-09-04
I had a crash and was forced to reinstall (long story) Ubuntu 18.04 x64 from a Live CD.  Fortunately I had backups of ~/ and all major config files.  When I selected Install from the Live CD, I let Ubuntu configure my System disk.  I was surprised after I had completed the install about why Ubuntu configured the drive as it did.  I have the following on sda:> sda1 537 MB EFI System FAT @ /boot/efi
sda2 2 TB Linux Filesystem Ext4 @ Filesystem RootI am used to seeing > sda1 as /
sda2 as a swap partition The drive is a 2 TB Western Digital Black with a GUID partition table.  I have other 2 and 3 TB Western Digital Black drives that have a GUID partition and an Ext4 filesystem that are not partitioned that way.  Some are bootable.  I have never had  Ubuntu install the system that way.  Additionally, there is no swap partition.  That doesn't really bother me because I h wave a 32 TB system, but I have never seen a default configuration without a swap file.  Does anyone know why Ubuntu partition the drive this way?

Another queston I have is if I choose to have a static fstab, how do I deal with sda1?

---

### Post by TheFu on 2019-09-05
I suspect you are interpreting things incorrectly.  Please post the command and output instead of an interpretation.

```
lsblk
sudo fdisk -l
df -Th

```
Please post using code tags, as I have above so the output lines up in columns correctly.

In 18.04, the installers switched from using a swap partition to using a swap file unless you manually set it up via "Something else"

---

### Post by cruzer001 on 2019-09-05
```
cat /proc/swaps
#and
cat /etc/fstab
```
Will show a swap file if installed.

---

### Post by cscj01 on 2019-09-05
> **TheFu said:**
> I suspect you are interpreting things incorrectly.  Please post the command and output instead of an interpretation.

```
lsblk
sudo fdisk -l
df -Th

```
Please post using code tags, as I have above so the output lines up in columns correctly.

In 18.04, the installers switched from using a swap partition to using a swap file unless you manually set it up via "Something else"

```
lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0   1.8T  0 disk 
&#9500;&#9472;sda1   8:1    0   512M  0 part /boot/efi
&#9492;&#9472;sda2   8:2    0   1.8T  0 part /
sdb      8:16   0   1.4T  0 disk 
&#9492;&#9472;sdb1   8:17   0   1.4T  0 part 
sdc      8:32   0 465.8G  0 disk 
&#9492;&#9472;sdc1   8:33   0 465.8G  0 part 
sdd      8:48   0   2.7T  0 disk 
&#9492;&#9472;sdd1   8:49   0   2.7T  0 part 
sde      8:64   1   2.7T  0 disk lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0   1.8T  0 disk 
&#9500;&#9472;sda1   8:1    0   512M  0 part /boot/efi
&#9492;&#9472;sda2   8:2    0   1.8T  0 part /
sdb      8:16   0   1.4T  0 disk 
&#9492;&#9472;sdb1   8:17   0   1.4T  0 part 
sdc      8:32   0 465.8G  0 disk 
&#9492;&#9472;sdc1   8:33   0 465.8G  0 part 
sdd      8:48   0   2.7T  0 disk 
&#9492;&#9472;sdd1   8:49   0   2.7T  0 part 
sde      8:64   1   2.7T  0 disk 
&#9492;&#9472;sde1   8:65   1   2.7T  0 part /media/butch/Data
sdf      8:80   0   1.8T  0 disk 
&#9492;&#9472;sdf1   8:81   0   1.8T  0 part /media/butch/System
sdg      8:96   0   2.7T  0 disk 
&#9492;&#9472;sdg1   8:97   0   2.7T  0 part /media/butch/Ubuntu_Data_Back
sr0     11:0    1  1024M  0 rom  
sr1     11:1    1  1024M  0 rom 
&#9492;&#9472;sde1   8:65   1   2.7T  0 part /media/butch/Data
sdf      8:80   0   1.8T  0 disk 
&#9492;&#9472;sdf1   8:81   0   1.8T  0 part /media/butch/System
sdg      8:96   0   2.7T  0 disk 
&#9492;&#9472;sdg1   8:97   0   2.7T  0 part /media/butch/Ubuntu_Data_Back
sr0     11:0    1  1024M  0 rom  
sr1     11:1    1  1024M  0 rom 
``````
sudo fdisk -l
Disk /dev/sda: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 16A678BF-D30A-491F-B103-F0D1E4F17712

Device       Start        End    Sectors  Size Type
/dev/sda1     2048    1050623    1048576  512M EFI System
/dev/sda2  1050624 3907028991 3905978368  1.8T Linux filesystem


Disk /dev/sdb: 1.4 TiB, 1500301910016 bytes, 2930277168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x000020a9

Device     Boot Start        End    Sectors  Size Id Type
/dev/sdb1        2048 2930276351 2930274304  1.4T 83 Linux




Disk /dev/sdc: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x89e80605

Device     Boot Start       End   Sectors   Size Id Type
/dev/sdc1        2048 976773119 976771072 465.8G 83 Linux


Disk /dev/sdd: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: BEAFD4E8-3C24-4F29-A11C-2341DD44346C

Device     Start        End    Sectors  Size Type
/dev/sdd1   2048 5860532223 5860530176  2.7T Microsoft basic data




Disk /dev/sde: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 0085F203-442E-4B3D-B09B-5DBD401BC683

Device     Start        End    Sectors  Size Type
/dev/sde1   2048 5860532223 5860530176  2.7T Linux filesystem


Disk /dev/sdf: 1.8 TiB, 2000365289472 bytes, 3906963456 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: ED997601-C9FC-4875-A7AF-3B5429805561

Device     Start        End    Sectors  Size Type
/dev/sdf1   2048 3906961407 3906959360  1.8T Microsoft basic data


Disk /dev/sdg: 2.7 TiB, 3000558944256 bytes, 732558336 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: F04F6D11-0033-4EEF-8396-66BB0FECB144

Device     Start       End   Sectors  Size Type
/dev/sdg1    256 732558079 732557824  2.7T Linux filesystem

``````
df -Th
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs   16G     0   16G   0% /dev
tmpfs          tmpfs     3.2G  1.9M  3.2G   1% /run
/dev/sda2      ext4      1.8T  615G  1.1T  36% /
tmpfs          tmpfs      16G   33M   16G   1% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs      16G     0   16G   0% /sys/fs/cgroup
/dev/sda1      vfat      511M  6.1M  505M   2% /boot/efi
tmpfs          tmpfs     3.2G  112K  3.2G   1% /run/user/1000
/dev/sdf1      ext4      1.8T  660G  1.1T  38% /media/butch/System
/dev/sde1      ext4      2.7T  1.3T  1.3T  51% /media/butch/Data
/dev/sdg1      ext4      2.7T  1.3T  1.3T  51% /media/butch/Ubuntu_Data_Back
```

---

### Post by Skaperen on 2019-09-05
choosing the partition scheme depends a lot about your intended use of the system.  ubuntu likely chooses a scheme that balances between what will work on many machines with what may already be there and what meets people's intended usage, which is constantly changing.

---

### Post by deadflowr on 2019-09-05
Looks normal, but we would need fstab output to confirm.
As posted Ubuntu switched to swap files over swap partition a few years ago, now.
[https://blog.surgut.co.uk/2016/12/swapfiles-by-default-in-ubuntu.html]("https://blog.surgut.co.uk/2016/12/swapfiles-by-default-in-ubuntu.html")

---

### Post by TheFu on 2019-09-05
Ok, we know you aren't using LVM anywhere today.

Thanks for the output, but the **lsblk** is mixed up and confusing. Please remove it and rerun the command ONCE, posting the output back in the post above.

If you can list all the partitions and what they are intended to hold, better guidance is possible.

I don't let partitions be mounted automatically.  Automatic mounting in /media/butch/ can cause issues on a multi-user system. For storage that is directly connected via SATA/eSATA, I use the fstab to mount it where it is needed with a few restrictions.  
For storage that is USB or network connected, I use autofs with settings so they don't block the entire OS or have 90 sec timeouts when the specific partition isn't available.
For example, I don't permanently mount anything under /mnt/ or /media/ or underneath any HOME directory.  This has to do with backup techniques that I use. I try to follow the Linux File System Hierarchy document which clearly spells out what each place is about.  That document is smart, BTW.

As for swap, use the **swapon -s** command to see all the swap used.

But it is your system, so you do it the way you want.

---

### Post by cscj01 on 2019-09-05
> **deadflowr said:**
> Looks normal, but we would need fstab output to confirm.
As posted Ubuntu switched to swap files over swap partition a few years ago, now.
[https://blog.surgut.co.uk/2016/12/swapfiles-by-default-in-ubuntu.html]("https://blog.surgut.co.uk/2016/12/swapfiles-by-default-in-ubuntu.html")
Here is the new fstab```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=ca2fb138-b09a-4aa1-8046-67149fb6334f /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=B503-AECA  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
```This is my original fstab```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=9ef58828-ffae-4248-ad25-44596e6440d1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=7677ace4-168d-4f94-87fe-d5a5c1372ff5 none            swap    sw              0       0
#Entry for /dev/sdb1
UUID=f3676964-3fac-407e-88f9-9b345f83c687 /media/Data_Three	ext4    errors=remount-ro 0 1
#Entry for /dev/sdc1 :
UUID=b61632e9-7186-4ec9-9e4c-214c01d39a4e /media/Data_Two 	ext4	errors=remount-ro 0 1
#Entry for /dev/sdd1 :
UUID=3573b59f-77c9-460d-9a29-9f6730954125 /media/Data_One	ext4	errors=remount-ro 0 1
#Entry for /dev/sde1 :
UUID=8e82c472-7f56-4183-8156-84d428887b43 /media/Data		ext4	errors=remount-ro 0 1
#Entry for External USB Data Backup Drive
UUID=ac5ef499-beec-42ba-b34b-a5a0d86d49b6 /media/butch/Ubuntu_Data_Back	ext4	errors=remount-ro 0 1

```I plan to go back to the original fstab, but I'm not sure what to do with sda1.

---

### Post by cscj01 on 2019-09-05
> **TheFu said:**
> Ok, we know you aren't using LVM anywhere today.

Thanks for the output, but the **lsblk** is mixed up and confusing. Please remove it and rerun the command ONCE, posting the output back in the post above.

If you can list all the partitions and what they are intended to hold, better guidance is possible.

I don't let partitions be mounted automatically.  Automatic mounting in /media/butch/ can cause issues on a multi-user system. For storage that is directly connected via SATA/eSATA, I use the fstab to mount it where it is needed with a few restrictions.  
For storage that is USB or network connected, I use autofs with settings so they don't block the entire OS or have 90 sec timeouts when the specific partition isn't available.
For example, I don't permanently mount anything under /mnt/ or /media/ or underneath any HOME directory.  This has to do with backup techniques that I use. I try to follow the Linux File System Hierarchy document which clearly spells out what each place is about.  That document is smart, BTW.

As for swap, use the **swapon -s** command to see all the swap used.

But it is your system, so you do it the way you want.

Here is my lsblk command.  I'm not sure what happened earlier, but it must have been a copy and paste error on my part without checking the results.```
lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0   1.8T  0 disk 
&#9500;&#9472;sda1   8:1    0   512M  0 part /boot/efi
&#9492;&#9472;sda2   8:2    0   1.8T  0 part /
sdb      8:16   0   1.4T  0 disk 
&#9492;&#9472;sdb1   8:17   0   1.4T  0 part 
sdc      8:32   0 465.8G  0 disk 
&#9492;&#9472;sdc1   8:33   0 465.8G  0 part 
sdd      8:48   0   2.7T  0 disk 
&#9492;&#9472;sdd1   8:49   0   2.7T  0 part 
sde      8:64   1   2.7T  0 disk 
&#9492;&#9472;sde1   8:65   1   2.7T  0 part /media/butch/Data
sdf      8:80   0   2.7T  0 disk 
&#9492;&#9472;sdf1   8:81   0   2.7T  0 part /media/butch/Ubuntu_Data_Back
sr0     11:0    1  1024M  0 rom  
sr1     11:1    1  1024M  0 rom
```As you can see from my previous post, I did not use auto mount for any of my sata disk that are directly connectly.  I'm not sure if /media is the correct mount point, but it has served me well.  I'll check on the Linux File System Hierarchy document you mentioned about that.  Also, you make a good point as well about USB drives, so I'll go to autofs.  Any suggestions as to appropriate settings for 2 and 3 TB desktop USB HDDs?  Thanks.

---

### Post by TheFu on 2019-09-05
The disks moved around!   We can use either LABELs or UUIDs to keep them straight.

Still hoping for a summary of what each partition will hold.  Games, media, programming files, etc.  Backups for each are a little different, unless you have lots-o-money.

Would also help if they were all mounted when running the **df -hT -x squashfs -x tmpfs -x devtmpfs**.  That way we can see how much free space is available and the file system on each. Those options remove the stuff that doesn't matter.

I'm concerned about the 3TB disks. Many of that size HDD had terrible failure rates across most makers. Please monitor those disks carefully.

```
Filesystem Type Size  Used Avail Use% Mounted on
/dev/sda1  vfat 511M  6.1M  505M   2% /boot/efi
/dev/sda2  ext4 1.8T  615G  1.1T  36% /
/dev/sde1  ext4 2.7T  1.3T  1.3T  51% /media/butch/Data
/dev/sdf1  ext4 1.8T  660G  1.1T  38% /media/butch/System
/dev/sdg1  ext4 2.7T  1.3T  1.3T  51% /media/butch/Ubuntu_Data_Back
```

Some comments about the current / allocation, that can help with future flexibility:

/ should be 25G or less. There are many reasons that the size of / should be limited.  If there are places outside /home/ that are using lots of space, then move /home/ to a different partition. This 25G doesn't include the 4.1G for the swapfile.  You can change to a swap partition, if you like.  It would make solid backups a little easier since you wouldn't need to exclude the swapfile.

**Limiting / **will help for moving to a new release, trying out new releases, etc.  With a swap partition, multiple Linux distros can all share it when running.  I've never needed more than 15G for /, so 25G is massive overkill.  If there are special places that need lots of storage, then you can mount a different partition where needed.  I do that with /var/lib/libvirt/ which is where KVM+libvirt can store file-based VM storage.

**/home/ **being on a different partition will reduce some risks with OS release upgrades and can make accessing it from different Linux installs easier.

Partitioning and storage design is mainly about how the backups for each area will be performed. Even if the decision is for a partition not to be included in backups.

If you really want more flexible storage capabilities, LVM could be worth a look, but it is more complicated. Flexibility requires complications. ZFS is another option, but only for non-OS needs.

As for mounting under /media/ - perhaps using /m/ would be better? It is shorter, so less typing. It isn't in a location that Ubuntu Desktop OSes expect to manage themselves, so conflicts can be prevented and it avoids the LFSH standards.  I use /D/ for static mounts and /misc/ for NFS and USB mounts via autofs.  For example:
```
$ dft|grep misc
/dev/sdf2                                    ext4  3.6T  3.5T   30G 100% /misc/b-D5
/dev/mapper/istar--8TB-istar--back3--a       ext4  3.6T  3.5T  153G  96% /misc/b-D3
/dev/mapper/istar--8TB-istar--back3--b       ext4  3.6T  3.5T   92G  98% /misc/b-D4
/dev/mapper/istar--vg2--back-lv_media2_back  ext4  3.6T  3.5T   53G  99% /misc/D5

```
b-D3, b-D4, b-D5 are all backup storage. There are D3 and D4 disks of the same size, but they are SATA connected, so mounted to different mount points. You can see both D5 and b-D5. Sorry the LV names don't map directly to the actual uses.  The b-D3/4 are physically on the same 8TB USB disk, but I have a rule about limiting all storage to a size I can easily get for a good price if an emergency happens.

All the /dev/mapper/ ... stuff is due to LVM. I prefer to use the PV-VG-LV naming for mounting, not UUIDs. This storage has been moving forward for almost a decade now, so it didn't start with LVM. That's why there are some inconsistencies.  

Nobody's storage is perfect. ;)  Certainly not mine.  Live and learn.

---

### Post by cscj01 on 2019-09-06
Okay, I have changed my **fstab** to account for the new partitioning of **sda** and all is well.  I did put an entry in for **/boot/efi** because Ubuntu put one in when I did the clean install.  I resolved an issue with my scanner and am now working on getting my **mysql** back to normal.  Thanks to all for your insight and help.  I'll mark this thread as closed.

---

