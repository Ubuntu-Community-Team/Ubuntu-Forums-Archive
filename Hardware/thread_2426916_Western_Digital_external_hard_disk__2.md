---
title: "Western Digital external hard disk_ 2"
date: 2019-09-15
forum: Hardware
---

### Post by christon74 on 2019-09-15
Good afternoon fellow ubunters_ Aaargh! I have yet another problem with my external hard disk! It has unmounted of its own accord. It is correctly connected to the PC, it is plugged to the mains. Everything was OK until this morning. I have no idea how to mount it back and have access to all the files saved to it.
Ubuntu flavour: 18.04 LTS.
I am on dual boot (Windows 7). If I boot windows, the external hard disk is there and the files can be accessed. I have tried several things like checking the wires and connections, try to make free space, dpkg. Nothing seems to help. Oddly enough, if I run "disks" the external hard disk is listed. I have tried a test but the result is that "self-test failed". Is this a serious problem? I have just tried mounting it using a terminal. Does not work. 
Thanks for any tip.

---

### Post by TheFu on 2019-09-15
That mount isn't the correct command. It is missing the directory where you want it mounted.  The mount manpage explains.

Do you have backups for that data?  If not, make some to a new disk.  Since you can't read the disk those backups might need to be a bit-for-bit copy - use **ddrescue** to make that.

Posting the output from **sudo fdisk -l** for the disks would be helpful too, but we don't want to see the parts with 'loop' devices. Those aren't real storage.

Is there any chance that Windows didn't properly close the disk/partitions?  Win8+ will leave it open. Also, if the system uses hibernation, there can be problems.  Boot into Windows and fix those things - look for "fast startup" in Windows forums.

BTW, please post text, not images. If you post text, we can copy/paste and correct issues much easier.

---

### Post by christon74 on 2019-09-16
Hello TheFuO:)_ And thank you for the quick answer. I have tryped several commands on a terminal window, including f-disk-l and here are the results. With the hope it sheds more light on what's happened to my external hard disk. 

 ```
 	 	 	 	   [sudo fdisk -l gives this:     ]
 
 
 Disk /dev/sda: 232,9 GiB, 250059350016 bytes, 488397168 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 Disklabel type: dos
 Disk identifier: 0x8e904d12
 
 
 Device     Boot     Start       End   Sectors   Size Id Type
 /dev/sda1  *         2048    206847    204800   100M  7 HPFS/NTFS/exFAT
 /dev/sda2          206848 226770943 226564096   108G  7 HPFS/NTFS/exFAT
 /dev/sda3       226772990 488396799 261623810 124,8G  5 Extended
 /dev/sda5       226772992 488396799 261623808 124,8G 83 Linux
 
 
 root@christophe-ESPRIMO-E5731:~# **sudo mount -t ntfs /dev/sdb1 /media**
 Mount is denied because the NTFS volume is already exclusively opened.
 The volume may be already mounted, or another software may use it which
 could be identified for example by the help of the 'fuser' command.
 [EMAIL="root@christophe-ESPRIMO-E5731"]root@christophe-ESPRIMO-E5731[/EMAIL]:~#
 
 
 root@christophe-ESPRIMO-E5731:~# **sudo parted -l**
 Model: ATA Hitachi HDS72102 (scsi)
 Disk /dev/sda: 250GB
 Sector size (logical/physical): 512B/512B
 Partition Table: msdos
 Disk Flags:  
 
 
 Number  Start   End    Size   Type      File system  Flags
  1      1049kB  106MB  105MB  primary   ntfs         boot
  2      106MB   116GB  116GB  primary   ntfs
  3      116GB   250GB  134GB  extended
  5      116GB   250GB  134GB  logical   ext4
 
 
 
 
 Model: WD My Book 1110 (scsi)
 Disk /dev/sdb: 749GB
 Sector size (logical/physical): 512B/512B
 Partition Table: msdos
 Disk Flags:  
 
 
 Number  Start   End    Size   Type      File system  Flags
  1      1049kB  428GB  428GB  primary   ntfs
  2      428GB   749GB  322GB  extended
  5      428GB   739GB  311GB  logical   ext4
 
 
 
 
 Warning: Unable to open /dev/sr1 read-write (Read-only file system).  /dev/sr1
 has been opened read-only.
 Error: The partition's data region doesn't occupy the entire partition.
```
 Ignore/Cancel?

---

### Post by wildmanne39 on 2019-09-16
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by christon74 on 2019-09-16
Hello Wildmanne. I'm sorry, but "code tags" is gobbledygook to me, I cannot make sense of them. I have clicked the link, but I really do not see what's their use. And I am trying to abide by the rules. I have followed TheFu's instruction to post text (and not images). I am French (nobody's perfect) and when I post I try to keep things simple and write in plain, understandable English.

---

### Post by TheFu on 2019-09-16
```
 root@christophe-ESPRIMO-E5731:~# sudo mount -t ntfs /dev/sdb1 /media
 [B]Mount is denied because the NTFS volume is already exclusively opened.
[/B] The volume may be already mounted, or another software may use it which
 could be identified for example by the help of the 'fuser' command.
 root@christophe-ESPRIMO-E5731:~#
```

