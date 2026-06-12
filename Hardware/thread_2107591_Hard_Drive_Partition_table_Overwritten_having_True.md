---
title: "Hard Drive Partition table Overwritten having Truecrypt Partition"
date: 2013-01-22
forum: Hardware
---

### Post by dranzer on 2013-01-22
Hello Everyone.

I know this is not a data recovery forum and I should  not ask such questions , but I do know that this community is very  large and have been helpful to most users time to time.
So here I Go with my Problem :

I  was actually trying to make a factory reset partition for my windows 8.  In order to that I made a partition , copied my backup dvd using dd  command. Everything was fine. But I did copied the bootrecord  of that  partition into my whole drive using command
dd if=/dev/sda10 of=/dev/sda bs=512 count=1

I  know this is very stupid thing that i just done but I'm helpless now.  My partition table in the last 64bytes from 512 bytes of HDD MBR is now  been overwritten and now I'm unable to boot or access anything. I booted  from live Ubuntu 12.04LTS to see the status of my HDD and gparted is  showing Unallocated space for the whole drive. Fdisk, parted and sfdisk  useless as I tried already. I don't have any backup of my MBR.

I  ran gpart tool from command line as well as from gparted, it took more  than 3 hours but it was just running under verbose option and showing  nothing so i dropped it. I  than used TestDisk, did Quick search, it found all of my partitions  except one. I even did Deeper search but it also didn't revealed it in  search.

I  then tried Hiren's Boot CD 15.2 , used most of the Recovery tools in it but  none of them is able to detect one partition which Testdisk escaped too.
Did tried Getdataback , now using Easeus partition recovery.

My last known partition table structure :

Toshiba 500 GB HDD

Device#                  Name/Detail                                Size              OS/Filesystem                     
/dev/sda1               System reserved(Primary)            350 MB          Windows Boot files
/dev/sda2               (Primary)                                    100 GB           Windows 8 Drive
/dev/sda3               (Primary)                                    200 GB           Truecrypt Partition
/dev/sda4               Extended                           
/dev/sda5               (logical)                                      100 GB           Truecrypt partition
/dev/sda9               (logical)                                        35 GB           BackTrack 5 R3
/dev/sda6               (logical)                                          3 GB           Linux-Swap
/dev/sda7               (logical)                                      168 MB           Grub 2(OpenSuse)
/dev/sda8               (logical)                                        21 GB           OpenSuse 12.2
/dev/sda10             (logical)                                       5.5 GB           NTFS Drive

here is the Analysis of Testdisk :

[ATTACH]230476[/ATTACH]

I don't have any other device to take a backup of 500 GB and I didn't wrote anything yet in my HDD after the incident. Everything is intact still.
I can't understand why these recovery tools even testdisk is unable to find my 200 GB partition. I'm using google from the last sunday night to find anything similar but my effort is futile yet. I can't even ask on truecrypt forum, they don't deal recovery stuff.
Cgsecurity forum blacklist my IP even if I use any public proxy.

Now at the End of this I  found that EasuUS partition Recovery  did the searching and is also unable to find that partition. It Only found 3 partitions. 

Help Me Please. My most important data, pictures, videos, lectures, music , college projects, and many stuff lies there.

Thank You
 
Regards
Dranzer

---

### Post by sidzen on 2013-01-22
dranzer said,
". . .
dd if=/dev/sda10 of=/dev/sda bs=512 count=1
. . .
Now at the End of this I found that EasuUS partition Recovery did the searching and is also unable to find that partition. It Only found 3 partitions. . ."

It's not called "data destroyer" for nothing!  dd assumes you know exactly what you are doing.

Doesn't look good for any data you may have had, but tell us -- Which partitions did it find?

---

### Post by dranzer on 2013-01-22
> **sidzen said:**
> dranzer said,
". . .
dd if=/dev/sda10 of=/dev/sda bs=512 count=1
. . .
Now at the End of this I found that EasuUS partition Recovery did the searching and is also unable to find that partition. It Only found 3 partitions. . ."

It's not called "data destroyer" for nothing!  dd assumes you know exactly what you are doing.

Doesn't look good for any data you may have had, but tell us -- Which partitions did it find?
It only found the 1st two partitions and it detected my vhd as a partition too.That's all.

---

