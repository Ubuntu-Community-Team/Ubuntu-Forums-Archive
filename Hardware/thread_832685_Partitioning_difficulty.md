---
title: "Partitioning difficulty"
date: 2008-06-17
forum: Hardware
---

### Post by untermensch on 2008-06-17
I have a 60gb ATA hard drive, that currently is mostly NTFS. It already has one partition to form the windows known "d" drive(FAT32) which keeps all the windows recovery stuff on it. I went to partition the hard drive to make room for an ext3 partition for ubuntu. This is where it gets odd. I tried gparted, When the drive is mounted it can see used and free space, but it can't partition it cause well.. it's mounted. However, when I unmount it, it can no longer see the used space, just the total amount and consequently it wont let me partition it. I've tried: Gparted, magic partition, 7.10, 8.04, and 8.04 alt cd to try to find a partitioner that would work, but so far I have yet to be able to scan my drive properly when the drive is not mounted. Can anyone help?

---

### Post by Odrodzona-Sarmacja on 2008-06-18
Download Gparted livecd iso and burn it on a cd, then boot up with it. It should do the trick. Good luck!

---

### Post by untermensch on 2008-06-19
The Gparted live cd did not work.

---

### Post by tubbygweilo on 2008-06-19
A few [screen shots]("http://gparted.sourceforge.net/screenshots.php") from the Gparted documentation may give you an idea as to what is and is not possible using the LiveCD.

Were you able to select the Gparted options such as type of screen, type of keyboard & language prior to having Gparted display your disks? 
What type of error did Gparted produce?

---

### Post by untermensch on 2008-06-19
I did get to set up screen resolution and all that good stuff. When I got to partition the drive it just has total space, no used and no free. consequently I can't partition in.

---

### Post by untermensch on 2008-06-19
There were no error messages. it just showed a blank drive. (which I guess can't be partitioned cause I couldn't click on resize/move)

---

### Post by housam on 2008-06-19
Type in a terminal the following code :
```
sudo fdisk -l
```
where -l is the lower case of L and post the result.

---

### Post by untermensch on 2008-06-19
why would i wanna fdisk my drive?

---

### Post by Tomatz on 2008-06-19
> **untermensch said:**
> why would i wanna fdisk my drive?

-l = list drives

---

### Post by housam on 2008-06-19
we need to list your drives using fdisk to check if there is any overlapping between partitions. this could be the cause of your problem.

---

### Post by untermensch on 2008-06-19
Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94e494e4

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6324    50797498+   7  HPFS/NTFS
/dev/hda2            6326        7296     7799557+   c  W95 FAT32 (LBA)
untermensch@untermensch-laptop:~$ 



