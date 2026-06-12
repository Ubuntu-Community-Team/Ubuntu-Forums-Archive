---
title: "rsync slow between 2 local SATA drives"
date: 2015-03-01
forum: Hardware
---

### Post by boris111 on 2015-03-01
Having a problem with rsync running slow (12 MB/s) between all my drives.  I tested this between two ext4 file systems as well as ext4->NTFS and I get similar results.  I tested read speeds with hdparm and that looks good on all drives.  I'm running Ubuntu Server 13.04.

Edit: I should add that over Gigabit ethernet from a Windows machine I'm getting better rates (25-35 MB/s) to these same drives.

My rsync command:
sudo rsync --progress -av --exclude 'lost+found*' /mnt/phobos /mnt/tharsis

Testing read speeds I look pretty good
~$ sudo hdparm -Tt /dev/sdc

/dev/sdc:
 Timing cached reads:   1946 MB in  2.00 seconds = 973.32 MB/sec

My fstab:
#Deimos
UUID=68314b72-b7d3-46f8-8319-83c643881395 /mnt/deimos auto defaults,comment=deimos1_5,nobootwait 0 0

#Phobos
UUID=7e512e35-c9a9-4b14-8bec-339adaa37864 /mnt/phobos auto defaults,comment=phobos3_0,nobootwait 0 0

#Tharsis
UUID=4A427C760BC50B5C /mnt/tharsis auto defaults,comment=tharsis3_0,nobootwait 0 0

mhddfs#/mnt/deimos,/mnt/phobos /mnt/hellas fuse nonempty,allow_other 0 0

---

### Post by weatherman2 on 2015-03-01
It looks like one of the drives (the destination drive) is NTFS?  In my experience, writing to NTFS especially is slower in Linux than writing to ext4.  You might also check the CPU load during rsync; I think you'll see not rsync using CPU but also the fuse driver for NTFS.  If by chance you have a really slow CPU, that could influence the copy speed significantly.

Still, 12MBps is really slow, you're right.  But how are you measuring that?  From rsync?  I'm not sure what that number really means.  If say half the files you are trying to copy already exist on the destination and half of the source files need to be copied, does that mean the reported copy rate is 1/2?  I'm not sure.

You might try a straight scp instead of rsync as an experiment.  Try a pretty large file; scp will report quick rates for small files that may not be meaningful.

---

### Post by boris111 on 2015-03-01
I was measuring from rsync's --progress.  NTFS is contributing to slowness as I'm able to get 30 MB/s ext4->ext4 rsync (still rather slow for local drives).

I tried test below and I'm seeing NTFS is performing worse here as well, but the ext4 is much much higher compared to rsync rates.  I'm out of ideas for why rsync is still so much slower even for ext4?  

root@mars:/mnt/MyNTFSMnt# dd if=/dev/zero of=testfile0 bs=8k count=10000; sync;
10000+0 records in
10000+0 records out
81920000 bytes (82 MB) copied, 4.70832 s, 17.4 MB/s
root@mars:/mnt/MyNTFSMnt# cd /mnt/MyExt4Mnt
root@mars:/mnt/MyExt4Mnt# dd if=/dev/zero of=testfile0 bs=8k count=10000; sync;
10000+0 records in
10000+0 records out
81920000 bytes (82 MB) copied, 0.532613 s, 154 MB/s
root@mars:/mnt/MyExt4Mnt# dd if=/dev/zero of=testfile0 bs=8k count=10000; sync;[/FONT]

---

