---
title: "Help me kill off windows"
date: 2005-09-12
forum: Hardware &amp; Laptops
---

### Post by lassel on 2005-09-12
I have just one 160gb disk in my machine.

hda1-3 is windows (120gb)
hda5-7 contains ubuntu (40gb)

I don't need windows anymore and I'd like to reclaim my 120gb for useful data.

Now, I have gparted installed and repartitioning will be a really simple task. I am just worried if it will work after I reboot.

hda1 (windows) is marked as bootable and I assume that this is where grub is installed?

If I delete hda1-3 and make one big new partition I bet that the bootmanager will die.
How can I reinstall it?

In making hda1-3 into one big partition will the partition numbers of the rest of the disk change so I need to change /etc/fstab and /boot/grub/menu.lst too to make sure that my system will still boot?

I need a little help so I don't make any mistakes.

---

### Post by sethmahoney on 2005-09-12
There's probably an easier way to do this, but you can always reinstall Ubuntu after you repartition if things go awry.  One word of advice that I've seen in several other places: Defrag your windows partition before you do any resizing of partitions if you want to keep the data stored there.

---

### Post by lassel on 2005-09-12
I do NOT want to reinstall ubuntu if it fails. I have spent a fair number of hours customizing it for my needs. What a silly suggestion!

I have backups of all important data. I just want to delete the windows partitions.
However I don't have enough space to backup ubuntu so I want to make sure that I don't make any avoidable mistakes.

---

### Post by Carpe Libertatem on 2005-09-12
[QUOTE=lassel]I have just one 160gb disk in my machine.

hda1-3 is windows (120gb)
hda5-7 contains ubuntu (40gb)

I don't need windows anymore and I'd like to reclaim my 120gb for useful data.

Now, I have gparted installed and repartitioning will be a really simple task. I am just worried if it will work after I reboot.

hda1 (windows) is marked as bootable and I assume that this is where grub is installed?

If I delete hda1-3 and make one big new partition I bet that the bootmanager will die.
How can I reinstall it?

In making hda1-3 into one big partition will the partition numbers of the rest of the disk change so I need to change /etc/fstab and /boot/grub/menu.lst too to make sure that my system will still boot?

I need a little help so I don't make any mistakes.[/QUOTE]
 I suggest you download the Ubuntu Live CD, and procede with what you are doing. That way - if you do mess-up, you can go in and correct the problem without too much hassle.

---

### Post by drogoh on 2005-09-12
[QUOTE=lassel]
If I delete hda1-3 and make one big new partition I bet that the bootmanager will die.
How can I reinstall it?

[/QUOTE]

That's easy.  Just do grub-install /dev/hda but yeah, you need a backup so make sure you have your live CD handy.  Oh, don't forget your towel too...

You may want to look into a reinstall in the future since you're dumping those partitions, just a suggestion since it'll be "proper" with a fresh install.  No, it is not a silly thing to suggest.

---

### Post by lassel on 2005-09-13
[QUOTE=drogoh]
You may want to look into a reinstall in the future since you're dumping those partitions, just a suggestion since it'll be "proper" with a fresh install.  No, it is not a silly thing to suggest.[/QUOTE]

Thanks for the grub-install tip.

Please explain why it would be "proper" to reinstall ubuntu just because I dump a couple of windows partitions ??

---

### Post by matthew on 2005-09-13
This should be possible without a reinstall.

One option: use parted (or gparted, or qtparted, etc) to remove the current windows partitions. Then make them all into one big ext3 partition and tell fstab to mount it on /home or as a folder within /home.

Another option *this is the one I would choose: 
Using the method outlined here: [http://www.ubuntuforums.org/showthread.php?t=35087](http://www.ubuntuforums.org/showthread.php?t=35087) make a backup of your ubuntu installation. Then save the archive file to an external medium...on a dvd-r if it will fit or perhaps on an external hard drive. I suppose you could also use a small, made for this purpose partition on your hard drive, though that would add some steps in here. Finally, reformat the whole hard drive as two ext3 partitions, one of about 10-15 Gb for / and another with the rest of the space for /home. Then restore your backup on the newly formatted drive.

Just some thoughts to get the creative juices flowing. You may very likely come up with an even better idea.

---

