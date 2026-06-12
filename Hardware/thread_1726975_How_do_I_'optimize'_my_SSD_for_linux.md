---
title: "How do I 'optimize' my SSD for linux?"
date: 2011-04-11
forum: Hardware
---

### Post by ownaginatious on 2011-04-11
So I recently got a 120 GB SSD, and I've been wondering how exactly I go about optimizing this thing for linux.

As soon as I got it, I built an MSDOS partition table in gparted and copied over my existing linux partition.

Everything works fine, but now I'm hearing this isn't recommended and that I should be using a gpt table.

Should I actually bother going through with all of this? Is the way I have it setup severely detrimental to the longevity/performance of the SSD?

Any help/advice on this would be much appreciated.

Thanks.

---

### Post by donalgodon on 2011-04-11
I kinda have the same question, so I hope you don't mind if I piggy back on this thread rather than starting my own. 

Does Ubuntu have TRIM support built into it like Win-doze 7?

---

### Post by wojox on 2011-04-11
I've got a 4GB ssd Asus eeepc. Installed Arch/Openbox with this thread [Solid State Drives]("https://wiki.archlinux.org/index.php/Solid_State_Drives")

---

### Post by srs5694 on 2011-04-12
I'm not an expert on SSDs, but I can say that the MBR-vs-GPT thing *per se* isn't an issue, although partition alignment *is*, and the tools you use to set up the disk might align differently for MBR vs. GPT.

Details differ from one disk to another, but my understanding is that SSDs perform best with partition start points aligned on some power-of-2 multiple of sectors, typically in the 256 sector (128 KiB) range. In the past, most partitioning tools aligned partitions' starts on "cylinder" boundaries, which have been fictions invented by the drive firmware for well over a decade, so if you use a partitioning tool that aligns this way, you're likely to get degraded performance. The issue is similar to that for Advanced Format drives, described [in this article I wrote](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) for IBM developerWorks, among other places.

In the past few months, most Linux partitioning tools have shifted to a default policy of aligning partitions on 2048-sector (1 MiB) boundaries, which works well with most devices. You've got to understand the issue and know how to check your partitions' start values to sector precision to verify this, though, in case you're using an old tool or accidentally set it to align in some other way.

---

