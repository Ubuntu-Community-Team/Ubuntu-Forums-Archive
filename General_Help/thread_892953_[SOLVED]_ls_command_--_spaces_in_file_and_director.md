---
title: "[SOLVED] ls command -- spaces in file and directory names"
date: 2008-08-17
forum: General Help
---

### Post by mike2357 on 2008-08-17
I am trying to develop a script which will list all of the files in my home directory and below, ordered by size.  I tried the following:

ls -lRS `find $HOME -type f -print`

The problem is that there are files and directories with spaces in them, and ls treats each word as a different file.  Any ideas?

---

### Post by caljohnsmith on 2008-08-17
I believe all you need to do is put the ls argument in quotes:
```
ls -lRS "`find $HOME -type f -print`"
```

---

### Post by mike2357 on 2008-08-17
I think we're on the right track, but not quite there.  Here's the command and output:

ls -lRS "`find $HOME -type f -print`"
bash: /bin/ls: Argument list too long

---

### Post by Mister.Vash on 2008-08-17
You probably aren't easily going to be able to get around the "Argument list too long" issue as most users home folders do contain a large number of files so you might be better off trying some other method.

You could use something like the following:
```
ls $HOME -alR | sort -k 5 -n
```

Are you looking for the entire list of files, or are you just looking for a summary? One way to do this would be the following
```
du $HOME -h --max-depth=1
```

---

### Post by mike2357 on 2008-08-17
I was looking for an entire list of files, and the command that included "sort" did the trick.

Thanks.

---

