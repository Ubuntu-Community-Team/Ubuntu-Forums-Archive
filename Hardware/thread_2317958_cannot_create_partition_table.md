---
title: "cannot create partition table"
date: 2016-03-21
forum: Hardware
---

### Post by jgw on 2016-03-21
I have attached a picture of gparted screen showing the offending thumb drive info and other stuff.  My problem seems simple.  I have this thumb drive and thought to format it and then give it a new partition after deleting any others to make sure it was absolutely clean.  Anyway, I formatted it and deleted partitions and then created a new partition table and then tried to add a partition.  When I try and add the partition I get "No partition table found on device /dev/sdc".  

I then tried to use fixparts but it could not open the mbr and failed with:
Loading MBR data from /dev/sdc/
Problem opening /dev/sdc/ for reading! Error is 20.
Unable to read MBR data from '/dev/sdc/'! Exiting!

I then tried fixdisk and got:
Unable to open file or device /dev/sdc

I have, basically, destroyed the sd card (micro), I think.  Hopefully I am wrong and somebody has a fix?

---

### Post by oldfred on 2016-03-21
You could try using dd to zero out MBR.
But realize dd's nickname is Data Destroyer. Any typo like wrong drive, totally erases data and is not recoverable.

Replace sdX with correct drive. This erases both boot code & partition table as first 512 is both.
       sudo dd if=/dev/zero of=/dev/sdX bs=512 count=1

---

### Post by jgw on 2016-03-21
Thanks for the reply.

I did as you suggested:
sudo dd if=/dev/zero of=/dev/sdc bs=512 count=1
[sudo] password for greg: 
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.0146428 s, 35.0 kB/s

I then went to gparted and tried again and got exactly the same results.  Same with testdisk and fixparts.
I also don't think this thing is mounted as it appears noplace and is not in either mount or mnt

I suspect I should just throw it away and get on with my life?

---

### Post by goofprog on 2016-03-21
maybe just try reformat the disk with **mkfs**.  It is zero and clean.  Have you also made sure the secure switch is unlocked on the disk?

---

### Post by oldfred on 2016-03-22
The dd command says it did copy data, so drive was seen?

And now it should have no MBR data at all, and you should be able to add partitions.

This should show all zeros if still sdc:
 sudo dd if=/dev/sdc bs=512 count=1 | hexdump -C

---

### Post by jgw on 2016-03-22
Thank you for the replies

sudo dd if=/dev/sdc1 bs=512 count=1 | hexdump -C returned:
00000000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
1+0 records in
1+0 records out
*
512 bytes (512 B) copied, 0.00220397 s, 232 kB/s
00000200

I have also attached the results of disks.  I have just turned on my machine and I also noticed that the address has changed from /dev/sdc to /dev/sdc1.  I also noticed that this is a 32gb micro sd and disks shows 34gb which is a bit strange.  

I have also attached a picture of gparted which seems to have the correct size although the address lists both sdc and sdc1 (same sd)  I have not messed with partitions at all this time around.  I was tempted with mkfs but thought I would post this first.   The main partition remains unknown.

I ran gparted with gksu and the gui came up (see picture).  However, the following was also in the terminal (appeared after I choose sdc1) which may help:
libparted : 2.3
======================
(gpartedbin:6155): GLib-CRITICAL **: Source ID 6 was not found when attempting to remove it
(gpartedbin:6155): GLib-CRITICAL **: Source ID 26 was not found when attempting to remove it
(gpartedbin:6155): GLib-CRITICAL **: Source ID 25 was not found when attempting to remove it
(gpartedbin:6155): GLib-CRITICAL **: Source ID 38 was not found when attempting to remove it
(gpartedbin:6155): GLib-CRITICAL **: Source ID 37 was not found when attempting to remove it
(gpartedbin:6155): GLib-CRITICAL **: Source ID 41 was not found when attempting to remove it
(gpartedbin:6155): GLib-CRITICAL **: Source ID 40 was not found when attempting to remove it
(gpartedbin:6155): GLib-CRITICAL **: Source ID 44 was not found when attempting to remove it
(gpartedbin:6155): GLib-CRITICAL **: Source ID 43 was not found when attempting to remove it
(gpartedbin:6155): GLib-CRITICAL **: Source ID 47 was not found when attempting to remove it
(gpartedbin:6155): GLib-CRITICAL **: Source ID 46 was not found when attempting to remove it
(gpartedbin:6155): GLib-CRITICAL **: Source ID 52 was not found when attempting to remove it
(gpartedbin:6155): GLib-CRITICAL **: Source ID 51 was not found when attempting to remove it
(gpartedbin:6155): GLib-CRITICAL **: Source ID 65 was not found when attempting to remove it
(gpartedbin:6155): GLib-CRITICAL **: Source ID 64 was not found when attempting to remove it

