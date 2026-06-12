---
title: "Rsync: How to avoid copying empty files"
date: 2008-11-07
forum: General Help
---

### Post by jonobr on 2008-11-07
Hello Friends


I use Rsync for backing up files.
I was wondering if there was a way of not copying empty files from the target location-just the files that contain something?

It would be easy to create a script to just remove files with no content before or after copied,
but I really need to leave both sides alone and just ensure that the empty files are not copied


Many thanks!!

---

### Post by cariboo on 2008-11-07
You can use the exclude option, to exclude files you don't want to copy. Have a look here:

[http://articles.slicehost.com/2007/10/10/rsync-exclude-files-and-folders](http://articles.slicehost.com/2007/10/10/rsync-exclude-files-and-folders)

Although I wouldn't worry about the empty files as they will only take up 1k per file of space on the hard drive.

Jim

---

### Post by jonobr on 2008-11-07
THanks a mill cariboo907 , 

The problem is not the size, its my processing at the copied end.
I have a script that processes whats copied, and I cant get it to get over empty files.It just throws a hissy fit

Cheers

):P

---

### Post by jonobr on 2008-11-07
Hi again,


I looked at this and its a good source, it doesn't cover the idea of the empty files, however, what I will do is nose around using the exclude file, (I have not used these before) and 
see what I come up with and post a solution here,

Again thanks!

---

