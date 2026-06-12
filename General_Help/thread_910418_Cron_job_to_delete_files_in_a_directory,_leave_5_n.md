---
title: "Cron job to delete files in a directory, leave 5 newest?"
date: 2008-09-04
forum: General Help
---

### Post by beelerspace on 2008-09-04
I've done some serious searching here on the forums and on the web, but I can't figure out how to generate a script that recursively goes through directories and deletes all files in each directory EXCEPT for the 5 newest. Is this possible?

Thanks so much!

---

### Post by bingoUV on 2008-09-04
Yes it is possible. You will find people doing it for you in less than $10 for sure. If you want to do it yourself, at least 2 approaches

1. cron job is a bad idea, but you want it this way so:
```

man cron
man find
man ls (emphasis on -t)
man head
man tail

```

2. much better performance, with lower resource consumption, but no cron. Creation of a file would trigger the code. Install inotify-tools from repositories. 
```

man inotifywait (see -e CREATE)
man ls
man head
man tail

```

---

### Post by Cheesehead on 2008-09-04
You could use 'ls -ltc' to generate a the file listing in order of last-modified,
then loop through lines 6 through the end,
awk each line to get the filename,
then mv each file to the trash.

---