a) use root or use sudo.  Not both.  Using a root shell is frowned upon for many reasons.

b) Something in Windows is preventing the /dev/sdb1 device (it is a partition) from being properly closed.  Since Windows8, Microsoft has a few ways that are enabled by default. You need to research the solutions to disable this inside Windows.  "Fast Startup" is one of the terms.  Also, ensure hibernation is not enabled.  And ensure that only Basic Partitions are used inside Windows.  The Windows Disk Manager can show that last one. 
the "fuser" command isn't helpful in the error above.

code tags make output look the same in these forums as it does in a terminal.  Columns line up.  Without code-tags, output is too hard to read. I won't bother.  The "advanced editor" or Adv Reply options get where there is a '#' button just like the Bold button.  Use it the same.

---

### Post by oldfred on 2019-09-16
How to use Code tags, # in advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)
[http://www.bbcode.org/reference.php](http://www.bbcode.org/reference.php)
If using Quick Reply then just type in the code tags. I use the quote tag in quick reply & edit.
( [noparse]```
 and 
```[/noparse] ) 

You may need to run chkdsk or defrag or other Windows type maintenance on your NTFS partition. That can only be done from Windows or a Windows repair disk.

---

### Post by christon74 on 2019-09-17
Hello TheFu and OldFred. Magic! WD hard disk (My book) is back! But I really have no explanation. Remember I have said I am on dual boot (Windows7 / Ubuntu 18.4LTS) It's Windows 7, not 8. I have changed something to the Power options. The power button shuts down the computer. But the fast start-up option is nowhere to be found.  The hdd drive is back, can be accessed, and I can see the icon on the left panel. Should I mark this thread as "solved"? Not sure. Anyway, thanks to both of you OldFred and TheFu. I think I will copy/paste this thread to a text document for future reference if needed.

Magic? Well, my hdd is under a spell. It has disappeared again. It was there a couple of hours ago.

---

### Post by yancek on 2019-09-17
I would check the power options on windows 7 to verify that hibernation is not enabled.  I doubt this is the problem but simple enough to verify.

When you boot Ubuntu, go to the /media/username directory to see if you have any partitions on the external drive available.  THey should show by UUID and replace username here with your actual username.   Your output above shows the external drive has an ntfs primary partition along with a logical partition which is Linux.  Are you able to access the ntfs partition in windows?  Do you have problems accessing both partitions from Ubuntu or only one and if one, which one?  I would be very surprised if you could access the Linux partition from windows 7.

 In your initial post, you indicate you tried a test on the drive and that it reported failure but you neglected to indicate what test that might have been.  As pointed out above, your attempt to mount from the terminal failed because the command was incorrect.

Did you run chkdsk on the first partition of the external drive as suggested above?

---

### Post by christon74 on 2019-09-17
Good afternoon Yancek_ The first test I tried yesterday was SMART and self-test (Disks). There was an anomaly to which I had not paid attention: Ubuntu 16.04.3 LTS (16.04) (on /dvd/sdb5). So I deleted this partition this morning. I also tried  fsck /dev/sdb1, which is the largest partition on this drive, containing a large amount of video files and other data. This too gave an error message. I first tried it using a terminal and it gave this : ```
                         christophe@christophe-ESPRIMO-E5731:~$ sudo fsck /dev/sdb1
 [sudo] password for christophe:  
 fsck from util-linux 2.31.1
 e2fsck 1.44.1 (24-Mar-2018)
 ext2fs_open2: Bad magic number in super-block
 fsck.ext2: Superblock invalid, trying backup blocks...
 fsck.ext2: Bad magic number in super-block while trying to open /dev/sdb1
 
 
 The superblock could not be read or does not describe a valid ext2/ext3/ext4
 filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
 filesystem (and not swap or ufs or something else), then the superblock
 is corrupt, and you might try running e2fsck with an alternate superblock:
     e2fsck -b 8193 <device>
  or
     e2fsck -b 32768 <device>
 
 
 christophe@christophe-ESPRIMO-E5731:~$ 
```

The media folder is empty. Location is .cache/totem
I also tried  fcsk /dev/sdb1 using gparted and got an error message yet again. Could it be this external hard disk is on its last legs?
-Hello again _ Thursday 19th September. I am marking this thread as solved. I tried formatting it (external drive) using "disks". This failed to solve the problem. I then booted Windows 7 and formatted it "ntfs". This worked. Some data loss, but not too much. Again, thank you all for your time and help.

---

### Post by TheFu on 2019-09-17
Use **smartctl** and post the exact commands used, followed by the exact output. We need to see the raw values and some of the header information.  About 20% of the time, a HDD will fail while SMART doesn't show any issues.

Any data you want to keep needs to be backed up BEFORE there are any issues.  A "backup" means having 3 copies on at least 3 different storage media, connected to at least 2 different computers.  Backups can solve 1001 problems, so you don't need to know any fancy solutions for fixing logical disk errors --- like a corrupt superblock or trashed partition table.

Why delete a partition?  That won't make anything easier, unless you've given up.

---

