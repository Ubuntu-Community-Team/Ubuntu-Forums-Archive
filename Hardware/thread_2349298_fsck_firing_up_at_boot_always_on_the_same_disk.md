---
title: "fsck firing up at boot always on the same disk"
date: 2017-01-13
forum: Hardware
---

### Post by marino3 on 2017-01-13
Hello,

I'm baffled. Since I updated to Xenial some weeks ago, fsck will check the same 160 Go data disk at boot again and again for more than 10 minutes. The fstab is correct, and should not trigger this.

As stated on this page ([https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1619753](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1619753)), I've modifed /etc/default/grub to include the following line to get a log in /run/initramfs/fsck.log : ```
GRUB_CMDLINE_LINUX="fsck.mode=force fsck.repair=yes"
```

Here is the log :

```
Log of fsck -C -f -y -V -t ext4 /dev/sdb6 
Fri Jan 13 06:51:15 2017

fsck from util-linux 2.27.1
[/sbin/fsck.ext4 (1) -- /dev/sdb6] fsck.ext4 -f -y -C0 /dev/sdb6 
e2fsck 1.42.13 (17-May-2015)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sdb6: 1045043/3440640 files (0.3% non-contiguous), 8979728/13736448 blocks

Fri Jan 1
```

0.3% non-contiguous... I've seen worse.
I've also used "SMART Data & Self-tests" of the disk utility, but nothing worrisome showed up.

Is this disk slowly dying ? I've tried massive data transfer on it without any problem. All the disks on the machine are set with tune2fs to get checked every 30 mounts.

Best regards,

MC

---

### Post by TheFu on 2017-01-14
So you are forcing fsck at every boot and wonder why fsck runs at every boot?  I'm confused.

The easy way to force an fsck just once is to touch a /forcefsck file in the root directory of the partition.
```
sudo touch /forcefsck
```

Sometimes poor performance is due to a controller issue or sector misalignment.  I have a USB3 dock that is behaving badly, but moving the HDD into another dock and it performs great.

---

### Post by Bashing-om on 2017-01-14
> **TheFu said:**
> So you are forcing fsck at every boot and wonder why fsck runs at every boot?  I'm confused.

The easy way to force an fsck just once is to touch a /forcefsck file in the root directory of the partition.
```
sudo touch /forcefsck
```

Sometimes poor performance is due to a controller issue or sector misalignment.  I have a USB3 dock that is behaving badly, but moving the HDD into another dock and it performance great.

But ; With the advent of systemd - the procedure is changed, systemd does not honor /forcefsck .
see: [https://www.freedesktop.org/software/systemd/man/systemd-fsck@.service.html](https://www.freedesktop.org/software/systemd/man/systemd-fsck@.service.html)

[INDENT][INDENT]just my bit to try and help
[/INDENT][/INDENT]

---

### Post by TheFu on 2017-01-14
Thanks for that.  

Yet another change from systemd that drops the old way for something different.  The ultimate in NIH syndrome.  
Think I'll stay on 14.04 for a few more years. ;)

---

### Post by marino3 on 2017-01-14
I altered GRUB just to get a fsck.log. I noticed the fsck fired up twice during boot time, on the same 160 Go data disk.

Without this modification, the fsck will fire up once anyway.

It's a SATA, not an USB, so can't easily change its connection.

Best regards,

---

### Post by QLee on 2017-01-16
> **TheFu said:**
> Yet another change from systemd that drops the old way for something different.  The ultimate in NIH syndrome.  
Think I'll stay on 14.04 for a few more years. ;)

TheFu, just so you will know, What Bashing-om wrote isn't correct. Systemd in 16.04 does still honor the empty forcefsck file in the root of the file system (does the check at boot and deletes the file), so you could still use it as a way to check the root of your filesystem during boot before it is mounted. I'm guessing you are acoustomed to doing that on your servers and if I remember correctly, I've seen you state that you have a 16.04 test bed on which you can verify. 

Maybe it will be deprecated at some point in the future but I couldn't find that stated anywhere.

marino3, is it always sda6 that gets checked? Do you have any reason to suspect corruption in sda6? Does it change behaviour if you set the sixth field in the fstab listing of sda6 to 0? That should make the system not check, similar to the way it doesn't check the swap. However, setting it to not check might effectively mask a corruption problem.

---

### Post by marino3 on 2017-01-21
Yes, zeroing the sixth field will make the symptom disappear, but I guess there's something amiss. I've check many ways to trigger a fsck at boot, but none seems to be activated.

I'm still searching. If I find a clue, I'll post it here.

Best regards,

MC

---

### Post by marino3 on 2017-02-05
Still looking for an answer.

Here is the first part of the results for a "sudo dumpe2fs /dev/sdb6"  :

```
Filesystem volume name:   <none>
Last mounted on:          /
Filesystem UUID:          a2ce10da-4ded-40e4-82ca-4e4a5766a907
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    user_xattr acl
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              3440640
Block count:              13736448
Reserved block count:     686822
Free blocks:              3105888
Free inodes:              2351921
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      1020
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Flex block group size:    16
Filesystem created:       Mon Nov  2 12:18:56 2015
Last mount time:          Sat Feb  4 14:58:17 2017
Last write time:          Sat Feb  4 15:55:45 2017
Mount count:              1
Maximum mount count:      30
Last checked:             Sat Feb  4 15:55:45 2017
Check interval:           950400 (1 week, 4 days)
Next check after:         Wed Feb 15 15:55:45 2017
Lifetime writes:          831 GB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:              256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
First orphan inode:       1187573
Default directory hash:   half_md4
Directory Hash Seed:      a34e9d95-90f5-4ada-8399-366d547ab205
Journal backup:           inode blocks
Journal features:         journal_incompat_revoke
Journal size:             128M
Journal length:           32768
Journal sequence:         0x00cb1310
Journal start:            28612
```

I guess I got it wrong... sdb6 is the linux system partition and not the data disk I thought it was ; it is obvious through a "sudo fdisk -l" :

```
Disk /dev/sdb: 149,1 GiB, 160041885696 bytes, 312581808 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00003b1d

Device     Boot     Start       End   Sectors  Size Id Type
/dev/sdb1  *         2048    206847    204800  100M  7 HPFS/NTFS/exFAT
/dev/sdb2          206848 199544758 199337911 95,1G  7 HPFS/NTFS/exFAT
/dev/sdb3       199544830 312580095 113035266 53,9G  5 Extended
/dev/sdb5       309436416 312580095   3143680  1,5G 82 Linux swap / Solaris
/dev/sdb6       199544832 309436415 109891584 52,4G 83 Linux

Partition table entries are not in disk order.
```

Here are the results of a "sudo tune2fs -l /dev/sdb" :

```
tune2fs 1.42.13 (17-May-2015)
tune2fs: Bad magic number in super-block while trying to open /dev/sdb
Couldn't find valid filesystem superblock.
```

Ok, superblock problem.

MC

---

### Post by marino3 on 2017-03-04
Well, it was not a superblock issue.

I got rid of the two NTFS partitions, reformated their space to a new ext4 partition, and voilà.

---

### Post by Bashing-om on 2017-03-04
marino3; Outstanding !

You do good work . Pleased you came back and provided the solution.
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Just goes to prove:
[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

