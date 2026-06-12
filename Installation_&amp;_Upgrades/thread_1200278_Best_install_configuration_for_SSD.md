---
title: "Best install configuration for SSD"
date: 2009-06-29
forum: Installation &amp; Upgrades
---

### Post by Rocks and Water on 2009-06-29
I recently purchased a Thinkpad x301 that shipped with Vista Basic. I'm contemplating a fresh start with just Ubuntu 9.04, but my laptop has a 128 gig SSD, which I've never used before. I looked around a bit for suggestions on install configs, but most of what I found either contradicted each other or focused on after-the-fact tweaks aimed at reducing wear on the drive.

What is the best approach to installing linux on solid state drives? Should I use Ext2, 3 (or 4)? Do I need a swap partition?

In case it's relevant, I only have 2 gigs of ram at the moment, but am planning on upgrading to either 3 or 4 in the near future.

---

### Post by Rocks and Water on 2009-07-02
bump

---

### Post by Ruhani04 on 2009-07-02
I am running 9.04 on a vertex ssd without swap with 2GB ram.
You might want to check the following for setup:

[http://www.ocztechnologyforum.com/forum/showthread.php?t=54379](http://www.ocztechnologyforum.com/forum/showthread.php?t=54379)

I am very happy with the performance. I get around 180MB/s with hdparm test.

---

### Post by Rocks and Water on 2009-07-03
> **Ruhani04 said:**
> I am running 9.04 on a vertex ssd without swap with 2GB ram.
You might want to check the following for setup:

[http://www.ocztechnologyforum.com/forum/showthread.php?t=54379](http://www.ocztechnologyforum.com/forum/showthread.php?t=54379)

I am very happy with the performance. I get around 180MB/s with hdparm test.

Thanks for the link. Unfortunately, I'm finding it a bit overly technical and difficult to discern what I should actually be doing during the install.

I'm also still confused about contradictory advice. That link, for instance, says turning journaling off is "not recommended as you might experience a data loss after an unclean shutdown," while a post on [this forum]("http://ubuntuforums.org/showthread.php?t=866375") seems to argue that a filesystem without a journal is essential for reducing excessive writes.

That post also argues for the use of Ext2. I find it odd that Ext3 and 4 are supposedly so poor at handing SSDs, especially since they're newer. It seems counter intuitive to me.

---

### Post by Rocks and Water on 2009-07-03
If anyone, like me, is looking for info on this subject, [here is another good resource]("http://thunk.org/tytso/blog/category/computers/ssd/"). This guy seems to know what he's talking about and has found that using the Ext2 filesystem is only necessary if you have a first-generation SSD.

---

### Post by Ruhani04 on 2009-07-03
I use ext4 with journaling. Works great and in my opinion according to the info I have even with journaling your ssd should last many years. I think people get a little bit carried away with overprotecting their ssds.

---

