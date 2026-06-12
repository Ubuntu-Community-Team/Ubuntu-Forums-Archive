---
title: "FSCK checks disk every time I boot up"
date: 2008-09-23
forum: General Help
---

### Post by linuxguy6 on 2008-09-23
This started happening a couple of weeks ago. I would turn on my computer, use it for a while, and shut it down using the Power button in the top right hand corner. The next time I would boot, FSCK would run, and then would say, "fsck died with status 1" and beside it would say [fail]. This adds over 30 second to my boot time. Any ideas about how this happened, and how to fix this?

---

### Post by russlar on 2008-09-23
Sounds like you have a filesystem that's been corrupted. Do you know whick partition it's trying to fsck?

---

### Post by plucky on 2008-09-23
> **linuxguy6 said:**
> This started happening a couple of weeks ago. I would turn on my computer, use it for a while, and shut it down using the Power button in the top right hand corner. The next time I would boot, FSCK would run, and then would say, "fsck died with status 1" and beside it would say [fail]. This adds over 30 second to my boot time. Any ideas about how this happened, and how to fix this?

Post output of ```
cat /var/log/fsck/checkfs
``` which should be where the fsck log is saved.

---

### Post by linuxguy6 on 2008-09-29
Log of fsck -C -R -A -a 
Mon Sep 29 16:46:36 2008

fsck 1.40.8 (13-Mar-2008)

Mon Sep 29 16:46:36 2008

The partition it is scanning is sda2 (my Ubuntu partition). It is bootable, and I seem to be able to access all the files. My partition setup is:

sda1: Windows partition (NTFS)
sda2: Ubuntu partition (Ext3)
sda3: Swap partition (swap)
sda5: Mixed use partition (NTFS)

---

### Post by plucky on 2008-09-30
> **linuxguy6 said:**
> Log of fsck -C -R -A -a 
Mon Sep 29 16:46:36 2008

fsck 1.40.8 (13-Mar-2008)

Mon Sep 29 16:46:36 2008

The partition it is scanning is sda2 (my Ubuntu partition). It is bootable, and I seem to be able to access all the files. My partition setup is:

sda1: Windows partition (NTFS)
sda2: Ubuntu partition (Ext3)
sda3: Swap partition (swap)
sda5: Mixed use partition (NTFS)



Boot the Live Cd and from a terminal window run ```
sudo e2fsck -C0 -p -f -v /dev/sda2
``` to fix the problem.

**Do not run fsck on a mounted file system**

Type **man e2fsck** to see the options available.

Good Luck

---

### Post by linuxguy6 on 2008-09-30
I got your message a little too late, because this error message appeared the last time fsck ran:

[http://cid-bc093e661dc82bf9.skydrive.live.com/self.aspx/Public](http://cid-bc093e661dc82bf9.skydrive.live.com/self.aspx/Public)

Picture is named edit.jpg.

Something also happened before this. I booted into Ubuntu and logged in. The problem was that I couldn't do anything. I ended up forcing the computer off, but there was no data activity.

---

### Post by linuxguy6 on 2008-10-01
I ran e2fsck with all the options specified, and it did not find any problems. However, fsck still tries to run when I boot the computer.

---

### Post by vanadium on 2008-10-01
With the command

```

sudo tune2fs /dev/sda2 -l

```

you can check the settings of the drive. The behaviour you see could be possible - for an ext2 drive (or an ext3 drive with journalling turned off) - for an ext 3 drive with Maximum mount count set to 1.

---

### Post by linuxguy6 on 2008-10-01
The output of this is:

tune2fs 1.40.8 (13-Mar-2008)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          fd1d5111-d06c-431d-90fc-b446ad25bec0
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery sparse_super large_file
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              396704
Block count:              1586418
Reserved block count:     79320
Free blocks:              426177
Free inodes:              248656
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      387
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8096
Inode blocks per group:   253
Filesystem created:       Sun Jun 22 00:06:52 2008
Last mount time:          Wed Oct  1 14:57:50 2008
Last write time:          Wed Oct  1 14:57:50 2008
Mount count:              3
Maximum mount count:      30
Last checked:             Tue Sep 30 13:40:06 2008
Check interval:           15552000 (6 months)
Next check after:         Sun Mar 29 13:40:06 2009
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:		  128
Journal inode:            8
First orphan inode:       291980
Default directory hash:   tea
Directory Hash Seed:      7853fc13-4da9-4fa2-a8aa-8eb1b584ebe9
Journal backup:           inode blocks

---

### Post by linuxguy6 on 2009-01-25
Problem solved. I just wiped Ubuntu and reinstalled it.

---

