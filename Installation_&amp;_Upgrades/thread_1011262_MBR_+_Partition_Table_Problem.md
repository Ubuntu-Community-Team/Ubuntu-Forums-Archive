---
title: "MBR + Partition Table Problem"
date: 2008-12-14
forum: Installation &amp; Upgrades
---

### Post by yebrahim on 2008-12-14
hello guys,

i've had this problem since a couple of weeks now, i tried many things, all to no avail.

the thing is, i had Ubuntu installed on my computer for a while, but then windows started nagging to be reinstalled. i reinstalled it. when i tried to restore grub, it didn't work. i tried everything, grub setup, reinstall, and many other options. then i started tampering with the menu.lst, stage1, and stage2 because it kept telling me that it cannot read the contents of stage1 while reinstalling grub.

anyway, so now i almost ruined the boot loader, and even when i boot from my ubuntu live cd and try to reinstall ubuntu, the partition tool (gparted) sees the disk as one chunk, no partitions (yes, seems i got so far to destroying the partition table itself) so now i can't think of any other solution but to backup the entire disk and repartition. i now have linux installed with all my apps and tweaks and i can't get it to boot :'(

anyone can help me out with this? backing up and repartitioning is a lengthy procedure for me in order to install everything from scratch.

sorry for the long msg.

---

### Post by albinootje on 2008-12-14
Just to get things clear :
Can you still access your old Ubuntu installation and Windows installation ?
If your partition-table is really messed up, you might not find your data back so easily.

---

### Post by yebrahim on 2008-12-14
thanks for the quick reply.
i can still access my windows (the new installation that messed it all up), and i can access my ubuntu through the live cd only. i tried chrooting and reinstalling grub, but i kept getting an error along the lines of "cannot read the contents of stage1 file" -- sorry can't remember the exact thing.

i know it might seem hopeless, but i've got to try everything before i get to the repartitioning solution :( i spend days customizing my os.

---

### Post by caljohnsmith on 2008-12-14
How about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and please post the output of:
```
sudo sfdisk -l
sudo fdisk -lu
sudo parted /dev/sda print
```
Then make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen and we can work from there if you want. :)

---

### Post by yebrahim on 2008-12-14
ok, here's what i've found. this is the result of the fdisk commands:

```

ubuntu@ubuntu:~$ sudo sfdisk -l

Disk /dev/sda: 9729 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+   1275-   1276-  10243768+   7  HPFS/NTFS
                end: (c,h,s) expected (1023,254,63) found (1023,239,63)
/dev/sda2       1276    9727    8452   67890690    f  W95 Ext'd (LBA)
                start: (c,h,s) expected (1023,254,63) found (1023,180,1)
                end: (c,h,s) expected (1023,254,63) found (1023,239,63)
/dev/sda3       3187+   9727    6541-  52534408+   7  HPFS/NTFS
                start: (c,h,s) expected (1023,254,63) found (1023,1,1)
                end: (c,h,s) expected (1023,254,63) found (1023,239,63)
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5       1276+   1639     364-   2923767   82  Linux swap / Solaris
                start: (c,h,s) expected (1023,254,63) found (1023,182,1)
                end: (c,h,s) expected (1023,254,63) found (1023,119,63)
/dev/sda6       1640+   3186    1547-  12426246   83  Linux
                start: (c,h,s) expected (1023,254,63) found (1023,121,1)
                end: (c,h,s) expected (1023,254,63) found (1023,44,63)
ubuntu@ubuntu:~$ sudo fdisk -lu
omitting empty partition (5)

Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x19731972

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    20487599    10243768+   7  HPFS/NTFS
/dev/sda2        20498940   156280319    67890690    f  W95 Ext'd (LBA)
/dev/sda3        51211503   156280319    52534408+   7  HPFS/NTFS
/dev/sda5        20499066    26346599     2923767   82  Linux swap / Solaris
/dev/sda6        26346663    51199154    12426246   83  Linux
ubuntu@ubuntu:~$ sudo parted /dev/sda print
Error: Can't have overlapping partitions.                                 
Information: Don't forget to update /etc/fstab, if necessary.

```

and here's what testdisk looked like.
[ATTACH]96401[/ATTACH]

[ATTACH]96402[/ATTACH]

i really appreciate your help here :) thank you.

---

