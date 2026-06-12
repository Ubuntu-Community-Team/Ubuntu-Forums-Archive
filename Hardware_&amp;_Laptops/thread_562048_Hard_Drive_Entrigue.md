---
title: "Hard Drive Entrigue"
date: 2007-09-28
forum: Hardware &amp; Laptops
---

### Post by dbcoolio on 2007-09-28
Here's my situation:

I just bought this laptop with WIndows XP Media Center (thank goodness it wasn't Vista)

anyways, I split the drive into 4 partitions- the Swap file (abt 4Gb), The main NTFS windows partition (abt 25 Gb), an ext3 Linux Partition (with Ubuntu 64) (abt 25 Gb)  and then I turned the rest of the space into a FAT32 partition so that both operating systems could have read write access, and I wouldn't have to worry about possible NTFS-3g issues (I still installed it so I can write to the My Documents Folder, but I figured if I was going to make a separate part, might as well keep it simple)

Well, the problem is that the FAT32 partition doesn't mount automatically on start-up.  It's not too big of a deal, because I can just double click on it and it mounts fine, but it seems like something that ought to be easy to fix.

I've messed with my fstab a bit, and haven't gotten it to mount automatically.  Here's what I've tried:

The original entry was something like this:
UUID=7C7703F97ABBA3BF /media/hda4 ntfs-3g defaults,locale=en_US.UTF-8 0 1

pretty much the same as the nts partition was, which makes sense why it didn't work.

I tired this that I found in an entry online:
/dev/hda4 /mnt/WHERELOVEIS vfat user,auto,umask=007,gid=100 0 1

but it did exactly the same thing as the top option.  so then I right clicked on the drive after it was mounted and used the information it showed in the last tab to make this:
UUID=46f9-43A0 /media/hda4 vfat rw nosuid nodevuid=1000 fmask=0077 dmask=0077 codepage=cp437 iocharset=iso8859-1 shortname=mixed utf8 0 1

but it did exactly the same thing.  So then I tried a really simple option:
/dev/hda4 /mnt/WHERELOVEIS vfat user defaults 0 1

That seemed like it kind of mounted the drive.  well, it didn't show up on the desktop, and it didn't show up anymore in the left pane of the explorer.  It did show up in the /mnt/ folder as just a normal folder, but I didn't have permission to even open it.

so I tried: 
/dev/hda4 /mnt/WHERELOVEIS vfat rw user defaults 0 1

and it didn't make any difference.

I've also tried mounting it to /WHERELOVEIS and /home/horizon/WHERELOVEIS each time creating the directory in that place like it said to on the other sites, but it gave me the same results as my other tries.

any suggestions?

---

