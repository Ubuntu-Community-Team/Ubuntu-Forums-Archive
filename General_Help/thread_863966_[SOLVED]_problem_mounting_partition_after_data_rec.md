---
title: "[SOLVED] problem mounting partition after data recovery"
date: 2008-07-19
forum: General Help
---

### Post by pooyaplus on 2008-07-19
Hi, 
I had problems with a faulty hard disk, after data recovery on a new HD it does not mount the ex3 filesystem with this error message:
```
mount: wrong fs type, bad option, bad superblock on dev/sdb1, missing codepage or other helper program, or other errors ........
```

The [COLOR="Red"]dmesg[/COLOR] gives me this:
```

[  304.704000] journal_bmap: journal block not found at offset 0 on sdb1
[  304.704000] journal_init_inode: Cannnot locate journal superblock
[  304.704000] EXT3-fs: Could not load journal inode

```

I did [COLOR="Red"]cat /etc/mtab[/COLOR] to make sure that it is not mounted on somewhere else:
```

/dev/sda9 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-15-generic/volatile tmpfs rw 0 0
/dev/sda8 /home reiserfs rw 0 0
/dev/sda1 /media/sda1 fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0
/dev/sda5 /media/sda5 fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0
/dev/sda6 /media/sda6 fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0
/dev/sda7 /media/sda7 ext3 rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0

```
 The first lines shows the error, do not know what is wrong with it!

And here is the output of the [COLOR="Red"]vol_id /dev/sdb1[/COLOR]:
```

ID_FS_USAGE=filesystem
ID_FS_TYPE=ext3
ID_FS_VERSION=1.0
ID_FS_UUID=4fce5b0b-5ef2-4e58-9aaf-28fa5575e67c
ID_FS_UUID_ENC=4fce5b0b-5ef2-4e58-9aaf-28fa5575e67c
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=

```

Any helps would be greatly appreciated.

---

### Post by pooyaplus on 2008-07-19
Bump  ](*,)

---

### Post by pooyaplus on 2008-07-19
Bump... Any body?

---

### Post by pooyaplus on 2008-07-19
:confused:

---

### Post by logos34 on 2008-07-19
why are you trying to mount a partition on a faulty drive?  You've recovered the data, so I don't understand...maybe I've misunderstood...

---

### Post by pooyaplus on 2008-07-19
Hi,
Thanks for the reply. But it is not a faulty HD. I have recovered them on a new hard disk. But the problem is that I can not have access to the data!! Funny (sad) but true. The only way I can see them is by a windows app called Diskintervals that browses the ext3/ext2 partition in windows.

---

### Post by logos34 on 2008-07-19
Let me get this straight: you copied the files and folders from the partition on the faulty drive to an ext3 partition (sdb1?) on the new drive, but get errors mounting it, and the only way to access the files is by 'DiskIntervals' app?  Or did you clone/make an **image** of the whole partition and copy it to sdb1?

---

### Post by pooyaplus on 2008-07-19
Actually the recovery process has been done by someone else and I do not exactly what has happened in between. But here is the whole story:
The data was on an old ext3 partitioned HD, and it got serious bad sectors after a power cut. Data was recovered on a new HD.

Ubuntu can not mount the partition but Diskintervals in windows knows it as an ext3 file system and shows the data.

The question is why I can not mount it here in ubuntu and how I can do it?

Thanks.

---

### Post by unutbu on 2008-07-19
This is just a guess, but perhaps sdb1 is an ext2 partition instead of ext3. The only difference between ext2 and ext3 is the lack of a journal in ext2. 
dmesg complains, "journal_bmap: journal block not found at offset 0 on sdb1" which is consistent with this guess.

Perhaps try opening a terminal and typing

```
sudo mkdir /media/sdb1
sudo mount /dev/sdb1 /media/sdb1
```

and if that does not work

```
sudo mount -t ext2 /dev/sdb1 /media/sdb1
```

If it works, the next step would be to edit /etc/fstab to make the change permanent. If it doesn't work, it might be helpful to take a look at /etc/fstab. So, in any case, please post
```

cat /etc/fstab
```

---

### Post by pooyaplus on 2008-07-19
> **unutbu said:**
> This is just a guess, but perhaps sdb1 is an ext2 partition instead of ext3. The only difference between ext2 and ext3 is the lack of a journal in ext2. 
dmesg complains, "journal_bmap: journal block not found at offset 0 on sdb1" which is consistent with this guess.

Perhaps try opening a terminal and typing

```
sudo mkdir /media/sdb1
sudo mount /dev/sdb1 /media/sdb1
```

and if that does not work

```
sudo mount -t ext2 /dev/sdb1 /media/sdb1
```

