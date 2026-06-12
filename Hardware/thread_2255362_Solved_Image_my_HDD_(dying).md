---
title: "Solved Image my HDD (dying)"
date: 2014-12-04
forum: Hardware
---

### Post by dave157 on 2014-12-04
Thinkpad T500 2241-cc1

I just found out that my HDD is dying and I wanted to image my xubuntu system so I can an restore it on a new HDD. How can I do that and what is the best software?

thanks

---

### Post by slickymaster on 2014-12-04
[Clonezilla]("http://clonezilla.org/")

---

### Post by Lorenz_ on 2014-12-04
First, I think this is the wrong forum. Post it either in "Installation & Upgrades" or "Hardware".

But to your problem:
I would recommend clonezilla. ([http://clonezilla.org/](http://clonezilla.org/))
But the best solution for you, I think, is to use [http://partedmagic.com/](http://partedmagic.com/). This is fully functional Live Disc, which includes everything you need to backup/restore/format/partition HDDs including clonezilla.

All the best, Lorenz.

---

### Post by slickymaster on 2014-12-04
> **Lorenz_ said:**
> First, I think this is the wrong forum. Post it either in "Installation & Upgrades" or "Hardware".
<---snip--->

Quite right and thus moved to the **Hardware** sub-forum.

---

### Post by Mark Phelps on 2014-12-04
Clonezilla can be difficult to figure out how to use, as it need the destination entered first -- which is the opposite of what you'd expect.

You should try RedoBackup.  You create a boot CD from it, and it boots into a graphical interface that is real easy to use.

---

### Post by tgalati4 on 2014-12-04
Copy has always worked for me:

```
sudo cp /dev/sda /dev/sdb
```

You can use *gparted* to expand the partition if the new drive is larger.  Use *blkid* to identify the UUID and change it in grub and /etc/fstab.

---

### Post by weatherman2 on 2014-12-05
> **Mark Phelps said:**
> Clonezilla can be difficult to figure out how to use, as it need the destination entered first -- which is the opposite of what you'd expect.

It is the opposite of what I'd expect having used Clonezilla more than once -  and that isn't how it works.  You pick the source disk first, then the destination, at least in "beginner" mode that most new users would be using.

But it is true that Clonezilla isn't the most user-friendly cloning tool out there, even though it works pretty well.  One limitation is that automatically cloning a larger partition to a smaller one is not supported.  Cloning a smaller partition to a larger one is easy though.

---

### Post by Mark Phelps on 2014-12-05
> You pick the source disk first, then the destination, at least in "beginner" mode that most new users would be using.

I've used CLonezilla literally HUNDREDS of times, and in fact, used it again not 30 minutes ago.  And, NO, you do NOT pict the source disk first.  The first thing you pick is where you want the images stored, first the partition, and then a folder.  After you select saveparts and the defaul directory name, THEN, you pick the source partition.

---

### Post by weatherman2 on 2014-12-05
> **Mark Phelps said:**
> I've used CLonezilla literally HUNDREDS of times, and in fact, used it again not 30 minutes ago.  And, NO, you do NOT pict the source disk first.

The Clonezilla I've used has you pick the source disk first - as at 1:57 here in YouTube:

[https://www.youtube.com/watch?v=YzxL95GmmYk](https://www.youtube.com/watch?v=YzxL95GmmYk)

---

