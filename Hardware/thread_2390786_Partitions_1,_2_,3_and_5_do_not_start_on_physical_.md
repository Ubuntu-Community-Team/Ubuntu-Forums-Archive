---
title: "Partitions 1, 2 ,3 and 5 do not start on physical sector boundaries."
date: 2018-05-02
forum: Hardware
---

### Post by pqwoerituytrueiwoq on 2018-05-02
Last Sunday this drive was acting up, it would not show up in my bios and one one point i could not get it to appear in the OS
right now sometimes it is in the bios and some times not, but lucky the OS sees it (tried 4 sata cables on multiple ports, worked again after a read benchmark on a decade old system)
no clue what is going on there...

I happened to notice this warning (related maybe?), from what i read this limits performance (the last thing you want to happen when you actually need swap space)
how should i fix this? please note that i can backup everything on this drive for what ever i need to do
the only thing i want to avoid is moving the partition, i am fine with resizing but moving takes all day (faster to backup reformat and restore data)
```
Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: D9E12CB1-E59D-4783-8B22-3783273A9C84

Device          Start        End   Sectors   Size Type
/dev/sda1          34    4192964   4192931     2G Linux filesystem
/dev/sda2     4192965  738202814 734009850   350G Linux filesystem
/dev/sda3   738202815 1577068919 838866105   400G Linux filesystem
/dev/sda4  1577068920 1919976344 342907425 163.5G Linux filesystem
/dev/sda5  1919976345 1953520064  33543720    16G Linux swap

Partition 1 does not start on physical sector boundary.
Partition 2 does not start on physical sector boundary.
Partition 3 does not start on physical sector boundary.
Partition 5 does not start on physical sector boundary.

```
[IMG]https://i.imgur.com/5ZOHUpi.png[/IMG]

On a side note is there a way i can make /dev/sdb always be:

```
Disk /dev/sdc: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 1E38ADCD-CDF7-4355-A43C-276BECF26C5E
```
If i have a drive in my hot swap bay at boot it end up being sdc, this makes sense as the drive is on port 3 and my hot swap bays are on ports 1 and 2 while the the 1TB drive is on port 0
well this time it made my empty card reader /dev/sdb

---

### Post by oldfred on 2018-05-02
I try to use ports in order on my Motherboard system. But sdc flash drive becomes sda on reboot. It is totally up to UEFI/BIOS on what order it assigns to drives. 
There used to be a file that specified drive order, but it was discontinued. I thought it could be used if found, but cannot find in my notes anymore. Not even sure if it still is available or works.

When or how did you partition drive?
Windows 7 when released used correct boundaries. And all Linux tools soon after also changed. I thought all gpt drives were on correct boundaries.
Since your drive is 512, not newer 4K, it may not matter.

       Partition does not start on physical sector boundary.
First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). 
[https://www.ibm.com/developerworks/linux/library/l-linux-on-4kb-sector-disks/](https://www.ibm.com/developerworks/linux/library/l-linux-on-4kb-sector-disks/)
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)

---

### Post by Claus7 on 2018-05-02
Hello,

other users most probably will help you more. Just to tell you that searching about the message you are getting a long time ago, it seems to be completely harmless. I have actually 2 partitions (default ubuntu installation) and one of them reports the problem you are facing. 

I think that the answer you are expecting is someone to tell you exactly how to rezise your swap partition so as to eliminate the problem. 

We have the same disk size and my swap is looking like this:
/dev/sda5       1945147392 1953523711    8376320     4G 82 Linux swap / Solaris

and it does not "complain" about this partition. The thing is: do you need such a low space swap partition as mine?
My humble opinion is that you do not need such a huge size of swap partition that you have, yet this might be me.

If I were in your shoes, I would try to resize the swap partition in half.

As I mentioned other users might provide you a better answer.

Regards!

---

### Post by pqwoerituytrueiwoq on 2018-05-02
I know i used gparted, i do not recall which version was used, i would the version on ubuntu 10.04 or later
maybe i had it align to cylinder?

as for the swap partition, when i made it it was normal for the installer to make one based on system memory, so i followed that rule, do i need 16g swap, nope, do i need 16gb ram, probably not, but i use a 8gb ram disk, the only time i use swap is when running more than one virtualbox

should i just back and redo the partition layout with gparted?

---

### Post by oldfred on 2018-05-02
Even moving a few sectors has risks. It may want to copy entire thing & then take forever.

---

### Post by pqwoerituytrueiwoq on 2018-05-03
So i copied everything to a alt drive
remade all my partations
copied ed all my data back and found out 3 of my virtualbox disks are now damaged as i get a I/O error reading on the backup...
none of those were important only one is a potential minor inconvenience 
so then all i needed to do was fix the UUIDs
and here is where i get laughed at after spending 2 hours coping data i forget to type the partition number so instead of setting sda5 to a swap partition with a specific uuid i turned sda into one...
edit: that TOOK all night just to back up and restore the data twice

EDIT:
As for specifying what drive is sda, sdb, sdc, etc.
figured out i can use /dev/disk/by-id/
[FONT=courier new]echo "$(ls /dev/disk/by-id/ | [FONT=courier new]grep '^ata-'[/FONT] | egrep -v '\-part[0-9]$')"[/FONT]
I needed to be able to get the drive for a script to use with hddtemp

---

