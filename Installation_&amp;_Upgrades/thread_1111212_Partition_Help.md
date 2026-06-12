---
title: "Partition Help"
date: 2009-03-30
forum: Installation &amp; Upgrades
---

### Post by dankev on 2009-03-30
I am trying to install Ubuntu along side Windows XP. When I get to the partition section, I can't figure out how to create it and not wipe out the entire drive, losing XP and all my data.

I did do a backup in case of a failure, and I also just did a defrag.

---

### Post by Linoobius on 2009-03-30
dankev,

Best solution would be to give ubuntu the entire drive wiping out windows but if that's not feasible...

I prefer to do the partitioning apart from the installation process, I boot from the ubuntu live cd and use gparted to shrink the windows partition and just leave an unallocated block of disk space, then when you launch the installer you will be presented with the option of installing into the unallocated space. This eliminates the need to do manual partitioning of your root and swap partitions during the install. This is my noob crutch, the real gurus do it manually. BTW, if you're using kubuntu, the livecd will not have gparted but if you have an internet connection you can boot the live cd and

sudo apt-get install gparted

and you can then use gparted from you live boot.

Linoobius

---

### Post by dankev on 2009-03-30
Thanks for the suggestion. Partitioning through gparted looks to be more straight forward. I'm still having trouble, though. When I try to move/change the partition, it sets as both the min and max the size of the whole hard drive, so it won't let me shrink it down. I feel like I'm missing something, but I can't figure out what.

---

### Post by infoseeker on 2009-03-30
If I remember correctly the partitions have to be unmounted before resizing...right-click the partition and select 'unmount' and then try again.  You can then right-click the partition and select 'resize'....this can then be done with the mouse by dragging the boundary line.

---

### Post by dankev on 2009-03-30
I did unmount it first. I forgot to mention that.

---

### Post by dankev on 2009-03-30
I think I figured out why Ubuntu can't partition my drive, sort of. I tried one of the commercial partition programs through Windows, and during the analysis part, it said something was interfering. It gave a vague suggestion to run a program to fix it. 

Not really sure what to do at this point.

---

### Post by Linoobius on 2009-03-30
dankev,

If you were booting from a live CD then I don't think you'd have to unmount anything, I didn't think the live CD auto mounted NTFS or FAT partitions but that aside, infoseeker was correct, the partition could not be mounted during any modification to the partition table with the possible exception of setting an active patition, I'd have to look that one up. So assuming  you are booting from a live CD and the disk you are working with has no mounted partitions and then you are running gparted, I'm not sure what would keep that from working. Did you sudo gparted or just gparted? I know when you run it from a disk install it prompts you for admin password but it's been a while since I did exactly what you're doing, you might try sudo gparted if you didn't and see if that makes a difference, it can't hurt to try. I'll check back later, gotta run just now.

Linoobius

---

