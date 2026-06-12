---
title: "caching mechanism"
date: 2008-10-17
forum: General Help
---

### Post by sulekha on 2008-10-17
Hi all,

This is what i have read in a book

Linux uses a caching mechanism for frequently accessed files that speeds the process of locating an inode from a filename. This caching mechanism works only on filenames of up to 30 characters in length, so avoid giving frequently accessed files extremely long filenames.

 how valid is this claim ?
 what is the name of this caching mechanism ?

---

### Post by iponeverything on 2008-10-17
Fun Fun Fun!

Caching is done through VFS. Yes, the claim is real. But how many people exceed 30 char filenames?

File name size is not an issue with 64 bit linux (it essentially doubles). 

Anyway for a truly fascinating read (I am not being sarcastic!) about the VFS interface in 2.6.26 read this --
  
ref: [http://www.mjmwired.net/kernel/Documentation/filesystems/vfs.txt](http://www.mjmwired.net/kernel/Documentation/filesystems/vfs.txt)

---

