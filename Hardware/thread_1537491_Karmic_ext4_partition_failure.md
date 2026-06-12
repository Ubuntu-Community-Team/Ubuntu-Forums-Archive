---
title: "Karmic ext4 partition failure"
date: 2010-07-23
forum: Hardware
---

### Post by sirpixalot on 2010-07-23
hi,

i have a HDD with multiple partitions. on one partition, i have intrepid using ext3. on another, i have karmic using ext4 (i actually have 2 partitions for karmic -- one for /root and another for /home).

i have used the intrepid ext3 partition for 1.5 years without a single glitch.

however, over the past 2 months, i have had my karmic ext4 partition fail on me several times. on a couple of these occasions, i have been able to go into Live CD and manually run fsck to recover the state.

however, on a couple of other occasions, i have found the same problem that i currently face. when i run fsck from Live CD, i get the following response:

 # fsck -a /dev/sda3
fsck from util-linux-ng 2.17.2
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda3
Could this be a zero-length partition?

also note that fdisk is not able to read the partition:
# fdisk /dev/sda
Unable to read /dev/sda

however, from Live CD's "Disk Utility" (under System->Administration), i can see all
of my partitions on the disk listed.

dmesg provides a series of the following:
[ 1954.498828] sd 2:0:0:0: [sda] Unhandled error code
[ 1954.498832] sd 2:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 1954.498838] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[ 1954.498852] end_request: I/O error, dev sda, sector 0

when i try booting into karmic's recovery mode from grub, fsck runs and then i get the following:

moutall: fsck /home [381] terminated with status 4
mountall: Filesystem has errors: /home

finally, from the Live CD, i listed the superblocks using:

 # mke2fs -n /dev/sda3
mke2fs 1.41.11 (14-Mar-2010)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
25640960 inodes, 102539008 blocks
5126950 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
3130 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
    4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
    102400000

i then tried fsck on these individual superblocks. i get two different types of error messages depending on which superblock i supply as a parameter:

# fsck -b 32768 /dev/sda3
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda3
Could this be a zero-length partition?

# fsck -b 11239424 /dev/sda3
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: Invalid argument while trying to open /dev/sda3

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

to reiterate, my intrepid ext3 partition on the same HDD works without problems. it is only the karmic ext4 partition on which i am having these issues.

any help would be greatly appreciated.

thank you.

---

