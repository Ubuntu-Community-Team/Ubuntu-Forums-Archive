---
title: "Data drive erased?"
date: 2022-10-17
forum: Hardware
---

### Post by peyre on 2022-10-17
I recently moved my data drive's mount point in fstab from ~/Storage to /media/Storage.  Then yesterday morning I was modifying my backup script, which copies files and folders from Storage to an ext4 partition on a 4TB portable drive.  Suddenly and without notice, the Storage drive disappeared.  No error message, except Audacious complaining that it couldn't find my music files any more.  Storage was *gone*.  A reboot didn't fix anything.

I shut down and removed the storage drive (an HDD formatted ext4) and booted again, with just the boot drive (SSD).  Now Linux boots, but it drops me to a CLI so I guess something's wrong with the desktop environment.  I'm working on that in another thread.

Plugging the storage drive into a USB enclosure, my Xubuntu laptop doesn't see the drive at all.  Yet oddly, if I take the drive & enclosure to a Windows machine with Ext2 Volume Manager installed, it can see the drive, but it says it's completely empty.  Uh oh.

Unfortunately I'm having some (probably related) weirdnesses with the portable drive, so my recent backups seem to be gone as well.  I have an offsite backup, but restoring from a months-old backup isn't an attractive idea.  Are there any tricks to maybe recover my data from the storage drive?

---

### Post by TheFu on 2022-10-17
I'd check the partitions and fstab entry first.  A simple typo is most likely.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)  This is a last-ditch method and shouldn't be expected to work.

Loosing the primary and backup storage in the same week is really odd.  Something about the process is wrong if that can happen.

For the fstab, I much prefer to use LABELs, not devices or UUIDs, unless I'm using LVM, then I'll use the /dev/{vgname}/{lvname} mapper generated link, since it provides the most useful information for me.

---

### Post by peyre on 2022-10-17
There is some weirdness with the backup drive - In Windows with Ext2VM I can open and see my files, but my Linux laptop doesn't see the drive.  The main problem, really, is that my backups had been missing the data from my storage drive because I had moved its mount point.  That's really a 10T error on my part, but I was trying to fix the script when this crash happened.

The thing is, I *should* be able to read the drive on another computer - I put it in a USB enclosure and plugged it into my laptop; it should have mounted the drive, but instead it pretends it can't see it.  Now I just plugged it into a Linux laptop here at the office.  It sees the drive and mounts it, but it shows as being empty. :(

I've installed ddrescue, but it keeps erroring out when I try to recover my data to an empty portable drive.  I must be doing this wrong.
sudo ddrescue /media/leon/Storage /media/leon/BSA02407 ~/log.txt

ddrescue: Output file exists and is not a regular file.
ddrescue: Use '--force' if you really want to overwrite it, but be aware that all existing data in the output file will be lost.
Try 'ddrescue --help' for more information.

---

### Post by TheFu on 2022-10-17
MS-Windows doesn't correctly un-mount file systems. Could that be the problem?  Ensure fast startup is disabled in MS-Windows.

I'd never use MS-Windows to directly mount non-Windows file systems, especially since any "try ubuntu" flash installer can do it easily.

---

### Post by TheFu on 2022-10-17
> **peyre said:**
>  
sudo ddrescue /media/leon/Storage /media/leon/BSA02407 ~/log.txt


Typically, ddrescue points at the device file, not the files inside a file system.  It is best used with both those devices not mounted.

Also, you cannot write to a log file anywhere in the source or target storage devices.

Be certain to seem my other post above.

---

### Post by peyre on 2022-10-18
I plugged in the storage drive, unmounted it, and rerun sudo ddrescue /media/leon/Storage /media/leon/BSA02515 ~/log.txt, but it returns the same error.  What am I doing wrong?

As you can see, I'm not pointing to individual files.

---

### Post by TheFu on 2022-10-18
Use the device file, not the mount location.  I don't have time to explain what that means, but device files are in /dev/  99.9% of the time.  Be very careful, since picking the wrong one can be terrible and clearly won't do what you want.
You'll need to understand the difference between the whole drive device, the partition devices and any specific volume manager devices.  The source and the target don't need to be the same type of devices, but for a beginner, it is strongly recommended they are.

