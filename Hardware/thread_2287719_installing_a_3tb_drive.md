---
title: "installing a 3tb drive"
date: 2015-07-21
forum: Hardware
---

### Post by jgw on 2015-07-21
I have been trying to get a hard drive installed.  I plugged it in (usb) ran gparted, created a new partition (gpt) then formatted the drive.  I cannot mount it.  I have read a number of postings on this one.  I did a number of things suggested to no avail.  The results of my efforts can be found at [http://pastebin.com/Du5mST8E](http://pastebin.com/Du5mST8E)   disks tells me its ok with one bad sector.  Its sitting there at /dev/sdb but ......

Hopefully, somebody can tell me where I went wrong - thank you.............

---

### Post by weatherman2 on 2015-07-21
I don't see any partitions listed in your output.  (fdisk may not show them anyway with a gpt disk  try the "parted -l" instead to show partitions.)    You need to create at least one partition - even if that's the only one on your whole hard drive.  If you use Gparted to create the partition, you can pick the file system (ext4, NTFS, etc.) at that time and the partition will be formatted during the process of creating the partition.

And FYI, once you've created a partition, the correct mount command would be:

```
sudo mount /dev/sdb1 /mnt
```

(use /dev/sdb1 not /dev/sdb - sdb1 indicates partition 1).

You mount partitions, not disks.

---

### Post by oldfred on 2015-07-21
Some USB caddies do not support drives over 2TB. 

Your drive shows 512/512 and new drives almost always are 512/4096 or new 4K drives.
If that is from caddy not translating it correctly it then could be the issue.

       [URL="http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/"]http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/
[/URL]
 Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)

Also fdisk does not work on gpt partitioned drives. There is now a new copy but only in newest Ubuntu.
use parted or gdisk.
       
 sudo parted /dev/sdb unit s print
      
 sudo gdisk -l /dev/sdb

If you do not have gdisk which is the fdisk for gpt drives:
sudo apt-get install gdisk

Can you plug it into a SATA port?

Other issues once mounted may be ownership & permissions.

        


[URL="http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/"]
[/URL]

---

### Post by jgw on 2015-07-21
Thanks for the replies.  I changed the caddy and suddenly my 3tb drive became a 800+mb drive.  Then I ran :
greg@greg-MS-7222:~$ sudo gdisk -l /dev/sdb
[sudo] password for greg: 
GPT fdisk (gdisk) version 0.8.8

Warning! Disk size is smaller than the main header indicates! Loading
secondary header from the last sector of the disk! You should use 'v' to
verify disk integrity, and perhaps options on the experts' menu to repair
the disk.
Caution: invalid backup GPT header, but valid main header; regenerating
backup header from main header.

Warning! One or more CRCs don't match. You should repair the disk!

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: damaged

****************************************************************************
Caution: Found protective or hybrid MBR and corrupt GPT. Using GPT, but disk
verification and recovery are STRONGLY recommended.
****************************************************************************
Disk /dev/sdb: 1565565872 sectors, 746.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 146E0C40-F6A8-4B8C-BF11-0B6AFA4A80F3
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 5860533134
Partitions will be aligned on 2048-sector boundaries
Total free space is 5860533101 sectors (2.7 TiB)

Number  Start (sector)    End (sector)  Size       Code  Name
greg@greg-MS-7222:~$ sudo gdisk -l /dev/sdb
[sudo] password for greg: 
GPT fdisk (gdisk) version 0.8.8

Warning! Disk size is smaller than the main header indicates! Loading
secondary header from the last sector of the disk! You should use 'v' to
verify disk integrity, and perhaps options on the experts' menu to repair
the disk.
Caution: invalid backup GPT header, but valid main header; regenerating
backup header from main header.

Warning! One or more CRCs don't match. You should repair the disk!

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: damaged

****************************************************************************
Caution: Found protective or hybrid MBR and corrupt GPT. Using GPT, but disk
verification and recovery are STRONGLY recommended.
****************************************************************************
Disk /dev/sdb: 1565565872 sectors, 746.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 146E0C40-F6A8-4B8C-BF11-0B6AFA4A80F3
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 5860533134
Partitions will be aligned on 2048-sector boundaries
Total free space is 5860533101 sectors (2.7 TiB)

