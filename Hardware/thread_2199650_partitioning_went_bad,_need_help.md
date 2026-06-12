---
title: "partitioning went bad, need help"
date: 2014-01-15
forum: Hardware
---

### Post by machina_13 on 2014-01-15
Please click the URL below to read the full issue and leave replys. I don't want to abuse this forum but I am in desperate need of help.
[ http://askubuntu.com/questions/405759/need-expert-help-partitioning-went-extremely-bad?noredirect=1#comment521195_405759]("http://askubuntu.com/questions/405759/need-expert-help-partitioning-went-extremely-bad?noredirect=1#comment521195_405759")


My question, or rather issue, is in the extent of  [http://askubuntu.com/questions/405370/bios-grub-partition-in-the-way-of-resizing-ubuntu-partition/405371?noredirect=1#comment520502_405371](http://askubuntu.com/questions/405370/bios-grub-partition-in-the-way-of-resizing-ubuntu-partition/405371?noredirect=1#comment520502_405371) in which I wanted to grow my Linux (ext4) partition. The partition /dev/sda6 was in the way of doing this and since it contained bios_grub I didn't touch it until someone with expert knowledge could help me.


[http://i.stack.imgur.com/xnb4T.png](http://i.stack.imgur.com/xnb4T.png)
****As suggested by the helper I deleted the highlighted partition /dev/sda6****


[http://i.stack.imgur.com/Whpsd.png](http://i.stack.imgur.com/Whpsd.png)
****All seemed well****

The partition was successfully removed so I went on to step 3, merging /dev/sda7 (the ext4 containing everything Ubuntu) with the unallocated partition to grow my Linux partition.

[http://i.stack.imgur.com/uMv5J.png](http://i.stack.imgur.com/uMv5J.png)
****Everything still seemed to be going the right way****

So everything went well. The helper suggested to turn swappoff on /sda8 during the process, so I did.
Gparted kept on merging the two partitions, which I think was a good thing, as well as refreshing itself to find all the partitions after turning swapoff.

When GParted finally refreshed, the program just stopped and shut itself down while it was still in the middle of growing /dev/sda7.

I restarted GParted to find this:
[http://i.stack.imgur.com/LhKGt.png](http://i.stack.imgur.com/LhKGt.png)
****Mini heart attack****

Now I'm running `sudo testdisk` from Ubuntu live DVD session, performing a deeper search on the hard drive. I did this yesterday allready, but I realized fixing this was a little, if not way over my head. So please, if you have the time (but especially the **knowledge**to help me with this (preferably in real time through chat or anything), Please...

[http://i.stack.imgur.com/Dyy2E.png](http://i.stack.imgur.com/Dyy2E.png)
****Depiction of TestDisk results****

---

### Post by vanadium on 2014-01-15
This shows (again) that moving a partition is a risky business, with limited chance of success. It is much safer to delete and recreate to grow a partition. You will be helped most quickly by reinstalling the system the way you want: this provides an opportunity for a thorough cleanup.

---

### Post by machina_13 on 2014-01-15
Thank you for your reply. Making backups on an external disks will be my first priority after this unfortunate event has ended. I want to restore as much data as possible though. Running TestDisk shows me that a lot, if not all my files are still present on the hard disk, including all the 'lost' partitions. I will post the results when it's finished with the deeper scan.

---

### Post by machina_13 on 2014-01-15
Screenshot attached.

---

### Post by Bucky Ball on 2014-01-15
Please refrain from inserting your screenshots in the body of your posts and attach them instead. Spare a thought for those with slow connections and vision issues.

To attach, 'Go Advanced' and use the paper clip icon. Thanks.

---

### Post by machina_13 on 2014-01-15
Ok, thanks

---

### Post by mastablasta on 2014-01-15
if your data is still there you probably only deleted/corrupted your partition table. in windows programs like partition doctor (not free) can restore partitions. i am not sure which one in linux does that. probably fdisk has some commands one could run to recreate the table. i don't know.

backups have to be done _**before**_ messing arround with partitions.

it happened to me once when the all data partitions but the first C "drive" dissapered on windows after a filezilla client update got stuck and crashed the OS. partition doctor recovered the table.

---

### Post by machina_13 on 2014-01-15
I guess I learned the hard way, right? If you know anyone who know how to help me or knows anyone else who knows how to help me then I would be very gratefull. Anyone who knows something the main link to the question is [http://askubuntu.com/questions/405759/need-expert-help-partitioning-went-extremely-bad?noredirect=1#comment521195_405759](http://askubuntu.com/questions/405759/need-expert-help-partitioning-went-extremely-bad?noredirect=1#comment521195_405759)

---

### Post by oldfred on 2014-01-15
gpt has backup partition table also. 
What does gdisk show. Not in Ubuntu live installer, but may be in other Linux repairCds.

sudo apt-get install gdisk
       sudo gdisk -l /dev/sda
    
 repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

---

### Post by machina_13 on 2014-01-15
ubuntu@ubuntu:~$ sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.8.1

Caution: invalid main GPT header, but valid backup; regenerating main header
from backup!

Caution! After loading partitions, the CRC doesn't check out!
Warning! Main partition table CRC mismatch! Loaded backup partition table
instead of main partition table!

Warning! One or more CRCs don't match. You should repair the disk!

Partition table scan:
  MBR: not present
  BSD: not present
  APM: not present
  GPT: damaged

Found invalid MBR and corrupt GPT. What do you want to do? (Using the
GPT MAY permit recovery of GPT data.)
 1 - Use current GPT
 2 - Create blank GPT

Your answer:

---

### Post by oldfred on 2014-01-15
Since you know primary gpt is invalid, I might try recovery of backup gpt table.
Of course always best to have good backups anytime you are editing or changing partitions.

I think if you use the p to print partitions, but do not use the w, you can revert to original version. Otherwise use the w to write the updated version to primary partition table.

---

