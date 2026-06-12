---
title: "Hard drive failure"
date: 2010-10-03
forum: Hardware
---

### Post by Cadeyrn on 2010-10-03
I've been Googling around and I found many results, but I'm not entirely sure what to do. What happened was the Windows partition of my main hard drive (but not any other partition) and my external EXT2 hard drive both lost half their folders and all their files. It happened in Linux, and must have been caused by the python music program Quodlibet, or Drupal, or MySQL database-editing, or Firefox, or Epiphany, or Linux Mint 9 randomly ****ing up, or a simple hard drive failure, or any of the above.

Using a LiveCD I ran fsck on the external HDD and ntfsfix on the Windows partition. fsck found soooooo many errors, and it mentioned errors with files that I had in there before everything blew up. However, after dropping a few GB of numbered files In the lost+found folder, it did NOT restore any files to their original directories. The problem with that is the drive did not have a few GB of files that are now missing. It had about 400GB. ntfsfix did nothing at all.

After that, I used the Windows install boot disc and ran CHKDSK /p. It "performed additional checking or recovery" but it didn't change anything.

__________________________________________________________________________________________________________________________________________
**So basically**, the tables of contents of one partition and another hard drive have been corrupted. Disk checks found the missing files but did not recover them, and I don't know where to go from here, nor do I know what the lost+found files are or what to do with them.

Here's one more problem: the data recovery techniques that all the tutorials tell me about require a lot of extra storage for things like image files of the disc and output image files (the latter of which is always mandatory); storage I don't have. Is there some way to just recover my files and drop them in the same hard drive? Yes, I know it's risky, and yes I know it's no different from saving someone from a volcano only to drop them in a deep chasm with spikes at the bottom, but it's all I can do for now.

---

### Post by psusi on 2010-10-03
fsck gives the files numbered names because it can't figure out their original name.  You have to manually inspect them and try to figure out what they are.  You also should look at the smart numbers in the disk utility to see if the drive is physically dieing, and if so, stop using it.

---

### Post by Cadeyrn on 2010-10-03
I was going to stop using it anyway, but thanks for giving me a means to find out if it's safe to keep using. However, I don't know which program is the "disk utility." Do you mean GParted? And could I have some tips on how to manually inspect the files?

---

### Post by psusi on 2010-10-03
System -> Administration -> Disk Utility.

---

### Post by Cadeyrn on 2010-10-03
That's odd... gnome-disk-utility wasn't installed. Perhaps not having it is a Linux Mint thing.

Installing it now. Thanks for the tips! And it turns out all those files I lost are easily replacable, so I don't really give a crap about those lost+found files. They'll be gone when I reformat and/or stop using the drive anyway.

---

