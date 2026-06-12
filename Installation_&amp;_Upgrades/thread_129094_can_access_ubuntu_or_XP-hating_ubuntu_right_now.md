---
title: "can access ubuntu or XP-hating ubuntu right now"
date: 2006-02-12
forum: Installation &amp; Upgrades
---

### Post by adambeazley on 2006-02-12
Hello,
Well I had a perfectly working xp install on a 200 gig SATA hard drive. The hard drive was partitioned with 180gigs for NTFS and the rest left unformated for linux. I installed ubuntu, set up 300MB swap partition-Primary and a 14 gig / root partition-bootable. Went through the install and it asked about installing grub to my hda0 mbr and I said ok. Now when I restart I get the "ERROR LOADING OPERAATING SYSTEM".  I tried reinstalling ubuntu and using windows xp cd and running the recovery console and doing a fixmbr to fix the master boot record but to no avail. Im still stuck here not able to boot, im just glad I have this laptop to get some help.
Please help,
Adam

---

### Post by matthewv on 2006-02-13
Can you boot to the ubuntu install cd and then selecting the recovery option...
Once there you can try reinstalling grub... ```
grub-install /dev/hda
```

---

### Post by adambeazley on 2006-02-13
thanks for the help, I have already reformated and reloaded my saved Drive image so im back to where I was Sunday morning which is good.
Again, anyone who is about to try a dual boot install please go download driveimage XML and image your drive so you can restore to a previous point if something goes wrong.
Adam

---

