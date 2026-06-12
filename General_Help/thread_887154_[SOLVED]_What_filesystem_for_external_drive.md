---
title: "[SOLVED] What filesystem for external drive?"
date: 2008-08-11
forum: General Help
---

### Post by robert shearer on 2008-08-11
Our local store had W/D external usb 250 gig hard drives cheaper than a single 250 gig internal drive, so I bought one and took the hard drive out and put it into my Ubuntubox.

Now I've been given a W/D 20 gig hard drive that is annoyingly noisey but otherwise ok.

I've put this into the usb case and it is recognised and can be browsed when I connect it.

I going to wipe and reformatt it (currently has winxp/ntfs) and need to know what filesystem to use?.

Would like to be able to read and write to it with Linux and Windows and will be using as a temporary store/transfer method for mostly audio files.

I believe that usb 'memory sticks' are fat16 for universal use ?

Yes,I should have checked the filesystem on the drive I took out.

Any suggestions ?

---

### Post by sillyxone on 2008-08-11
NTFS can be read/written in Ubuntu but I think FAT32 is the safest choice. Both Windows and Ubuntu (and OSX) can read/write to it reliably.

Edit: I just remember slightly from about 10 years ago where FAT16 was used in Windows 95/98, it was limited to 2GB, and also had problem with fragmentation. So, don't use FAT16, use FAT32 instead.

---

### Post by cybrsaylr on 2008-08-11
I've been using NTFS on my ext HDD for months now and have no problems playing audio mp3 files with Ubuntu and even dragging them back and forth between the ext HDD and the Ubuntu partition. The same goes for moving audio files back and forth between Ubuntu and a Vista partition on my dual boot system.

---

### Post by djrobthaman on 2008-08-11
Fat32 is universally readable (win/mac/linux) which is good, but there are a few limitations.

1.  You can't store files larger than 4 GB (or something around that).  May not be an issue, but you never know.

2.  You can't format a drive larger than 32 GB using Windows XP as fat 32 (not sure if they lightened up on vista).  You'd have to do it in linux.

Also, a little bit of light googling has led me to believe that ntfs-3g (the same driver that's made it possible to read/write to ntfs with linux for so long) is available fo mac osx.  So, looks like ntfs isn't that big of a deal for a mac.

I'd go with ntfs.

---

