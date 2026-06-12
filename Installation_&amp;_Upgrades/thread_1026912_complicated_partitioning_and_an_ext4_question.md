---
title: "complicated partitioning and an ext4 question"
date: 2008-12-31
forum: Installation &amp; Upgrades
---

### Post by estyles on 2008-12-31
Okay, hopefully this hasn't been done to death - a search turned up some results, but nothing like what I want to do.  For those who follow KISS on drive partitioning - there *are* reasons that I want to have kind of a complicated partitioning scheme, I'll try to explain what those reasons are.  Basically looking for some advice on this partitioning scheme - will be installing clean on a brand new PC - and if you think that I should do things differently.

First an ext4 question - is there anyway to install ubuntu on an ext4 partition on a brand new computer?  As far as I know, there aren't any distros that support ext4 (without downloading a module).  So, when installing, the install CD won't recognize an ext4, will it?  And even if it would recognize it, you'd have to create the ext4 first, so it would involve installing, making the filesystem, and then reinstalling onto that filesystem?  Anyway, I'll assume for now that I can create the ext4 partitions - probably via installing to a different partition, then copying everything onto an existing ext4 partition.  Don't worry - all data will be backed up from my current PC before starting.

Anyway, I'm thinking of doing something like this (1 TB drive):

Primary:
1 - 80 GB (NTFS) - Windows XP
2 - 4 GB (swap) - Linux Swap
3 - 50 MB (Ext2) - Grub partition (a)
Extended:
4 - 50 MB (Ext2) - Ubuntu /boot (b)
5 - 15 GB (Ext4?) - Ubuntu root
6 - 5 GB (ReiserFS) - Ubuntu /var (c)
7 - 5 GB (ReiserFS) - shared /tmp (c)
8 - 50 MB (Ext2) - Archlinux /boot (b)
9 - 15 GB (Ext4?) - Archlinux root
10 - 5 GB (ReiserFS) - Archlinux /var (c)
11 - 800 GB (Ext3) - Data (d)
12 - ~50 GB unallocated (e)

(a) I have a Grub partition on my current machine and it works wonders.  It has a menu.lst that simply chainloads another partition.  Frex, if I choose Ubuntu from the menu.lst, it runs: (savedefault  root( hd0,8 )  chainloader +1).  Meanwhile Ubuntu maintains its own grub, menu.lst, and kernel images.  I currently have arch, mint, xp, and ubuntu installed.  I used to have to merge menu.lst files by hand to keep everything organized after kernel upgrades, until I figured out how to have a Grub partition.

(b) I wouldn't bother with /boot partitions, except that I hope to be able to switch my root partitions to ext4 and grub can't boot from ext4.

(c) I like the idea of keeping /var and /tmp on separate partitions because they get written a lot and this will keep the rest of the drive from getting fragmented by that.  Also, I think it might help if those sectors wear out, and in the unlikely case that something goes berserk and fills up /var or /tmp, root won't be affected.  I think that ReiserFS is a good choise for filesystem because they tend to consist of lots of small files (at least for var, not sure about tmp).  I thought about using a shared /var partition, but overwriting log files seems like it might be annoying.  /tmp should be cleared on reboot, so a shared partition for tmp works fine.  Actually would be nice to have 1 partition for combined /tmp and swap, but that doesn't work.

(d) Instead of separate /home partitions, I tend to keep /home with its own OS, because the settings that are stored there tend to be useless when upgrading or distro-hopping.  All of my Data will go on a separate Data partition, mounted at /home/username/Data/.  All the standard folders like Documents, Videos, Music, etc...  will be replaced with symbolic links that link to the corresponding folders in Data.  I would consider having a small separate /home for each distro, but Data would still stay on its own.  In which case, it would be difficult to decide how big to make /home (2GB?).  Probably not worth bothering.

(e) Reserved for distro-hopping or beta testing new Ubuntu releases.

So...  too complicated to bother reading all the way through or what?  :D

---