Thank you.............

---

### Post by oldfred on 2016-03-22
If MBR and we zeroed out MBR so you have no partitions, I do not understand why it shows sdc1?
It says MBR, but only if gpt might it still have partitions as those are located in different locations on drive.

---

### Post by jgw on 2016-03-22
Oldfred;

Thanks for the reply.  I am convinced, more and more, that I did something incredible clever that trashed the chip.  If you take a look at the gparted picture I attached you will see that gparted thinks I have a partition and will actually allow me to edit it or format it to another partition type (fat, ext, etc)  After having said all that gparted also tells me:
Unable to detect file system! Possible reasons are:
- The file system is damaged
- The file system is unknown to GParted
- There is no file system available (unformatted)
- The device entry /dev/sdc1 is missing

Then there is disks.  Disks will also allow me to edit the partition or format same.  

Unless you might think there is a solution my suspicion remains that I would be better off just to toss the thing and get on with my life.  All this started because I was having problem with the micro card with a Nikon camera.  That problem turned out to be pretty simple.  Nikon got back to me and told me that the camera will not work properly with a micro chip in a sd holder (which amazes me as I have always thought that is just a simple connection in the holder and should work (timing problem?)).    Anyway, after that I recovered whatever was on the chip and started to play with it which has brought me to this point.  I have been messing with this stuff for over 55 years and should have known better <g>

---

### Post by oldfred on 2016-03-22
Gparted should say no partition data as we zeroed it out. But then it should not show sdc1 either?

What does this show?
       sudo gdisk -l /dev/sdc

---

### Post by jgw on 2016-03-22
It just keeps on giving?  First I did as you asked, then I did the same but for sdc1.  After that I did it again for sdc and got, exactly, the same thing as the first time (it said it was converting, it did not as far as the chip is concerned, only in memory)

sudo gdisk -l /dev/sdc 
GPT fdisk (gdisk) version 0.8.8

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. 
***************************************************************

