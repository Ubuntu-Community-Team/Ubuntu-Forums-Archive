---
title: "Partition unusable!"
date: 2005-12-23
forum: Installation &amp; Upgrades
---

### Post by kalle314 on 2005-12-23
I tried to resize the windows ntfs partition to get room for another ubuntu partition.
However, when I did resize it, the 9 GB showed up as "Unusable" in the "edit partition table manually"-section of the 
When I chose the "unusable" partition, there is only one option:
"Show Cylinder/Head/Sector Information" which lets me see where this partition starts and ends. I cannot do anything to this partition.

The problem which caused this is probably that i alread had four partitions, which I just learned is the maximum.
1. Windows backup FAT (primary)
2. Windows NTFS (primary) (Here i did the resizing)
3. Ubuntu
4. Extended (including Swap)

When I try to use gparted, I can see this partition as unallocated, but I cannot do anything to it - all the other partitions show up as locked, and the resize option are "greyed out" for them.

Edit: Maybe gparted will be able to let the windows partition take back the unallocated partition if I unmount it from ubuntu. I'll try that.
Edit 2: With the windows partition unmounted, gparted says the following about it "Warning. Unable to read the contents of this filesystem, Because of this some operations may be unavailable." I still cannot increase this partition, only convert it (to FAT or some other format.)

---

### Post by bernardfrancois on 2005-12-23
Maybe it's a better idea to change the size of a windows partition under windows... You might try partition magic. It can resize partitions easily, I dunno if it works as well for ext2/ext3 partitions, but ext2/ext3 is supported in a certain level.

In fact I'm not really sure what you were doing... Were you trying to resize an NTFS partiton with gparted? NTFS is not usable under linux, unless you use something (I dunno the name, I don't use it) to work with the ntfs.dll file which you have if you have windows. But it might not be able to resize an NTFS file system using linux.

---

### Post by kalle314 on 2005-12-24
What I did was to resize the windows NTFS partition with the partitioner that the Ubuntu installer uses.

I have already used it to resize the windows partition once to make room for an Ubuntu partition.
Then I got a partition of some gigabytes of "Free Space" which I used to install ubuntu.

Since I didn't know about the four partition limit of a HD, I though a might resize the NTFS partiton again, to install a different ubuntu version (to get a windows-ubuntu-ubuntu triple boot system.)
The ubuntu installer partitioner did this, but instead of a 9 GB "Free space" partition, I got a 9 GB partition that was "unusable".

I downloaded the free evaluation copy of Partition Magic, and it claims it can resize the windows partition so that it uses that partition which is now unallocated, but will not do so unless I buy the program.

Edit: If anyone is interested, I did put back the unallocated memory into the ntfs partition, using the system rescue cd. 
I would have preferred to give the memory to the linux partition, but to do that I guess I will have to remove my current linux install because of the 4 partition limit.

---

### Post by bernardfrancois on 2005-12-27
I never heard of such a 4 partitions limit... My other computer has more partitions, on a single hard drive:
1. a windows NTFS partition
2. a windows FAT32 partition (which I have mounted in linux)
3. a linux ext3 partition (mounted on /)
4. a linux ext3 partition (mounted on my home directory)
5. a linux ext3 partition (mounted on /home/media, containing music and film)
6. a linux swap partition

Notice that after resizing a partition in the ubutnu installer's partitioner, it's probably normal that it wil be shown as 'unusable', that means that you still need to specify the type of the partition (probably selecting the partition with the cursor keys and pressing the return key will show the screen where you can change the settings of the partition).

---

### Post by mike_d on 2005-12-27
[QUOTE=bernardfrancois]I never heard of such a 4 partitions limit... [/QUOTE]

it's a limit on the number of primary partitions.  you can only have 4 primary partitions, to get more than 4 partitions, you use extented partitions which are partitions of a primary partition.  it's silly, but left in there because of legacy reasons.  outside of lowlevel partitioning programs (fdisk and the like), this is completely transparent to everything else.

so if you had 6 partitions on your disk they probably look like this:

[ [--hda1--] [--hda2--] [--hda3--] [ [--hda4--] [--hda5--] [--hda6--] ] ]

---

### Post by bernardfrancois on 2005-12-27
Ok, now I remember that kind of limit. Because most partitions on a system with multiple partitions are data partitions, most users never encounter this problem when they use a partitioner that does all the work automatically.

In the meantime, I thought of the partitioning of that particular computer, and I think one or two partitions might be on a different hard disk. I can't check it since that computer is in a different place (where I study).

---

### Post by Kasanax on 2005-12-27
I had a similar problem when I first installed Ubuntu. I'm real newbie, but having to go through the installation a few times (i think it was 5 times in total :rolleyes: ) taught me a thing or two.

Not sure about this (like I said, I'm a newbie!), but I seemed to have problems depending on whether i created a new partition at the beginning or end of an open space... basically, if I had things set up like:

[[hda1][hda2][free space][hda3]]

It wouldn't let me create any new partitions in the free space. Once I rearranged things, I was able to create all the new partitions I needed in order.

I now have 5 partition: the Dell recovery partition (FAT16), the WindowsXP partition (NTFS), Ubuntu (ext3), swap, and shared storage (FAT32).

As for shrinking one partition and expanding another, there I can't really help...

---

### Post by exchequer598 on 2007-10-18
> **kalle314 said:**
> I tried to resize the windows ntfs partition to get room for another ubuntu partition.
However, when I did resize it, the 9 GB showed up as "Unusable" in the "edit partition table manually"-section of the 
When I chose the "unusable" partition, there is only one option:
"Show Cylinder/Head/Sector Information" which lets me see where this partition starts and ends. I cannot do anything to this partition.

The problem which caused this is probably that i alread had four partitions, which I just learned is the maximum.
1. Windows backup FAT (primary)
2. Windows NTFS (primary) (Here i did the resizing)
3. Ubuntu
4. Extended (including Swap)

When I try to use gparted, I can see this partition as unallocated, but I cannot do anything to it - all the other partitions show up as locked, and the resize option are "greyed out" for them.

Edit: Maybe gparted will be able to let the windows partition take back the unallocated partition if I unmount it from ubuntu. I'll try that.
Edit 2: With the windows partition unmounted, gparted says the following about it "Warning. Unable to read the contents of this filesystem, Because of this some operations may be unavailable." I still cannot increase this partition, only convert it (to FAT or some other format.)

I have the same problem now when I tried installing Gutsy this morning! I was able to recover that unusable space using Partition Magic! But still I don't know a workaround. What can I do about the 4 primary partitions I have now? I want to resize a single 40 GB partition with the folloeing scheme: 

1. 15 GB - Gutsy
2. 14 GB - Windows XP SP2
3. 10 GB - Shared (FAT32)
4. 1 GB - Swap Area

Can someone please help me with my problem? I'm a total rookie as far as Ubuntu goes, so can someone explain it to me like I'm a 6-year old?

Thanks

---

### Post by crypticmystic on 2008-02-17
I just ran into this also, and there is a 4 partition limit for Primary partitions (you can have upto 128 logical partitions, I think)..  There is an ancient reason for this probably going back to the days of DOS, but regardless, when I went to make my swap space, and it asked me if I wanted to create a logical or primary partition, create the the last two partitions as logical, it all is well....

I vaguely remember that only bootable partitions need to be primary partitions (so the windows partition and the / partition for ubuntu)...  A quick google seems to confirm there is not difference between a logical and a primary partition otherwise...

---

