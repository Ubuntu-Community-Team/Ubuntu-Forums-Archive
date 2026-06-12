---
title: "recover  deleted files on external ssd"
date: 2021-12-19
forum: Hardware
---

### Post by winn100 on 2021-12-19
[I'm a newbie]  I accidentally deleted data on external ssd while using gparted. I chose wrong device and hit "delete" by mistake.. I have not done anything further with the drive. I[SUB]s there any way I can recover/restore the deleted data?[/SUB]] :(

---

### Post by oldfred on 2021-12-19
SSD do not save data like HDDs. The trim function clears data so writes are faster.
But some SSD do not support trim on USB/external drives which is another issue.

You may be able to use parted rescue or testdisk to find old partitions & restore them.

backup partition table before any changes, so you can get back to current if changes not correct, change example from sda to your device /dev/sdb or whatever it is.
sudo sfdisk -d /dev/sda > PT_sda.txt
So you know sectors:
sudo parted /dev/sda unit s print

Used parted rescue
[https://ubuntuforums.org/showthread.php?t=2362656](https://ubuntuforums.org/showthread.php?t=2362656)
[http://ubuntuforums.org/showthread.php?t=2315405](http://ubuntuforums.org/showthread.php?t=2315405)
GParted's partition-recovery tool.
Device -> Attempt Data Rescue in GParted
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) & 
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[https://help.ubuntu.com/community/DataRecovery#Lost_Partition](https://help.ubuntu.com/community/DataRecovery#Lost_Partition)

---

