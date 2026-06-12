---
title: "changing /dev/sda* number"
date: 2012-01-13
forum: Hardware
---

### Post by Tares on 2012-01-13
hello,

is there a nice and clean way to change the partition numbers? 

I've recently deleted my sda1 and merged it with sda2, but the partition stayed sda2. I don't want to remove everything and create whole partition table from scratch.

---

### Post by coffeecat on 2012-01-13
The only way I know is to edit the partition table directly with the terminal command sfdisk. If you want to do this, run this command:

```
sudo sfdisk -d /dev/sda > Desktop/PT.txt
```

Then post the contents of PT.txt, which will appear on your desktop, between [noparse]```
 and 
```[/noparse] tags in order to preserve formatting. The simplest way of doing this is to highlight the output and then click on the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar.

Then we can take it from there.

---

### Post by Tares on 2012-01-13
```
  1 # partition table of /dev/sdb
  2 unit: sectors
  3 
  4 /dev/sdb1 : start=        0, size=        0, Id= 0
  5 /dev/sdb2 : start=     2048, size= 40996864, Id= 7, bootable
  6 /dev/sdb3 : start= 40998912, size=935770112, Id= f
  7 /dev/sdb4 : start=        0, size=        0, Id= 0
  8 /dev/sdb5 : start= 41000960, size=133175296, Id=83
  9 /dev/sdb6 : start=174176793, size=802592231, Id=83

```
I want to remove sdb1 and move everything up. sdb4 is a logical partition.


ps. I know how to use code tags :P

---

### Post by coffeecat on 2012-01-13
> **Tares said:**
> 
I want to remove sdb1 and move everything up. sdb4 is a logical partition.

I'll post back in the morning because it's late here and I want to get this right while I'm fresh. The principle is simple. You edit the PT.txt file and rewrite that back to the partition table with sfdisk. In the meantime, make backups of everything, which is a good idea whenever manipulating partitions.

I follow what you want, but sdb4 is not a logical partition. sdb4 is non-existent. At the moment sdb3 is your extended partition which contains the logical partitions, sdb5 and sdb6. What I'll do in the morning is give you the code to make your current primary sdb2 into sdb1, and your extended sdb3 into sdb2. sdb5 and sdb6 must remain as they are because logical partitions are numbered 5 and upwards.

> **Tares said:**
> 
ps. I know how to use code tags :P

I'm very glad to hear it! Not everyone does. You would not believe how many times I have asked someone to post stuff in code tags and they haven't. :|

---

### Post by Tares on 2012-01-13
> **coffeecat said:**
> I'll post back in the morning because it's late here and I want to get this right while I'm fresh. The principle is simple. You edit the PT.txt file and rewrite that back to the partition table with sfdisk. In the meantime, make backups of everything, which is a good idea whenever manipulating partitions.

The problem is I don't have enough space to backup everything ;) that's why I've asked for a "clean" way to do it. I can try anyway ;)

> **coffeecat said:**
> 
I follow what you want, but sdb4 is not a logical partition. sdb4 is non-existent. At the moment sdb3 is your extended partition which contains the logical partitions, sdb5 and sdb6. What I'll do in the morning is give you the code to make your current primary sdb2 into sdb1, and your extended sdb3 into sdb2. sdb5 and sdb6 must remain as they are because logical partitions are numbered 5 and upwards.

You're right. I forgot that I removed one of logical paritions and merged it with sdb5. Thats why sdb4 is 0. 

> **coffeecat said:**
> 
I'm very glad to hear it! Not everyone does. You would not believe how many times I have asked someone to post stuff in code tags and they haven't. :|
I can use quote quite efficiently too :p

---

### Post by coffeecat on 2012-01-14
Before we go any further, we need to clarify one detail that I didn't notice last night. Your sfdisk output has line numbers, which is not expected. You should have got output looking something like this:

```
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=        0, size=        0, Id= 0
/dev/sdb2 : start=     2048, size= 40996864, Id= 7, bootable
/dev/sdb3 : start= 40998912, size=935770112, Id= f
/dev/sdb4 : start=        0, size=        0, Id= 0
/dev/sdb5 : start= 41000960, size=133175296, Id=83
/dev/sdb6 : start=174176793, size=802592231, Id=83
```

