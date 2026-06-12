---
title: "Reformatting an external hard drive, FAT32 - EXT3 problems"
date: 2010-03-19
forum: Hardware
---

### Post by hihihi100 on 2010-03-19
Hi there:

I have recently bought a 500 GB Samsung external hard drive, which the vendor formatted using FAT32, the standard i have been using for the 2 days that have passed since the acquisition. Later, I decided to re format the volume in this linux based standard (EXT3), but, after the process, Gparted shows that 25 GBs of the drive are in use, 25 GBs of data i cannot access, erase, not even read. Again, I have re formatted, for a second time, the external hard drive, this time choosing FAT32. After the process, those 25 GBs of junk are gone, and I can enjoy the whole 500 Gbs of the hard drive. Now, for the third time I have re formatted the hard drive, using EXT3 this time, the standard I have decided to use, and those 25 Gbs of data I cannot access, read, edit, whatever, are there again.
 

 Any tips? Cause I have no idea the reason why 25 Gbs of memory can be lost, just by changing from FAT32 to EXT3.

Almost forgot: the name of the folder that contains the 25 GBs of data is called "lost+found"
 

 Cheers

---

### Post by coffeecat on 2010-03-19
Let's start here:

> **hihihi100 said:**
> Almost forgot: the name of the folder that contains the 25 GBs of data is called "lost+found"

The lost+found folder in an ext3/4 filesystem is the location where corrupted files are placed when they are found during a filesystem check. Normally, it will be empty. So, if you have 25GB of files in lost+found either something very strange happened when you created the filesystem or there's something you are not telling us. :wink:

Ext3 is a journalled filesystem and the journal takes up quite a bit of space - in my systems about 2% of the total space. This is necessary in a journalled filesystem. Fat32 is not journalled so there's only the file allocation table to worry about. Downside: corrupt a FAT32 filesystem and you've probably lost your data.

25GB is 5% of 500GB so that seems a bit big. Can you give us the exact figures that Gparted reports?

---

### Post by hihihi100 on 2010-03-19
Thk for the prompt answer:

U r kinda right, I made a mistake regarding the percentages, but only partially:

THis is what Gparted shows:

File system: ext3
Size: 465.76 GiB
Used: 7.50 GiB
Unused: 458.26 GiB

And those figures concur with the 2% u mention. However, if I right click on the external drive icon, and go to properties, in basic:

Contents: 1 item, with size 16.0 KB (some contents unreadable)
Free space: 435.0 GB
23.5 GB used
435.0 GB free
Total capacity: 458.4 GB
Filesystem type: ext3/ext4

This is where I got the 25 GB (well, 23.5 GB) figure

Hope you can explain to me the different figures regarding used space: 7.50 GB and 23.5 GB

CHeers

---

### Post by coffeecat on 2010-03-19
Well, that's most interesting. You've pointed out something I hadn't noticed before. The figures in Gparted and right-click > properties don't agree.

I've mounted an empty ext4 internal partition. Gparted shows this as:

Size - 24.07 GiB
Used - 558.82 MiB

Which is about 2%

But right-click > properties, I see:

Total - 23.7 GB
Used - 1.4GB

~ 6%

And if I look in System > Administration > System Monitor > File Systems tab, I see:

Total - 23.7 GiB
Used - 171.9 MiB

~ 0.7%
:lol:

Clearly there's something not right here, but I don't know which one is at fault. Also, GiB refers to Gibibytes (= 1,073,741,824bytes = 1024 mebibytes), whereas GB usually refers to 1,000,000,000 bytes. (Which is how manufacturers get away with calling 465GiB drives 500GB.) And the properties pie chart seems to be reporting GiB but calling them GB.

Anyway, clearly some confusion there which I'll look into tomorrow - too late here and too tired atm.

But the main message is that you always lose some space on a journalled filesystem to the journal, but whether it would be 5-6%, 2% or less than 1%, I'll need to read up on.

---

### Post by srs5694 on 2010-03-19
Ext2/3/4 enables setting aside a fixed percentage of the disk space for use by root. The idea is that if a user process runs out of control and fills the hard disk, the administrator will still have enough free space to log in and fix the problem. By default, these filesystems set aside 5% of the disk space for this purpose. Unfortunately, 5% adds up to a lot of space on big modern drives. You can change the percentage on an already-formatted filesystem using the text-mode tune2fs program. For instance, if the partition in question is /dev/sdb1 and if it's mounted at /path/to/drive:

```

sudo umount /path/to/drive
sudo tune2fs -m 0

```

This sets the reserved blocks percentage to 0. Change the number after the -m parameter if you still want to reserve some disk space, just less than the default. A similar option to mke2fs will change the reserved blocks percentage when the filesystem is created.

