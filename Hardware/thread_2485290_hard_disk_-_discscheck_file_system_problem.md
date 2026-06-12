---
title: "hard disk - discs/check file system problem"
date: 2023-03-25
forum: Hardware
---

### Post by jgw on 2023-03-25
I was checking things out on a system.  I opened Discs to see what I had (3 discs).  So I clicked on one and told it to check the filesystem.  I don't remember it Disks told me there was a problem or not.  I, however, then tried to check the data on the disks and was told there was NOTHING on the disk!  I have now taken the disk out and can access it from another machine (don't currently know what is going on).  I have yet to access it and, hopefully, somebody can tell me if/how I can save what is on that drive (I googled this and got 91,000 replies so I am trying to narrow the gap)

Thank you....

---

### Post by Bashing-om on 2023-03-25
jgw; Ouchie ..

Hey does Bios see the drives ? loose power to the drive ?

If Bios sees the drive - does the kernel ?
what shows:
```

sudo fdisk -lu

```

Are any of the partitions on the drive mounted ?
```

mount

```

Else - can you mount a partition on the drive manually ?

[INDENT]nothing happens without a reason
[/INDENT]

---

### Post by jgw on 2023-03-26
Thanks for the reply!

I have removed the drive and have it as an external drive.  I have done nothing but make sure it knows its there and, according to disks, it does.  the problem is that it says that its:
 
DRIVE    
Generic ATA/ATAPI Device

The only thing available is to Edit Mount Options

Also tried Gparted but it doesn't recognize it

I'm tempted to edit the mount options and see what happens but fear I might do that wrong.  

Thoughts?

---

### Post by Bashing-om on 2023-03-26
jgw; Humm ...

If Gparted does not see the drive - there is indeed a problem.
does 'fdisk -lu ' show the drive ?

What is the end result for using this drive ?

If 'fdisk' sees - then from that info we can attempt to mount the drive manually.

[INDENT]maybe Yes
[INDENT]could be not so yes[/INDENT][/INDENT]

---

### Post by jgw on 2023-03-26
fdisk -lu gets me about 30 lines that look like (first two lines):
fdisk: cannot open /dev/sda: Permission denied
fdisk: cannot open /dev/loop8: Permission denied

Disks tell me: Generic ATA/ATAPI Device (0036) followed by a serial number.
I can also open the computer and install the drive instead of doing what I am doing now  

I can also deal with the disks boot thing and see what happens.  (kinda scary)

Disk also tells me there is no media on the drive.  We are dealing with a 3tb hard drive.  Disks is, I think, a bit confused.  Disks, basically, doesn't even have the size.

There there is stuff like I found at: [https://www.digitalocean.com/community/tutorials/top-best-linux-data-recovery-tools](https://www.digitalocean.com/community/tutorials/top-best-linux-data-recovery-tools)

Thoughts?

---

### Post by Bashing-om on 2023-03-26
jgw; Well ...


My thoughts --
I have yet to get beyond what
```

sudo fdisk -lu

```
has to tell us .

Please post that result so I see what we have to work with - it not have to work with. 

-We have done so much
-for so long
-with so little
-we can now do the impossible
-with nothing

[INDENT][INDENT]nOoo - not yet !
[/INDENT][/INDENT]

---

### Post by jgw on 2023-03-26
fdisk -lu gets me about 30 lines that look like (first two lines):
fdisk: cannot open /dev/sda: Permission denied
fdisk: cannot open /dev/loop8: Permission denied

Disks tell me: Generic ATA/ATAPI Device (0036) followed by a serial number.
I can also open the computer and install the drive instead of doing what I am doing now  

I can also deal with the disks boot thing and see what happens.  (kinda scary)

Thoughts?

---

### Post by jgw on 2023-03-26
Here is where the results are: [https://pastebin.com/HwANPjWE](https://pastebin.com/HwANPjWE)

I spent a lot of time trying to remember where to past stuff for ubuntu.  Never did find it.

---

### Post by Bashing-om on 2023-03-26
jgw; Hummm ...

"fdisk" only shows one drive, As it does not see the other drive(s), all at this point I can suggest is to insure that the drive connectors are clean ( contact cleaner in a can ) and perhaps change the SATA cable ?

Until the kernel sees the drive - not a thing we can do.

[INDENT]is it dead, Jim ?
[/INDENT]

---

### Post by jgw on 2023-03-27
I surrender!  I also thank for all the help - we tried! 

I think I will take the drive apart and rescue the magnet (hard drives have very strong magnets - good for fishing for stuff off of piers to pass the time of day.  Sometimes one can get lucky and finda crab track full and abandoned.

---

### Post by jgw on 2023-03-28
I should probably start a new thread but I will see what happens here.  

I decided to run synaptic on my system and it kept finding things to fix and do.  I had to run it about 4 times!  anyway, I now kinda have access to the bad drive as it appeared.  I am currently backing up the two folders on it.  If that is successful I think I will run a program over the drive to fix stuff that might be wrong (have no idea what might be found).  

So, I would appreciate a suggestion as to what program I should use to try and fix the hard drive.  Since I will have backed up the stuff on it I won't be worried about hurting anything.

Thank you..................

---

### Post by SeijiSensei on 2023-03-28
You can create a new ext4 filesystem and check the drive for bad blocks at the same time with:
```
sudo mkfs -t ext4 -c /dev/sdX
```
where "/dev/sdX" refers to the partition to be formatted.

From "man mkfs.ext4":
```
-c     Check the device for bad blocks before creating the file system.  If this option is  specified  twice,
              then a slower read-write test is used instead of a fast read-only test.
```

Running the badblocks program can take hours, especially if you use read/write testing.

---

