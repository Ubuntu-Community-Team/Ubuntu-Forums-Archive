---
title: "Finished with ddrescue ... now stuck because of ext2 ???"
date: 2010-11-18
forum: Hardware
---

### Post by WinRiddance on 2010-11-18
I finally managed to get an old 250 GB drive of mine to start up with some external ide cables/adapters so that I could run it via a USB port on my laptop. Gparted recognized the disk just fine so I went ahead and had the entire disk formatted as an ext3 linux partition that I was going to use for data recovery purposes.

Following the instructions from this Link:
[How to save data from crashed disks with ddrescue ...]("http://www.cyberciti.biz/tips/how-do-i-save-recover-data-from-crashed-disks-with-dd-and-ddrescue-command.html")

... I used my Ubuntu root terminal and entered this:  **ddrescue  /dev/sda3 /dev/sdd1**
sda3 is the partition that I wanted to backup, to the newly formatted sdd1 partition on the IDE drive.

It took a few hours but eventually the ddrescue process completed, showing zero errors anywhere. When done, the message stated:  **Process completed** (still no errors)

Then, according to the instructions, I followed the next step by entering:  **fsck /dev/sdd1**
This brought up a warning, stating that alls data on sdd1 would be irrevocably altered ... followed by numerous explanation marks.

Panicking, I immediately choose "NO" when asked if I wanted to proceed.

After lots more reading and forum searches I went ahead and tried the same fsck command again, this time receiving this output:

> root@winriddance-laptop:~# fsck /dev/sdd1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdd1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

root@winriddance-laptop:~# What really gets me is the fact that those instructions **didn't say anything about needing an ext2 partition** in order to use ddrescue in this particular manner. I'd formatted that entire IDE partition as ext3 since I knew this to be standard for Linux. I do have an image.dd file in the root of my primary drive, but now I have absolutely no idea what I can do with it, or how to gain access to the information within that file.

Again, my backed up data, consisting of an image.dd file when all was said and done, is located in the root of my primary ext4 64bit Ubuntu drive. According to the properties that file was created this morning and accessed late this afternoon ... all of which makes sense. Now what do I do ... ???

---

