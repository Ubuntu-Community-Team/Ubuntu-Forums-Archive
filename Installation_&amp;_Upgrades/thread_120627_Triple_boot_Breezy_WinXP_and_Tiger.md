---
title: "Triple boot Breezy WinXP and Tiger"
date: 2006-01-23
forum: Installation &amp; Upgrades
---

### Post by Luke771 on 2006-01-23
I have an AMD Duron 1600, 512 MB RAM and two 40GB HDDs, dual boot running Ubuntu 5.10 on hdb0 (Ext3) WinXP pro SP2 on hda0 (NTFS) with hda6 and hdb6 formatted as FAT32, and no free space left (but I do have Partition Magic that can resize partitions "almost" safely).
My hda drive is not very good, it still good enough to run Windows without any major problems but I get some I/O errors under Linux whent mounting the NTFS partition automatically with fstab (no biggie anyway, I mount it manually when I need it i.e. not often).
Now, what I'm planning to do is install Tiger on the same machine, making it a triple boot: I'm keeping my FAT32 paritions for data storage, as they are accsessible by all OSes, that way I only need a relatively small mac-partition to run Tiger and related programs while non-program files like video, music and so on will still be stored on FAT32 partitions.
Right now I am downloading Tiger-x86.tar.bz2, then I plan to resize my partitions on hdb (my "good hdd"), leave something like 7 or 8 GB of free space and install Tiger there.
The questions are:
Will 7 gig be enough? (I run WinXP on a 6GB partition (plus dedicated pagefile partition) and Ubuntu on another 6GB partition).
and most imprtant: How do I configure Grub (installed on MBR)?
I mean, when I install Tiger, it will probably modify the MBR, so I should back up the existing MBR, restore it after having installed Tiger and then manually add an entry pointing to Tiger: How do I do that?
I know I could google that up, but I didn't find any sufficiently foolprof walkthrough and I am no "real" computer geek myself; an "apprentice geek" maybe, but I still need help some times, and anyways, this is actually something that should be "easy-googled", and it will be when I get some answers, here :-)
Oh, yeah, AND I never installed any MacOS before (but I don't think that is a big problem)

OK, then, here come the questions again:
How much free space do I nead at least?
How do I back up and restore MBR and Grub?
How do I add an entry for Tiger in Grub?

Thanks for anwering

---

