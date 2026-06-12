---
title: "Problems with Reiserfs"
date: 2006-04-09
forum: Hardware &amp; Laptops
---

### Post by calandryll on 2006-04-09
After a reboot today, the first after updating my server with a bunch of recent updates, one of my hard drives in my system has decided to have a bad superblock.  I did some searching and found that if I run reiserfsck --rebuild-sb /dev/hde1 on it, the super block should be rebuilt.  Except that it refuses to work.  I can't find any other way of fixing this.  I would also prefer not to format the drive as I do have it almost filled with files.  
I am running:
Breezy 5.10
Kernel 2.6.12-10-368
the hard drive has reiser 3.6.19 installed on it

Since a new kernel was recently installed could it be a possible kernel issue for it not working?


```
chris@miriam:~$ sudo reiserfsck --rebuild-sb /dev/hde1
reiserfsck 3.6.19 (2003 www.namesys.com)

*************************************************************
** If you are using the latest reiserfsprogs and  it fails **
** please  email bug reports to reiserfs-list@namesys.com, **
** providing  as  much  information  as  possible --  your **
** hardware,  kernel,  patches,  settings,  all reiserfsck **
** messages  (including version),  the reiserfsck logfile, **
** check  the  syslog file  for  any  related information. **
** If you would like advice on using this program, support **
** is available  for $25 at  www.namesys.com/support.html. **
*************************************************************

Will check superblock and rebuild it if needed
Will put log info to 'stdout'

Do you want to run this program?[N/Yes] (note need to type Yes if you do):Yes

reiserfs_open: the reiserfs superblock cannot be found on /dev/hde1.

what the version of ReiserFS do you use[1-4]
        (1)   3.6.x
        (2) >=3.5.9 (introduced in the middle of 1999) (if you use linux 2.2, choose this one)
        (3) < 3.5.9 converted to new format (don't choose if unsure)
        (4) < 3.5.9 (this is very old format, don't choose if unsure)
        (X)   exit
1

Enter block size [4096]:
4096

No journal device was specified. (If journal is not available, re-run with --no-journal-available option specified).
Is journal default? (y/n)[y]: y

Did you use resizer(y/n)[n]: n
rebuild-sb: no uuid found, a new uuid was generated (7cf2f10e-2aa8-4245-9fc0-8e8dab89dc25)

rebuild-sb: You either have a corrupted journal or have just changed
the start of the partition with some partition table editor. If you are
sure that the start of the partition is ok, rebuild the journal header.
Do you want to rebuild the journal header? (y/n)[n]: y
Reiserfs super block in block 16 on 0x2101 of format 3.6 with standard journal
Count of blocks on the device: 30015168
Number of bitmaps: 916
Blocksize: 4096
Free blocks (count of blocks - used [journal, bitmaps, data, reserved] blocks): 0
Root block: 0
Filesystem is NOT clean
Tree height: 0
Hash function used to sort names: not set
Objectid map size 0, max 972
Journal parameters:
        Device [0x0]
        Magic [0x0]
        Size 8193 blocks (including 1 for journal header) (first block 18)
        Max transaction length 1024 blocks
        Max batch size 900 blocks
        Max commit age 30
Blocks reserved by journal: 0
Fs state field: 0x1:
         some corruptions exist.
sb_version: 2
inode generation number: 0
UUID: 7cf2f10e-2aa8-4245-9fc0-8e8dab89dc25
LABEL:
Set flags in SB:
Is this ok ? (y/n)[n]: y
The fs may still be unconsistent. Run reiserfsck --check.

chris@miriam:~$ sudo reiserfsck --check /dev/hde1
reiserfsck 3.6.19 (2003 www.namesys.com)

*************************************************************
** If you are using the latest reiserfsprogs and  it fails **
** please  email bug reports to reiserfs-list@namesys.com, **
** providing  as  much  information  as  possible --  your **
** hardware,  kernel,  patches,  settings,  all reiserfsck **
** messages  (including version),  the reiserfsck logfile, **
** check  the  syslog file  for  any  related information. **
** If you would like advice on using this program, support **
** is available  for $25 at  www.namesys.com/support.html. **
*************************************************************

Will read-only check consistency of the filesystem on /dev/hde1
Will put log info to 'stdout'

Do you want to run this program?[N/Yes] (note need to type Yes if you do):Yes

reiserfs_open: the reiserfs superblock cannot be found on /dev/hde1.
Failed to open the filesystem.

If the partition table has not been changed, and the partition is
valid  and  it really  contains  a reiserfs  partition,  then the
superblock  is corrupted and you need to run this utility with
--rebuild-sb.

```

Any suggestions would greatly be appreciated.

---

### Post by pizzach on 2006-04-09
A random shot in the air: The partition is unmounted right?  I think most disk utilites require them that way for repair.

---

### Post by calandryll on 2006-04-09
[QUOTE=pizzach]A random shot in the air: The partition is unmounted right?  I think most disk utilites require them that way for repair.[/QUOTE]

Yep it's not mounted at all.  I tried it again just to see still no luck.  Time to try out a different kernel to see if that works.  I did do a reboot before and was getting Buffer I/O errors on the HDD.

```
chris@miriam:~$ sudo umount /dev/hde1
umount: /dev/hde1: not mounted

```

Edit: I had put in a new HDD this afternoon, hence the reboot, and that is when all of my troubles started.  I rearranged a few things, mostly power connectors, I had to split one to get all of my HDDs in there.  And the tree is now currently being rebuilt.  Of course once that is done I'm moving everything off onto the new hard drive and making all of my drives ext3, I've always run into some problem using reiser.

---