Number  Start (sector)    End (sector)  Size       Code  Name

So, I think its time to run gparted again, delete any partitions and then create a new one and see what happens?

---

### Post by weatherman2 on 2015-07-21
Yes - and go back to the original caddy.

---

### Post by jgw on 2015-07-21
Thank you for the reply.  I have now inserted a new partition.  When I did that I had one option: gpt.  The results were:

greg@greg-desktop:~$ sudo gdisk -l /dev/sde
[sudo] password for greg: 
GPT fdisk (gdisk) version 0.8.10

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sde: 5860533168 sectors, 2.7 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): C8506CB4-0368-4185-B277-62035728C0AD
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 5860533134
Partitions will be aligned on 2048-sector boundaries
Total free space is 5860533101 sectors (2.7 TiB)

Number  Start (sector)    End (sector)  Size       Code  Name

This looks better?

For the heck of it I tried to mount the drive.  I got:
reg@greg-desktop:~$ sudo mount /dev/sde /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sde,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.
greg@greg-desktop:~$

---

### Post by oldfred on 2015-07-21
Much better.

Not sure if first caddy caused issue or the tools you used to partition it?
Often gparted or gdisk with new gpt partitioning work best.

---

### Post by jgw on 2015-07-21
Thank you for the help

I did a quick format, with disks, and then tried to mount it, I failed:
reg@greg-desktop:~$ sudo mount /dev/sde /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sde,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.
greg@greg-desktop:~$ dmesg | tail
[18323.447460] sd 10:0:0:0: [sde] Very big device. Trying to use READ CAPACITY(16).
[18323.453859]  sde:
[19006.820127] sd 10:0:0:0: [sde] Very big device. Trying to use READ CAPACITY(16).
[19006.823862]  sde: unknown partition table
[19006.824861] sd 10:0:0:0: [sde] Very big device. Trying to use READ CAPACITY(16).
[19006.828480]  sde: unknown partition table
[19007.098710] sd 10:0:0:0: [sde] Very big device. Trying to use READ CAPACITY(16).
[19007.101953]  sde: unknown partition table
[19007.201602] sd 10:0:0:0: [sde] Very big device. Trying to use READ CAPACITY(16).
[19007.210749]  sde:


I must be missing something here?

---

### Post by oldfred on 2015-07-21
I have seen others with issues using Disks and gpt with very large drives. 
What version of Ubuntu? I think newer versions have major fixes to Disks.

I have used gparted for gpt since 10.10, but do not have any multi-TB drives.

---

### Post by weatherman2 on 2015-07-21
> **jgw said:**
> Thank you for the help

I did a quick format, with disks, and then tried to mount it, I failed:
reg@greg-desktop:~$ sudo mount /dev/sde /mnt

I must be missing something here?

Again: you mount PARTITIONS not DISKS.

/dev/sde is a reference to your DISK.

/dev/sde1 is a reference to the first PARTITION on the disk.

Try this:

```
sudo mount /dev/sde1 /mnt
```

---

### Post by jgw on 2015-07-21
Thank you for the replies.  

