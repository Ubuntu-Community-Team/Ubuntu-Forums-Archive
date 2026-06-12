---
title: "Can't use alternative SuperBlock to fix and mount hard drive"
date: 2012-12-22
forum: Hardware
---

### Post by phinsil6 on 2012-12-22
Recently I restarted my perfectly fine ubuntu 12.04 computer.  only to find when it came back up that it was reporting a disk boot failure.  after searching and troubleshooting a lot, it seems i have a bad superblock.  so i tried the following three tutorials:
[http://erikimh.com/linux-recover-corrupted-partition-from-a-bad-superblock/](http://erikimh.com/linux-recover-corrupted-partition-from-a-bad-superblock/)
[http://www.cyberciti.biz/faq/linux-list-disk-partitions-command/](http://www.cyberciti.biz/faq/linux-list-disk-partitions-command/)
[http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html](http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html)
None of them worked, every suberblock i tried said that it couldn't read it.  many of them said, could it be a zero length partition.  Can somebody please help me out.  I have about 150gb of videos on there that i would really not like to lose.

Thanks,
phinsil6

---

### Post by phinsil6 on 2012-12-23
nobody have any ideas?

---

### Post by oldfred on 2012-12-23
Using alternative superblock is an advanced repair. Did you also do the standard e2fsck first?

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

    
If still not working you could try testdisk, but if large files like videos it may be difficult to recover with photorec or other scan tools.
       [https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)


Last ditch redo superblocks:
 [http://ubuntuforums.org/showthread.php?t=1681972&page=5](http://ubuntuforums.org/showthread.php?t=1681972&page=5)
Worked for this user:
[http://ubuntuforums.org/showthread.php?t=2033778](http://ubuntuforums.org/showthread.php?t=2033778)
[http://ubuntuforums.org/showthread.php?t=1684746](http://ubuntuforums.org/showthread.php?t=1684746)
Some additional advanced ways:
[http://animeshdas.wordpress.com/2009/11/18/data-recovery-from-corrupted-ext2ext3-filesystem-having-bad-superblock/](http://animeshdas.wordpress.com/2009/11/18/data-recovery-from-corrupted-ext2ext3-filesystem-having-bad-superblock/)
[http://www.hanksaves.com/hddrecovery/index.php/Welcome_to_Hank%27s_Data_Recovery_Wiki](http://www.hanksaves.com/hddrecovery/index.php/Welcome_to_Hank%27s_Data_Recovery_Wiki)

---

