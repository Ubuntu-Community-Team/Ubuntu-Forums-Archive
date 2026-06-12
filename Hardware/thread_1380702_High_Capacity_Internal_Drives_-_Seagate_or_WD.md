---
title: "High Capacity Internal Drives - Seagate or WD?"
date: 2010-01-14
forum: Hardware
---

### Post by shreepads on 2010-01-14
Using Hardy Heron on an Intel DG33FB board

Have narrowed down to two options for additional internal drive.
- Seagate Barracuda 7200.11, 1.5 TB, 3 Gbps SATA, 32 MB cache
- WD Caviar Green, 1.5 TB, 3 Gbps SATA, 64/ 32 MB cache

Which would be better?
- Have read a posts re problems with Seagate Barracuda 7200.11, not sure if that is resolved in the latest production batches, don't want to mess around with firmware updates...
- Also read posts titled "Western Digital Does Not Support Linux" so confused...

---

### Post by Dark_Stang on 2010-01-14
I'm running a western digital drive in my laptop right now and it works fine. I tend to stay away from the WD "Green" drives because they like to spool down a lot. I'd recommend a WD Black edition or the Segate drive.

---

### Post by shreepads on 2010-01-14
> **Dark_Stang said:**
>  I tend to stay away from the WD "Green" drives because they like to spool down a lot. I'd recommend a WD Black edition or the Segate drive. Thanks, though as per WD site no 1.5 TB in Caviar Black

---

### Post by Dark_Stang on 2010-01-14
> **shreepads said:**
> Thanks, though as per WD site no 1.5 TB in Caviar Black
So do 2x1TB and RAID them. ;)

---

### Post by shreepads on 2010-01-15
> **Dark_Stang said:**
> So do 2x1TB and RAID them. ;)

He he, but seriously that's an interesting idea, the DG33FB board has 4 SATA connectors so I have a couple to spare and the cabinet has space as well...

Plus planning to plunk all my data on this new one and put an ext3 driver on the Win XP partition. So would be nice to RAID it all...

Problem being have never done this or RAID before so a little uncertain of the pros/ cons and the procedure involved and whether it will be available from Win XP via ext3 driver.

---

### Post by Dark_Stang on 2010-01-15
Well, you'd be doing a RAID 0 setup for this so the 2X1TB drives look like a single 2TB drive. The pro is fairly obvious. 2 drives that appear to be one. Write speeds are generally increased compared to 1 drie. Read speeds can be slightly faster but are generally comparable.

The biggest drawback is pretty obvious too. If 1 drive fails, you lose everything. Since a file is almost always split between the discs (not evenly) if one drive crashes then everything is lost.

Now if you wanted to buy 3 drives you could do a RAID 5 setup. In a RAID 5 setup each part of a file is coppied between 2 discs. This way if one drive fails, you don't lose everything. Also this will make 3X1TB drives look like one 2TB volume. Overall performance is increased with this as well.

As far as the ext3 driver working with a RAID setup, it should.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

---

### Post by cascade9 on 2010-01-16
> **shreepads said:**
> Using Hardy Heron on an Intel DG33FB board

Have narrowed down to two options for additional internal drive.
- Seagate Barracuda 7200.11, 1.5 TB, 3 Gbps SATA, 32 MB cache
- WD Caviar Green, 1.5 TB, 3 Gbps SATA, 64/ 32 MB cache

Which would be better?
- Have read a posts re problems with Seagate Barracuda 7200.11, not sure if that is resolved in the latest production batches, don't want to mess around with firmware updates...
- Also read posts titled "Western Digital Does Not Support Linux" so confused...

It really depends on what you call 'better'. What is better, faster, more reliable, quieter, lower power consumption? 

I wouldnt get the seagate myself. I've used a few, and seen tests on the 7200.11, and they were....unimpressive. 

