---
title: "Formatting 2nd HD, Not all space is reported"
date: 2008-07-11
forum: Hardware
---

### Post by drhiii on 2008-07-11
G'day.

Installed an Ubuntu system a few months ago.  Have decided to tear down and reformat the 2nd drive, which I have already done.  fdisk reports correct storage size.  I deleted ay partitions, created one single partition, and ran mkfs.ext3.  

Everything appeared to be dandy.  But, when I df, it shows almost 1/3rd of the drive is used.  I have copied info that reflects the process below, but I am perplexed.  If I fdisk all partitions, I flatten the whole harddrive and reinit it, then format it.  But... I can't recover the full drive.

Help?  Thoughts?



Info:

Fdisk first-


Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c88f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       48641   390708801   83  Linux

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.



mkfs second-

root@tpl:/etc# mkfs.ext3 -b 4096 /dev/sdb1
mke2fs 1.40.2 (12-Jul-2007)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
48840704 inodes, 97677200 blocks
4883860 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
2981 block groups
32768 blocks per group, 32768 fragments per group
16384 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968

Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 23 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.



Reported space right after fdisk and mkfs -

root@tpl:/etc# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             357G  274G   65G  81% /
varrun                2.0G   92K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G  140K  2.0G   1% /dev
devshm                2.0G     0  2.0G   0% /dev/shm
/dev/sdb1             367G  195M  348G   1% /media/sdb


Am stumped???

---

### Post by kidders on 2008-07-13
Hi there,

As far as I can see, you're not losing as much space as you think ...[LIST]
[*]fdisk reports the capacity as 400,088,457,216 bytes (372.6 GiB).
[*]Then, it creates a partition very slightly smaller than that (a few megabytes out).
[*]Next, you create a filesystem 97,677,200 blocks (372.6 GiB) in size, with a reported capacity about 6.6% less than that.
[*]df then reports 195MiB (0.05%) as initially used.
[/LIST]
The total formatted space available for use is about 93.3% of the disk's unformatted capacity.

There isn't really anything unusual about those numbers ... they're typical of a standard single-filesystem disk configuration. I'm not sure where your figure of around 1/3 unavailable space came from though. Perhaps my sums are wrong?

---

### Post by matt$2 on 2008-07-13
Now the previous writer may be right, BUT
you HAVEN'T SAID THE EXPECTED SIZE OF THE DRIVE/

I'm wondering if it's meant to be a 500 Gig drive??? z! ???

thoughts

---

### Post by drhiii on 2008-07-13
It is a 400GB drive.  But, as I saw earlier, I was misreading the information, badly.  Not being a hardware geek, I am not 100% certain of the numbers, but I was misreading MBs for GBs in one case.  Duh, on my part.  The dive appears to be correctly formatted.... and I need to RTFS (Read The F---- Screen) more carefully....



> **matt$2 said:**
> Now the previous writer may be right, BUT
you HAVEN'T SAID THE EXPECTED SIZE OF THE DRIVE/

I'm wondering if it's meant to be a 500 Gig drive??? z! ???

thoughts

---

### Post by lukjad on 2008-07-13
Don't forget that when it says on a drive package that you can get 500Gs on it what it means is that it got 500,000,000,000 bytes on the drive. What they don't tell you is that you need 536,870,912,000 bytes to make 500Gs. So you loose some Gigs right off the bat.   ):
Lousy I know.

---

### Post by drhiii on 2008-07-13
Yes, this is right.  The 400GB drive I have as you state will under-report the size which is what it does here.

Tx for your response.  Main thing is I need to pay attention to the screen and not be in such a hurry.

tx


> **lukjad007 said:**
> Don't forget that when it says on a drive package that you can get 500Gs on it what it means is that it got 500,000,000,000 bytes on the drive. What they don't tell you is that you need 536,870,912,000 bytes to make 500Gs. So you loose some Gigs right off the bat.   ):
Lousy I know.

---

