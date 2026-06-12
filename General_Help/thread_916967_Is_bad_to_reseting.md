---
title: "Is bad to reseting ?"
date: 2008-09-11
forum: General Help
---

### Post by sowhat12345 on 2008-09-11
Is bab to reseting Ubuntu or the other Linux operation systems ? I know that it is bad to reseting the Mac and Windows when are starting(and closing) or on desktop. It is the same for Linux operation systems ? can you explain why ? 
Thanks...

---

### Post by Titan8990 on 2008-09-11
It is important to all OSes that they are shut down properly. Some will argue that Linux and MACs are less affected by it because of their journaling file systems.

---

### Post by jerome1232 on 2008-09-11
This is bad, but is more or less dependant on the filesystem in use

To improve preformance not all file operations are actually done immediately, it might be cached and still waiting to actually be written to disc. So in the event of a hard reset, y ou can lose data or you can get file corruption if the system was in the middle of writting to disc.

This is why all modern filesystem (ntfs, ext3, jfs, xfs, resierfs, whatever the mac filesystem is called (hpfs+?)) are journeled in one way or another, I don't know the details but after a crash they can go back and replay the file write that was in progress and remedy the file corruption that would've resulted from the hard reset. 

fat32 file systems are not journaled and a very susceptible to file corruption this way.

---

### Post by Vivaldi Gloria on 2008-09-11
The filesystem on a disk may become corrupted if that disk is in use when you reset or power is cut. Different kind of filesystems have different levels of resilience to powercuts. I read a few times that ext3 is better than XFS in this regard. 

If your system becomes unresponsive then before resetting you should try to raise a skinny elephant even if it's utterly boring:

[[COLOR="Sienna"]RSEIUB1[/COLOR]]("http://www.arsgeek.com/2006/12/12/how-to-gracefully-reboot-your-ubuntudebian-system-if-all-else-fails/") - [[COLOR="Sienna"]RSEIUB2[/COLOR]]("http://en.wikipedia.org/wiki/Rseiub")

If you have to reset then use fsck to scan a corrupted ext3 partition.

---

