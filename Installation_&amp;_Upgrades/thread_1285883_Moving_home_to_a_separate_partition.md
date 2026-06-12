---
title: "Moving /home to a separate partition"
date: 2009-10-08
forum: Installation &amp; Upgrades
---

### Post by AlanQ on 2009-10-08
I was asked a question about this in another thread.
As it was getting a bit off-topic, I decided to post my answer here.

There seem to be several threads about this topic but they all (of course I haven't read them all) seem to be specific to one or other person's problem.

This is my attempt at a more generic post on the subject.
Corrections, etc most welcome.

_Putting **/home** on a different partition_

The biggest advantage is that it allows you to upgrade/re-install the OS without having to re-install your user files in your home directory.

If you do it at the time of installation, it's easy :)

Moving /home at a later date is not for the faint-hearted but it can be done.

Because the process involves modifying a system that you are on (like cutting the branch you are sitting on) at some point you will need to either drop the system to single-user and do most of it as root or, if you're not an expert or you simply like an easier life, do it from a *live CD*.

The following is intended as a simple check list -- don't rely on it alone, read other references first and make your own plan.

The main stages of the process are [software in brackets]:
[LIST=1]
[*]Take a complete copy (backup) of your current /home [*cp -a* or *rsync*]
[*]Re-partitioning a disc can damage the data on it so, take a complete copy/backup of everything else of value on the disc and, to be extra safe, defragment any Windows partitions.
[*]Create the new partition [*GParted* or *cfdisk* or *fdisk*]
[*]Format the partition [*GParted* or *mkfs.ext3*]
[*]Mount the new partition and copy _to_ it the backup of /home
[*]Move the current /home to /old_home [*mv*]
[*]Modify /etc/fstab so that the system will see and mount the new partition as /home when it boots
[/LIST]

There's an old but very good reference for this at [http://www.ibm.com/developerworks/library/l-partplan.html](http://www.ibm.com/developerworks/library/l-partplan.html) .
There's also an Ubuntu help page, which points to two other references, here: [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving) (with some edits as people discovered the gotchas :) ).

NB (for everyone reading this and any other post giving technical advice/instructions) Always make sure you understand what you are doing before you do it: if I've made a mistake or forgotten something here, it's merely embarrassing for me; if you implement my mistake, it's potentially big data loss for you. Read other references. Read the man pages.

Good luck.

---

### Post by zvacet on 2009-10-09
[This]("http://psychocats.s465.sureserver.com/ubuntu/separatehome") is good guide for making/moving separate home partition.

---

