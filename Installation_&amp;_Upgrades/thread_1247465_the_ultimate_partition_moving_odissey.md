---
title: "the ultimate partition moving odissey"
date: 2009-08-23
forum: Installation &amp; Upgrades
---

### Post by vexorian on 2009-08-23
Man, I have finally decided to upgrade my old computer, problem is that SATA became popular, and now motherboards come with only one IDE port. This means that if I want to use my CD and DVD burners, I'll have to ditch my 2 IDE hard disks.

I have 2 IDE hard drives totalling 60 GB, each has its own share of partitions, the first one has C: and ubuntu's / and swap, the second has D: , M: , V: ,  /home and another ext3 partition.

I purchased one sata 320 GB drive.
A nightmare scenario would be having to start the new computer from scratch having to reinstall both XP (for my brother) and ubuntu from zero completely, specially considering I don't have an ubuntu CD since I just updated through the repos for 9.04 and my brother lost CD's of his fav windows software.

So, the optimal would be finding a way to move the partitions from the two disks to the new one. I have a 500 GB external drive as well, so transportation of data is not a big issue. Are there cloning programs that could do this sort of stuff? (dealing with both windows and ubuntu partitions)

To sum up:
I need to copy the partitions from 2 disks to a single bigger disk, each of the first 2 disks contains many partitions both NTFS and ext3.

---

### Post by starcraft.man on 2009-08-23
It's late, don't think I have the alertness to detail the steps thoroughly so I'll sketch this out step by step.

The only rule to gparted: BACKUP! Any files you can't live without need to exist somewhere else than the drives your copying to, like that 500GB external. Nobody's responsible for data loss but you. For the following guide, I'd just hook up the IDEs one at a time and copy right to the SATA.

1. Read gparted [docs]("http://gparted.sourceforge.net/documentation.php"), all of em, top to bottom, especially copy section (start with general, go down).
2. Decide on a partition schema for new drive. Your first primary partition will be Windows C, the rest up to you. I assume put two other windows partitions to primary then dump everything else in extended partitions including all the linux related ones.
3. Make partitions on new drive, just create and format as ya want. Ensure, they are at least as big as partitions your copying into them.
4. Copy data from windows partitions over to new drives partitions.
5. Use fix mbr command from a windows disc (google for how to by microsoft) to make sure it's bootable.
6. Ensure everything works on Windows partitions.
7. Copy over linux partitions to extended partitions.
8. Reinstall grub to the MBR of this new drive. To do so follow this guide, [here]("https://help.ubuntu.com/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB"). Do install to the MBR (i.e. (hd0) or so, not a partition). Do it from a live CD.

I haven't exactly done this exact set of steps before, should work, else post back. Ask questions BEFORE doing anything to your drives.

---

### Post by vexorian on 2009-08-23
> 4. Copy data from windows partitions over to new drives partitions.
Actually, I wonder if this is possible without corrupting the windows setup. There are a lot of NTFS quirks that I am not sure would be replicated completely when using ntfs-3g to copy them. And if I used the windows setup to do the copying, some files wouldn't copy.

Or is there a way to copy bits of data with gparted? *reads documentation*

Edit: wow gparted can copy, I am saved. God bless gparted.

---

### Post by starcraft.man on 2009-08-23
> **vexorian said:**
> Actually, I wonder if this is possible without corrupting the windows setup. There are a lot of NTFS quirks that I am not sure would be replicated completely when using ntfs-3g to copy them. And if I used the windows setup to do the copying, some files wouldn't copy.

Or is there a way to copy bits of data with gparted? *reads documentation*

Edit: wow gparted can copy, I am saved. God bless gparted.

Ahem. Don't forget the devs, somebody wrote the code and twasn't an omnipotent being. :)

Anyway, have fun. Will take a while...... have a movie or something to watch.

---

### Post by vexorian on 2009-08-23
damn I got myself into a little chicken and egg problem.

I setup the copying sequence, but the first thing it did was call ntfs to look for bad sectors in C, it found a few. So I am supposed to run chkdsk /f /r on windows, the only problem is that as I am on a new computer, I can't boot windows anymore, in order to boot it, I need my windows CD. The problem with that is that I can't use CD because I haven't moved the disks' contents yet. ouch.

Will have to find me an USB CD reader or something like that.

edit: I am copying the windows partition manually using: [http://www.nilbus.com/linux/disk-copy.php](http://www.nilbus.com/linux/disk-copy.php) let's see if it works.

Edit: I did something INCREDIBLY RETARDED, in the last step, instead of dd if=inputdrive of=outputdrive I did dd if=outputdrive of=inputdrive , effectively wiping my C partition.

Anyway, the reason I had so many NTFS partitions was to avoid having more than windows itself on C:, the bad news is that I'll have to reinstall, but I didn't lose important data, oh well, I hope this helps someone prevent making the same mistake...

---

