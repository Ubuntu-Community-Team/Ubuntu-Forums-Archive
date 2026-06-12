---
title: "How to check if the data written to my SATA disks gets corrupted"
date: 2018-11-07
forum: Hardware
---

### Post by hiec2 on 2018-11-07
Hello!

I'm trying to diagnose weird problems with SATA disks. My suspicion is that there are problems with my SATA controller which cause a little bit of data corruption, just enough to cause checksum errors. To that end I would like to methodically check if data that gets written to the disks gets corrupted. Currently I am using badblocks, because for some reason I could not find a program that explicitly tests for data corruption. I would really appreciate it if someone could point out a better way to test for data corruption when writing to/reading from hard disks.

If badblocks completes a read/write test cycle, e.g. "sudo badblocks -wsv /dev/sda", on a hard disk without errors, is it safe to assume that my mainboard, SATA controller and SATA cables do not cause data corruption? If no, what would be a better way to test this? Create a file checksum with shasum1, copy the file to the disk in question, create another checksum and compare? How often should I do this until it is reasonably safe to assume my hardware works the way it should? I have five disks to test, so a solution with some automation, like a testing tool, would be optimal :-)

Any help would be greatly appreciated!
Thank you!

---

### Post by TheFu on 2018-11-07
Any part of a storage system can allow corruption.  cables, controller, HDD, SSD, motherboard, OS, any of them.  Don't assume.

Use ZFS.  It is the only file system that verifies what was sent to the disk was actually written.
The problem with ZFS is that it isn't supported for OS devices or boot devices, just data.

For all other storage issues, use the SMART data provided by smartctl.  I think gnome-disks can access this too.  Look for issues in the data and watch any counts that change from week-to-week.

So, storage systems have CRC checking built in which corrects many errors automatically, at a cost of performance.  Slow disks usually get slow because there's a HW issue that is getting worse and worse.  If you need extra confidence and can't/won't use ZFS, then you can manually use par2 files to keep track of any corruption.  10% par2 is standard.

And if you haven't done this already, get backup religion ASAP.  That's versioned backups, not mirrors.  Corrupted data mirrored to other storage just provides 2 copies of the corrupted data. Not useful.  Backups are 100x easier to handle than attempting data recovery.

All storage devices are going to fail.  That's their goal in life.  Our goal is to be prepared regardless of when that occurs and have know-we-can-restore backups, always.

---

### Post by slickymaster on 2018-11-07
*Thread moved to **Hardware**.*

---

### Post by hiec2 on 2018-11-09
> **TheFu said:**
> Any part of a storage system can allow corruption.  cables, controller, HDD, SSD, motherboard, OS, any of them.  Don't assume.
Thank you very much for your reply! You are right of course. Anything can fail and it is never safe to assume it won't fail in the future, even if it works now. With that beeing said, how do I determine if my storage system works the way it should right now? You can't prove a negative, so proving there is no data corruption at all is impossible. All we can do is test for data corruption and, if we don't find any, at some point declare the system is working at this point in time. 

The storage system I am interested in will be used for a file server for personal data in a non-commercial setting. Let me set a really low bar. Let's say the storage system needs to write and read files 99.99% of the time without data corruption. So, on average, if the system writes one million files to disk, one hundred of them would get corrupted. How do I test, in a sensible way, if a system fulfilles this arbitrary standard?

Am I looking at this wrong? I get the feeling that I am approaching the problem of preserving my data from the wrong direction. Basically all I want to do is build a server that will keep my personal data safe with the limited ressources I have available. 


> **TheFu said:**
> Use ZFS.  It is the only file system that verifies what was sent to the disk was actually written.

Thank you for making me aware ZFS is an option on Linux. I still thought you had to have an expensive commercial server to use it.
Unfortunately I am using a 32bit system for my fileserver project and the zfsonlinux project states that [ZFS may be unstable in a 32bit system]("https://github.com/zfsonlinux/zfs/wiki/FAQ#32-bit-vs-64-bit-systems"). Until now I was planning to use BTRFS for its checksumming features. I will look more into ZFS, maybe it is incentive enough to switch to 64bit hardware.

> **TheFu said:**
> 
If you need extra confidence and can't/won't use ZFS, then you can manually use par2 files to keep track of any corruption.  10% par2 is standard.

I will look into par2 files. Again, I am grateful for the suggestion.

> **TheFu said:**
> 
And if you haven't done this already, get backup religion ASAP.  That's versioned backups, not mirrors.  Corrupted data mirrored to other storage just provides 2 copies of the corrupted data. Not useful.  Backups are 100x easier to handle than attempting data recovery.

All storage devices are going to fail. That's their goal in life. Our goal is to be prepared regardless of when that occurs and have know-we-can-restore backups, always.

This is great advise. Currently I intend to set up rsync scripts for incremental backups, unless I find a better command line tool for this.


@[COLOR=#000000]slickymaster
[/COLOR]Thank you for moving the thread. I am still hoping to learn more about testing storage systems for data corruption.

---

### Post by TheFu on 2018-11-09
> **hiec2 said:**
>    
This is great advise. Currently I intend to set up rsync scripts for incremental backups, unless I find a better command line tool for this.
 

I won't touch btrfs. Redhat has deprecated using it.  It has a history of data loss and doesn't tell du or df the truth about used storage.  Hopefully, the data loss issues with it have all been fixed, but for a few years it was recommended against using btrfs in my primary use-case, so I simply decided to avoid it.

As for backups, rsync even with hardlinking for versions, isn't the best choice.  Check out **rdiff-backup**.  It captures the file metadata that changes over time, not just the data changes in the versioning.

I already answered your first questions.

---

### Post by hiec2 on 2018-11-11
> **TheFu said:**
> I already answered your first questions.
Indeed you have. Par2 files can do what I was looking for, even if I would have to choose the test data myself and write some scripts to automate the test. Given that no one seems to have written a tool doing that already this is probably the wrong way to test a new storage system for data corruption. 


I will look into rdiff-backup once my fileserver progresses that far. For now I will go find some 64bit hardware so I can use ZFS.


Thank you for all the help! I really appreciate it.


For future reference, a program called "duplicity" has built-in support for par2 files. Its man page says it uses librsync, so it might have similar drawbacks as rsync compared to rdiff-backup.

---

### Post by TheFu on 2018-11-11
I have a par2 creation script. It was trivial. I used it when my backups were stored on optical media. Turns out that the built-in CRC stuff in optical media isn't very good. I've restored unreadable data from DVDs multiple times, thanks to having par2 files.

Duplicity is a backup tool that checks all the boxes for what we should want in a backup, except 2, IMHO.  It does capture the changes to file metadata over time.  It is slow. It doesn't use an opaque storage format.  The other things it does well might make up for those two problem for your needs.

When you play with backup tool, just backup /etc/ for your initial testing.  It is a small area, it has file ownership by different userids, modifying a small text file there is easy (testing the versioning) and it has "funny" files which will never finish backing up if the backup tool doesn't recognize them.
Then be certain to test the different restore methods.
* 1 file, the most recent.
* 1 file, 3 versions ago.
* all files, the most recent.
* all files, 5 versions ago.
How easy is it to do that for the admin?  How easy is it for self-service by non-Admins?

---

