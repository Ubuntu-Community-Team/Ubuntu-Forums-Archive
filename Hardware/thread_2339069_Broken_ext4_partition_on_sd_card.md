---
title: "Broken ext4 partition on sd card"
date: 2016-10-04
forum: Hardware
---

### Post by lngs on 2016-10-04
Hi.
Although my question is not fully related to linux and is rather related to android, I decide to post my question on this forum firstly, because the tools I use to recover it is on a Kubuntu machine and secondly because the issue seems to affect only the ext4 partitions on the card.
I have 8gb sd card, with two partitions on it (4gb - fat32 partition and 3.4gb ext4 partition according to link2sd manual for android) , on which most applications (including google play and link2sd itself) are linked to the second (ext4 partition). Everything worked fine, until few days ago, when I had an application hang on my smartphone which I tried to resolve with cleaning some space with a cleaner app which caused a greater system hang. After a quick, manual reboot android booted up with "android is upgrading 1 of 3" message and when it loaded, all applications linked to the second partition disappeared. 
Now it comes to linux - when I connected the drive to my Kubuntu 16.04 machine, it recognized both two drives, although it could not load the ext4 partition (superblock error in dolphin) but was able to get into the fat32 partition although dolphin was listing the files only, excluding 3 hidden partitions (when tried after that on Windows, it was able to access the fat32 partition with no problem, also the surface scan with "Minitool Partition Wizard" Windows partition manager did not find any errors). Then I dd cloned the whole sd card (without error) and tried to recreate the partition table in GParted with "unable to create partition table" error. After that I ran both fsck.ext4 and e2fsck commands on the ext4 partition with many "Buffer I/O error on ...., logical block ..., lost async page write" errors ending up with "unable to set superblock flags on /dev/sdxy". 
Does all this mean that the sd card is totally broken and if yes, why it happens only to the ext4 partition and not to the fat32 one? And what else could I try to restore the data from the sd card (or the dd cloned copy of it). And if it comes to it - are cloned partition more easily recoverable than that on the sd card?
(sorry about my hard-to-read english writing, I am not a native speaker obviously  )

---

