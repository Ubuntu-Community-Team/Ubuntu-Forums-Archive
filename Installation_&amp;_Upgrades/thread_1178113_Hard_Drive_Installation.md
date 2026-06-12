---
title: "Hard Drive Installation"
date: 2009-06-04
forum: Installation &amp; Upgrades
---

### Post by dsbw on 2009-06-04
I just installed a 1TB hard-drive on my existing Mythbuntu system.

I used this reasonably helpful guide [here]("https://help.ubuntu.com/community/InstallingANewHardDrive").

For the "sudo lshw -C disk" step, things looked good:

>  *-disk:1
       description: ATA Disk
       product: WDC WD10EADS-00L
       vendor: Western Digital
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/sdb
       version: 01.0
       serial: WD-WCAU4A062288
       size: 931GiB (1TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=312e5b05

The capabilities: partitioned stuff wasn't there, but I've been messing with it. I noticed the the drive doesn't show up with a df, among other utilities.

Everything seemed okay until the formatting. The formatting didn't seem like it took long enough. I didn't know if that was an XFS thing or not. 

I rebooted and started copying files over, and the disk refuses to copy more than 4GB.

I tried clearing the partition, and reformatting as EXT3, which took a seemingly fitting amount of time--but I still can only get 4GB.

No idea how to proceed. Or how to "reset", since mkfs is complaining about fragment size when I try to reformat.

Help?

---

