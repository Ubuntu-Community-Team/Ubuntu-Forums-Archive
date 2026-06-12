---
title: "40 gig Hitachi hard drive, partition/format help"
date: 2005-10-11
forum: Hardware &amp; Laptops
---

### Post by 11hjpphty76lkjj on 2005-10-11
Hello,

Here is my setup.  I have a 40 gig hitachi hard drive in a USB hard drive enclosure and I'm booting Hoary from the USB hard drive.

Currently I have 13 gig partitioned for Ubuntu, and it's working great.  I have 1 gig or so for the swap.  so that means i have like 23 gig's unpartitioned.  My original thought was I'd leave 20 gigs for fat32 so I can move data between a Windows box.  But now I don't need to do that.  And I want to format the extra 23 gigs to either 1 or 2 ext3 partitions.  Sounds straight forward enough.  I've created the partitions using gparted (gnome app) and I'm using the command line to format the partitions to ext3.

However EVERY time I try to format the parititons the system locks up hard.  I've tried restarting X, switching to anothe console, nothing.  All frozen.  Only way that I've found is to power off and reboot, and then Ubuntu loads fine, but the partitions are not formated.

I've tried different partitions sizes thinking maybe there is a bad spot or something.  Same thing.  I can take it to a windows machine and format it (I didn't do quick format) to FAT32, no problem.  I've had windows check the partition, no errors or bad sectors found. (using chkdsk /f I believe)

What in the world is going on here..how do I get this partition/s setup.  I need the space and I'm wasting 20 gig doing nothing with it.

How can I get this to work?
How can I check the partition for bad sectors and such?
Can I use a windows app to format the partition to ext3? (I do not want to do that..)
Can I use the Ubuntu boot rescue cd to repartition without killing my main partition?
Any other ideas?

Thanks ahead of time.

Aaron

---

### Post by glug101 on 2005-10-11
I would give the live cd (not the install cd) a try.  If that locks then this might be a different issue. (however I would wager that the livecd will do it)

Hope things go smooth for ya!

---

### Post by 11hjpphty76lkjj on 2005-10-11
Okay, 

I booted on to the livecd (where I am right now).  Installed gparted.  Repartitioned the empty space to one 23 gig hard drive.  Went to terminal and typed:

mkfs.ext3 -jcv /dev/sdb3

It started the process and then somewhere during the badblock test is exited x windows and droped to the console.  So I restarted x and try it again, this time it didn't exit X windows but it just froze at about 2000000/5000000. So about half way through the test.

****

root@dhcp:/home/ubuntu # mkfs.ext3 -jcv /dev/sdb3
mke2fs 1.35 (28-Feb-2004)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
2965504 inodes, 5927985 blocks
296399 blocks (5.00%) reserved for the super user
First data block=0
181 block groups
32768 blocks per group, 32768 fragments per group
16384 inodes per group
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
        4096000

Running command: badblocks -b 4096 -s /dev/sdb3 5927985
Checking for bad blocks (read-only test):   2226360/  5927985

****

Then I exited terminal and restarted gparted.  gparted didn't see the usb hard drive anymore.  So I unplugged it and plugged it back in and now gparted see's the usb hard drive and partitions.

Now i'm making 2 partitions--one that is 10 gig and one that is 13 gig.  and going to try and format the 10 gig to ext3.  This is very frustrating.

---

### Post by 11hjpphty76lkjj on 2005-10-11
```
root@dhcp56247:/home/ubuntu # mkfs.ext3 -jcv /dev/sdc4
mke2fs 1.35 (28-Feb-2004)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
1300480 inodes, 2600521 blocks
130026 blocks (5.00%) reserved for the super user
First data block=0
80 block groups
32768 blocks per group, 32768 fragments per group
16256 inodes per group
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632

Running command: badblocks -b 4096 -s /dev/sdc4 2600521
Checking for bad blocks (read-only test):   2195392/  2600521

```

And she locks up again at this point.

](*,) Ouch 
](*,) Ouch
](*,) Oh that's better.

Aaron

---

### Post by 11hjpphty76lkjj on 2005-10-11
Okay this time I tried creating a logical drive instead of primary, and tried just formating it instead of doing the block check.  It froze up again during writing idnode: 90/180

Help?

Aaron

---

### Post by 11hjpphty76lkjj on 2005-10-11
I am so confused.  So I formated the drive to fat32 with gparted.  And it worked.  No problem.  I tried ext2 and ext3 both lock up the system.  What the?????????

Aaron

---

### Post by glug101 on 2005-10-12
[QUOTE=kalosaurusrex]I am so confused.  So I formated the drive to fat32 with gparted.  And it worked.  No problem.  I tried ext2 and ext3 both lock up the system.  What the?????????

Aaron[/QUOTE]

Good question.  I must admit that I am completely baffled by this one.  I would suspect a hardware problem... but it worked fine under windows.  Might be a Linux driver problem with the USB drive... but you said that you formatted fat32 without incident under Linux.

I wish I could be of more help because it feels like I'm missing something basic here.

---

