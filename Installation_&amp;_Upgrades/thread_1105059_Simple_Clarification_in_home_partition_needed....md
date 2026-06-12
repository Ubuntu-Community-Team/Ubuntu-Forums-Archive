---
title: "Simple Clarification in /home partition needed..."
date: 2009-03-24
forum: Installation &amp; Upgrades
---

### Post by vpnm_87 on 2009-03-24
i have 80 GB harddisk which i partitioned into
10GB----> / (primary)
10GB----> /home (logical)
5GB----> swap area (logical)

successfully installed Ubuntu 8.10...

My doubt is 

considering i add many users in /home and saved many files...if my PC suddenly crashes now...if my understanding is correct i wont lose files in /home directory..is that so?

also i want to know how to install same Ubuntu 8.10 again?

can anybody tell the steps involved to reinstall ubuntu 8.10 after crash without affecting files in /home?


I hav partitioned and formatted windows PC so many times without affecting files in D:,E: drives and just reinstalling windows in C:.

I hope its possible in Ubuntu also..but dont the exact steps..

I am a recent lover of linux:)hope to get some reply for this atleast:)

---

### Post by rustutzman on 2009-03-24
When you go to re-install you will want to choose the manual method in the partitioning section. Highlight the partition of interest and click the little drop down to select the mount point. for your Home partition select /Home and do not check the format box. Do the same for your root partition but his time select / as the mount point. You will want to check the format box for your new install root.

Be sure you know which partition is which before undertaking this exercise. With both partitions the same size you really want to be sure you're formatting the right one.

Russ

---

### Post by vpnm_87 on 2009-03-25
Thank u so much for the reply rustutzman...

BTW,what would happen if i had made /home and swap area as primary rather than logical partitions?

Will it cause any bad effect while re-installing?

---

### Post by TiredBird on 2009-03-25
The partioning method we use was established in the days of MS-DOS, before Windows had even been thought of, so its pretty clunky but here goes...

It can only have four "primary" partitions. If you want more partions than four, one of those four has to be an "extended" partition which can then hold additional "logical" partitions. 

Unless something has changed that I am unaware of, you can only number partitions 1 through 16 on a single drive. Since one of those is an "extended" partition, (usually number 4), which holds the "logical" partitions, (numbers 5 through 16), instead of data, you can really only have fifteen separate partitions of data, ("primaries 1 - 3, and logical 5 - 16).

Hope this answers your question.

---

### Post by vpnm_87 on 2009-03-26
Thank u so much for the reply TiredBird..

That restriction of primary partition to four is due to tha structure of Master Boot Record(MBR)..i remember reading that in Wikipedia also..

i just wanted to know the effect of using primary partition for /home and swap area rather than logical partitions..

---

### Post by logos34 on 2009-03-26
> **vpnm_87 said:**
> 
i just wanted to know the effect of using primary partition for /home and swap area rather than logical partitions..

There's really no practical difference, either works the same.  Personally I have /, /home and /swap on logical partitions.  Keeping your home and swap inside the extended will at least allow you the option of adding a fourth partition (if you have unallocated space).

Just be careful when reinstalling...it is critical to NOT check the 'format?' box for /home, as rustutzman said.

---

### Post by vpnm_87 on 2009-03-26
Thanks for ur info and advice about reinstallation...
I hope i am clear now:)

---