### Post by caljohnsmith on 2008-12-14
I think you probably all ready guessed from the output of those commands that you definitely have a partition table problem. I notice you are only using testdisk version 6.6, and the latest one available in Intrepid is 6.9. What Live CD are you running? It would be good to run at least Hardy (which has version 6.8 ) or Intrepid so you can use the latest testdisk. To try and recover your partitions, go ahead and run testdisk again, but this time do a "deep search":
```
sudo testdisk
```
**If you are using Version 6.8:**
After starting testdisk with the above command, choose "no log", select HDD and "Proceed", "Intel", "Analyze", "Proceed", Y/N depending on if you have any Vista partitions, hit enter to continue, and select "Search!" so it does a deeper search, which could take a while. Post the output of the screen that has the deep search results.
[B]
If you are using Version 6.9:[/B]
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", "quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, and select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results.

Also, really important, let me know what you think your partitions are supposed to be, because that will make it easier to use testdisk to recover your partitions. Let me know how it goes. :)

---

### Post by yebrahim on 2008-12-14
ok, i'm using the 6.6 version because the only live CD i found now was Gutsy's.
anyway, so the way i used to partition my system is

NTFS partition for windows root and system files
NTFS partition for my stuff (i also call it Stuff)
EXT3 partition for ubuntu's system files
SWAP partition for ubuntu too

so that's four partitions plus the MBR. here's what testdisk got for me, two extra linux partitions:

[ATTACH]96412[/ATTACH]

i'm starting to feel good about this :D thanks a lot man.

---

### Post by caljohnsmith on 2008-12-14
OK, that's great, it looks like there's a good chance of piecing back together your partition table. In that deep search screen, use the up/down arrow keys to select each partition, then the right/left arrow keys to change how it is marked; leave the 1st NTFS entry as "*", the next swap entry as "L", and then mark the last NTFS partition as "L" if it will let you, otherwise mark it as "P", and leave the 3rd Linux partition marked as "D". That leaves only the first two linux entries, so select each one and press "P" to get a directory listing; for whichever one gives you a directory listing, change it to "L", or if it won't let you, change it to "P". It looks like the first linux entry is the one that will work, but I can't know for sure. Mark the linux entry that didn't work with "D". Then you should be done, press enter to continue, and "write" to write the new partition table. Then reboot, see if by chance the drive will boot, and if not, boot your Live CD again and post:
```
sudo fdisk -lu
```
And we can work from there. Good luck and let me know how it goes. :)

---

### Post by yebrahim on 2008-12-15
thanks, but that didn't work :(
are you sure i should still have my first NTFS as the boot partition? what if i make my ext3 as the boot partition?

anyway, here's what you requested:

```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x19731972

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    20498939    10249438+   7  HPFS/NTFS
/dev/sda2        20499003   156280319    67890658+   f  W95 Ext'd (LBA)
/dev/sda5        20499066    26346599     2923767   82  Linux swap / Solaris
/dev/sda6        26346663    51199154    12426246   83  Linux
/dev/sda7        51211503   156280319    52534408+   7  HPFS/NTFS

```

are you sure there is no problem with the MBR? maybe i can try rewriting it?

thanks :)

---

### Post by caljohnsmith on 2008-12-15
OK, let's do a check and see which partitions are mountable and readable, so please download the attached "script1.sh.txt" to your desktop and do:
```
sudo sh ~/Desktop/script1.sh.txt
```
And please post the output. We can work from there.

---

### Post by albinootje on 2008-12-15
> **caljohnsmith said:**
> OK, let's do a check and see which partitions are mountable and readable, so please download the attached "script1.sh.txt" to your desktop and do:
```
sudo sh ~/Desktop/script1.sh.txt
```
And please post the output. We can work from there.

I didn't see any attachment. 
Why don't you post it as text also ?

We're not on some private mailinglist here, but on a worldwide open forum with the idea to build and share knowledge :)

---

### Post by caljohnsmith on 2008-12-15
> **albinootje said:**
> I didn't see any attachment. 
Why don't you post it as text also ?

We're not on some private mailinglist here, but on a worldwide open forum with the idea to build and share knowledge :)
I just checked, and I was able to download the attachment just fine; so I'm not sure what problem you might be having accessing it. I'm not trying to hide anything, I'm only trying to make it easier for yebrahim so he doesn't have to copy/paste several commands. Sometimes people can't copy/paste into the terminal, so running a script reduces the chance of typos. :)

---

### Post by albinootje on 2008-12-15
> **caljohnsmith said:**
> I just checked, and I was able to download the attachment just fine; so I'm not sure what problem you might be having accessing it. I'm not trying to hide anything, I'm only trying to make it easier for yebrahim so he doesn't have to copy/paste several commands. Sometimes people can't copy/paste into the terminal, so running a script reduces the chance of typos. :)

Yes, i understand, that's why i used the word "also".

I've seen images attached before, but i didn't see your attachment,
so i thought that you forgot or something went wrong somehow.

I guess i should read some more Forum Beginner stuff, only last night i found out how to start a fresh new posting :)

---

