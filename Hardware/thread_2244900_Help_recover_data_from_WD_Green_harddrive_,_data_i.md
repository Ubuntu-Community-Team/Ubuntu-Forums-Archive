---
title: "Help recover data from WD Green harddrive , data inaccessable"
date: 2014-09-19
forum: Hardware
---

### Post by Hmnyn on 2014-09-19
Hello guys,
This is my first post thread, so I apologize if it is not compiled in correct way. I searched all the subfora and eventually decided to put my problem under the hardware subforum.
If you kindly please help me sort this out, i will write a detailed tutorial with screen shots so others will benefit from your help here.

**THe story.**
I have a Mybook Live 3TB Nas, and due to power/circuit break in my house, it won't start up.
Now i found a repair script that can help you unbrick it, but there's a crucial superblock backup that is needed to make the script work. And from all the superblock backups, this specific superblock is damaged which interups the process to unbrick the Nas hdd. Nor do i know how to manually install a new firmware and partition it correctly.
Now i am at wit's end, and lacking the knowledge to manually input the commands that are in the script to make it work via terminal. 
i followed this guide, even bought the same icy box for it.
[http://mybookworld.wikidot.com/mybook-live-debricking-guide-osx-and-windows](http://mybookworld.wikidot.com/mybook-live-debricking-guide-osx-and-windows)

**Things i have done so far**
Installed curl and mdam (default settings)
```
sudo apt-get install curl
sudo apt-get install mdadm
```

-made the script executable
```
chmod +x sudo repair_mybooklive.sh
```

Gave terminal root and administrative privileges, before starting the script
```
su root
```
```
sudo -i
```

made sure dev/md0 is not mounted or in use, before starting the script

```
mdadm --stop /dev/md0
```
```
mdadm --remove /dev/md0
```


made sure i have the right hdd to run the script
```
sudo fdsik -l
```

Model: WDC WD30 EZRX-00MMMB0 (scsi)
Disk **/dev/sdc**: 3001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name     Flags
 3      15,7MB  528MB   513MB                primary  msftdata
 1      528MB   2576MB  2048MB  ext3         primary  raid
 2      2576MB  4624MB  2048MB               primary  raid
 4      4624MB  3001GB  2996GB  ext4         primary  msftdata

[B]Results from the script

[/B]> Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912

Checking for bad blocks (read-only test):   0.00% done, 0:00 elapsed. (0/0/0 errdone                                                 
*_Warning: the backup superblock/group descriptors at block 65536 contain bad blocks_.*

Warning: the backup superblock/group descriptors at block 98304 contain bad blocks.

Warning: the backup superblock/group descriptors at block 131072 contain bad blocks.

Warning: the backup superblock/group descriptors at block 425984 contain bad blocks.

Warning: the backup superblock/group descriptors at block 458752 contain bad blocks.

Warning: the backup superblock/group descriptors at block 491520 contain bad blocks.

Allocating group tables: done                            
Writing inode tables: done                            
Creating journal (8192 blocks): done
Writing superblocks and filesystem accounting information:  0/16
*_Warning, had trouble writing out superblocks.mdadm: added /dev/sdc2_*
copying image to disk... 
dd: writing to ‘/dev/md0’: Input/output error
362273+0 records in
362272+0 records out
185483264 bytes (185 MB) copied, 486,404 s, 381 kB/s
cp: failed to access ‘/mnt/md0/boot/boot.scr’: Input/output error
./repair_mybooklive.sh: line 359: /mnt/md0/etc/nas/service_startup/ssh: Input/output error
mdadm: stopped /dev/md0


**My request**
Could someone please help me with the following:
Basically i have two issues, superblock backup 65536 is damaged, and i can't install the image.

Please tell me step-by-step instructions how i can repair this hdd.

1. fix the superblock  size 65536 so this error goes away
> #blocksize 65536 is required by the hardware, you won't be able to mount if different. 
    mkfs.ext4 -b 65536 -m 0 $diskData
2. what to delete from the script to make it run-*without* checking for bad superblock. (i already finished that test , took me 13 hours.)
OR
3. help me decript the script commands, so i can manually enter them in terminal

4. How to implement this command to restore superblock from other superblock backup.

```
sudo e2fsck -b block_number /dev/xxx
```

in the attachments you can find the debrick scrip plus the results where it went wrong.

[ATTACH]256544[/ATTACH]
[ATTACH]256545[/ATTACH]
[ATTACH]256546[/ATTACH]



or you can download it from [https://github.com/chnrxn/MyBookLive/blob/master/debrick.sh](https://github.com/chnrxn/MyBookLive/blob/master/debrick.sh)

---

### Post by Hmnyn on 2014-10-07
anyone please help!! 2 weeks no answer!

---

### Post by Michael_McKenney on 2014-10-07
I know how to do it in Windows not Linux.  In Windows, I have seen the boot sector fail but the data part of the drive stay intact. 

1.) Try booting a Live CD and see if you can access the drive and copy your files to USB thumb drive.
2.) Remove the old hard drive cables so you don't touch the drive.  You can install a new hard drive with Linux on it.  Shut down. Plug in the old drive and see if you can fix the bad sectors and copy your data off.

---

### Post by Hmnyn on 2014-10-07
thnx for reply Michael,really appreciate it

your advice is exactly what I want to achieve too.but somehow WD decided to make the partition unreachable.

The blocksize on the filesystem is set to **16k**, whereas 64-bit computers  can only use a **4k** block size. This means that it is impossible to mount  this partition to get files off of it!

you can see this from the results of debrick guide.

> mdadm: /dev/sdc1 appears to contain an ext2fs file system
    size=1999808K  mtime=Thu Sep 18 09:10:04 2014
mdadm: size set to 1999808K
mdadm: creation continuing despite oddities due to --run
mdadm: array /dev/md0 started.
mke2fs 1.42.9 (4-Feb-2014)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
125184 inodes, 499952 blocks
24997 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=515899392
16 block groups
32768 blocks per group, 32768 fragments per group
7824 inodes per group
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1  4294967295  2147483647+  ee  GPT

**here's the gparted partition table**
[IMG]http://i.imgur.com/Wgwrz4D.png?1[/IMG]

[LIST]
[*]How can I mount ext4 to copy files to another hdd. 
[/LIST]


or 
[LIST]
[*]how do i use this command in my situation? 
[/LIST]
```
sudo e2fsck -y -b block_location /dev/????
```

I know where my superblock bad blocks are.
> Warning: the backup superblock/group descriptors at block 65536, 98304, 131072, 425984, 458752, 491520 contain bad blocks.
> Superblock backups stored on blocks: 32768, 98304, 163840, 229376, 294912

i only used this command now
```
sudo mke2fs -n /dev/sdd1
```
and i got this result
> mke2fs 1.42.9 (4-Feb-2014)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
125184 inodes, 499968 blocks
24998 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=515899392
16 block groups
32768 blocks per group, 32768 fragments per group
7824 inodes per group
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912

any help would be appreciated

---

### Post by Michael_McKenney on 2014-10-07
16KB is the raid chunk size per disk.  4KB is the physical sector size. Two different things.   

I would say you have a damaged hard drive or corrupted RAID partition.  bad blocks means damage to the hard drive.  How did you configure your RAID?  How many drives?

---

### Post by Hmnyn on 2014-10-07
Thanks for info on the chuck and Physical sector size.
this hdd was inside a WD Mybook Live NAS. And it went nuclear , when i had a power shortage.
I am most certain that i have a corrupted RAID. because the EXT4 partition with my files is intact.

I didnt confige RAID myself, but online it is said that WD configeures it with RAID1 or RAID2.
personally not sure how t verify that.

is there a away to access the EXT4 partition to mount it, you think? without using the sd1 and sd2 partition.

finally there's a script for debricking this hdd, it's just it requires superblock backup 65536 to rewrite the image. And that is exactly the block that is corrupted.

if you know a way around this to mount the hdd in Windows, I'm all ears too.Untill now windows doesnt recognize the drive and doesnt show it.

---

### Post by Michael_McKenney on 2014-10-07
I am used to doing this in Windows not Linux.  You have four solid state drives 1 to 4 in the NAS?    

WD Mybook Live NAS can do RAID 0 or 1.  If it was 1, mirroring, you could see the data.  If RAID 0, and you lost one of the two drive, data is gone.  

From reading the Gpart table.  Looks like SSD1 and SSD2 are in RAID 1.  Where SSD1 is active and it looks like its RAID 1 mirror drive also crashed.  SSD4 is single JBOD and is working.  SSD3 crashed and has bad sectors.   I would try to access the NAS administrator screen instead of trying this from Linux.   The NAS will give you better errors on what crashed.  Looks like two hard drives were damaged.

---

### Post by Michael_McKenney on 2014-10-07
If you have a red light on the outside of the NAS, you have a bad hard drive.

---

### Post by Hmnyn on 2014-10-07
okey Michael, I'm totally following you on this one.
about the 3TB HDD, it's actually 1 drive. so not sure what you meant with second drive.

the Led light is constantly yellow, meaning it can't find the network, plus normally you hear the drive make sound when mounting, now its just quiet.

> Model: WDC WD30 EZRX-00MMMB0 (scsi)
Disk /dev/sdc: 3001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
you said:

> I would try to access the NAS administrator screen instead of trying this from Linux.

could you describe a step by step guide how to do this, I am going to windows a try to fix it from there.

all i am looking for i mount ext4, that is intact and rescue my files.

thanx again for your help

---

### Post by Michael_McKenney on 2014-10-07
Yellow is 100 Mbps.  Green would be Gigabit.  

[http://www.wdc.com/wdproducts/library/UM/ENG/4779-705058.pdf](http://www.wdc.com/wdproducts/library/UM/ENG/4779-705058.pdf)

Read the manual to access it.  I have never used one of these.  I use HP SANs at work and SAS RAID at home.

---

### Post by MartyBuntu on 2014-10-08
There is no software "fix" for mechanical failure.
That's what *backups* up for. Good luck with your attempts.

---

### Post by tgalati4 on 2014-10-08
So, going through this thread, a few things are clear.  A power outage can cause hardware damage.  That damage can be subtle and make data recovery difficult or impossible.

It appears that the NAS used a software EXT3 RAID for the firmware/operating system (about 1 GB worth), and the data is stored on the EXT4 partition (1.48 TB out of 2.7 TB).  

The debricking script did not work, perhaps because there is physical damage to the partition that holds the NAS operating system.  Unless you can modify the script to get around the damage, your NAS is probably toast.

So, moving to data recovery.

Plug the drive into a Linux machine and open a terminal.  Post the output of:

```
sudo fdisk -l
```

Once you find out what the data partition is called, you can start the recovery process.  To see the SMART parameters of the drive, do the following:

```
sudo smartctl -a /dev/sdg
```

Your drive is called something different than /dev/sdg.

How old is this NAS?  Green drives and NAS should not be used in the same sentence.

---

