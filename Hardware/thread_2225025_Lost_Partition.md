---
title: "Lost Partition"
date: 2014-05-19
forum: Hardware
---

### Post by julian8 on 2014-05-19
Hi everyone! first of all, 2 things... english isnt my first language and im new in linux.

Recently i decided to replace my Windows 7 with xubuntu. Before the instalation i had 1 HDD with 2 partitions, one with the OS (windows) and 1 with all my data. When i installed xubuntu i choose the "replace windows" option, and xubuntu used all the HDD for the instalation. The question is, i'ts any way to recover my "Data" partition?

---

### Post by oldfred on 2014-05-19
Reinstall says overwrite Ubuntu but it also erases existing Windows.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

STOP using system.
Ubuntu is not large, so it have not overwritten all your data. But you will not be able to recover all of it as Linux writes to various locations thought the install partition.
Always better to use Something Else to manually choose partitions.

I would first try testdisk to see if it can restore the data partition.
      
 [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[URL="http://www.cgsecurity.org/wiki/TestDisk"]http://www.cgsecurity.org/wiki/TestDisk
[/URL]
 Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[URL="http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS"]http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS

      [/URL]
 NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)
For NTFS but may charge to actually get your data, but can run to see if it works better.
[http://ubuntuforums.org/showthread.php?t=2193293](http://ubuntuforums.org/showthread.php?t=2193293)
[http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810](http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810)
[http://www.getdata.com/](http://www.getdata.com/)
For NTFS - GetDataBack often recommended
Caution: getdataback is not the same and is a scam.

    [URL="http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS"]
[/URL]

[URL="http://www.cgsecurity.org/wiki/TestDisk"]
[/URL]

---

