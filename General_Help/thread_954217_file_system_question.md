---
title: "file system question"
date: 2008-10-21
forum: General Help
---

### Post by pmooney78 on 2008-10-21
What's a hardlink?

---

### Post by shawnrgr on 2008-10-21
A hard link is essentially a label or name assigned to a file. Conventionally, we think of a file as consisting of a set of information that has a single name. However, it is possible to create a number of different names that all refer to the same contents. Commands executed upon any of these different names will then operate upon the same file contents. 

To make a hard link to an existing file, enter:
  ln oldfile newlink

Replace oldfile with the original filename, and newlink with the additional name you'd like to use to refer to the original file.

This will create a new item in your working directory, newlink, which is linked to the contents of oldfile. The new link will show up along with the rest of your filenames when you list them using the ls command. This new link is not a separate copy of the old file, but rather a different name for exactly the same file contents as the old file. Consequently, any changes you make to oldfile will be visible in newlink. 

You can use the standard Unix rm command to delete a link. After a link has been removed, the file contents will still exist as long as there is one name referencing the file. Thus, if you use the rm command on a filename, and a separate link exists to the same file contents, you have not really deleted the file; you can still access it through the other link. Consequently, hard links can make it difficult to keep track of files. Furthermore, hard links cannot refer to files located on different computers linked by NFS, nor can they refer to directories. For all of these reasons, you should consider using a symbolic link, also known as a soft link, instead of a hard link.

Credit: [http://kb.iu.edu/data/aibc.html](http://kb.iu.edu/data/aibc.html)

---

### Post by pmooney78 on 2008-10-21
How is a symbolic link different?

---

### Post by shawnrgr on 2008-10-21
> **pmooney78 said:**
> How is a symbolic link different?

google google google

[Symbolic link]("http://en.wikipedia.org/wiki/Symbolic_link")

---

### Post by dcstar on 2008-10-21
> **pmooney78 said:**
> How is a symbolic link different?

A hardlink can only exist inside a single filesystem, a symlink can exist across all your mounted filesystems.

---

### Post by pmooney78 on 2008-10-25
I guess I understand the technical distinction decently well now, but I still don't understand why one should be used rather than another (outside of situations where only symbolic links can be used, like across file systems). Is there ever an advantage to using a hard link?

---

### Post by koenn on 2008-10-25
> **pmooney78 said:**
> I guess I understand the technical distinction decently well now, but I still don't understand why one should be used rather than another (outside of situations where only symbolic links can be used, like across file systems). Is there ever an advantage to using a hard link?
in most cases, symlinks and hardlinks will behave the same so there's no real preference.
however, with symlinks, the filesystem is aware that the link is just a link (although most programs will just treat it as a file):
```
k@nix:~$ ls -l file.*
-rw-r--r-- 1 k k  0 2008-10-25 13:04 file.orig2
lrwxrwxrwx 1 k k 10 2008-10-25 13:06 file.softlink -> file.orig2
```
One side effect is that you can delete a file from under its symlink, and the link will point to nothing (or an empty file will be created when you try to edit it)

a hard link can be seen as "the same file existing in two (or more) places", there is no real distinction between the 'link' and the 'original file'
```

k@nix:~$ echo foo > file.orig
k@nix:~$ ln file.orig file.hardlink
k@nix:~$ ls -l file.*
-rw-r--r-- 2 k k  4 2008-10-25 13:15 file.hardlink
-rw-r--r-- 2 k k  4 2008-10-25 13:15 file.orig

k@nix:~$ rm file.orig
k@nix:~$ cat file.hardlink 
foo
k@nix:~$ 

```

it's up to you to decide which behavior is more suitable in the case where you want to appy links. It may affect programs such as cp, rsync, ... which have specific switches to govern the program's behavior in regard to (symbolic) links

---

### Post by pmooney78 on 2008-10-25
Very helpful! Thank you.

---

### Post by sandbox4us on 2008-12-01
I am a newbie... sorry... I was playing with a script to automatically unmount a CIFS drive, and ended up inadvertently creating a few links (not sure if they are hard or symlinks.... i think symlinks) to files in /etc/init.d directory that were were called from the /etc/rc0.d and rc6.d directories.

Long story short, i've ended up with broken link files that i cant remove with the "sudo rm" command.  i see them when i do a "dir" or "ls" command, but they dont wont erase.

How do I remove these broken links?

---

### Post by pmooney78 on 2008-12-05
Yipes. Beats me, that's over my head.

But I can tell you this: You'll get a better reponse from more experienced people if you create a new thread instead of tacking a new question on to the end of an old thread. :) That's what I'd do.

---