Here is what I have done.  
First I put a new partition on the drive (gpt)
then I put another partition on the gpt partition for ext4
Then I mounted it with sudo mount /dev/sde1 /mnt
then I restarted disks to see what I had and it said that it was now mounted on /mnt
then I went to mnt to see what was there (it didn't show up anyplace)
the only thing at /mnt was an empty lost & found folder

Thanks again for all the help.  I gotta eat dinner.  I will get back to this tomorrow (there has to be an answer)

Thanks again for all the help.

---

### Post by weatherman2 on 2015-07-21
You need to add the partition to your /etc/fstab file so that it gets automatically mounted at each boot.  (There are lines already in that file. DO NOT REMOVE OR CHANGE THEM!  Add ONE line to the bottom of it - see below.)

FYI, /mnt is not a good permanent place to mount your partition.  It's better to make a directory under /mnt and mount it there:

```

sudo mkdir /mnt/data
sudo mount /dev/sde1 /mnt/data

```

But /etc/fstab uses different syntax than the "mount" command.  And you may wish not to use the reference /dev/sde1 - because that could change depending on the order you have connected other devices.  (It could be /dev/sdd1 or /dev/sdf1 if you plug in some other device.)  Instead, use the partition's UUID to reference it.  UUID is a unique identifier code used to reference something in the operating system.

What's the UUID of your partition?  Find it using the blkid command:

```
sudo blkid
```

The output will have several lines like this:

```

/dev/sde1: UUID="e6b1edce-a04a-4eeb-83c5-940c63be77a1" TYPE="ext4"

```

(but your UUID will be different than this).

Now, using a text editor, add a line to the bottom of your /etc/fstab file, maybe this:

```

UUID=e6b1edce-a04a-4eeb-83c5-940c63be77a1 /mnt/data ext4 rw,nosuid,nodev,uhelper=udisks 0 0

```

(Again, replace "e6b1edce-a04a-4eeb-83c5-940c63be77a1" with whatever your UUID turns out to be.)

And that line is for an ext4 (Linux) format partition.  If you used something else, you'll need a different line than I gave above.

Finally, BEFORE YOU REBOOT, but after you have edited your /etc/fstab file, make sure the line you added is correct.  Type this command:

```
sudo mount -a
```

If all is correct, you will get NO OUTPUT from that command.  If you get an error, go back and fix your /etc/fstab file, or remove the new line until you figure out what you want it to be, otherwise you will have trouble booting up next time.

---

### Post by jgw on 2015-07-21
Thanks for all the help!

My current problem is kinda simple (to express).  the disks program tells me the drive is mounted on /mnt  I cannot find, or see it anyplace but there.  I am not sure how that is even possible.  My second thing is that I bought this drive to replace another, on another machine (current drive is too small)  Anyway, once I can get this machine, recognized and accessible (showing me its ready to goto work) I am going to attach it to my existing, smaller drive, copy everything over to this drive and then install this drive as the new drive on that machine.

---

### Post by weatherman2 on 2015-07-21
If you mounted the new drive's partition to /mnt, then navigate in the file system to the /mnt directory (so at the top of your files system, you'll see directories like /var /etc /home ... and /mnt, among others.)  If it's a new ext4 partition, the only directory or file there should be one called "lost+found."

If this is an ext4 partition, you'll also need to set permissions on the top level directory, otherwise you won't be able to write anything to it (without "sudo").  If the partition was formatted in some other format - say Windows NTFS or FAT32 - then you shouldn't need to worry about permissions.

If you haven't mounted anything to /mnt since last reboot then it's just an empty directory in your file system.

The mount command itself isn't persistent between reboots - that is, if you used "mount" once then rebooted, you'll have to issue the mount command again to get the partition mounted back in /mnt .

If you want it automatically mounted each time you boot, edit your /etc/fstab file as described above.

---

### Post by jgw on 2015-07-22
Thank you for all the help.

Here is what I did:
removed all partitions
installed the new, gpt, partition
inserted the ext4 partition
formatted the drive with disks program
mounted the drive (sudo mount /dev/sde1 /mnt)
opened the drive and found the empty lost & found folder 

As far as I can tell everything is fine and I can see the lost & found thing.  I think what confused me was the lost & found.  I thought something was terribly wrong but I got straightened out on that one.  I also didn't understand that, after I had created the initial, new, partition (gpt) I then needed to create another partition for the operating system (ext4).   Now I will hook this drive up to the machine that I am going to swap out an existing, smaller, drive and replace it with this drive after I am through copying the contents of the old drive.  On reflection I think I will open up that machine and use an unused sata connection to get it done.

Anyway, thanks for all the help, I REALLY do appreciate it!!!

---

### Post by oldfred on 2015-07-22
Just because we now have multi-TB sized drives, we should not make very large / (root) partitions. Back when they set up defaults of / & swap you were typically dual booting with Windows on a  100 to 500GB drive. 
Often best to have data partition(s) or separate /home.

       One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

