---
title: "[SOLVED] remove hard link to a directory"
date: 2008-07-29
forum: General Help
---

### Post by r.stiltskin on 2008-07-29
I seem to have unintentionally created a hard link to a directory.

Is there any way to remove the hard link without emptying all the files out of the directory?

---

### Post by ibuclaw on 2008-07-29
You cannot create hardlinks to directories, only soft symlinks.

Removing them should do nothing to the original directory, but that said... just to be sure, what is the output and the highlighted colour of it when you type in the following?
```
ls -ld **foldername**
```
replace "foldername" with the name of the link you've created.

Regards
Iain

---

### Post by knightcoder on 2008-07-29
I don't think you can create hard links for directories in Linux/Unix systems.
It messes up the directory hierarchy.

---

### Post by r.stiltskin on 2008-07-29
Sorry, it wasn't a link at all.  It seems I mistakenly made an entire copy of a directory in another directory.

Thanks for your suggestions.

---

### Post by bodhi.zazen on 2008-07-29
A little late, but I suggest you use the command unlink to remove links :twisted:

```
unlink <link>
```

This will prevent you from deleting things :)

---

### Post by r.stiltskin on 2008-07-29
Just to be complete I did some experimenting.  knightcoder is correct --  in a directory 'scrap' I created a directory 'testdir' containing a file 'junkfile'. I tried but was not able to create a hard link to testdir in my home directory (ln scrap/testdir); that attempt gave the error msg "hard link not allowed for directory".

After creating a soft link to testdir in my home directory (ln -s scrap/testdir), I was able to delete t he link simply by using 'rm testdir' (even though the actual testdir directory is non-empty) in my home directory.  This deleted the link without disturbing the actual directory or its contents.  Same goes for 'unlink testdir'.

---