If it works, the next step would be to edit /etc/fstab to make the change permanent. If it doesn't work, it might be helpful to take a look at /etc/fstab. So, in any case, please post
```

cat /etc/fstab
```
Hey, nice shot buddy. Thanks that worked.:guitar:

But there is one more thing. How I can set it permanently as you pointed out? I have connected the hard disk to another PC running ubuntu. Can I keep the ext2 (!) partition and have a clean new install of ubuntu on the rest of the hard space? 

Here is the fstab:

```


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda9
UUID=d271ff7f-ed90-4a84-9d85-92771e89054b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda8
UUID=7815bda6-3732-44fd-87b7-8302a72394c9 /home           reiserfs defaults        0       2
# /dev/sda1
UUID=245C76165C75E2CA /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=9AB41CCBB41CABAF /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=D228234928232BC3 /media/sda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=37db42bc-f81b-4c51-a814-3f059df3ae6c /media/sda7     ext3    defaults        0       2
# /dev/sda10
UUID=68365cb6-6524-463b-9ac4-62a69a8d94c7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

Thanks again.

---

### Post by logos34 on 2008-07-19
> **unutbu said:**
> This is just a guess, but **perhaps sdb1 is an ext2 partition instead of ext3.** The only difference between ext2 and ext3 is the lack of a journal in ext2. 
dmesg complains,** "journal_bmap: journal block not found at offset 0 on sdb1" which is consistent with this guess.**


Nice job!  I'll have to remember that in the future.

---

### Post by pooyaplus on 2008-07-19
One more thing guys, the fstab in the first line says:

```

# /dev/sda9
UUID=d271ff7f-ed90-4a84-9d85-92771e89054b /    ext3 defaults,errors=remount-ro 0       1

```

It still sees the partition as ext3 (!) :confused: 

How can I fix this?

---

### Post by unutbu on 2008-07-19
sda9 is your root partition. it probably is ext3 so there is nothing to fix there.

However, it's a good idea to make sdb1 an ext3 partition. The journal may save you if you ever have a power outage or abruptly shut off the computer.
```

sudo umount /dev/sdb1                     # unmount sdb1
tune2fs -j /dev/sdb1                      # add a journal to sdb1. Now sdb1 is ext3
sudo mount -t ext3 /dev/sdb1 /media/sdb1  # test that sdb1 is ext3
```
Stop and report back if you encounter any errors.

To make the change permanent:
Run
```

blkid /dev/sdb1
```

This should return a line similar to this:
```
/dev/sdb1: **UUID="03a507ee-cdac-4bd9-b438-eccd616b66ed"** SEC_TYPE="ext2" TYPE="ext3" 
```
Notice the UUID="..." part. We'll use that in /etc/fstab:

```
gksu gedit /etc/fstab
```

Add the lines
```

# /dev/sdb1
UUID=03a507ee-cdac-4bd9-b438-eccd616b66ed /media/sdb1 ext3 defaults 0 2
```

changing "03a507ee-cdac-4bd9-b438-eccd616b66ed" to your real UUID. Next time you boot up sdb1 should be mounted at /media/sdb1.

---

### Post by pooyaplus on 2008-07-19
Thanks, I will check that and let you know. My major problem is solved, the partition is mounted. 

I will report back the last issue; and then will mark the thread as solved. Thanks again for the help.:KS

---

### Post by pooyaplus on 2008-07-19
> **unutbu said:**
> sda9 is your root partition. it probably is ext3 so there is nothing to fix there.

However, it's a good idea to make sdb1 an ext3 partition. The journal may save you if you ever have a power outage or abruptly shut off the computer.
```

sudo umount /dev/sdb1                     # unmount sdb1
tune2fs -j /dev/sdb1                      # add a journal to sdb1. Now sdb1 is ext3


tune2fs -j /dev/sdb1 says:
[CODE]
tune2fs 1.40.2 (12-Jul-2007)
The filesystem already has a journal.

```
This means that sdb1 is already ext3 but can not be mounted with its native journal. Correct me if I am wrong. Right?

---

### Post by unutbu on 2008-07-19
Hm. I'm not sure why it is saying that there already exists a journal. Please post
```

tune2fs -l /dev/sdb1
```

You might be right -- perhaps the Windows recovery program did create a journal, but it is somehow incompatible with linux's idea of a journal? I really don't know.

Do you have any extra space where you can backup your sdb1 data? The easiest way to solve this problem may be to back up, then destroy the partition using GParted, create a new ext3 partition, then copy the data back...

Or we could try editing /etc/fstab first as described in post #13 and just see what happens...

---

### Post by pooyaplus on 2008-07-19
Aaaa, I think I can find another hard disk to make a backup copy and repartition the current disk. 
I will let you know if I could find that then we can forget about the fstab thing. 

But the question still remains why "Diskinterval" can recognize the filesystem. Beside that Diskinterval can read both ext2 and ext3 filesystems. 

Will need some rest :D Be back soon.:)

---

### Post by pooyaplus on 2008-07-20
Hi again,
here is what the [COLOR="Red"]tune2fd -l /dev/sdb1[/COLOR] says:

```

