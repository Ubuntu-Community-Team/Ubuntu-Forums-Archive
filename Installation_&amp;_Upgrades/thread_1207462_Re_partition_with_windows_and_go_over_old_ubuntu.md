---
title: "Re partition with windows and go over old ubuntu"
date: 2009-07-08
forum: Installation &amp; Upgrades
---

### Post by ASNet0007 on 2009-07-08
Hi,

I have already setup windows and ubuntu as dual boot but need to reinstall ubuntu and keep the dual boot.

It looks to me on the partition screen when I try to reinstall ubuntu as though I will end up with windows and 2 installs of ubuntu, but I simply want to go over the ubuntu already installed.

How do I do this. Thanks

---

### Post by AndyCee on 2009-07-08
To be honest I've done exactly the same thing before.

When faced with the partitioning option (assuming you're using the LiveCD install) choose "manual".

It's pretty obvious which is the Windows partition (ntfs), just delete all the non-windows ones and choose a new ext3 partition to take up that space, and install a root filesystem (/) there. This has NO graphical assistance.

The other way would be to boot into a liveCD, go to "System->Administration->Partition Editor" and delete the partitions there. Create a new ext3 partition where you want, and save your changes. Then when you install and are asked about partitioning, choose manual and install a root filesystem on the ext3 partition as above.

I understand if this doesn't appear simple. Post back if not happy with my response :-).

---

### Post by ASNet0007 on 2009-07-08
Thanks for the fast response.

Should I select primary or leave as logical?

Does location beginning  / end refer to all the HDD or just the part I am partitioning? I have windows in the beginning of the HDD.

What should I select for mount point?

Am I ok leaving the swap partition from last install?

Sorry for so many basic questions.

---

### Post by running_rabbit07 on 2009-07-08
> **ASNet0007 said:**
> Thanks for the fast response.

Should I select primary or leave as logical?

Does location beginning  / end refer to all the HDD or just the part I am partitioning? I have windows in the beginning of the HDD.

What should I select for mount point?

Am I ok leaving the swap partition from last install?

Sorry for so many basic questions.

You should be OK with leaving MS as your Primary and EXT3 (or whichever format you used for Ubuntu) as logical or extended.

/ should be on the partition which you plan to load Ubuntu. 

When selecting the mount point, you select the partition you made for Ubuntu.

If the swap is still there, then you should be able to leave it and use it.

Hope this helps you.

Don't worry about asking the basic question, better to ask before a mishap than after.

P.S. If you want more info on RAID, message me via the icon under my avatar __and I can send you a PDF that explains a lot.

---

### Post by ASNet0007 on 2009-07-08
Thanks for the help. All done

---

