---
title: "i deleted files??? how to recover them?"
date: 2008-11-27
forum: General Help
---

### Post by elidoperezmd on 2008-11-27
hi guys, thanks for reading. i deleted some files yesterday and after that i emptied the trashcan. Is there any wAy to recover these files in ubuntu? or can i run a file recovery for windows using wubi?

---

### Post by ajgreeny on 2008-11-27
Deleted from windows or ubuntu?  If windows there are several undelete programs available - just google for them.  If ubuntu, I think you have more of a problem as the ext3 journaling file system works totally differently to ntfs or fat32 and undeleting seems to be more or less impossible without what appears to be a huge amount of knowledge and coding expertise.

Do a google on "undelete linux" and I think you will find that you have a problem that may mean you have to take this whole exercise as a reminder to **backup **more often.

---

### Post by brigadoon on 2008-11-27
I just did a quick google search and found this link...

[http://www.stud.tu-ilmenau.de/~mojo/undelete.html](http://www.stud.tu-ilmenau.de/~mojo/undelete.html)

It may or may not help you. I haven't tried it but it sounds like it would do what you need. Good luck.

---

### Post by ajgreeny on 2008-11-27
From other things I have read, I don't think that this ext2 tool will work on ext3 filesystems due to the journaling that the ext3 has enabled.  I did read that you could change the fs from ext3 to ext2 without losing or corrupting the files on it, though I don't know how, and then do the undelete on the ext2 fs.  However, by that time I understand it is too late and the fact that you deleted from the fs while it was ext3 means the files are not easily recoverable.  No doubt a forensic examiner could, but not we ordinary people, as far as I can see.

If, however, the wubi filesystem is ext2 as a result of installing in this way, rather than ext3, you may just be lucky.  Good luck to you whichever is the case; I hope you get them back again.  But don't forget, ** backup, backup, backup!**

---

