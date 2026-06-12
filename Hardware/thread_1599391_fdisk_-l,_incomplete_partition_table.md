---
title: "fdisk -l, incomplete partition table"
date: 2010-10-17
forum: Hardware
---

### Post by ubfan01 on 2010-10-17
Dear all

On Dell inspiron 1545, I use dual Win XP as well as Ubuntu. In WinXP I deleted a partition and then on restart, I got an error "no such partition, grub rescue ". To resolve the problem I tried to repair the grub using Ubuntu Live CD. But using terminal, unfortunately the command "fdisk -l"  does not show me the partition where ubuntu is installed. It only shows 

/dev/sda1 for HPFS/NTFS, 
/dev/sda2 for W95 Ext'd (LBA)
/dev/sda5 for  W95 FAT(LBA)

Please see the attached screen shot of terminal window.

Now I really dont know that which partition I mount to install new grub. Please help me. :(:(

Thanks in advance

---

### Post by garvinrick4 on 2010-10-17
sda5 looks like it was one time a linux partition. sda2 is the extended partition and sda5 is where logical partitions(linux partitions reside) start and it is now Fat partitition. Did you mess with sda2 or sda5 ? Any which way linux is in ext4 format nowadays.

---

### Post by ubfan01 on 2010-10-18
Thanks for your reply. Before messing up, the 250GB harddisk was divide as follows:
**_Win XP:_**
Partition C (40GB)
Partition D (50GB)
Partition E (50GB) 

**_Ubuntu:_**
Installed on rest of 150GB of the harddisk

Then I deleted partition D in Win XP and from there I did something horribly wrong.

**Now before reinstalling Win XP/Ubuntu, [COLOR="Red"]I am only interested in saving my data[/COLOR]** which was saved in "Documents" folder in Ubuntu. Please advice me some solution to access that data.

---

### Post by garvinrick4 on 2010-10-18
I know not a single way of recouping data after has been formatted over. You were in ext4 format and I would just google and google for a while and see if there is a application that is out there that does that kind of thing. I keep back-ups of all data be it any operating System. A long time ago I used to bring costumer drives to companies and or services that did this before Windows and they would collect data from bad drives, was expensive. I am sure for a price there is a way, up to you and how far you want to go with your efforts. Good luck to you

---

### Post by srs5694 on 2010-10-18
The data have almost certainly *not* been "formatted over." Note that the last used cylinder, according to the fdisk output, is 11218; but the disk goes up to cylinder 30401. Thus, there's a lot of space that's *unallocated,* but (probably) not erased.

In fact, I think I know what happened: Logical partitions are defined in what's known as a "linked-list" data structure, in which one element points to another which points to the next one and so on. Every link in the chain needs to be valid for this to work. When you deleted the Windows D: drive, the Windows partitioning software messed up the links to the Linux partitions, making them disappear.

The solution is to use [TestDisk](http://www.cgsecurity.org/wiki/TestDisk) to search the disk for filesystem signatures and restore them. This will probably bring back not only the Linux partitions, but also the Windows D: partition, or at least giving you the option to restore it. If you restore the D: partition, I recommend deleting it using Linux's fdisk to avoid whatever bug in the Windows partitioner created this mess in the first place.

---

### Post by garvinrick4 on 2010-10-18
I just presumed he had a 50 gig linux in sda5 logical and the extended was 200 gig and he had 150 unallocated on the get go. I hope you are right for his sake. And he does say he installed linux in the unallocated which is now unallocated again. Was it just deleted or part of the Horribly wrong OP talks about. HMMM
Let us know how it turns out partner. Good luck

---

### Post by srs5694 on 2010-10-18
Ubfan01 reported initially having three Windows partitions (C:, D:, and E: in Windows terminology; no report on what they were called in Linux). There are now apparently two Windows partitions (/dev/sda1 and /dev/sda5), which matches with the description of having deleted one. This is consistent with the hypothesis that the partitioning utility "lost" the Linux partitions.

FWIW, I've had this happen to me in the past, although I was using some obscure partitioning tool in an effort to resize an extended partition, IIRC. Linked-list data structures are susceptible to this sort of problem, unfortunately. It's one of MBR's more obscure problems.

---

### Post by efflandt on 2010-10-19
It looks like your Ubuntu partition may have been /dev/sda6, and that may have been what you accidentally deleted.

I would first try running **sudo fdisk**  from install CD or USB and use it to create a "logical" partition at default start (likely 11219) and default end (likely 30402), then see if Ubuntu is able to boot.

But if the partition was created with Ubuntu 10.04 or 10.10 without using **partman/alignment=cylinder** kernel boot parameter during install, it might be aligned to MB boundaries instead of cylinder boundaries, and that may be more difficult to figure out.  If the partition was created with 9.10 or earlier, default start and end should work fine.

---

### Post by srs5694 on 2010-10-19
I wouldn't recommend creating partitions "blind," as efflandt suggests. The trouble, at least for logical partitions, is that creating a logical partition requires writing one sector of data to the disk shortly before where the partition begins. Thus, if your guess about where the partition begins is too late on the disk, you'll end up overwriting some random sector of the real partition. This could badly damage filesystem data, making it harder to recover the system. Furthermore, if there was more than one partition (say, separate root and swap partitions), you won't know where the end point is.

Furthermore, as ubfan01 reports having successfully deleted a FAT partition, it's likely that the first partition found on the disk will in fact be that FAT partition. If so, creating a single big partition in the remaining disk space will, at best, recover that one FAT filesystem in a too-big partition. (The partition will contain two or more filesystems, but only the first will be readily accessible.)

IMHO, it's much better to use TestDisk, as I suggested in my earlier post to this thread. That tool looks for filesystem signatures, and from there it can determine the correct start location and, using filesystem size, the correct end location for a lost partition. It then repeats the process after the partition it's just recovered. This process can work quite well, although it can also be thrown off if the disk has been repartitioned -- there could be old data that it will detect before it detects the filesystem you really want. Since it doesn't write anything to disk until you've confirmed what you want to recover, though, it's fairly safe to at least run it and see if it generates something reasonable.

---

