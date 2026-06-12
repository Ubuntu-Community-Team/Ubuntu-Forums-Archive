---
title: "[SOLVED] Broken Ubuntu Partition table"
date: 2008-11-02
forum: General Help
---

### Post by thestig_992 on 2008-11-02
I needed to install windows (i have another thread about this and what i did), and some people recomended gparted to split my ubuntu drive. however, windows would not install on a sata drive, so i found another ide drive and installed windows on that. 
On the windows setup, when it asks you about partitioning drives, it formatted my sata drive. I dont really know why this happened, but thats not the issue. Im pretty sure that my data is still on the drive, because it took less than 10 secs to format before i realised something was wrong. I then shutdown, removed the sata, and did a normal install on the ide drive. Then i plugged the sata drive back in, but its broken.

Gparted on the live cd cant seem to fix the problem. It just sees the entire drive as unallocated, and wants to create a disklabel, that will result in all the data on the drive being deleted. What I think i need is to rewrite the partition table at the front of the disk, maybe using mkfs?
I'm hesitant to just try some things on my own though, because i dont want to lose any data on my sata drive.

I found another thread which looks promising: [http://ubuntuforums.org/showthread.php?p=2210436](http://ubuntuforums.org/showthread.php?p=2210436)
Will try unless someone warns me not to in the next few mins...

---

### Post by thestig_992 on 2008-11-02
Seems that that guide does not work. Gave me an error stating that the "partition table is outside the disk" when i tried to rescue the partition table.

Is it possible to use fdisk to fix? Delete and create a new partition? Though i would have to do swap space and extended..?

---

### Post by thestig_992 on 2008-11-02
Going to try using testdisk to fix...
Again if this is wrong, please tell me quickly before i do it...

---

### Post by sharkbite1414 on 2008-11-02
When Windows deletes something it either deletes the actual file or more usually just deletes the registry value that tells your computer were to find the file. This means the file is still there but your computer doesn't know were to fined it. So if this is the case it is likley your files are still there so I suggest you try a file recovery tool ('PC Inspector File Recovery 4' and 'Pandora Recovery 2.0.7' are good and free but are for windows). I'd suggest some for Ubuntu but I'm fairly new and haven't tried any. So anyway I going to assume you will be working in windows as by the sound of it that you've working at the minute. 

*Pug in your sata drive (Unplug and anti-static wristbands of course),
*Download your file recovery tool,
*Scan your sata drive,
*If there anything there this should find it.

Hope this helps!

---

### Post by thestig_992 on 2008-11-02
Problem is, i cant actually boot windows, since the bios points to the sata drive. I know i can fix this, but i want to see if there are any better linux options first.

If I use fdisk to delete all the partitions, then rewrite a single partition over the entire drive, i wont loose any data right?
Then i can backup onto an external drive, and restore over a fresh install...?

---

### Post by sharkbite1414 on 2008-11-02
If you delete the partitions you automatically format them . . . I think.

---

### Post by thestig_992 on 2008-11-02
well deleting the partitions and recreating them is formatting, though that wont delete any data. I just dont wanna screw up my drive any more than it already is.

---

### Post by thestig_992 on 2008-11-03
bump, this is rly an emergency....


UPDATE: deleted all partition with fdisk and created a single partition over the entire drive. Now my data is all visible.
Ofcourse, I dont have a boot partition, extended, or swap space, so i was wondering if is possible to recover an old partition table? Does linux/ubuntu keep a file or a log somewhere of things like this. Im using 8.10 if that helps...

---

### Post by simon.a.ruiz on 2008-11-03
@thestig_992: Hey, I was in the same boat as you a few minutes ago and found you on the forums asking my very question.

I had accidently wiped out the partition table on an old hard disk that had a bunch of un-backed-up emotionally significant data.

testdisk is definitely your tool for recovering what partitions went where:

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step) is a simple tutorial.

I was able to recover my partition information, verify (by listing the partition contents) that it was correct, and apply the recovered partition info directly to the disk's partition table in less than a minute. (I've used PhotoRec before, so I'm pretty used to the interface.)

Then (since it was plugged in via USB), I just unplugged it and plugged it back in so Ubuntu would re-read the partition table and bam. Up popped the partition, automounted.

*Cue huge sigh of relief* I'm definitely going to take a look at Backup-PC, now. ;-)

If you can't get the partition table recovered right /in situ/, you may have to resort to copying all your data off to another storage place, re-creating the partitions as you want them, and copying all your data back.

You'll still be lucky enough not to lose any of your data.

Best of luck!

Simón

P.S. In the future, might I recommend using dd to make a bit-by-bit copy of your hard disk the MOMENT you suspect there's something awry if there's any data of value to you on the disk.

sudo dd if=/dev/sdX of=harddiskbackup.dd # Where /dev/sdx is the relevant disk

That way, when you go to play with power tools (like testdisk) to try to get your data back, IF you make a false move and ruin the data, you can always just use dd to undo your mistake and start over.

sudo dd if=harddiskbackup.dd of=/dev/sdX # Where /dev/sdx is the relevant disk

---

### Post by thestig_992 on 2008-11-04
Testdisk didnt work becuase windows screwed up my ext3 table with its ntfs rubbish, but becuase the drive was sata, it didnt have proper drivers and so made some errors, i think. Anyways, the only thing testdisk found was a broken ntfs partition table.
I managed to be able to view my data again by deleting all my paritions (fdisk said they were screwed over as well) and then creating a single partition over the entire drive. Now I think ill just backup all my data to another hdd, then reinstall ubuntu on my current drive, and copy all my stuff back over the top of the fresh install. That way ubuntu will make all the reccomended partition sizes etc. Also ill have a working MBR.

Ty for the suggestion with backing up my partition table. I think ill write a script to save both dd and fdisk -l, and put them on my server...
Theres not a better way to view the parition table is there? I dont really like the way of runnign a script as root all the time.

---

### Post by simon.a.ruiz on 2008-11-04
Careful with using dd to back up a partition table, dd is a very low level tool.

The command lines I gave earlier were for backing up a /entire disk/ bit-by-bit so if you screw something up you can revert it back to that point. Main point: if you've got an 80 GB disk, you'll create an 80 GB file that takes 80GB worth of write time to make.

There are ways of making dd only grab so much info so, for instance, if you want to grab a device's Master Boot Record, you can:
# dd if=/dev/sdX of=sdX.mbr bs=512 count=1   # Where /dev/sdX is your disk device.

This'll read the first 512 bytes of /dev/sdX into the newly created (or overwritten) file sdX.mbr. Then, to restore that MBR, you can:
# dd if=sdX/mbr of=/dev/sdX

HOWEVER, if what you're looking for is just a good way to back up your partition table, check out sfdisk.

In order to back up the current partition table I run:
# sfdisk -d /dev/sdX > sdX.sfdisk

This dumps the partition table data into a plain text file (in this case, sdX.sfdisk). Then in order to take that data and re-write it to the disk (i.e. restore the partition table), I run:
# sfdisk /dev/sdX < sdX.sfdisk

The most important command here, however, is "man sfdisk". ;-)


UPDATE: P.S. these are all built in commands in Ubuntu.

---

### Post by simon.a.ruiz on 2008-11-04
Re: A better way to view the partition table.

You mean like Gparted? ("sudo apt-get install gparted")

You still run it as root, though. Only root has access to those disk sectors, I believe.

---

