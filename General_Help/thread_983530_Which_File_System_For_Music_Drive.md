---
title: "Which File System For Music Drive?"
date: 2008-11-15
forum: General Help
---

### Post by jetjaguar on 2008-11-15
I'm going to format my my 250GB NTFS external drive (which I only store mp3s on) to a Linux file system.  Which one would be best for this type of application?

---

### Post by dcstar on 2008-11-15
> **jetjaguar said:**
> I'm going to format my my 250GB NTFS external drive (which I only store mp3s on) to a Linux file system.  Which one would be best for this type of application?

EXT2 probably - you don't really need to use 5% of the space for EXT3 journaling for just storing MP3s.

---

### Post by binbash on 2008-11-15
If it is external, go for ntfs since you may want to mount drive at windows pcs.

---

### Post by Sef on 2008-11-15
> EXT2 probably - you don't really need to use 5% of the space for EXT3 journaling for just storing MP3s.It would be better to go with ext3 instead of ext2.   The journaling is the only difference between ext2 and ext3.  

From [Wikipedia on Journaling]("http://en.wikipedia.org/wiki/Journaling_file_system"):

> A **journaling** **file system** is a [file system]("http://en.wikipedia.org/wiki/File_system") that logs changes to a journal (usually a circular log in a dedicated area) before committing them to the main file system. Such file systems are less likely to become corrupted in the event of power failure or system crash.

---

