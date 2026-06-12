---
title: "how can i backup my entire OS"
date: 2009-01-20
forum: Installation &amp; Upgrades
---

### Post by Will4 on 2009-01-20
guys i need to install Windows XP in order to have my brother happy with some software (so sad) and i have no idea of how to back up my entire OS, does any of you know about it? How could i have all my configurations, stored dictioneries, email, etc... backed up?

 ASAP please, or my bro will kill me. 

any help will be appreciated. Thanks

---

### Post by Will4 on 2009-01-20
or how can i install Windows in an IDE second HD Maxtor 40 Gb without the regular "non booting" problem?

---

### Post by Tek-E on 2009-01-20
are you backing up windows XP? or ubuntu??

---

### Post by Will4 on 2009-01-20
I need to install Windows, 

so i want my whole Ubuntu backed up!! is that possible?
say YES please, haha

---

### Post by bgerlich on 2009-01-20
Plug in only the second drive, install XP, after plugging in your primary HD, configure GRUB to boot XP of your second drive.

BTW, why don't you give the Virualbox a spin, to please your revlatives ungodly urges and keep your Ubuntu intact ?

---

### Post by Tek-E on 2009-01-21
I have never done a backup of ubuntu myself. 
But maybe this guide will be of use to you.
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

Best of luck! =D

---

### Post by Will4 on 2009-01-21
thanks anyway!! much appreciation

---

### Post by andyFI on 2009-01-21
Hi,
There is an article in Personal Computer World (Jan 2009 Vol32 No. 1, under hands on, linux) about backing up and restoring linux partitions if this is still of interest.
Andy

---

### Post by imagodei on 2009-01-21
Do an image of entire disk or partition with Clonezilla. If you are going to backup entire disk, you'll need external disk or a network share on another comp; if you are going to backup single partition, you can backup it to another partition on the same disk. Clonzilla makes byte-to-byte copy of disk/partition and saves it to file(s). When you want to restore the disk/partition, you simply start Clonezilla again and instruct it to copy file contents back to disk/partition.

FWIW, you can do it very quickly with dd command, but you'll be safer if the partition is unmounted. So Clonezilla is perfect for the job, cause in fact it runs from bootable CD.

Hope that helps!

---

### Post by mdpalow on 2009-02-03
QuickStart can help you with that. See link in signature.

---

