---
title: "Grub...error 18 after regular reboot on functioning desktop"
date: 2007-11-28
forum: Hardware &amp; Laptops
---

### Post by phineaus on 2007-11-28
So, there are clearly a very large number of threads on various websites regarding this particular error when loading Grub.  I have read many of them and arrived at good understanding of what the error means, and the processes and communication between the bios, MBR, kernel, etc. (especially liked this description... [http://www.nabble.com/Grub-tf4291271.html#a12218543](http://www.nabble.com/Grub-tf4291271.html#a12218543))

The bottom line is that I have already been using this install of Gutsy for over a month and have a large amount of data on my UBUNTU partition, which I believe is configured as '/' and not /boot.  

The mystery is what the hell could have happened.  I indeed had been messing with IDE cables and basic BIOS config to install a friends HD and rescue some data from it.  I did this in WinXP since UBUNTU was not able to mount the drive once I installed it.  I rescued the data, burnt a CD...shut off the computer and restored the original drive configuration (including BIOS)...yadda yadda etc.  I proceeded to boot UBUNTU and things started up fine, but then I was having some serious lag time loading various programs and decided to reboot leaving my computer off for a few minutes.  It is old and was running MUCH slower than XP anyway for some reason...  IMPORTANT: I did NOT update anything in UBUNTU, much less the kernel.  Upon reboot I get the error 18 message and cannot boot either OS.  

I checked to make sure LBA was on in the BIOS in case I had messed with that and even turned it off.  Nothing got better.  Then I decided to use the live CD to boot and maybe gain access to create a boot partition without loosing any of my data.  By the way, is this possible?  

From the live CD I could mount my WinXP partition and even my other hard drive, but my primary UBUNTU partition would not mount.  I checked details and it noted, amongst other things, that there may be an issue with a bad /dev/hd6...a partition and or disk (pardon my bad understanding) that I do not believe was ever listed in my /etc/fstab file that I can no longer access because its on that partition.  I ran dmesg and saw some error messages accessing sectors on that partition.

Not sure what to make of all this, but it appears as if I cannot even save my data and repartition the drive if that is indeed the solution to error 18 from Grub.  Could I have a hardware failure issue?  Bad sectors?  If so, these are issues I am much more comfortable addressing from a Windows machine, just based on previous experience.  Any help is appreciated.  My apologies for the long post, but I figured I would get the background out of the way.  No other threads I have seen describe this error occurring out of the blue...

Thanx,
phineaus

---

### Post by meierfra on 2007-11-28
Boot from the Ubuntu Life CD and post the output of 

sudo fdisk -l

---

### Post by phineaus on 2007-11-28
Ok.  I just booted from the Live Cd and same deal.  

Cannot mount volume.  mount: wrong fs type, bad option, bad superblock on /dev/hda6, missing codepage or helper program, or other error.  In some cases useful info is found in syslog - try dmesg | tail or so

Output from fdisk -l

Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x783d8f59

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1612    12948358+   7  HPFS/NTFS
/dev/hda3            1613        7297    45664762+   5  Extended
/dev/hda5            7221        7297      618471   82  Linux swap / Solaris
/dev/hda6            1613        7220    45046197   83  Linux

Partition table entries are not in disk order

Disk /dev/hdd: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1f7be346

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        1026     8241313+   7  HPFS/NTFS

Output from dmesg | tail

[  577.267851] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=25905122, sector=25905122
[  577.267862] ide: failed opcode was: unknown
[  577.267870] end_request: I/O error, dev hda, sector 25905122
[  577.268533] EXT3-fs error (device hda6): ext3_get_inode_loc: unable to read inode block - inode=8, block=1027
[  577.269071] EXT3-fs: invalid journal inode.
[ 1022.434035] NET: Registered protocol family 17
[ 1034.180452] NET: Registered protocol family 10
[ 1034.180802] lo: Disabled Privacy Extensions
[ 1034.181123] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1044.593270] ath0: no IPv6 routers present

Sorry for not posting this before, but I had some issues with connect to the internet when booting from the Live CD.  I figured it out this time :)

Thanks for your help.

---

### Post by meierfra on 2007-11-29
Looks like your ubuntu partition is corrupt. You might use "fsck" and/or testdisk [(Hermanzone info on testdisk)]("http://www.users.bigpond.net.au/hermanzone/p21.html")

---

### Post by phineaus on 2007-11-29
Ok.  Thanks for the suggestion.  I tried to figure out fsck but I was having some issues and could not find documentation on my level...so I opted for testdisk.  After analyzing the disk, I came up with these results:

