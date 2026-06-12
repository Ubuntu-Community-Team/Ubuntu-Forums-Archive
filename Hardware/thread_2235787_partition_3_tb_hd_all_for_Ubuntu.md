---
title: "partition 3 tb hd all for Ubuntu"
date: 2014-07-22
forum: Hardware
---

### Post by radar2609 on 2014-07-22
I have a PC that HAD windows 7 with 3 partitions ; 1 for windows, 1 for ubuntu (dual boot) and one for data (because windows couldnt make bigger partitions). I recently took off windows and made my pc full Ubuntu. BUT I cant figure out how to make ONE partition all Ubuntu. I have 4 gig ram, 3 tb internal HD and years and years experience with windows.

---

### Post by TheFu on 2014-07-22
Any HDD over 2TB needs to be GPT formated.
Having 1 partition for Ubuntu is against best practices.  It is strongly recommended to have 3 partitions:
* /
* /home
* swap
If you don't hibernate, then make the swap 2G, not larger.
/ - doesn't need to be over 50G ... I routinely allocate only 10G, but don't use many GUI programs, so 50G should be extreme overkill.
/home - can be the rest, but I'd probably limit that as well - large media files - I don't want those in my ~/ *HOME* - it makes backups less fun.  Media files outside HOME, in a special partition make backups cleaner.

So - if you want to repartition your system and start over, boot off any liveCD and run gparted. It is not possible to modify any partitions that are currently "in-use".  Be certain to backup your data first, if you care about it.

If more detailed instructions are needed, please post the link from the **boot-info** script.

---

### Post by oldfred on 2014-07-22
What one partition do you want?
You need to have gpt partitioning, so post this:

       sudo apt-get install gdisk
sudo gdisk -l /dev/sda
sudo parted -l

If installing Ubuntu do not make one very large /  (root) partition. Many have had issues. Better to have a 25GB / and have separate /home or what many of us use data partition(s).

      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4
2. all but 2 GB Mountpoint /home logical beginning ext4
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