If you edit the file as it is and feed it back with sfdisk you will get an error message. It's easy enough to remove the line numbers, but I would like to clarify this point before we proceed. Was this the the output of this command?

```
sudo sfdisk -d /dev/sdb > Desktop/PT.txt
```

Did you do anything else to get those line numbers?

Also - your thread title refers to /dev/sda*, yet the HD in question appears to be /dev/sdb. How many hard drives do you have and can you confirm that you need to amend the partition table of sdb, not sda.

---

### Post by Tares on 2012-01-14
> **coffeecat said:**
> 
Did you do anything else to get those line numbers?

I guess some text editor added them. PT.txt doesn't have line numbers.

> **coffeecat said:**
> 
Also - your thread title refers to /dev/sda*, yet the HD in question appears to be /dev/sdb. How many hard drives do you have and can you confirm that you need to amend the partition table of sdb, not sda.
Yes, I want to change sdb. Typo ;)

---

### Post by oldfred on 2012-01-14
You can use sfdisk and should keep the copy of the output on another device as it can restore your partition table if it gets too messed up.

I do not know if fdisk's f command just changes the order of existing partition or starts at one?

you do the following :
fdisk /dev/sda
use option : x (expert mode)
use option : f (fix partition order)
use option : r (return)
use option : p (to print)
use option : v to verify partition
if it is ok
then you can do
option : w ( to write table to disk)
option : q to quit

Note that all this change may wreck havoc with your system. Most is done with UUIDs now, so those settings will be ok. But anything you have in grub or fstab that uses device like /dev/sda2 will be wrong and have to be edited.


Within some limits you can cahnge logical to primary & vice versa.

To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it.
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives

---

### Post by coffeecat on 2012-01-14
> **Tares said:**
> I guess some text editor added them. PT.txt doesn't have line numbers.

That worries me somewhat. We need to be 100% precise when doing work like this. Ubuntu's default gedit would not do this. Which text editor did you use that added the line numbers?

Anyway. Before I give you the code to effect this, a few caveats.

