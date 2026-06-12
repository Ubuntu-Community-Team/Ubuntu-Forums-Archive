---
title: "A Tough Partitioning Question"
date: 2008-09-03
forum: General Help
---

### Post by Tag_yer_dead on 2008-09-03
Hey Everyone,
I've finally had it with Vista and would like to move back to ubuntu, problem is I have about 200 GB of videos on a 250 GB hard drive.  I was wondering if there was a way to get these moved onto an ubuntu partition, basically by resizing partitions as i move info to it.

I'm a college kid and have ZERO money for an external drive so that is out of the question lol.

Thanks

---

### Post by Oldsoldier2003 on 2008-09-03
You could jockey your partitions around using the gparted live cd, but tbh I think it would not be worth the effort and could very easily lead to data loss. My advice would be to find some way to offload the files, format, install Ubuntu then restore the files.

---

### Post by Liviu-Theodor on 2008-09-03
If the videos are on a separate partition, you could use it on ubuntu as it is, with the NTFS or FAT32 filesystem.

If it is the only partition you have, you should first defragment your HDD in Windows, than you should delete (with the ubuntu LiveCD) the [FONT="Courier New"]Windows[/FONT] and [FONT="Courier New"]Program Files[/FONT] folders (and anything else you don't need - don't delete your documents, though - see the [FONT="Century Gothic"]Documents and Settings[/FONT] and the [FONT="Courier New"]Users[/FONT] folders). Now, resize the partition to have just enough space to accomodate these files.
And from now, you have have the videos on a separate partition.

But a good backup is always the best idea, even if you don't have the money for it. You could also put your videos on dvd-s, if you have a dvd-witer. It will be less expensive than a HDD.

---

