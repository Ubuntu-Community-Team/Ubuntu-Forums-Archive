---
title: "ext4 and backups"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by johnhenry on 2009-04-23
Ubuntu 9.04 is unquestionably excellent, and ext4 seems to add an edge to the speed as well. I shall certainly not abandon it.

I foresee one problem for a while though - how to do backups? Neither Partimage nor Acronis seem to be able to cope with the new file system, and for the present I am reduced to using dd - which is effective but very slow and also very heavy on disk space.

For those who like to make regular backups this is going to be a problem until Partimage etc. catch up. They might be wiser to stick with ext3 until that time. For the time being I have created an identical sized partition and dd my ext4 installation to that as a backup, but I can't wait to have Partimage back again.

JohnHenry

---

### Post by dabl on 2009-04-23
I haven't used it for backup, but I'll bet this one has some tools that would do the trick:

[http://partedmagic.com/](http://partedmagic.com/)

:)

---

### Post by cornflake000 on 2009-04-23
no... parted magic doesn't support ext4 backup. only partitioning.  It uses partimage for .iso.  I also understand partimage is stagnant at the moment.  It's a big issue for me too.

---

### Post by george1984 on 2009-04-23
I am so clumsy a root partition backup is not an option, it is essential.

For 9.04/ext4 all I could find was dd. It works, it is dependable, but as noted above it is slow and large. I regularly backup root partitions - using Partimage this is fast and the backups are not enormous.

I hope Partimage can be updated to support ext4. I very nearly avoided ext4 because of this.

    p.s.  ext4 seems to be o.k. so far.

---

### Post by Ericyzfr1 on 2009-04-24
> **george1984 said:**
> I am so clumsy a root partition backup is not an option, it is essential.

For 9.04/ext4 all I could find was dd. It works, it is dependable, but as noted above it is slow and large. I regularly backup root partitions - using Partimage this is fast and the backups are not enormous.

I hope Partimage can be updated to support ext4. I very nearly avoided ext4 because of this.

    p.s.  ext4 seems to be o.k. so far.

Same here, until now I relied on partimage, I tested Clonezilla and it went to dd which was my last option.

---

### Post by johnhenry on 2009-04-26
I find that fsarchiver does the job very efficiently. It is included on the SystemRescueCD, for example, and has a good -h listing of typical syntaxes. Its only drawback in comparison with partimage is that it is a command line program and it does not show a scale of progress. But, from fairly limited testing, I would say it is at least as fast as partimage, and copes well with ext4. For example, it compressed a 20G partition of mine to 1.4G, which is also slightly better than partimage in the circumstances, I would say.

---

### Post by Schapie123 on 2009-04-26
I use Areca Backup ([http://areca.sourceforge.net/]("http://areca.sourceforge.net/")). It isn't suited to create images of your partitions, but backups on file level are really practical in my opinion. I've had some difficulty getting it to work in 64 bits initially, but now it works fine.

---

