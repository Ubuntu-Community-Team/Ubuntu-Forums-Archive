---
title: "HDD won't mount: &quot;can't read superblock&quot; and &quot;bad magic number in superblock&quot;"
date: 2018-06-05
forum: Hardware
---

### Post by zunou on 2018-06-05
I have no idea what happened. One day my computer was fine, I usually leave it suspended, rarely leave it running over night, or I turn it off. The next day, my HDD wouldn't mount; I use this for all my files, my OS is on my SSD. My HDD has never automatically mounted after I built and partitioned it and all, and I always told myself I would do it some other time. I have to manually go into Dolphin and click on it to mount it. This time I get this full error:

```

An error occurred while accessing '1.8 TiB Hard Drive', the system responded: The requested operation has failed: Error mounting /dev/sda1 at /media/smitty/4e288f7f-24d6-4755-954d-8414c5d95b17: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sda1" "/media/smitty/4e288f7f-24d6-4755-954d-8414c5d95b17"' exited with non-zero exit status 32: mount: /dev/sda1: can't read superblock
```

I honestly feel like this happened to me a while back and my friend fixed it for me, but I don't know how. I have run fsck and this is what I get for the drive that won't mount:

```
Disk /dev/sda: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x795837c1

Device Boot Start      End   Sectors[ Size Id Type 
/dev/sda1        2048 3907028991 3907026944  1.8T 83 Linux

```

I found some various support sites and one suggested to run fsck -y /dev/sda so I did and this is what I get:

```
e2fsck 1.43.4 (31-Jan-2017)
ext2fs_open2: Bad magic number in super-block
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

Found a dos partition table in /dev/sda


```

Running e2fsck does not work. It spits out the same error. (admittedly I have not tried all the superblocks that are listed when I run mke2fs -n /dev/sda ... I figured maybe I should consult someone more knowledgeable.) The only thing that struck me was when running mke2fs it responds with "Found a dos partition table in /dev/sda"

Please help???

---

### Post by QIII on 2018-06-06
Hello!

Please use code tags instead of quote tags when posting commands and their results.  That preserves terminal formatting and makes you post easier to read.

Please also use the default font and colors unless there is a clear need to draw attention to a particular point in your post.

Thanks!

---

### Post by leunam12 on 2018-06-06
Time for a new hard drive? Check the S.M.A.R.T. data to see if the drive is corrupt.

---

### Post by slickymaster on 2018-06-06
Thread moved to **Hardware** for a better fit

---

### Post by zunou on 2018-06-06
Thank you forum admins, I'm very much a noob, but I'll note for the future.

I solved my issue. Every time I was running commands and using fsck I was calling the whole drive ( /dev/sda ) rather than just the partition ( /dev/sda1 ). I ran this code:

```
fsck -y /dev/sda1
```

and my hard drive mounted and the file system is repaired.

I guess for the reference of others in case they were as stuck on it as I was, this is the output I got once I ran fsck properly:

```
[FONT=monospace]
fsck from util-linux 2.29
e2fsck 1.43.4 (31-Jan-2017)
/dev/sda1: recovering journal
JBD2: Invalid checksum recovering block 10 in log
Journal checksum error found in /dev/sda1
/dev/sda1 was not cleanly unmounted, check forced.
Pass 1: Checking inodes, blocks, and sizes
Inode 48366584 extent tree (at level 1) could be narrower.  Fix? yes

Pass 1E: Optimizing extent trees
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Free blocks count wrong (464135213, counted=461225698).
Fix? yes

Free inodes count wrong (122086369, counted=122082817).
Fix? yes


/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda1: 18943/122101760 files (3.5% non-contiguous), 27152670/488378368 blocks

[/FONT]
```

---

### Post by bubbchubb on 2019-02-20
[SIZE=4]Thanks so much, guys for helping me solve a problem I've been working on for 3 to 4 days!


Update: Oh, well. I thought it was solved. Back to churning out search keywords for duckduckgo.[/SIZE]

---

