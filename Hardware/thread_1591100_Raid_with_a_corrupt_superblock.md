---
title: "Raid with a corrupt superblock"
date: 2010-10-08
forum: Hardware
---

### Post by mrmaster on 2010-10-08
Hi Everyone,

I bought a Drobo which is basically an easy to use NAS. Because I am an utter idiot I decided to do a firmware upgrade on this perfectly fine working NAS which messed it up.

When I plug it in the pc it does detect it under /dev/sdb but gives me an error message telling me to check dmesg | tail. So I did and got the error bellow:

```
[ 466.675761] sd 6:0:0:0: [sdb] Very big device. Trying to use READ
CAPACITY(16).
[ 466.676889] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 466.676895] sdb:
[ 466.740015] Alternate GPT is invalid, using primary GPT.
[ 466.740027] sdb1
[ 466.743140] sd 6:0:0:0: [sdb] Very big device. Trying to use READ
CAPACITY(16).
[ 466.744372] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 466.744382] sd 6:0:0:0: [sdb] Attached SCSI disk
[ 467.831478] EXT3-fs: no journal found.
[ 522.972597] CE: hpet increasing min_delta_ns to 15000 nsec 
```

I ran fsck /dev/sdb and it was not able to fix the partition and gave me the error below:

```
mrmaster@Laptop:~$ sudo fsck /dev/sdb
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdb

The superblock could not be read or does not describe a correct ext2
filesystem. If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
e2fsck -b 8193 <device>
```

When I ran e2fsck -b 8193 /dev/sdb I received the exact same error as above appeared.

I'm not sure how to proceed from here and if possible I would love to get my data back.

Thanks,
Igor

---

### Post by psusi on 2010-10-08
sdb is the whole drive, you want to check some partition on the drive ( sdb1 maybe? ).

---

### Post by mrmaster on 2010-10-10
I tried running it on a single partition and it gave me the same message. I also tried 8193, 16384, and 32768 addresses. All gave me the same error as below.


```
mrmaster@Laptop:/dev$ sudo e2fsck -b 8193 /dev/sdc1
e2fsck 1.41.11 (14-Mar-2010)
e2fsck: Bad magic number in super-block while trying to open /dev/sdc1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

I think the superblock is corrupt but i am not able to restore it. I tried linux recovery tools like stellar phoenix but they were not able to do anything. 

The only reason why i still have hope is that when i lunch drobo utils it says that the drobo is 77 percent full and that is what the lights on the machine show. 

Thanks

---

### Post by psusi on 2010-10-10
Then it isn't an ext2 filesystem.

---

### Post by mrmaster on 2010-10-10
It is an ext3 filesystem. I also tried fsck.ext3 -b <with multiple block locations> and all gave me the same error as i showed below with e2fsck

---

### Post by S.R on 2010-10-10
Any chance of going back to the old firmware?

---

### Post by mrmaster on 2010-10-10
I wish I knew what old firmware I had. I know i bought the device around November of 08. I can try to look for that firmware version but in the meantime would love to see if anyone else has any ideas.

---

### Post by mrmaster on 2010-10-10
while reading through the man pages of e2fsck i found a command mke2fs that with -n option is supposed to give you all of the locations that the systems used to back up superblocks. I ran it and it gave me the options below. Now i will be trying them out with sudo e2fsk -b <super_block_locations> /dev/sdc1 


```
mrmaster@Laptop:/dev$ sudo mke2fs -n /dev/sdc1
mke2fs 1.41.11 (14-Mar-2010)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
536870912 inodes, 2147483639 blocks
107374181 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
65536 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
	102400000, 214990848, 512000000, 550731776, 644972544, 1934917632

```

---

### Post by psusi on 2010-10-10
Why did you switch from sdb to sdc?  Either it isn't an ext filesystem, or you are running it on the wrong drive.

---

### Post by mrmaster on 2010-10-10
Honestly I have no idea why it switched. Originally I had it on sdb then I ran Stellar Phoenix(on windows machine) program by recommendation of Drobo support but it was not able to detect any filesystems or files. When I plugged it back into my linux box the device showed up under sdc. 


ARGGGGGGGGGG
---------- 2 minutes after writing the message up top.

I created a support ticket with drobo staff asking for a link to firmware when i bought the device. While trying to write down the serial number the power must have slipped and the box turned off. I put the power plug back in, ran drobom list command and it shows up now under sdb. 

ps. before i did an ls on /dev and there was no sdb. i'm not trying to make you run in circles here :(

---

