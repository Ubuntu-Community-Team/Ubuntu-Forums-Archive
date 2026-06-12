---
title: "Xubuntu will not boot"
date: 2015-08-12
forum: Hardware
---

### Post by hopefulcd on 2015-08-12
Today, my computer decided that it  wouldn't boot into the operating system. The drive was working fine for a few years now, but today it wouldn't boot. I spent awhile diagnosing the  problem to narrow down what was causing it. Basically, the partition  table is not able to be read so the drive is not able to boot into the  OS. The drive was running xubuntu 13.10 64bit desktop. Basically, I'm  not sure what to do now to retrieve the data from the drive, so I wanted  to reach out to others and see if anyone has any ideas. So far, I did a  couple of things:

1) I took the hard drive out and tried to boot  the drive from another computer. The drive wouldn't boot from a  different machine.

2) Using a Boot Repair Live CD, I ran the recommended repair, but the drive still wouldn't boot into the OS after restarting.

Here's the pastebin of the Boot Repair that I did:
[http://paste.ubuntu.com/12062569/](http://paste.ubuntu.com/12062569/)

3) Using an Ubuntu 14.04.3 Live disc, I ran a few different tests.
# fdisk -l
This showed a warning that the disc has a GPT partition table and fdisk will not read it.

# sudo badblocks -v /dev/sdb > /tmp/bad-blocks.txt
This test ran and found no bad sectors in the physical drive itself.

# sudo gdisk /dev/sdb
This  showed at first that no partition table was found. I then ran the  backup command 'b' to save the current partition table (even though it  said it didn't find one) and then ran the 'o' command to create a new  partition table/mbr/etc. I executed the command again and now it shows  the new partition table:
GPT fdisk (gdisk) version 0.8.8

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.


I  tried to reboot the drive using the new partition table, but the drive  was still not bootable to the OS. After this I reloaded the Live disc  and tried to mount the drive in order to save any files from the drive  itself. However, the drive will not mount using the new partition table.  Here's what I ran:


# sudo mount /dev/sdb1 /mnt
mount: block device /dev/sdb1 is write-protected, mounting read-only
mount: you must specify the filesystem type


The  mount command fails to mount the drive since there is no filesystem  specified. I tried a few commands to see what the filesystem on the  drive is, but the commands I ran didn't show any filesystem type for the  bad drive. The commands did show filesystem types for both the USB  drive and the backup harddrive.


Aside from just reinstalling the OS on the drive or a different drive, I really want to save some files from the hard drive and not lose any files. 

Any ideas?

Thanks for any help or comments.

---

### Post by kerry_s on 2015-08-12
sounds like the drive is going bad.

---

### Post by hopefulcd on 2015-08-14
As an update, I ran the # fsck command on the drive and it took awhile to complete. After it was done, a part of the old partition was restored. However, the part that was restored was for a different user on the harddrive, and all of the relevant information is still in the missing part of the drive. I'm at the point now that I'm about to send the drive in to a specialist company unless there are some other commands that I can try.

---

### Post by Bashing-om on 2015-08-14
hopefulcd; Hello;

Specialist cost big bucks . Might give :
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
a good read, and consider 'testdisk' to recover the files from an image.

[INDENT][INDENT]I hate when that happens
[/INDENT][/INDENT]

---

