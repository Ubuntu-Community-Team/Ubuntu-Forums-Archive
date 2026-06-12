---
title: "How man soft/hard links?"
date: 2008-09-28
forum: General Help
---

### Post by clarkhuke on 2008-09-28
Is there a terminal command to determine how many soft/hard links point to a file?

Thanks.

---

### Post by mb_webguy on 2008-09-28
Try this:```
sudo ls -lR / | grep "> /path/to/dir"
```
The -l option of ls gives the long listing, which shows the target of links.  The -R option makes it recursive.  Running it through grep checks for any instances of the directory path preceded by "> ", which would indicate a link.

Note that this will also grab any links to subdirectories of the specified directory.  You could use a regular expression to only catch strings ending with the directory path if you want, but the above command will get the job done...

---

### Post by taladan on 2008-09-28
ls -l filename | cut -d" "  -f2

It doesn't discriminate between types of links, just how many links there are to that file.

Tal

---