(is the result from fdisk -l

---

### Post by housam on 2008-06-19
Your partition table is ok, no overlapping between partitions.
What version of windows you have on that machine?

---

### Post by housam on 2008-06-19
You can try [[COLOR="Red"]_testdisk_[/COLOR]]("http://linuxappfinder.com/package/testdisk") to rearrange your partitions.
Here is how to use it :[[COLOR="Red"]_http://en.wikipedia.org/wiki/TestDisk_[/COLOR]]("http://en.wikipedia.org/wiki/TestDisk")

---

### Post by untermensch on 2008-06-19
I have windows xp.

---

### Post by untermensch on 2008-06-20
What exactly would testdisk do?

---

### Post by Odrodzona-Sarmacja on 2008-06-21
> **untermensch said:**
> Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94e494e4

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6324    50797498+   7  HPFS/NTFS
/dev/hda2            6326        7296     7799557+   c  W95 FAT32 (LBA)
untermensch@untermensch-laptop:~$ 



(is the result from fdisk -l

Imho you should run defrag on hda1 and then shrink it preferably with some windows partitioner like Partition Magic. Then use that partitioner or alternatively gparted livecd to create three ext3 partitions for ubuntu between hda1 and hda2. Minimum 8gb for "/", 2gb for "/home" and 512mb for "swap". Also if that hpfs/ntfs partition is filled up, then... well... you can't really shrink it without deleting something big for few gb on it, can you. ;)

Good luck!

---

### Post by untermensch on 2008-06-23
i can't partition. non of the partitioners i have used show my drives

---

### Post by Odrodzona-Sarmacja on 2008-06-25
> **untermensch said:**
> i can't partition. non of the partitioners i have used show my drives

You mean like you boot up with gparted and then you see just only one hard drive there? Yes?

In the right upper window of gparted is a label saying "/dev/hda" or "/dev/sda" or something alike... Now if you click on it there will be a listing of all hard drives on your computer together with their sizes. Now you need just click on the correct hard drive to go to its partitions.

Or do you mean your partitioner can't detect any hard drives connected to your computer at all?

---

### Post by untermensch on 2008-06-26
I only have one hard drive. (not the greatest comp ever) but when it is chosen, it shows the total space, but it doesn't show any free or used space.

---

### Post by Odrodzona-Sarmacja on 2008-06-26
I think you should look up problems with formating ntfs drives in general. I think it is something with ntfs locked for windows use only.
To force ntfs drive to mount I know this something do works on ubuntu:
"sudo mkdir /mnt/alabama"
"sudo mount -t ntfs-3g /dev/hda /mnt/alabama"
Maybe after forcing it, you will be able to access it with partitioner.

---

### Post by untermensch on 2008-06-27
That last one didn't work =\ Nothing is working so far. I tried ntfsfix but that gave me an error. I even got on *shivers* windows... and tried to scan the disk for errors but it came up with nothing.

---

### Post by untermensch on 2008-06-29
bump?

---

### Post by Aearenda on 2008-06-29
When you close Windows XP, are you shutting down or hibernating? I wonder if the partitioners are seeing an in-use hibernate file, and so preventing you from changing stuff that must not be changed while hibernated?

Also, in XP's disk management console (right-click on 'My Computer', choose manage, open 'disk management'), is the drive showing 'basic mode' along with the status details to the left of the partition map? I don't see how it could be anything else, but worth checking anyway.

BTW, the line ```
sudo mount -t ntfs-3g /dev/hda /mnt/alabama
```given in an earlier post should have had /dev/hda1, not /dev/hda.

Also, the fdisk -l output shows a one-cylinder gap between your partitions. I don't think there is anything wrong with that necessarily, but it's unusual.

Finally, are you sure you are running the partitioning programs using 'sudo' (or 'gksudo') to get admin rights? Sorry if this seems obvious, I'm just trying to rule out what might be wrong.

---

### Post by untermensch on 2008-06-29
> **Aearenda said:**
> When you close Windows XP, are you shutting down or hibernating? I wonder if the partitioners are seeing an in-use hibernate file, and so preventing you from changing stuff that must not be changed while hibernated?

Also, in XP's disk management console (right-click on 'My Computer', choose manage, open 'disk management'), is the drive showing 'basic mode' along with the status details to the left of the partition map? I don't see how it could be anything else, but worth checking anyway.

BTW, the line ```
sudo mount -t ntfs-3g /dev/hda /mnt/alabama
```given in an earlier post should have had /dev/hda1, not /dev/hda.

Also, the fdisk -l output shows a one-cylinder gap between your partitions. I don't think there is anything wrong with that necessarily, but it's unusual.

Yes I shut down, I rarely set it to hibernate.

I'll check xp in a second.

That could explain the error message. 

Yes there is an 8mb unused space between my "c" drive (ntfs) and my "d" drive (fat32)

---

### Post by untermensch on 2008-06-30
It is in basic mode. Is that bad?

---

### Post by Aearenda on 2008-06-30
That's good - it just means assumptions we've been making along the way are true, and the disk partitioning table is normal. 

OTOH, it's bad, because now we have no idea why you can't run GPartEd on that drive.

What's the result of:
1. Boot from an Ubuntu 8.04 liveCD and accept the language
2. Choose "Try without any change"
3. When it has come up start a command line
4. Type ```
sudo gparted /dev/hda
```
5. Look back at the terminal window - is there any output other than the 'libparted : 1.7.1' notice? 
6. Back in the GPartEd window, what happens if you select a partition and then try 'Resize/Move'?
7. Did any further output appear in the terminal window when you tried the resize?

---

### Post by untermensch on 2008-07-01
Can I only do this on a livecd? I just gave out my 8.04 copy. would gparted work ? I can always burn another 8.04

---

### Post by Aearenda on 2008-07-01
Best to do it from an Ubuntu CD because that's what I have - I can compare what you see with what I see and from there we try to work out what is different. Also, GPartEd doesn't start automatically, so we can use the command line to see what's happening. The version doesn't matter - 7.10 or 7.04 will do. Didn't you say the GParted CD didn't work (post 3)?

Unfortunately I'm about to go out again and will not be back for several hours, after which it will be night here, so my next reply will be slow in coming.

---

### Post by untermensch on 2008-07-01
Gparted didn't detect the disks either. I have a 7.10 cd so I'll try that first.  Lol, it's cool, I know what it's like to be busy.

---

### Post by untermensch on 2008-07-02
> **Aearenda said:**
> That's good - it just means assumptions we've been making along the way are true, and the disk partitioning table is normal. 

OTOH, it's bad, because now we have no idea why you can't run GPartEd on that drive.

What's the result of:
1. Boot from an Ubuntu 8.04 liveCD and accept the language
2. Choose "Try without any change"
3. When it has come up start a command line
4. Type ```
sudo gparted /dev/hda
```
5. Look back at the terminal window - is there any output other than the 'libparted : 1.7.1' notice? 
6. Back in the GPartEd window, what happens if you select a partition and then try 'Resize/Move'?
7. Did any further output appear in the terminal window when you tried the resize?

All the terminal output was libparted :1.7.1
All I can do to a partition is move it infront of or fill up the 8mb gap between my two current partitions. Nothing further came from the terminal

---

### Post by Aearenda on 2008-07-02
Good, then there is nothing intrinsically wrong with the drive layout. 

In Windows XP, how much free space does the NTFS partition have?

---

### Post by untermensch on 2008-07-02
I wanna say about 17 gigs? something like that.

---

### Post by Aearenda on 2008-07-03
Looks like you might need to install ntfsprogs to enable the resize feature in gparted on your CD. It ought to tell you that, I reckon. Anyway, if you start a command line on the liveCD and type 'man ntfsresize', does anything show up? If not, then do ```
sudo apt-get install ntfsprogs
``` and let that finish.

Then try ```
sudo ntfsresize -i /dev/hda1
``` and see what that tells you - it doesn't change anything, so it is quite safe to do, and it might tell us what the problem is.

I just checked on my Hardy Desktop CD, and ntfsprogs is definitely already there.

---

### Post by untermensch on 2008-07-03
What is ntfsprogs?

---

### Post by Aearenda on 2008-07-03
> What is ntfsprogs?
Its the package that contains ntfsresize, and other useful ntfs tools.

---

### Post by untermensch on 2008-07-05
this is the result i got from ntfs resize -i /dev/hda1

ubuntu@ubuntu:~$ sudo apt-get install ntfsprogs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ntfsprogs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ubuntu@ubuntu:~$ sudo ntfsresize -i /dev/hda1
ntfsresize v1.13.1 (libntfs 9:0:0)
Device name        : /dev/hda1
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 52016636416 bytes (52017 MB)
Current device size: 52016638464 bytes (52017 MB)
Checking filesystem consistency ...
100.00 percent completed
Accounting clusters ...
Cluster accounting failed at 3147732 (0x3007d4): extra cluster in $Bitmap
Filesystem check failed! Totally 1 cluster accounting mismatches.
ERROR: NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
and will be made to NTFS by this software until it gets repaired.

---

### Post by jocko on 2008-07-05
> **untermensch said:**
> ERROR: NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
and will be made to NTFS by this software until it gets repaired.

Did you do what it tells you to do? Did it solve the problem?

---

### Post by untermensch on 2008-07-05
I ran chkdsk /f and rebooted twice. then i booted up the livecd and tried sudo ntfsresize -i /dev/hda1

and i got this... 


ubuntu@ubuntu:~$ sudo ntfsresize -i /dev/hda1
ntfsresize v1.13.1 (libntfs 9:0:0)
Device name        : /dev/hda1
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 52016636416 bytes (52017 MB)
Current device size: 52016638464 bytes (52017 MB)
Checking filesystem consistency ...
100.00 percent completed
Accounting clusters ...
Space in use       : 42232 MB (81.2%)
Collecting resizing constraints ...
You might resize at 42231746560 bytes or 42232 MB (freeing 9785 MB).
Please make a test run using both the -n and -s options before real resizing!


Is that what i should've gotten?

---

### Post by untermensch on 2008-07-05
IT WORKED!! w00t! So now I'm going to take off wubi and make a fully dedicated ext3 partition=]. Thank you both very much! I've been trying to get this to work for months. THANK YOU!

---

### Post by Aearenda on 2008-07-05
Congratulations! I hope you made sure you have backups of your data :-)

---

### Post by untermensch on 2008-07-05
Backing it all up right now =] I can't wait to have a REAL Linux partition.

---