Western digital internal drives work fine with linux (I've used a lot of WD drives with linux, everything from old 40GB 8MB cache PATA drives through to 1TB WD 'caviar black' + 'blue' and GP models) drives  There might be some issues with the external drives. 

> **Dark_Stang said:**
> I'm running a western digital drive in my laptop right now and it works fine. I tend to stay away from the WD "Green" drives because they like to spool down a lot. I'd recommend a WD Black edition or the Segate drive.

That is either your power saving settings or inteliparrk. I'm running a 1TB WD GP drive and I'm having no problems with intlipark at all, and my power saving settings arent set that low. 

0 problems with that for me, anyway. 

> **Dark_Stang said:**
> Well, you'd be doing a RAID 0 setup for this so the 2X1TB drives look like a single 2TB drive. The pro is fairly obvious. 2 drives that appear to be one. Write speeds are generally increased compared to 1 drie. Read speeds can be slightly faster but are generally comparable.

The biggest drawback is pretty obvious too. If 1 drive fails, you lose everything. Since a file is almost always split between the discs (not evenly) if one drive crashes then everything is lost.

Now if you wanted to buy 3 drives you could do a RAID 5 setup. In a RAID 5 setup each part of a file is coppied between 2 discs. This way if one drive fails, you don't lose everything. Also this will make 3X1TB drives look like one 2TB volume. Overall performance is increased with this as well.

As far as the ext3 driver working with a RAID setup, it should.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

I really wouldnt do RAID 0. Srue, RAID works, but the data loss with a single drive death isnt worth whatever speed gains you get. A better option is 1.5TB and a SSD. It might cost a bit more than 2x1TB caviar black, but the SSD would be faster than RAID 0. Put /root and /home onto the SSD, and then store your files in the 1.5TB WD GP drive. 

RAID 5 is a nicer solution..but IMO, that is not such a great idea as well. 

Why? More of a stuff around, and also not worth it for the cost now.

---

### Post by Dark_Stang on 2010-01-16
> **cascade9 said:**
> I'm running a 1TB WD GP drive and I'm having no problems with intlipark at all, and my power saving settings arent set that low. 

0 problems with that for me, anyway. 
The problem with intellipark is that the drive will spin down to 5400 RPM if you stop using it for a few seconds. Thus hurting overall performance a little.


> **cascade9 said:**
> but the SSD would be faster than RAID 0. Put /root and /home onto the SSD, and then store your files in the 1.5TB WD GP drive. 
The WD Black drives have read speeds over 100mbps and you can pick one up a 1TB for about $100. However a 128gig SSD may have read speeds up to about 140+mbps, but you're going to pay $300 for it. So uh... yeah.

---

### Post by cascade9 on 2010-01-17
> **Dark_Stang said:**
> The problem with intellipark is that the drive will spin down to 5400 RPM if you stop using it for a few seconds. Thus hurting overall performance a little.

You've got park and power mixed up- 

> IntelliPower 
A fine-tuned balance of spin speed, transfer rate, and caching algorithms designed to deliver both significant power savings and solid performance. For each drive model, WD may use a different, invariable RPM.  
      
Drives featuring WD GreenPower Technology consume less current during start up allowing more drives to spin up simultaneously resulting in faster system readiness which is a big plus for enterprise customers.       
        IntelliPark 
Delivers lower power consumption by automatically unloading recording heads during idle to reduce aerodynamic drag, and disengages read/write channel electronics.

[http://www.wdc.com/en/products/greenpower/technology.asp](http://www.wdc.com/en/products/greenpower/technology.asp)

Before you start thinking that I did the same thing (got park and power confused)...I've never seen any evidence that the GP drives can alter spin speed. They appear to be pure 5400 RPM drives (but very quick ones). Its not like the GP drivers are really slow- 

[http://www.xbitlabs.com/articles/storage/display/1tb-14hdd-roundup.html](http://www.xbitlabs.com/articles/storage/display/1tb-14hdd-roundup.html)

> **Dark_Stang said:**
> 
The WD Black drives have read speeds over 100mbps and you can pick one up a 1TB for about $100. However a 128gig SSD may have read speeds up to about 140+mbps, but you're going to pay $300 for it. So uh... yeah.

You dont need a 128GB SSD if you are running a nice, big traditional HDD. 40 GB should do fine. You can get a 40GB Intel X25-V for $130 (and a few other brands/sizes in a similar prices range).Much faster than a traditional hdd (apart from sequential write). 

[http://www.newegg.com/Product/Product.aspx?Item=N82E16820167025](http://www.newegg.com/Product/Product.aspx?Item=N82E16820167025)
[http://www.myce.com/review/intel-x25-m-ssd-review-19929/Benchmarks-4/](http://www.myce.com/review/intel-x25-m-ssd-review-19929/Benchmarks-4/)

---

### Post by shreepads on 2010-01-18
> **Dark_Stang said:**
> Well, you'd be doing a RAID 0 setup for this so the 2X1TB drives look like a single 2TB drive. The pro is fairly obvious. 2 drives that appear to be one. Write speeds are generally increased compared to 1 drie. Read speeds can be slightly faster but are generally comparable.
As far as the ext3 driver working with a RAID setup, it should.

[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

Thanks! After reading thru the links there and other RAID guides I guess this is not the thing for me, reasons explained further below.

> **cascade9 said:**
> It really depends on what you call 'better'. What is better, faster, more reliable, quieter, lower power consumption? 


You're right I should have given more details, sorry! I'm basically looking for additional storage where I can store all the large files (read videos, photos, pictures) that are currently scattered over different HDD partitions (on one 250GB Seagate Barracuda drive) and several external HDDs and pen drives.

Also to take a backup of all documents on the hard drive.

So in descreasing order of importance:
- Reliability
- Data transfer rate
- Power consumption
- Noise

Re RAID, basic benefit, i.e. redundancy, is not what I need, what I need is storage of large files and backup of key documents. Data transfer rate is important as far as streaming videos is concerned where I think the standard SATA 3Gbps seems quite good!

And I could do without the additional complexity involved in building and maintaining it. After all am only using as a home desktop!

Thanks guys, will do a local hunt for both drives, buy, plug in and feedback results!

---

### Post by ShakeyJake on 2010-01-18
RAID 0 != RAID. The 'R' in RAID stands for redundant, and RAID 0  has no redundancy. You're quite right (IMHO) to decide against it. Let us know how things get on, but there certainly arent any reasons to decide against the WD Greens.

I had the exact same dilemma as you and I arrived at the solution of a nice, small and extremely fast SSD for the OS and all of it's files. My / partition is on a 32GB OCZ Vertex Turbo. My /home is on a 1.5TB WD15EADS. That's the newest green drive with 32MB cache (there is also now a 64MB version).

---

### Post by cascade9 on 2010-01-20
> **shreepads said:**
> You're right I should have given more details, sorry! I'm basically looking for additional storage where I can store all the large files (read videos, photos, pictures) that are currently scattered over different HDD partitions (on one 250GB Seagate Barracuda drive) and several external HDDs and pen drives.

Also to take a backup of all documents on the hard drive.

So in descreasing order of importance:
- Reliability
- Data transfer rate
- Power consumption
- Noise

Re RAID, basic benefit, i.e. redundancy, is not what I need, what I need is storage of large files and backup of key documents. Data transfer rate is important as far as streaming videos is concerned where I think the standard SATA 3Gbps seems quite good!

And I could do without the additional complexity involved in building and maintaining it. After all am only using as a home desktop!

I'd use 1xSSD, 1x1.5TB (or 2TB) internal storage, and get a 2nd 1.5TB drive for external backups. No RAID is less hassle, with similar transfer speeds, lower power consumption and noise. 

If you get an eSATA (external SATA) for your backup, it should transfer the files as fast as an internal drive (non of this 'gah USB 2.0 is slow' business).   

Yeah, SATA 3g/bit is plenty fast. Its faster than any single traditional HDD so far. Not that you need massive amounts of speed for streaming videos, I've watched streamed video from a machine with a UDMA/66 drive (and the fastest UDMA 66 drive is probably about half as fast as any modern SATA 2 HDD).

---

### Post by shreepads on 2010-01-23
Well folks I got the WD Caviar Green 1.5 TB one, installed and recognized by the BIOS no problems...

Following the instructions at this link to add and ran into a few problems: [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

Firstly the disk seems to be recognised OK. Output from lshw
```
sudo lshw -C disk

...

  *-disk
       description: ATA Disk
       product: WDC WD15EADS-00S
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdb
       version: 04.0
       serial: WD-WCAVY1005937
       size: 1397GiB (1500GB)
       configuration: ansiversion=5

```

Attempted to add partition via GParted returned a 'Partition cannot have -1 sectors" error. A bit of hunting turned up that GParted (in Hardy) is unable to handle more than 1TB disk size.

So went with the command line using fdisk
```
 sudo fdisk /dev/sdb

...

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-182401, default 1): 1
Last cylinder or +size or +sizeM or +sizeK (1-182401, default 182401): 
Using default value 182401

Command (m for help): p

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      182401  1465136001   83  Linux

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.



```

Now when I try to format it to ext3 using mkfs I get an error as follows:
```
sudo mkfs -t ext3 -cv /dev/sdb1
mke2fs 1.40.8 (13-Mar-2008)
mkfs.ext3: invalid blocks count - /dev/sdb1

```

Any ideas??

---

### Post by shreepads on 2010-01-23
OK dumb mistake on my part the mkfs command should read

```
sudo mkfs -t ext3 **-c -v** /dev/sdb1

mke2fs 1.40.8 (13-Mar-2008)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
91578368 inodes, 366284000 blocks
18314200 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
11179 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
	102400000, 214990848

Running command: badblocks -b 4096 -X -s /dev/sdb1 366283999


```

Gonna be a while methinks!!

EDIT: badblocks ran for 4 hrs!! Rest of the stuff done in a few minutes...

```

Running command: badblocks -b 4096 -X -s /dev/sdb1 366283999
Checking for bad blocks (read-only test): done                                
Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 33 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.


```

---