Disk /dev/hda - 60 GB / 55 GiB - CHS 116301 16 63
Current partition structure:
     Partition                  Start        End    Size in sectors

Warning: Incorrect number of heads/cylinder 255 (NTFS) != 16 (HD)
 1 * HPFS - NTFS              0   1  1 25691   3 63   25896717

Warning: Bad ending head (CHS and LBA don't match)
 3 E extended             25691   4  1 116295  14 63   91329525

Warning: Bad starting head (CHS and LBA don't match)
 5 L Linux Swap           115068  13  1 116295  14 63    1236942

Warning: Bad starting head (CHS and LBA don't match)
   X extended             25691   4  2 115068  11 63   90092519

Warning: Bad starting head (CHS and LBA don't match)
     6 L Linux                25691   6  1 115068  11 63   90092394

Warning: Bad starting head (CHS and LBA don't match)

This clearly looks like some issues.  However, beyond this, I cannot seem to wrap my head around how to repair the problem.  Next step I got this warning message:

Warning: the current number of heads per cylinder is 16
but the correct value may be 255.
You can use the Geometry menu to change this value.
It's something to try if
- some partitions are not found by TestDisk
- or the partition table can not be written because partitions overlaps.

With only the option to continue which left me here:

Disk /dev/hda - 60 GB / 55 GiB - CHS 116301 16 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0   1  1 25691  15 63   25897473
D Linux                25691   6  1 115068  15 63   90092646
D Linux Swap           115068  13  1 116295  15 63    1237005


Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, 13 GB / 12 GiB

Those are indeed my partitions as they should be (as far as I can tell), but the whole idea of changing partitions makes me tremble for fear of doing some permanent damage!  As it is set above, does that mean that I will be deleting all partitions?  That sounds like losing data to me.  I am in over my head and just want to make my non-bootable partition bootable again.  Help por favor!

---

### Post by phineaus on 2007-11-29
That said...here is my output after running fsck on the partition implicated with my bad sectors problem...

ubuntu@ubuntu:~$ sudo fsck /dev/hda6
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
fsck.ext3: Attempt to read block from filesystem resulted in short read while checking ext3 journal for /dev/hda6

Just in case thats an easier route to making my drive bootable again.

---

### Post by meierfra on 2007-11-29
> Those are indeed my partitions as they should be (as far as I can tell), but the whole idea of changing partitions makes me tremble for fear of doing some permanent damage! As it is set above, does that mean that I will be deleting all partitions? That sounds like losing data to me. I am in over my head and just want to make my non-bootable partition bootable again. Help por favor!

Testdisk does will only change the partition  table. It will not delete the actual partitions. Also Testdisk won't carry out any changes until you select "write".  It looks like that your partition table is screwed up. And testdisk (in my experience) does a good job fixing  partition tables. 
Try selecting one of the partitions and press "P'. See whether testdisk can access the files on the partition. Press Esc to get back  to the screen with the partitions. 
 You might also change the "D" in front of the partition, to let testdisk know that you think that these partitions really exist.(Change the characteristic of NTFS partition to "*" and the other two to "L")
Then select "proceed".  If you  select "search"  at the next screen,  testdisk will do a much longer analysis of your hard drive.
Post the result of this deeper search.

---

### Post by phineaus on 2007-11-30
Ok.  I am going to change the letters in front of the partitions to let it know which is which.  However, I do not believe that I need to do a deeper search, as all three of the partitions are listed in this search.  Since the drive is already unbootable, I will change the partition table by choosing write, and then see if it indeed boots.  If not, I should be able to change the partition table again from my understanding of your reply.  I will post to tell if that worked after reboot....

---

### Post by phineaus on 2007-11-30
I used the P option to check a file listing on said partitions, and was able to navigate the NTFS partition, but TestDisk was unable to list the files on the linux partition, saying that the partition appeared to be damaged.  

No file found, filesystem seems damaged. 

was the exact message.

---

### Post by phineaus on 2007-11-30
In addition, when I change the partition table to have the ntfs bootable primary and the other two logical, TestDisk informs me that this is a abad structure.  Anyone have any idea how to use fsck to actually repair the linux partition and make it not only bootable, but readable again?

---

### Post by meierfra on 2007-11-30
Try the longer search. Isn't quite as long as I made  it sound like. Just a few minutes

---

### Post by phineaus on 2007-11-30
It is when its a 43 gig partition!  It is only at 31%.  I have to head out for a couple hours, but will post the deeper results then.  Thanks for you help!  Actually learning how to use fsck based on my results from the previous posts would be nice... I have a feeling that my partition is just damaged and that is resulting in my boot problem.  We shall see shortly...ohh the suspense....

---

### Post by meierfra on 2007-11-30
Well it checks the whole hard drive. I have a 60 GB hard drive just like yours. So I would have expected it to  take about the same time. Seems not. 

You probably are right that you will have to use fsck too. But if you start with the wrong partition table, fsck won't get very far. 

But I never had any real problems with my filesystems. (Used fsck just once So I won't be able to help you with fsck.
Anyway I'm headed for bed, but will be back tomorrow.

---

### Post by phineaus on 2007-11-30
The deeper search found nothing different.  It left me with the screen stating that the number of heads was different....the same as I posted in a previous message.  Any ideas?

---

### Post by meierfra on 2007-11-30
> Warning: the current number of heads per cylinder is 16
but the correct value may be 255.
You can use the Geometry menu to change this value.
It's something to try if


You might try this.

---

### Post by phineaus on 2007-11-30
That recommendation seemed to be aimed at those situations where someone could not find a partition even after they tried the deep search.  All of my partitions have been found, but I have issues with file corruption on only my linux partition.  Not sure how this is going to change anything.  I just want to repair the damaged file system and boot again.  I will post back in tell what happened.

---

### Post by phineaus on 2007-11-30
So here we go...
I changed the disk geometry, a nd that made it see all the partitions correctly, as primary bootable, logical, and logical, respectively.  I was still unable to list the contents of the linux partition with the same error about the disk seems to be damaged.  But figured that could just be because changes havent taken effect.  I wrote upon exiting, and rebooted.  

Only to find Error 17 given as the reason for not booting.  Meaning it was simply unable to mount the filesystem.  

What I absolutely do not understand is how the number of heads on my drive could have gotten changed to the incorrect value of 16 from the correct value of 255.  Any ideas?

---

### Post by phineaus on 2007-11-30
These are my new partition table values, and the results of me trying to use fsck to fix or even find out about the problems with my linux partition (/dev/hda5...which by the way is not the one implicated in not being able to mount).

ubuntu@ubuntu:~$ sudo fsck -v -f /dev/hda5
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
fsck.ext3: Attempt to read block from filesystem resulted in short read while checking ext3 journal for /dev/hda5

ubuntu@ubuntu:~$ sudo mke2fs -n /dev/hda5
mke2fs 1.40.2 (12-Jul-2007)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
5636096 inodes, 11261549 blocks
563077 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
344 block groups
32768 blocks per group, 32768 fragments per group
16384 inodes per group
Superblock backups stored on blocks: 
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
        4096000, 7962624, 11239424

ubuntu@ubuntu:~$ sudo fsck -b 32768 -v -f /dev/hda5
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
fsck.ext3: Attempt to read block from filesystem resulted in short read while checking ext3 journal for /dev/hda5

ubuntu@ubuntu:~$ sudo fsck -b 32768 -cf /dev/hda5
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
fsck.ext3: Attempt to read block from filesystem resulted in short read while checking ext3 journal for /dev/hda5

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x783d8f59

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1612    12948358+   7  HPFS/NTFS
/dev/hda2            1613        7297    45664731    f  W95 Ext'd (LBA)
/dev/hda5            1613        7220    45046197   83  Linux
/dev/hda6            7221        7297      618471   82  Linux swap / Solaris

Disk /dev/hdd: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1f7be346

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        1026     8241313+   7  HPFS/NTFS
ubuntu@ubuntu:~$

---

### Post by meierfra on 2007-11-30
I don't think that it will solve your problem, but since your partition table has changed you have to reinstall grub:

```
sudo grub
root (hd0,4)
setup (hd0)
quit
```


 I don't know  what could have caused your problems.  And I  don't know enough about  fsck  to be of much  further help.  You might start a new thread with a different title to attract  attention from people who know about file system troubles.

---

### Post by phineaus on 2007-11-30
Re install grub?  Just to make sure...will the code you posted do that even though I cannot access the partition grub is on?

---

### Post by meierfra on 2007-11-30
> e install grub? Just to make sure...will the code you posted do that even though I cannot access the partition grub is on?

Probably not. But won't hurt trying.

---

### Post by phineaus on 2007-11-30
Here is what happened...

ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> root (hd0,4)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 25: Disk read error

grub>          

So I guess that says something...not sure what.

---

### Post by meierfra on 2007-11-30
Well it just means that grub can´t access your ubuntu partition  either.

---