[https://en.wikipedia.org/wiki/Device_file](https://en.wikipedia.org/wiki/Device_file) has an overview, but talks about all the device files for many different OSes, not just storage. It could be confusing.  The "Naming Convention" section should be helpful.

[https://tldp.org/HOWTO/Partition/devices.html](https://tldp.org/HOWTO/Partition/devices.html) is a little dated, but still relevant. Probably just ignore the "/dev/hd" stuff.  May want to read up on partitions, since that is probably the level you want to work in doing ddrescue, but the level you want is completely up to you.  ddrescue is dumb. It copies bits from A ---> B.  That's it.  The human typing the commands needs to ensure that "A" and "B" are appropriate for the desired task.  The computer can't tell if the command it stupid or genius .... sometimes both.  Copying bits from A-->B is very powerful, since we can copy from a device to a normal file or from a normal file into a device.  We can copy from a whole drive device into a file or a partition too.  Very powerful, but only if you understand why those things can be useful.

Since you never shared the fstab, I cannot guess what the device file is.  You've only said what the mount point for the file system was. That isn't the same thing.

---

### Post by peyre on 2022-10-18
Oh!  I see.  Well, to find the device file, I should be able to use gparted, I would think.  It shows them as /dev/sda, /dev/sdb, etc.  Does that sound right?

I haven't included my fstab partly because I don't see how it could be the source of the problem--since the issue started *during* a session, and the drive shows blank when I hook it up to other machines via an enclosure.

---

### Post by TheFu on 2022-10-18
> **peyre said:**
> Oh!  I see.  Well, to find the device file, I should be able to use gparted, I would think.  It shows them as /dev/sda, /dev/sdb, etc.  Does that sound right?

I haven't included my fstab partly because I don't see how it could be the source of the problem--since the issue started *during* a session, and the drive shows blank when I hook it up to other machines via an enclosure.

NO.  Probably NOT what you want, but I don't know. Again, it could be genius or stupid. I cannot tell, but I'm leaning towards "stupid" now.  BTW, I learned the difference the hard way myself - wiping an entire drive when that wasn't my intent.

Learn what device files map to which devices BEFORE you make mistakes.

Of course, if you just want to wipe the entire drive, that's easier.  Use /dev/zero as the source/input device file.  But that probably isn't what you really want, is it?

Is the fstab some super secret thing to be hidden?  I'm happy to post mine, but doubt they'd be useful, since I use LVM and my device file names are completely different from what is on your system(s), I suspect.

---

### Post by peyre on 2022-10-18
No, there's no secret to my fstab - it's just that it's at home, not here.  I'll bring it in tomorrow morning.

I've used the /dev/sd* information from gparted to successfully [FONT=Courier New]shred[/FONT] USB drives we needed securely wiped.  Seemed like that would work for this as well--but, I guess not.

---

### Post by peyre on 2022-10-18
No, there's no secret about my fstab - it's just that it's at home, not here.  I'll bring it in tomorrow morning.

I'd definitely rather not wipe this drive before I can recover my data from it, if that's even possible (it's starting not to look hopeful).

I've used the /dev/sd* information from gparted to successfully [FONT=Courier New]shred[/FONT] USB drives we needed securely wiped.  Seemed like that would work for identifying device files for this purpose as well--but, I guess not.

---

### Post by peyre on 2022-10-18
What the...?  I'll be d**ned - my fstab is almost empty; all it contains is a remmed out statement about mounting floppy disks.

I copied the contents of my fstab.bak into it (I did at least make some backup of it at one point!) but the machine still won't boot.  In any case I don't see how this would have affected my data disk, though it might be preventing my GUI from opening (which I'm working on in [https://ubuntuforums.org/showthread.php?t=2480028](https://ubuntuforums.org/showthread.php?t=2480028)).

**Here's the contents of fstab at the moment, with the contents of fstab.bak pasted in, with the one line that was in it this evening at the bottom.**  The contents of fstab.bak I think were from before I wiped the drive and reinstalled from scratch a few months ago.

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb3 during installation
UUID=526d1aaf-fab5-4dbf-9d57-8919cf91a3c2 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sdb2 during installation
UUID=3D1B-BAAB  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# mount sdc1 on /data
UUID="002e92c4-784a-4cb3-9d52-4171af4804c8"  /home/leon/Storage             ext4    defaults  0       2


# mount floppy disks

---

### Post by TheFu on 2022-10-19
```
UUID=526d1aaf-fab5-4dbf-9d57-8919cf91a3c2 / ext4 errors=remount-ro 0 1
 UUID=3D1B-BAAB /boot/efi vfat umask=0077 0 1

/swapfile none swap sw 0 0

/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0

# mount sdc1 on /data
UUID="002e92c4-784a-4cb3-9d52-4171af4804c8" /home/leon/Storage ext4 defaults 0 2
```
Those are the important lines.  You need to use 'blkid' to look up the UUID -to- device name mapping.  I dislike using UUIDs, but with some setups, it is the least bad choice.

I also hate, hate, hate, hate, using swapfiles.  Use a swap partition or swap logical volume instead.
Mounting extra storage under a single user's HOME is a bad practice for a number of reasons.  Best to mount it somewhere else, perhaps /Storage, then create a symbolic link from your HOME to that location for easy access.  

That would be 
```

$ sudo mkdir /Storage
$ sudoedit /etc/fstab
```
Contents for that last line:
```
UUID=002e92c4-784a-4cb3-9d52-4171af4804c8 /Storage ext4 defaults 0 2
```

I'm not a fan of "defaults" for the mount options on ext4 file systems.
```
UUID=002e92c4-784a-4cb3-9d52-4171af4804c8      /Storage     ext4     nofail,noatime,errors=remount-ro     0     2
```
 is what I'd use. Don't worry about the extra spaces. 1 or more spaces in the fstab are the same, provided there are 6 groups of entries, never more.  No spaces are allowed in the options, that's the main thing.  If you put a LABEL on the partition (gparted can do that), say  "STORAGE", then you could use this fstab entry:
```
LABEL=STORAGE        /Storage     ext4     nofail,noatime,errors=remount-ro     0     2
```
Much easier for a human. If a label isn't in the right place (on the partition with the file system, that won't work.

---

### Post by peyre on 2022-10-19
Thanks!  I'll try that tonight.  FWIW, when I installed Xubuntu I let it do its default partition structure - I haven't messed with the swap space.

When I first set it up a few months ago, I mounted it as /home/leon/Storage because that worked, but figured that wasn't a best practice, so I moved it to /media/Storage.  So this backup file must be from just before I moved the drive to /media/Storage.

---

### Post by TheFu on 2022-10-19
Default storage is seldom a good idea for anything other than play installs, IMHO.  There are lots of threads in these forums about a good way to setup storage.  Ignore any for releases before 20.04, since Canonical drastically increased the amount of bloat in 20.04 and later releases.  What used to fit in 20GB now needs 35G or more.
In general, for non-toy installs with real users, I have at least 4 logical volumes.
/  (35G)
/var (4GB)
/boot (700MB)
and 
swap (4.1GB).

The size of HOME depends on many things, mainly the purpose of the system.  If end users are going to have logins and data on the system, I'll probably give them 2G each and have network storage mounted via NFS they can access for writing larger data into. The sizes are all about my backup and recovery methods.  I really don't want huge amounts of data on end user workstations.  I want to force them to put data on storage servers.

For a toy install, I'll likely allow the default, but move to a swap LV - I hate swapfiles. They have lots of limitations that should work, but don't. They also eat storage in /.  LVM makes resizing any logical volume bigger while it is running about 5 seconds of effort. No reboot needed. No editing the fstab.  Of course, using LVM does add complexity for the increased flexibility.  If you use lots of snaps, you may need to increase the LV for /var.  Again, that's 5 seconds of effort, so don't worry about it until it is needed.  I try to allocate as little of the available storage for use until it is needed and on SSDs, I try to leave 20% of the total size unused to aid with SSD lifespan.  My laptop has a 500GB SSD, but I'm using less than 250GB, for example.  When I travel, I'll create a 100G LV just for crap like music and videos to watch while stuck in a hotel room in a new city.  That temporary storage isn't backed up and I don't care if everything inside it is lost.

---

