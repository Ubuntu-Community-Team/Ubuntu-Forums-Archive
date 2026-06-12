---
title: "Repeated / mount fails on boot but disk ok?"
date: 2011-04-10
forum: Hardware
---

### Post by remerson on 2011-04-10
I have a laptop running xubuntu 9.10 64-bit that has been running fine for a year or so. Machine is circa Dec 2009, so not very old.

I generally reboot the machine around once every few weeks, I usually prefer to suspend.

Starting about two months ago, the machine failed to boot with errors reported on /dev/sda2 (my / partition) when I restarted it for a kernel update.

Manual fsck fixed this issue. While worrying once, I put this down to a glitch.

Rebooted a few more times to check and no errors. I then started to reboot more often to see if the problem came back - it did.

1-2 weeks later, the same issue happened again. Again, manually fixed. Further reboots fine for a few weeks. Then breaks again. Rinse, repeat. Does not happen every reboot but quite often. Probably 4-5 times in total now. Generally takes several days/a week for the problem to appear.

In all cases, the fsck errors flagged are "small" i.e. 1-2 problems. Generally low inode numbers reported as having issues (first few 100/1000 inodes), so looks like the front of the disk. No superblock issues.

So, I thought this is failing hardware...


Ran fsck -c badblocks scan several times - no problems have ever been reported.

Also ran smartmontools several times. SMART reports passed. Multiple short and extended online SMART tests all pass as well. Again, no problems ever reported.

My /home partition has been fine and never failed to mount once - only my / partition. My /home is also fully backed up, so I'm not too scared if the disk does die completely.


As SMART and badblocks both seem fine, I'm stumped as to the problem here. I don't want to buy a new disk and go through hassle of fitting/restoring etc. if unnecessary.


Anyone seen anything like this before?

Is the disk really going bad or is this something else like strange ext4 corruption? 

What other tools/diagnosis can I try here to help isolate the issue?


Any help/advice much appreciated!

---

