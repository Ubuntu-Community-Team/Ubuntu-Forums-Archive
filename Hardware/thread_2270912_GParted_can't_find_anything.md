---
title: "GParted can't find anything"
date: 2015-03-26
forum: Hardware
---

### Post by Derek_Carr on 2015-03-26
I've just installed xubuntu 14.04 and gparted. When I start gparted it just sits there saying 'searching /dev/sda partitions' and is otherwise blank. The 'Disks' app finds the partitions with no problem and all the partitions are mountable (I unmouted them afterwards - neither seems to make any difference). How long does GParted normally take to find the partitions? Does it need several hours?

Thanks, Derek Carr, 
Birmingham, UK

---

### Post by yancek on 2015-03-26
Did you install GParted in Xubuntu?  Are you planning to create or modify partitions other than the one(s) on which Xubuntu is?  You can't modify the partition on which you have GParted installed because you need to unmount partitions before modifying.  This is one of the reasons why people usually put GParted on a separate disk or use it from the installation medium.  Generally, I would not expect it to take more than 10-20 seconds to open unless you have a lot of disks/partitions so probably the download or install was bad, hard to say

---

### Post by Derek_Carr on 2015-03-26
> **yancek said:**
> Did you install GParted in Xubuntu?  Are you planning to create or modify partitions other than the one(s) on which Xubuntu is?  You can't modify the partition on which you have GParted installed because you need to unmount partitions before modifying.  This is one of the reasons why people usually put GParted on a separate disk or use it from the installation medium.  Generally, I would not expect it to take more than 10-20 seconds to open unless you have a lot of disks/partitions so probably the download or install was bad, hard to say

Yes, I installed it in Xubuntu, but that is on a separate disk, so shouldn't be a problem. There are a lot of partitions, but the time you mentioned was about what 'Disks' took to see them. I'll have to uninstall GParted, download it again and try again. I did think that I should try and do it from the Xubuntu installation USB, but that seems to have developed a fault! I'll report back when I've tried some of that. Thanks for the reply.

Here's the update: I uninstalled GParted, rebooted then installed it again then ran it. Exactly the same, so I don't think that was the problem. I then found an image of lubuntu 14.04 which I burned to disk and booted with that. I tried GParted from that and exactly the same result, so I think there must be a problem with the partitions that Linux can't handle. I can work with them in Windows (XP), but, as you say, you can't do anything with mounted partitions. There are still a couple of things I might be able to try. I'll keep you posted!

---

### Post by weatherman2 on 2015-03-26
What devices do you have that Gparted would be scanning?  How many hard drives?  What kind?

What is the result of the terminal command

```
sudo parted -l
```

---

### Post by yancek on 2015-03-26
I think a good point to start is to post the output of the 'parted' command suggested above and also give some specific information such as which partition you have GParted installed to and which partition(s) you want to modify.

---

### Post by Derek_Carr on 2015-03-27
> **weatherman2 said:**
> What devices do you have that Gparted would be scanning?  How many hard drives?  What kind?

What is the result of the terminal command

```
sudo parted -l
```

Thanks for the  tip: this is what I got (which was about what I was expecting) -
[INDENT]derek@TOGAN-XU:~$ sudo parted -l
Model: ATA Maxtor 6Y160P0 (scsi)
Disk /dev/sda: 164GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  10.7GB  10.7GB  primary   fat32           lba
 2      10.7GB  21.4GB  10.7GB  primary   fat32           lba
 3      21.4GB  39.7GB  18.3GB  primary   fat32           boot, lba
 4      39.7GB  164GB   124GB   extended                  lba
 5      39.7GB  48.2GB  8456MB  logical   fat32
 6      48.2GB  58.9GB  10.7GB  logical   fat32
 7      58.9GB  64.2GB  5346MB  logical   linux-swap(v1)
 8      64.2GB  96.8GB  32.6GB  logical   fat32
 9      122GB   155GB   32.7GB  logical   ntfs
10      155GB   164GB   8809MB  logical   ntfs


Model: ATA Maxtor 6L250R0 (scsi)
Disk /dev/sdb: 251GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 2      2096kB  251GB   251GB   extended
 6      2097kB  14.7GB  14.7GB  logical   ext3
 5      14.7GB  251GB   236GB   logical   ntfs
[/INDENT]

 Which is quite a lot of partitions, I know, but I did it that way so they could be backed up to DVDs!
So that was OK, right? However, that gave me the idea of trying gparted in the terminal and this is what I got then -

[INDENT]derek@TOGAN-XU:~$ sudo gparted
======================
libparted : 2.3
======================

(gpartedbin:2181): GLib-CRITICAL **: Source ID 7 was not found when attempting to remove it

(gpartedbin:2181): GLib-CRITICAL **: Source ID 6 was not found when attempting to remove it

(gpartedbin:2181): GLib-CRITICAL **: Source ID 26 was not found when attempting to remove it

(gpartedbin:2181): GLib-CRITICAL **: Source ID 25 was not found when attempting to remove it