Disk /dev/sdc: 65536000 sectors, 31.2 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 37DD4CD9-3858-4640-ABF9-ECD3F2A43EFE
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 65535966
Partitions will be aligned on 2048-sector boundaries
Total free space is 6077 sectors (3.0 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048        65531903   31.2 GiB    8300  Linux filesystem

for sdc1:
sudo gdisk -l /dev/sdc1 
GPT fdisk (gdisk) version 0.8.8

Partition table scan:
  MBR: not present
  BSD: not present
  APM: not present
  GPT: not present

Creating new GPT entries.
Disk /dev/sdc1: 65529856 sectors, 31.2 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 48A64545-1EF8-4D06-826D-D6EABF5001CA
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 65529822
Partitions will be aligned on 2048-sector boundaries
Total free space is 65529789 sectors (31.2 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name

---

### Post by oldfred on 2016-03-22
Do not run gdisk on a partition, just on a drive. You cannot partition a partition.

But gdisk is seeing the partition? So the dd erase must not have worked.

I might use gdisk to convert to gpt and see what gparted then sees.
       GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

sudo gdisk /dev/sdc

 Use gdisk and verify partitions are correct with p, or v to review issues,  and use w to write the partition table. If not correct just use q to quit. That should update primary, backup & protective MBR. Details:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html) 

[URL="http://www.rodsbooks.com/gdisk/"]
[/URL]

---

### Post by jgw on 2016-03-23
oldfred;
I converted to gtp and then it was unrecognisable by anything.  I then went to gparted and tried for a new partition (results below).  Then pressed the partition tab again, tried new, took a look and found that there was no partition.  I went to device/create and, in theory, created a partition table.  I then went to partition to create new and was told that there was no partition table.  So, basically, I have created a situation which gives me random results for whatever I try and do.  This is very odd.  Again - are we wasting our time?

GParted 0.18.0 --enable-libparted-dmraid --enable-online-resize

Libparted 2.3
Create Primary Partition #1 (fat32, 31.25 GiB) on /dev/sde  00:00:01    ( ERROR )
     	
create empty partition  00:00:01    ( SUCCESS )
     	
path: /dev/sde1
start: 2048
end: 65535999
size: 65533952 (31.25 GiB)
clear old file system signatures in /dev/sde1  00:00:00    ( SUCCESS )
     	
write 68.00 KiB of zeros at byte offset 0  00:00:00    ( SUCCESS )
write 4.00 KiB of zeros at byte offset 67108864  00:00:00    ( SUCCESS )
write 4.00 KiB of zeros at byte offset 33553379328  00:00:00    ( SUCCESS )
flush operating system cache of /dev/sde  00:00:00    ( SUCCESS )
set partition type on /dev/sde1  00:00:00    ( ERROR )
libparted messages    ( INFO )
     	
/dev/sde: unrecognised disk label

========================================

---

### Post by oldfred on 2016-03-23
there is this post:
 Partition wizard repaired NTFS partition table that gparted could not see with disk label error
[http://ubuntuforums.org/showthread.php?t=2112005](http://ubuntuforums.org/showthread.php?t=2112005)

---

### Post by jgw on 2016-03-23
oldfred:
I think I will give up on this one, its just to strange.  I went to the first link and found:
this occasionally fixes issues and is worth trying:
you do the following :
fdisk /dev/sdd
use option : x (expert mode)
use option : f (fix partition order)
use option : r (return)
use option : p (to print)
use option : v to verify partition
if it is ok
then you can do
option : w ( to write table to disk)
option : q to quit
else if it is not ok
then post the output of option p and v 

The problem with this one is that the options listed above don't exist for fdisk (they do for sdisk).  anyway I made a run at both and got:
sudo sfdisk -l /dev/sde
Disk /dev/sde: 32000 cylinders, 64 heads, 32 sectors/track
sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/sde: unrecognized partition table type
No partitions found

sudo fdisk -l /dev/sde
Disk /dev/sde: 33.6 GB, 33554432000 bytes
64 heads, 32 sectors/track, 32000 cylinders, total 65536000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xffffffff
Disk /dev/sde doesn't contain a valid partition table

I tried this set first - nothing changed:
sudo fdisk /dev/sde
[sudo] password for greg: 
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0xbe29c329.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.
Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help): w
The partition table has been altered!
Calling ioctl() to re-read partition table.
Syncing disks.

now run it again to see what happened.  Please note that I was supposed to write and change.  The results below show no change at all:
sudo fdisk /dev/sde
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0x6b7c601c.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.
Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

---

### Post by oldfred on 2016-03-24
If the dd to erase partitions worked then the errors on having no partitions would be correct. When erased like that it is like a blank drive.

And then you should be able to create a partition and update partition table entries with the one entry.

---

### Post by jgw on 2016-03-24
oldfred;
I went into fstab and found some stuff that came from messing with this chip.  I removed it.  I then rebooted plugged it in again.  I then went to gparted, created a partition table and then created a new partition.  It all looked like it should.  I then went to disks to see what it had to say.  It still said 34gb which is wrong.  It did tell me that I now had a partition though!  Then I tried to access it and could not, even though disks told me everything was dandy.  I then saw that disks would let me delete the partition so I did (for the heck of it).  Now I am right back where I started.  I give up.  If you had a mailing address I would send you the chip for mess with as I am going to throw it away.  I would not, however, suggest you give me the address here (too public) and so, I guess, we are stuck.

Thank you, very much, for all the help and time you spent on this, it IS appreciated!  I will mark this whole mess as solved.  I wish there was a "waste of time" mark, or the possibility of just deleting this whole thing but, as far as I can tell, that does not exist.

---

### Post by oldfred on 2016-03-24
We do try to solve issues, just to understand for next user.

But sometimes, it is just better to move on.

---