Alternatively, you could use something other than ext2/3/4 to begin with. AFAIK, ReiserFS, JFS, and XFS don't reserve any space in this way. ReiserFS is particularly good for storing many very small files, since it can cram small files into less space than most other filesystems require. (I don't recall if it shows more or less free space than ext3fs immediately after format, but that's unimportant; when you add many small files, ReiserFS can definitely hold more files.) JFS and XFS are both excellent at handling very large files (multimedia recordings, system backup files, etc.), with XFS being a bit more well-respected in this regard. You could reformat using mkfs:

```

sudo mkfs -t xfs /dev/sdb1

```

FWIW, my personal preference is to use ReiserFS for my main Linux installation and most other general-purpose uses, with XFS for bigger filesystems that hold larger files.

---

### Post by hihihi100 on 2010-03-20
About the reserved blocks percentage... would you recommend, for the _external_ hard drive, to reserve a small  percentage? I just want to use the external hard drive to store data, mainly multimedia, no OS.

I mention this because if my laptop has ext3 as the standard, it means that the _internal_ hard drive of the laptop also reserves that 5% of blocks for the rationale u mention. In this case, we are talking about an OS (unlike the external hard drive). Would you recommend me to reserve a percentage of blocks in the internal hard drive, bigger than the external one (maybe 2%), and to just set the external reserved blocks percentage to, if not 0, maybe 0.5% or 1%?

and about the other standards u mention: well, the smallest file I want to store in the external hard drive occupies 15 MB, and the largest one occupies 130 MB... are those figures too small? too big?

And, if I set the percentage to 2%, can I, later, set it to 3% without formatting the hard drive?

Cheers

---

### Post by srs5694 on 2010-03-20
With ext*fs, you can change the reserved block percentage at any time, so long as the disk has enough free space to support the new percentage. (Maybe even if it doesn't; I've never tried increasing it past the amount of available space.)

I can't think of a good reason you'd need much, if any, reserved free space on an external drive, especially one that's used for ordinary user data. If the drive were necessary for emergency repairs, then maybe, but it doesn't sound like that's the case.

As to filesystem choice, you'll see little or no increase in the number of files you can store on ReiserFS vs. ext*fs with files in the 15MB-to-130MB range. You might start to see some advantage to JFS or XFS at the top of that range, but not a whole lot. Thus, I think you'll be good with ext3fs, ext4fs, JFS, or XFS on your external drive.

---

### Post by hihihi100 on 2010-03-20
It seems im a total useless user:

In Gparted I can see that the external drive is Mounted on /media/Volume 1, so thats what I type right after "sudo umount", like:

sudo umount /media/Volume 1

to get:

sudo umount /media/Volume 1
umount: /media/Volume: not found
umount: 1: not found

I have tried typing - between Volume and 1 (Volume-1), same with _, to not avail.

What am I doing wrong?

I dont know if this may help:

If I just type sudo umount /media:

sudo umount /media
umount: /media: not mounted

then:

sudo tune2fs -m 1
tune2fs 1.41.9 (22-Aug-2009)
Usage: tune2fs [-c max_mounts_count] [-e errors_behavior] [-g group]
    [-i interval[d|m|w]] [-j] [-J journal_options] [-l]
    [-m reserved_blocks_percent] [-o [^]mount_options[,...]] 
    [-r reserved_blocks_count] [-u user] [-C mount_count] [-L volume_label]
    [-M last_mounted_dir] [-O [^]feature[,...]]
    [-E extended-option[,...]] [-T last_check_time] [-U UUID]
    [ -I new_inode_size ] device

---

### Post by srs5694 on 2010-03-20
If a file or directory contains a space in its name, you can specify it on the command line in either of two ways:


[list]
[*]Put a backslash ("\") before the space, as in 'sudo umount /media/Volume\ 1'
[*]Put double quotes around the whole filename, including its path (if specified), as in 'sudo umount "/media/Volume 1"'
[/list]

---

### Post by hihihi100 on 2010-03-20
Hi there...

Thx again for ur prompt answer, but I havent been able to do it following ur instructions.

However, after typing:

*[I]sudo tune2fs -m 1 /dev/sdb1*[/I]
I succesfully set the percentage to 1%

Setting reserved blocks percentage to 1% (1220960 blocks)

It may habe been my lousy computing skills, or maybe that adding the "/dev/sdb1" at the end of the line was too obvious for you (not for a noob like me), but thanks anyway.

Are you running Ubuntu 9.10? does it make a difference if the user runs a Ubuntu 9.04 or 8.10?

---

### Post by srs5694 on 2010-03-20
Sorry; I did indeed forget the "/dev/sdb1" when I first specified the tune2fs command.

The tune2fs utility has existed for many years and is delivered with just about every version of Linux that's intended for desktop or server use. It should work fine between Ubuntu 9.04 and 8.10, at least for ext2 and ext3 filesystems. (I'm not sure about the exact milestones in ext4fs developments with respect to those two Ubuntu versions.)

---

