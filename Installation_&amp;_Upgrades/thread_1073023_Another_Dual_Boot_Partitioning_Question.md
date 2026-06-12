---
title: "Another Dual Boot Partitioning Question"
date: 2009-02-17
forum: Installation &amp; Upgrades
---

### Post by wlaxdad on 2009-02-17
I've reviewed a number of Q&A's on this topic and I'm still confused as there doesn't seem to be a consistent response.  So, sorry to post another question on this topic...

I've got a new 1TB drive and 4GB RAM.  I want to dual boot XP and Ubuntu.  I want a single shared data directory for XP and Ubuntu.  I am coming from the Windows environment and have no experience with Linux but want to dive in.  My family will stay in the XP environment so, if there are options, I want a setup that will not confuse them.

From what I been able to gather I want to:
   1) Create the XP partition first--NTFS format, 30-50GB
   2) Create /swap partition--ext3 format, 8GB
   3) Create / partition--ext3 format, 10-20GB
   4) Create /home partition--ext3 format, xxxGB or balance of disk?
   5) Create a shared data partition--NTFS format, balance of disk

I'm not clear about the shared data partition or the partition sizes.  

[COLOR="Red"]Regarding the shared data partition, should I create a separate NTFS partition or use the ext3 /home partition?[/COLOR]  Can you go either way?  I've seen recommendations both ways.  Does it matter which way?  Is one recommended over the other?  If I use /home, will that be transparent to the XP users?

[COLOR="Red"]Regarding the partition sizes, what are recommended partition sizes?[/COLOR]  I have plenty of disk space so I would rather go big than regret it later.

[COLOR="Red"]Is there anything I've got wrong or I'm missing?[/COLOR]

I'd appreciate any assistance you could give.  Thanks in advance.

---

### Post by konqueror7 on 2009-02-17
i think your shared partition would be better if you format it as NTFS, because windows will get a BSOD when you try to execute files from non-microsoft filesystems...

and also, about the swap, i think its too big. yes, its true that it is recommended to have double its size of your RAM, but i think its too much...

all in all, it all looks good to me, other people make an extra for the /boot parition, i do not...

hope it helps...

---

### Post by wlaxdad on 2009-02-18
Thanks.

What size for /swap--4GB?

If I use NTFS for the shared data partition, what size should I make /home?

Regarding the /boot partition, is this just moving the /boot directory from root to a separate partition?  What purpose would a separate /boot partition serve?  In what order would it appear--after XP but before /?  What size?

Thanks.

---

### Post by caljohnsmith on 2009-02-18
> **wlaxdad said:**
> Thanks.

What size for /swap--4GB?

If I use NTFS for the shared data partition, what size should I make /home?

Regarding the /boot partition, is this just moving the /boot directory from root to a separate partition?  What purpose would a separate /boot partition serve?  In what order would it appear--after XP but before /?  What size?

Thanks.
I would definitely go with just 4 GB of swap space if I were you. Also, if you are planning on putting all your personal files in the shared NTFS partition, I don't think you really need a separate home partition, but it's up to you of course. And about a boot partition, only if you get a Grub error 18 when trying to boot Ubuntu does it usually make sense to have a boot partition, because otherwise there is no distinct advantage of having a whole separate partition for /boot. It sounds like you've researched everything really well though, so I bet your dual-boot setup should go smoothly. Good luck and let us know how it goes.

---

### Post by nxs1954 on 2009-02-18
Just a quik note === linux cant rite to ntfs file systems. It has to be formated in FAT - preferably make it FAT 32 ... :)
By itself -- that it ...
You'll need The NTFS-3G driver ... then you be ok ...

---

### Post by caljohnsmith on 2009-02-18
> **nxs1954 said:**
> Just a quik note === linux cant rite to ntfs file systems. It has to be formated in FAT - preferably make it FAT 32 ... :)
Although that was true some years ago, fortunately that is not true now. With Linux's ntfs-3g drivers, writing to an NTFS partitions is not a problem any more.

---

