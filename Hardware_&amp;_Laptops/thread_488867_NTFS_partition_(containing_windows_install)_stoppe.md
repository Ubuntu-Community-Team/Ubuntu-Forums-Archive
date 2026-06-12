---
title: "NTFS partition (containing windows install) stopped mounting properly"
date: 2007-06-30
forum: Hardware &amp; Laptops
---

### Post by Mountaingod on 2007-06-30
Something has gone very wrong with the partition containing my dual-booting Windows XP installation. Originally it worked fine - I'd just started the whole thing over from scratch, using a 4gb  hidden recovery partition included in my HDD.

I converted the hidden partition into recovery discs to free the 4gb - it was given to me in the form of a FAT16 partition. I installed ubuntu by shortening my windows partition and creating an ext3 partition in the freed space, as is standard.

At this point everything is still running fine. Windows and ubuntu both boot from GRUB fine, and ubuntu could 'see' and mount both the empty 4gb partition and my NTFS windows one.

I wanted to encorporate that 4gb free space into my ubuntu partition rather than having it separate, so I deleted it using gparted. My ultimate aim was to shift the two remaining partitions around until I was able to extend the ext3 one into the now unallocated space.

However, at this point something went wrong. gparted told me the NTFS partition would no longer mount and could not be read - I couldn't mount it on the desktop. I can't boot into windows from GRUB anymore too, because it tells me it can't find neccessary DLLs. From the looks of it, I don't think it can even find the windows partition at all.

I tried ntfsfix on it with little success. Nautilus doesn't even give that partition as an option for mounting - gparted has managed to mount it once, but it still didn't show up in the usual places in nautilus - I have to go into /media/HDD to see the contents, and even then I need root privileges. It's reassuring to see the contents are still there though.

I haven't touched that partition. All I did was delete the *empty* 4gb FAT16 partition in front of it. Why won't it mount or boot windows anymore? I've since found the recovery discs I made are defective somehow, so essentially my copy of windows now relies on this partition being recoverable.

EDIT: To be clear, the 4gb partition was the *first* one on the disk (sda1), followed by the NTFS partition (sda2), followed by the ext3 partition (sda3), followed by the linux swap partitions etc. at the end. I'm thinking maybe I've deleted something else besides the 4gb FAT partition itself as it was the first partition on the hard drive. GRUB still works fine though...

---

### Post by Mountaingod on 2007-07-01
OK, the partition will mount if I go into gparted and mount it, but it doesn't show up on the desktop, or *Places > Computer*. I have to navigate to /media/HDD manually to get to it once mounted, and even then I 'don't have the permissions' to access the contents - I can only get to them with root permissions.

So if the files are all still in there and fine, why won't windows XP boot from it? Why won't it show up to be mounted in *Places > Computer*, so I have to do so with gparted or *sudo mount /dev/sda2...*? Most importantly, why won't Windows XP boot from it, instead telling me the relevant dll's (which I *know* are in that partition) are missing?

My deleting the 4gb FAT16 partition in front of it (ie the first partition on the disk) must have done something. I'm guessing deleting that partition with gparted has messed something up which allows for the easy identification and mounting of the succeeding partition - my ntfs windows one. The fact I've **seen** and **know** the contents of that partition are still intact means it can't be a problem with the partition itself - after all, I didn't touch it.

[Here's](http://i182.photobucket.com/albums/x154/MountainGod/Screenshot--dev-sda-GParted.png) a screenshot of gparted, so you can see how my disk is laid out. The 4.1gb at the beginning is the gap left by the FAT16 partition I deleted. The next one, seemingly mounted fine (but not) is the NTFS partition I'm talking about. The last one is Ubuntu's partition, and after that the linux swap partition.

Any help would be appreciated.

---

### Post by Arrdee on 2007-07-01
Oy. From my *limited* (and I'll stress that) experience, I'll say the following:

 I'm inclined to think it may not have been wise to wipe out that 4GB partition. Possibly a messed-up partition table/GRUB now? What kind of computer is this? Also, before you wiped it out, was the first partition (a.k.a. sda1) flagged as boot or anything else?

Since your Windows partition is NTFS, I know if the last time you were in Windows and you shut down improperly, or if the partition is otherwise labeled "unclean" (if I recall the term correctly), you won't be able to mount it regularly. 

Wasn't able to help much, maybe someone will come along that knows a lot more than I do.

---

### Post by Mountaingod on 2007-07-02
I'm making slow progress with this. That 4gb partition was indeed the first one, and as it used to be a recovery partition it would (a long time ago, before I emptied its contents into CD-Rs) have been bootable. I don't think the NTFS partition was 'dirty' to start with; it is now though because I ran ntfsfix on it. Again, force-mounting it and then using nautilus with admin privileges to access it shows the contents themselves to be fine. As far as I can tell.

It's a laptop, and there are 2 identical ones in the house that we bought at the same time. Last night I copied the (still untouched) 4gb recovery partition from one of them, using the Trinity Rescue Kit and the 'dd' command. I'll fill the unnallocated space on my hard drive with their recovery partition, and see if that remedies things.

If not, I've cloned their entire hard disk too, which I'll just place on my computer and then restore the whole thing to factory default with their data. One way or another, it'll sort out.

EDIT: OK, I've sorted it all out. All I needed to do was make a *new* FAT partition in the unallocated space. This meant the next partition, my NTFS one with windows installed, showed up fine and windows booted normally. Still leaves me with an unwanted extra FAT partition, but at least windows is going again. And I learnt how to use the Trinity Rescue Kit, even though I didn't need it in the end.

---

### Post by Arrdee on 2007-07-08
If you're still interested, I did something *very* similar to your situation with my own laptop, and all I had to do was edit Window's boot.ini to redirect it to the first partition on the hard drive, rather than the second. Worked like a charm, and Windows boots fine!

---

### Post by Mountaingod on 2007-07-12
That's interesting, thanks. I might end up encorporating that partition into the wider linux one after all!

---

