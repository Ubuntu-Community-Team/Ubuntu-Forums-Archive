---
title: "Help using fsck on an ntfs drive"
date: 2008-10-28
forum: General Help
---

### Post by sideburns on 2008-10-28
Recently, after a motherboard failure (possibly caused by a failing drive) we had to move my sister's dual boot system from two old drives to a new 500 GB SATA drive.  Ubuntu works fine.  I've done everything I can to get 2K running, but it crashes on boot asking for chkdsk, even in Safe Mode.  We've tried to upgrade to XP and gotten the same result.

I suddenly realized that maybe the ntfs file system is corrupt.  (D'oh!)  From Ubuntu, I tried running fsck but it wouldn't cooperate.  After RTFM time, I tried this to see what it thought it should do:

sudo 'fsck -A -N -t ntfs-3g'

It reported that it couldn't find the command.  Trying with only -A and -N got the same results.  Using 'fsck.nfs' got a report that the drive was, in fact an NFS drive but didn't try to do anything.

Does anybody know what's going on, or how to get fsck to run on it?

---

### Post by TeoBigusGeekus on 2008-10-28
The fsck command doesn't support ntfs partitions.
Check out this link:
[http://www.linux-ntfs.org/doku.php?id=ntfsck]("http://www.linux-ntfs.org/doku.php?id=ntfsck")

---

### Post by TeXtonyx on 2008-10-28
Use chkdsk /f when Windows starts up. It can take quite awhile to
complete, so start it when you have something else to do.

---

### Post by Herman on 2008-10-28
Even if you run ntfsfix, (from ntfsprogs), all it does is set the 'dirty' flag in the NTFS file system to induce Windows to run CHKDSK on it at next boot time.
You can try that if you want, 
```
sudo ntfsfix /dev/sda1
```Where: /dev/sda1 is the partition containing the NTFS file system to be checked and repaired. If you're not sure you can check first with Gnome Partition Editor or by running 'sudo fdisk -lu'.

If an NTFS file system needs repair or maintenance and Windows won't even boot, you may need to use a [Windows XP Recovery Console]("http://www.kellys-korner-xp.com/win_xp_rec.htm"), available from your Windows XP Installation disk (CD-ROM). 
If your  computers came with a 'Recovery' CD or worse, a 'Recovery Partition' instead of a real Windows 'Installation' disc, you will need to go borrow a Windows XP 'Installation' CD from a friend, just to use the Recovery Console.
Then run 'CHKDSK /F', as TeXtonyx already posted, or CHKDSK /R, which is the one I like.

---

### Post by TeXtonyx on 2008-10-28
I think chkdsk can be run from My Computer for XP or Vista.
In some cases anti-virus software requires a reboot into Safe Mode.

[http://www.ehow.com/how_2052292_run-chkdsk-f-windows-xp.html](http://www.ehow.com/how_2052292_run-chkdsk-f-windows-xp.html)

I don't remember that the XP install disk RC, works on Win2K, maybe so. 
If you can't boot into Safe Mode, tapping F8 at startup, then you can
try Herman's RC suggestion. I think you could try backing up the data
on Win2K by mounting it from Ubuntu, but that will also likely fail.

Next, you can hook up the old Win2K drive as a slave to the new drive.
Mount it from Ubuntu and save the data if you can. The point of this is
to find out if the old drive worked/booted, itself, before you cloned it,
regardless of the mainboard. Probably more informative is to unplug the
new drive, set the old drive Win2K jumpers to master, connect the cables,
and see if the old 2K drive boots up. It isn't necessary to use screws
for a brief test. If the old 2K drive boots in this situation it tells 
you that the problem is not the disk or the OS. If it doesn't boot, you
can download a disk testing program from the manufacturer of the drive.
If the drive is bad, the clone is corrupt, and though you can try to use
chkdsk, I doubt it will work and you will have to reinstall the OS. If
the drive is OK, but it didn't boot, then the OS itself presents a less
fundamental challenge to repair because the clone doesn't have corrupt sectors. 

But in any event, I think you should backup any key data files if you
can from the Win2K drive or its clone to the new drive partition. I'd
do the step, connect old 2K drive and test, first, because chkdsk can
take a long time to run.

---

### Post by sideburns on 2008-10-28
I may be able to use ntfsresize to force chkdsk on reboot.  I can't currently use chkdsk myself because, as I said, it crashes before giving me a command line.

The Windows Vista installation and recovery partition are long gone.  If needed, I'll see if I can get into the Recovery Console of the XP CD and go from there.

---

### Post by sideburns on 2008-10-28
Windows still crashes before getting to a command line in Safe Mode.  (In fact, it looks like it's trying a normal boot when we try it.)  If I try for the Recovery Console from the XP CD, it asks me to insert the floppy with the Recovery Console info.  This is impossible for two reasons: first, because it doesn't come with one and we've never had a chance to make one and second, the computer doesn't have a floppy drive.

Thanx anyway.

---

### Post by snova on 2008-10-28
sudo isn't working because you aren't supposed to quote its arguments.

In any case, fsck doesn't operate on NTFS filesystems.

---

### Post by TeXtonyx on 2008-10-28
Recently, after a motherboard failure (possibly caused by a 
failing drive) we had to move my sister's dual boot system 
from two old drives to a new 500 GB SATA drive. Ubuntu works 
fine. I've done everything I can to get 2K running, but it 
crashes on boot asking for chkdsk, even in Safe Mode. We've 
tried to upgrade to XP and gotten the same result.
...

If I try for the Recovery Console from the XP CD, it asks me 
to insert the floppy with the Recovery Console info. This is 
impossible for two reasons: first, because it doesn't come 
with one and we've never had a chance to make one and second, 
the computer doesn't have a floppy drive.
---------------------

[http://www.windowsnetworking.com/articles_tutorials/wxprcons.html](http://www.windowsnetworking.com/articles_tutorials/wxprcons.html)

Usually the Administrator Password is, just type the, Enter, key.

This is a tutorial on how to use Win2K Recovery Console. It also
has XP information. Use the Win2K disk if you have it. If you
follow the steps in the tutorial you should get to C:\WINNT>
usually.  C:\WINNT>chkdsk /f /r will work if 
C:\WINNT>chkdsk c: /f /r doesn't work.

4. Run the chkdsk utility by typing in the following command:
chkdsk c: /f /r
NOTE: the /f command automatically fixes any errors encountered, 
the /r command locates bad sectors and recovers readable information

If you follow the instructions you are not supposed to receive
a prompt for another floppy. If you still get the request for
another floppy it bodes poorly for your Win2K installation. 
Remember to backup data files if you can. And try hooking up
the old Win2K drive to see if it boots as suggested before. 
If you are going to do a repair Win2K install or a new install,
you will need the Win2K install disk. Otherwise, you will have
to wipe the Win2K partition on the 500GB drive and install XP.
So backing up key data files is important now.

Also, as you may not know, when you install an OS it uses drivers
for that motherboard and hardware. If you move that installed OS
to a new computer, it uses different drivers. So new drivers have
to be installed for the OS to work properly. One of the problems
with wiping an OEM hidden/restore partition is that this partition
has the drivers for the currently installed OS. If you wipe that
currently installed OS, you have to locate the drivers that work
for the replacement OS. That can take a fair amount of capable effort.
Sometimes computers ship with a duplicate of the hidden partition
written to a recovery CD.

---

### Post by ciscosurfer on 2008-10-28
@sideburns, give this a shot: [http://ubuntuguru.wordpress.com/2007/03/15/testdisk-saves-the-day/](http://ubuntuguru.wordpress.com/2007/03/15/testdisk-saves-the-day/)

Direct link to author's page: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by mahdif62 on 2010-04-30
You can use this command to check an NTFS file system:
```
ntfsresize  -fi /dev/hdXY
```

---

### Post by sideburns on 2010-04-30
Why are you responding to a thread that's 18 months old?  Do you really think we're still going to need advice after this long?  Thanx for the suggestion, but it's not been relevant for over a year now.

---

### Post by mahdif62 on 2010-04-30
Dear sideburns , tonight I had a failing ntfs drive, and I DEED NEED ADVICE on this. Chances are someone else has this problem, so I thought if I put a reply here someone else with such a problem could get here by googling and  find the answer easily.

---

### Post by vinkic on 2011-02-17
Like me :)

I have a problem with ntfs drive and I did ntfsresize but...

[I]dacha@radovan:~$ sudo ntfsresize  -fi /dev/sdd1
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sdd1
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 1000202039808 bytes (1000203 MB)
Current device size: 1000202043392 bytes (1000203 MB)
Checking filesystem consistency ...
Cluster 56920046 is referenced multiple times!
Cluster 56920047 is referenced multiple times!
Cluster 56920048 is referenced multiple times!
Cluster 56920049 is referenced multiple times!
Cluster 56920050 is referenced multiple times!
Cluster 56920051 is referenced multiple times!
Cluster 56920052 is referenced multiple times!
Cluster 56920053 is referenced multiple times!
Cluster 56920054 is referenced multiple times!
Cluster 134645716 is referenced multiple times!
100.00 percent completed
ERROR: Filesystem check failed!
ERROR: 5857 clusters are referenced multiply times.
NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
and will be made to NTFS by this software until it gets repaired.


[/I]

---

### Post by kalmdave on 2012-01-16
> **mahdif62 said:**
> Dear sideburns , tonight I had a failing ntfs drive, and I DEED NEED ADVICE on this. Chances are someone else has this problem, so I thought if I put a reply here someone else with such a problem could get here by googling and  find the answer easily.

Thanks and like me too. Am on Lucid and want check/repair/maintain ntfs disks/partitions.

---

### Post by oldos2er on 2012-01-16
Closed, necromancy.

---

