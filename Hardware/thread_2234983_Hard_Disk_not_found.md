---
title: "Hard Disk not found"
date: 2014-07-18
forum: Hardware
---

### Post by vissertw on 2014-07-18
Hi, I am trying to install a new harddisk on my laptop. When trying formatting it GParted says:

The driver descriptor says the physical block size is 512 bytes, but Linux says it is 2048 bytes.
Can't have a partition outside the disk!

What should I do now?

It appears I have got a Advanced AF Format harddisk how can I make this harddisk visable on my laptop by using the terminal? Or any other way?
 
Thanks,

Ton.

---

### Post by oldfred on 2014-07-18
IF 2048 that is odd. I think I have seen one or two others with that though.
Normally 512 is used but Advanced format drives are 4096.

Did you use Windows originally to format or is this a drive where drive vendor requires Windows software to make it work correctly?

       First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)
srs's to show 8 sector alignment
$ sudo parted /dev/sda unit s print

---

