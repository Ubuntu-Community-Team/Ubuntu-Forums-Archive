---
title: "[SOLVED] Find data files from previous installation"
date: 2008-09-21
forum: General Help
---

### Post by djb132 on 2008-09-21
Are "orphaned" files recoverable?

I reinstalled ubuntu Hardy server and now I can't figure out how to find/mount/get to the data files I have on another hard drive that wasn't touched by the installation.

ubuntu is on a scsi drive (sda) - I overwrote & reinstalled ubuntu here
I had media/music on a SATA drive (sdb)
and media/files on an EIDE drive (sdc)

After re-installing ubuntu, I executed 
sudo mkdir /media/music
sudo mkdir /media/datastorage

and edited fstab to include
/dev/sdb1 /media/music ntfs defaults 0 0
/dev/sdc1 /media/datastorage ntfs defaults 0 0

the media/files directory is what I'm really concerned about - is there a good non-gui (I've not installed the desktop) way to remount or search for the files in here?

What about media/music?  is that data just plain gone since I remounted the directory with the same name?

Thanks - David

---

### Post by djb132 on 2008-09-21
Solved the problem by rebooting - all the files are now visible there (big sigh of relief)

---

