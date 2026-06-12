---
title: "exFAT troubles"
date: 2014-06-27
forum: Hardware
---

### Post by SpindizZzy on 2014-06-27
Hi there,

One of my external HD's is formatted to exFAT (it's a WD, 1 TB) because I move files around a lot between Ubuntu, Mac and Windows. It seemed a good choice at the time.

However, apparently Macs 'eat' exFAT bootsectors for breakfast and this recently also happened to mine. By using CGSecurity's fantastic tool Testdisk ([http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)) I was able to find out that the Volume Boot Record has been overwritten with zeroes :mad: As always, the files on this HD are important and I have been too lazy to backup everything :(

Question: Is there a tool (for linux) that can repair exFAT VBR's ? I could obviously download and install the similar fsck_exfat on a Mac, but I was wondering if Ubuntu could fix this for me. I just happen to like Linux better :D

Thanks, esteemed panel

---

### Post by sp40140 on 2014-06-29
I think you should post this question to windows forums. exFat is modified version of FAT which MS specifically designed for high capacity flash cards. 
History aside, exFat doesn't work well with any non-MS stuff.
For futuer, you are better off with NTFS.
But to recover the data, you better check on windows / MS forums.

Cheers,

---

### Post by SpindizZzy on 2014-06-30
And I did exactly that. Sort of :p

I also posted here: [http://forum.hddguru.com/viewtopic.php?f=1&t=28938&p=199651#p199651](http://forum.hddguru.com/viewtopic.php?f=1&t=28938&p=199651#p199651) and got my problem solved.

Basically I let Testdisk run an analysis again, then I overwrote the VBR with the backup Superblock, and all of a sudden I could access my data again (through Testdisk). Copied everything to a different HD and reformatted this one...

---

### Post by sp40140 on 2014-06-30
Good for you man!
Could you mark this thread closed?


Cheers,

---

### Post by kurt18947 on 2014-06-30
For future reference, there are exfat tools in the repository, exfat-utils & exfat-fuse.  I installed them once some time ago and they read and wrote an exfat formatted flash drive.  I uninstalled, didn't do anything beyond establishing I could read and write between Windows and Ubuntu.  For large drives, how about formatting NTFS?  That seems to work pretty well.

---