tune2fs 1.40.2 (12-Jul-2007)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          4fce5b0b-5ef2-4e58-9aaf-28fa5575e67c
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal resize_inode dir_index filetype sparse_super large_file
Filesystem flags:         signed directory hash 
Default mount options:    (none)
Filesystem state:         not clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              9830400
Block count:              19633430
Reserved block count:     981671
Free blocks:              17971203
Free inodes:              9691494
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      1019
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         16384
Inode blocks per group:   512
Filesystem created:       Tue Sep  4 15:12:06 2007
Last mount time:          Sun Jul 20 11:10:26 2008
Last write time:          Sun Jul 20 11:10:26 2008
Mount count:              3
Maximum mount count:      24
Last checked:             Mon Jul 14 13:32:19 2008
Check interval:           15552000 (6 months)
Next check after:         Sat Jan 10 12:32:19 2009
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               128
Journal inode:            8
Default directory hash:   tea
Directory Hash Seed:      1d6aeaeb-061b-4c92-b4bb-3a5fdf4be8e1
Journal backup:           inode blocks

```

again it says that sdb1 has already has the journal! It is confusing me again.

---

### Post by pooyaplus on 2008-07-20
Bump

---

### Post by unutbu on 2008-07-20
Note this line in the tune2fs output:

> Filesystem state:         not clean

To try to fix that, let's run fsck:

```
sudo umount /dev/sdb1         # you must unmount the partition before fsck'ing it
fsck -p /dev/sdb1
```

Report the output if fsck stops with an error. Otherwise, 
try mounting sdb1 again.

---

### Post by pooyaplus on 2008-07-20
Thanks, good to see you agian.
The fsck says the /dev/sdb1 is clean and a report pf occupied blocks and files. 
Here's the tune2fs -l output with sdb1 mounted:
```

tune2fs 1.40.2 (12-Jul-2007)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          4fce5b0b-5ef2-4e58-9aaf-28fa5575e67c
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal resize_inode dir_index filetype sparse_super large_file
Filesystem flags:         signed directory hash 
Default mount options:    (none)
Filesystem state:         not clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              9830400
Block count:              19633430
Reserved block count:     981671
Free blocks:              17971203
Free inodes:              9691494
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      1019
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         16384
Inode blocks per group:   512
Filesystem created:       Tue Sep  4 15:12:06 2007
Last mount time:          Sun Jul 20 16:04:18 2008
Last write time:          Sun Jul 20 16:04:18 2008
Mount count:              4
Maximum mount count:      24
Last checked:             Mon Jul 14 13:32:19 2008
Check interval:           15552000 (6 months)
Next check after:         Sat Jan 10 12:32:19 2009
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               128
Journal inode:            8
Default directory hash:   tea
Directory Hash Seed:      1d6aeaeb-061b-4c92-b4bb-3a5fdf4be8e1
Journal backup:           inode blocks

```

But it still says that the filesystem is not clean. What is going on?

---

### Post by unutbu on 2008-07-20
I googled "filesystem state not clean" and found some pages which say this is normal when a partition is mounted. Oddly, when I try the tune2fs command on my system, it comes back saying clean, even on mounted partitions, so I'm not really sure what to believe.

Let's go back to the symptions.

You can now mount sdb1 using the command

mount /dev/sdb1 /media/sdb1

right? So please remind me... what is the problem?

---

### Post by pooyaplus on 2008-07-20
Actually the problem was that the partition did not mount with its ordinary file system (ext3), then you came up with the idea that it might be ext2 rather than ext3. It did mount (and does) with -t ext2 suffix, but the problem is that system still sees the partition as ext3 but opens it only as ext2. 

As I can mount the partition as ext2 there is always danger of journaling mismatch when I am going to make another backup copy. But I will give that a try. Lets see what happens, I do not believe that can make so much trouble but just a precaution I have in mind.

---

### Post by unutbu on 2008-07-20
Sorry pooyaplus, I don't know of any elegant way to fix this. The crude but probably effective way (as mentioned before) would be to backup the data, destroy the partition, recreate an ext3 partition (using a linux tool like GParted or even fdisk) and then copying the data back.

---

### Post by pooyaplus on 2008-07-21
Hi, I appreciate your help. I do believe that's the best course of action in this case. 

Thank you very much indeed.

---

