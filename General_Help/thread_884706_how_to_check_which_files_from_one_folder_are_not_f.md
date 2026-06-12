---
title: "how to check which files from one folder are not found in another"
date: 2008-08-09
forum: General Help
---

### Post by starkes on 2008-08-09
Hi,

I'm trying to come up with a script i guess it would most likely be, that will check one source directory against a target directory and tell me which files from the source directory are not found somewhere in the target directory. (and dont have to be in the same place)

I have two music folders, on my desktop and laptop respectively, that i want to merge. But i dont want to copy one over the other because there will be many redundant copies of songs since both music folders are not layed out the same, though they are 90% identical.

has anyone happened to come across just such a thing before i try to make it myself?

---

### Post by pytheas22 on 2008-08-09
[rsync]("http://www.samba.org/ftp/rsync/rsync.html") is a great tool that will automatically look at two directories and sync them by copying over from one what's missing in the other (but not copying what's already there).  To use it, run:
```

rsync -av /dir/one /dir/two
```

That would cause rsync to copy from dir-one into dir-two whatever is in dir-one but not in dir-two.

If you want to do the copying manually, you could generate lists of the files contents, pipe them into text files and compare the files using 'diff':

```
ls /dir/one > dir-one.txt
ls /dir/two > dir-two.txt
diff dir-one.txt dir-two.txt
```

The result would print out differences between the directory listings for the two folders, and then you could copy over the differences manually.  But if it were me, I'd use rsync.

---