[list]
[*]Since you are not able to back everything up, do this at your own risk. The risk of something going wrong is small, but the risk is there. You will be rewriting someting very fundamental in the layout of your hard drive.
[*]Keep a copy of your original PT.txt file. (In fact you have a copy in your post #3.) This will be needed if you need to revert your partition table to what it was for any reason.
[*]Run the sfdisk command from an Ubuntu live USB or live CD session. It is possible to do this from your permanant installation using a --force option, but it is probably bad practice to write a partition table from a system running from the same hard drive.
[*]If you use a live USB, the designation of your drive may change from sdb depending on your BIOS. It may change anyway with a live CD. Before you run the sfdisk command, check that the drive is still /dev/sdb with:

```
sudo fdisk -lu
```

If it is no longer /dev/sdb, stop and amend the PT2.txt file or post back.

[/list]

Save this following as PT2.txt:

```

partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=     2048, size= 40996864, Id= 7, bootable
/dev/sdb2 : start= 40998912, size=935770112, Id= f
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0
/dev/sdb5 : start= 41000960, size=133175296, Id=83
/dev/sdb6 : start=174176793, size=802592231, Id=83
```

For the next, I'll assume you've copied PT2.txt to the desktop of your live session. Boot up a live Ubuntu CD or USB and check that the hard drive whose partition table you want to amend is /deb/sdb. Don't mount any partitions. Now from a terminal:

```
sudo swapoff -a
sudo sfdisk /dev/sdb < Desktop/PT2.txt
```

I've included the swapoff command because the live session automatically mounts the swap partition and sfdisk will not overwrite the partition table if anything on the drive is mounted. You don't have a swap partition on sdb, but I'm assuming you may have one on another drive. If you get an error saying that sfdisk has not written the amended partition table, you'll have to use the force option like this:

```
sudo sfdisk --force /dev/sdb < Desktop/PT2.txt
```

Whether you use the force option or not you will get a message saying (among other things) "The command to re-read the partition table failed." Don't worry about it. Just reboot into your Ubuntu system and let us know how you get on.

By the way, I've done a simulation on my test system which worked just fine. It had a primary partition for sda1 and extended for sda2 (+logicals) which I shuffled up to sda2 and sda3 repectively, and then shuffled back down again using sfdisk.

---

### Post by Tares on 2012-01-15
> **coffeecat said:**
> That worries me somewhat. We need to be 100% precise when doing work like this. Ubuntu's default gedit would not do this. Which text editor did you use that added the line numbers?

I used vim to edit the file and copied it from there. That's why it has line numbers.

Thanks everyone for help. As for now I've decided to not to change the partition table. I'll borrow a small HDD next week and try those operations on that one (I have too much valuable data on current one). In case of any problems I've report here :)

EDIT:

One more thing. If I would like to change logical partitions to primary ones my PT would look like this?
```
partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=     2048, size= 40996864, Id= 7, bootable
/dev/sdb2 : start= 41000960, size=133175296, Id=83
/dev/sdb3 : start=174176793, size=802592231, Id=83

```

---

### Post by oldfred on 2012-01-15
It looks like I did not post the link to fix parts which is the easier way to change partitions from logical to primary if you can within the rules. 

You can use sfdisk but again have to be careful on following the rules on partitions - some of which are only 4 primary partitions - sda1 thru sda4,  only one of which can be the extended, all logicals have to be inside the extended and are sda5 and up.

To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it.
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partiton table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

---

### Post by coffeecat on 2012-01-15
@Tares, +1 for using fixparts if you want to change the logicals to primaries. It will most likely renumber all the partitions starting with #1.

---

### Post by ridetheteapot on 2012-01-24
Hey, hope this isnt threadjacking, but just a quick question if either of your see it.

Would this would similarly (can't get the same table printout at least) with GPT and sgdisk?(you both mentioned fixparts so you might very well know)

FYI just a single partition on the drive but is sda2.

---

### Post by oldfred on 2012-01-24
MBR only has one partition table. gpt has two, one is a backup of the original. So the process with MBR only updated the original and the way partition table is stored with gpt  is totally different. I would not attempt to manually change gpt especially with tools designed for MBR. fdisk does not work on gpt at all. 

The author of fixparts also did gdisk. I think it checks the gpt & the backup tables.

repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

---

### Post by ridetheteapot on 2012-01-24
> **oldfred said:**
> I would not attempt to manually change gpt especially with tools designed for MBR. fdisk does not work on gpt at all.

yea they will not. sgdisk (which I was referring to) is also written by gdisk author - it's like sfdisk for GPT.

I have actually already read most of the stuff on the three tools from rodsbooks.com/gdisk already and have not seen anything specific to this problem.

[http://www.rodsbooks.com/gdisk/sgdisk-walkthrough.html](http://www.rodsbooks.com/gdisk/sgdisk-walkthrough.html) seems to have the relevant info, but I am scared to wing it. I was kinda hoping I could dump the table info, edit it, then feed it back in -- like you guys where doing with sfdisk.

---

### Post by oldfred on 2012-01-24
Also see the man page it seems to have more info.

gdisk has a s option which sorts the partitions to match order on drive. Again you may cause major breakage as any entries using device /dev/sda1 type entries in grub or fstab will have to be updated.

gdisk also has a backup to file option.

---

### Post by ridetheteapot on 2012-01-24
Thanks oldfred! I had run through the options of gdisk and missed the reordering option.

Fortunately used UUID entries in fstab and grub doesn't look at this drive. I have only used uuid in fstab ever since one of my (raid) machines started swapping device names every other boot and got me sooooo scared. I still don't really understand how devices get ordered (who gets sda vs sdb) or why they seem to change between boot.

---

### Post by ridetheteapot on 2012-01-25
Hmmm, this method (gdisk reorder partions) does not seems to work if there is a single partition on the disk - when attempting it just says it's already correct. Guess I'll live with it.

---

