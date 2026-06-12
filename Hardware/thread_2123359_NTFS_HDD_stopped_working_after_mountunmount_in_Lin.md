---
title: "NTFS HDD stopped working after mount/unmount in Linux..."
date: 2013-03-07
forum: Hardware
---

### Post by odakrell on 2013-03-07
... or so I think at least.

(apologies if this doesn't belong in the hardware forum, by the way. I wasn't sure what's the right place to ask.)

I'm trying to keep it short, but I need to quickly summarize the backstory of my problem:

A few days ago my Thinkpad SL510 suddenly stopped working. More precisely, after turning it on, the screen stayed black (though under power), and no further activity happens. Cannot get into BIOS, nothing. I am still trying to figure out what exactly is wrong with it (I already was able to rule out RAM, CPU, broken USB and some other problems). 

I wasn't exactly able to rule out the HDD as the cause of the problem, so I took it out and put it into an external case and connected it to my 2nd PC that runs (x)ubuntu. Much to my relieve the HDD was recognized, and mounted, and I did a quick check to see if my files were still readable. They were.

Here's where the real problem started: I then tried to unmount the device (in Thunar), but got an error. Didn't think much of it and turned off the PC. But when I tried to mount the HDD again later, again under xubuntu, 2 out of 3 partitions are not mountable anymore (after all 3 of them could be mounte before). 

Here's the error message in detail:

> Error mounting: mount exited with exit code 13: ntfs_mst_post_read_fixup: magic: 0x43425355  size: 4096  usa_ofs: 1194  usa_count: 65535: Invalid argument
Actual VCN (0x80000e0000b0000) of index buffer is different from expected VCN (0x0).
Failed to mount '/dev/sdc1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.


I've already searched for this message, and found some topics with it on this forum as well. Both the error message and forum replies suggest to run chkdsk /f under Windows, which I tried (on a friend's Windows PC). Only one of the partititons of my HDD (the Lenovo recovery partition) is recognized without problems. For this partition chkdsk returned no problem.

The 2 other partitions (the important ones, one is 'system', the other holds most of my data) appear in Windows "My Computer", or at least they appear under some drive letter, but they are not accessible, and Windows Explorer doesn't manage to read their size, etc. Also, running chdksk /f on them simply results in an error.

The HDD in question is a 320 GB, 5400 rpm, SATA interface disk. Don't know the manufacturer, but I can find it out. File system is NTFS.

**To summarize:** My notebook doesn't boot up anymore, and I cannot rule out (nor confirm) that my HDD is the cause. However, I was able to mount it under xubuntu, and open several files without problems. But when I unmounted the disk, an error occured and since then 2 partiations of the HDD cannot be mounted/read anymore, neither in Linux nor Windows. No idea if it's a result of the unmount error in Linux, or part of the original problem that caused my notebook to stop working.

**My question:** Is it possible that the unmount error caused some fuckup in the filesystem/boot sector/whatever, and is the reason why I can't mount those two partitions anymore? Or can that be ruled out? Also, any idea what I can do to either make the HDD work again, or at least recover my data? I have a hard time believing that all the data would be lost, since an hour ago is was able to read it all just fine under Linux, and I didn't format/overwrite anything...

---

### Post by Mark Phelps on 2013-03-08
Couple of comments ...

First, if you can connect the drive to a Windows PC running Win7, then launch the Disk Management utility (with the drive connected).  Scroll down the list of drives.  You may see the external drive listed there, but without a drive letter.  See if it will let you assign a drive letter.  If it does, then run chkdsk on it.

Second, you should download and burn a CD of the Minitool Partition Wizard Boot CD.  That is a partitioning tool, and when you boot from it (with the drive connected), see if it will allow you to run a Check on the external drive.

---