(gpartedbin:2181): GLib-CRITICAL **: Source ID 38 was not found when attempting to remove it

(gpartedbin:2181): GLib-CRITICAL **: Source ID 37 was not found when attempting to remove it

(gpartedbin:2181): GLib-CRITICAL **: Source ID 41 was not found when attempting to remove it

(gpartedbin:2181): GLib-CRITICAL **: Source ID 46 was not found when attempting to remove it

(gpartedbin:2181): GLib-CRITICAL **: Source ID 45 was not found when attempting to remove it

(gpartedbin:2181): GLib-CRITICAL **: Source ID 49 was not found when attempting to remove it

(gpartedbin:2181): GLib-CRITICAL **: Source ID 48 was not found when attempting to remove it

(gpartedbin:2181): GLib-CRITICAL **: Source ID 200 was not found when attempting to remove it

(gpartedbin:2181): GLib-CRITICAL **: Source ID 199 was not found when attempting to remove it

(gpartedbin:2181): GLib-CRITICAL **: Source ID 416 was not found when attempting to remove it

(gpartedbin:2181): GLib-CRITICAL **: Source ID 1742 was not found when attempting to remove it

(gpartedbin:2181): GLib-CRITICAL **: Source ID 1741 was not found when attempting to remove it

(gpartedbin:2181): GLib-CRITICAL **: Source ID 1769 was not found when attempting to remove it

(gpartedbin:2181): GLib-CRITICAL **: Source ID 1768 was not found when attempting to remove it

(gpartedbin:2181): glibmm-CRITICAL **: 
unhandled exception (type Glib::Error) in signal handler:
domain: g_convert_error
code  : 1
what  : Invalid byte sequence in conversion input
[/INDENT]

So that solves the problem of what the error is. Trouble is I've NO IDEA what it all means. This why I'm here - so over to you guys - and thanks.

---

### Post by dino99 on 2015-03-27
To fix a partition table : [https://www.linux.com/learn/tutorials/781778-how-to-fix-a-mangled-partition-table-on-linux](https://www.linux.com/learn/tutorials/781778-how-to-fix-a-mangled-partition-table-on-linux)
Prefered workaround: [http://askubuntu.com/questions/48717/how-to-manually-fix-a-partition-table](http://askubuntu.com/questions/48717/how-to-manually-fix-a-partition-table)

question: how was iniatialy the ubuntu's patitions been formated  with ? windows partition tool ? or ubuntu gparted tool ?

---

### Post by Derek_Carr on 2015-03-27
OK, thanks 9d9 - I've looked at the links and tried gparted /dev/sdb first. It came up with all GLIB messages again, but did list the partitions OK. So a problem with sda. I saw on one link a mention of testdisk, so I downloaded that and ran it to find a disk read error on one (windows) partion. So I'm off to reboot to windows to see if it can correct it and I'll come back and try gparted again - I'm not happy with trying to repair partions read/write errors like that at a terminal!

---

### Post by oldfred on 2015-03-27
I had a similar issue with gparted and my old XP drive. But I thought gparted now worked but showed partition with a red or yellow caution icon.

With my system I had to run chkdsk on the NTFS partition. My XP did work and did not show any errors. But it did take 5 minutes to boot. After chkdsk it improved to 4 minutes where Ubuntu was 40 sec on that system.

You may need to just run chkdsk on all your FAT32 or NTFS partitions.
We do not recommend FAT32 anymore as it really is only for small partitions or removeable devices. It cannot hold any file over 4GB and does not have a journal like NTFS or ext4, so repairs like chkdsk can take a lot longer or may not work.

I backup to DVDs, but just select various folders till DVD is full. I know which are my most critical folders to back up so I choose them.

---

### Post by Derek_Carr on 2015-03-28
Exactly! I was running chkdsk on everything while you were posting that - it does take ages! So after that, gparted now works, sort of. It's not a very robust piece of software - it crashed twice, but we are getting there. I'm making some room where I need it. 
Now I have a new problem related to this. How do I move a linux swap partition (booted from lubuntu on DVD)?

---

### Post by oldfred on 2015-03-28
You can move swap just like you move any other partition.
But it can be a slide game where you have to move several other pieces before you can move it.
And if inside an extended partition you have to keep it inside, or may have to expand/move extended first.

Many times easier just to recreate it and if MBR inside an extended partition. If you already have an install, it still should boot but will give an error on swap and then you edit fstab with new UUID.

---

### Post by Derek_Carr on 2015-03-30
Thanks oldfred - that reassured me - a slide game was what I needed anyway :) 
Anyway, after a lot of work both in ubuntu and Windows XP I've achieved what I wanted to do even on a dying disk. I found gparted not terribly robust when dealing with bad sectors, but necessary to do some things - like resizing extended partitions - that my Windows programs can't. So I've marked this thread as solved with the following conclusions:
Always start gparted from a terminal specifying the disk to work on. 
If it has problems use native checking software like chkdsk to make the best of the disk.

Thanks for the input everyone that has commented.

---

